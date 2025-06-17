# Diagramas del Sistema - Centro Integral Alerce

Este documento contiene los diagramas técnicos del Sistema de Agendamiento del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## 1. Arquitectura General del Sistema

```mermaid
graph TB
    subgraph "Frontend (Separado)"
        A[Usuario] --> B[Next.js/Nuxt/Angular]
        B --> C[FullCalendar]
        B --> D[Componentes UI]
        B --> E[Axios/Fetch]
    end

    subgraph "Backend (Separado)"
        F[API Express] --> G[JWT Auth]
        F --> H[Multer Files]
        F --> I[Resend Email]
        F --> J[Prisma ORM]
    end

    subgraph "Base de Datos"
        K[MySQL 8.0+]
        K --> L[11 Tablas]
        K --> M[Permisos Granulares]
    end

    subgraph "Almacenamiento"
        N[File System]
        N --> O[Archivos Adjuntos]
    end

    E -->|HTTPS/CORS| F
    J --> K
    H --> N

    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style F fill:#e8f5e8
    style K fill:#fff3e0
```

**Descripción**: Arquitectura de microservicios con frontend y backend completamente separados, comunicándose vía API REST con autenticación JWT.

## 2. Modelo de Base de Datos (Entidad-Relación)

```mermaid
erDiagram
    usuarios {
        int id PK
        varchar nombre
        varchar email UK
        varchar password
        timestamp fecha_creacion
        timestamp ultimo_acceso
    }

    permisos_usuario {
        int id PK
        int usuario_id FK
        varchar permiso
        timestamp fecha_asignacion
        int asignado_por FK
    }

    actividades {
        int id PK
        varchar nombre
        text descripcion
        int tipo_actividad_id FK
        enum periodicidad
        date fecha_inicio
        date fecha_fin
        int cupo
        int usuario_creador FK
        enum estado
        text motivo_cancelacion
        timestamp fecha_creacion
    }

    citas {
        int id PK
        int actividad_id FK
        int lugar_id FK
        date fecha
        time hora_inicio
        time hora_fin
        enum estado
    }

    tipos_actividad {
        int id PK
        varchar nombre
        text descripcion
        boolean activo
    }

    lugares {
        int id PK
        varchar nombre
        int cupo
        boolean activo
    }

    usuarios ||--o{ permisos_usuario : tiene
    usuarios ||--o{ actividades : crea
    actividades ||--o{ citas : genera
    tipos_actividad ||--o{ actividades : clasifica
    lugares ||--o{ citas : ubicacion
```

**Descripción**: Modelo relacional con sistema de permisos granular por usuario, sin roles predefinidos. Actividades pueden generar múltiples citas según periodicidad.

## 3. Flujo de Autenticación

```mermaid
sequenceDiagram
    participant U as Usuario
    participant F as Frontend
    participant A as API Backend
    participant DB as MySQL/Prisma
    participant R as Resend

    Note over U,R: Flujo de Autenticación
    U->>F: Ingresa credenciales
    F->>A: POST /auth/login
    A->>DB: Verificar usuario
    DB-->>A: Datos usuario
    A->>A: Generar JWT
    A-->>F: Token + datos usuario
    F->>F: Guardar token
    F-->>U: Redireccionar a calendario

    Note over U,R: Flujo de Recuperación
    U->>F: Solicita recuperación
    F->>A: POST /auth/forgot-password
    A->>DB: Verificar email
    A->>R: Enviar correo
    R-->>A: Confirmación envío
    A-->>F: "Correo enviado"
    F-->>U: Mostrar mensaje
```

**Descripción**: Autenticación JWT con recuperación de contraseña vía Resend. Tokens almacenados en frontend para sesiones persistentes.

## 4. Flujo de Creación de Actividades

```mermaid
sequenceDiagram
    participant U as Usuario
    participant F as Frontend
    participant A as API Backend
    participant DB as MySQL/Prisma

    Note over U,DB: Crear Actividad Periódica
    U->>F: Completa formulario
    F->>F: Validación frontend
    F->>A: POST /activities
    A->>A: Validar permisos
    A->>A: Validar datos
    A->>DB: Verificar conflictos
    DB-->>A: Sin conflictos

    A->>DB: Crear actividad
    DB-->>A: ID actividad

    loop Para cada fecha en periodo
        A->>DB: Crear cita
        DB-->>A: Cita creada
    end

    A-->>F: Actividad + citas creadas
    F-->>U: Mensaje éxito + redirección
```

**Descripción**: Proceso de creación con validación de permisos, conflictos de horario y generación automática de citas para actividades periódicas.

## 5. Flujo de Navegación del Sistema

```mermaid
graph TD
    A[Sistema Iniciado] --> B{Usuario Autenticado?}
    B -->|No| C[Pantalla Login]
    B -->|Sí| D[Vista Calendario]

    C --> E{Credenciales Válidas?}
    E -->|No| F[Mostrar Error]
    F --> C
    E -->|Sí| G[Generar JWT]
    G --> D

    C --> H[Recuperar Contraseña]
    H --> I[Enviar Email]
    I --> C

    D --> J[Ver Actividad]
    D --> K[Crear Actividad]
    D --> L[Filtrar Calendario]
    D --> M[Cambiar Vista]

    J --> N{Tiene Permisos?}
    N -->|Sí| O[Mostrar Opciones]
    N -->|No| P[Solo Lectura]

    O --> Q[Modificar]
    O --> R[Cancelar]
    O --> S[Reagendar]

    K --> T{Validación OK?}
    T -->|No| U[Mostrar Errores]
    T -->|Sí| V[Guardar en BD]
    V --> D

    style C fill:#ffebee
    style D fill:#e8f5e8
    style G fill:#fff3e0
```

**Descripción**: Flujo principal de navegación con control de permisos y validaciones en cada etapa del proceso.

## 6. Sistema de Permisos Granulares

```mermaid
graph LR
    subgraph "Permisos de Visualización"
        A[ver_calendario]
    end

    subgraph "Permisos de Actividades"
        B[crear_actividad_propia]
        C[crear_actividad_cualquier]
        D[editar_actividad_propia]
        E[editar_actividad_cualquier]
        F[cancelar_actividad_propia]
        G[cancelar_actividad_cualquier]
        H[reagendar_actividad]
    end

    subgraph "Permisos Administrativos"
        I[gestionar_usuarios]
        J[gestionar_permisos]
        K[gestionar_mantenedores]
    end

    subgraph "Permisos de Sistema"
        L[generar_reportes]
        M[subir_archivos]
    end

    Usuario --> A
    A --> B
    B --> D
    D --> F

    B --> C
    C --> E
    E --> G

    style A fill:#e3f2fd
    style I fill:#fce4ec
    style L fill:#f3e5f5
```

**Descripción**: Sistema de 13 permisos granulares que se asignan individualmente a cada usuario, sin roles predefinidos.

## 7. Arquitectura de Despliegue

```mermaid
graph TB
    subgraph "Producción"
        subgraph "Frontend Service"
            A[Vercel/Netlify]
            A --> B[Next.js/Nuxt/Angular]
        end

        subgraph "Backend Service"
            C[Railway/Heroku]
            C --> D[Node.js + Express]
            D --> E[Prisma ORM]
        end

        subgraph "Database Service"
            F[PlanetScale/AWS RDS]
            F --> G[MySQL 8.0+]
        end

        subgraph "File Storage"
            H[File System/S3]
        end

        subgraph "Email Service"
            I[Resend]
        end
    end

    B -->|HTTPS API Calls| D
    E --> G
    D --> H
    D --> I

    style A fill:#e8f5e8
    style C fill:#fff3e0
    style F fill:#e3f2fd
```

**Descripción**: Arquitectura de despliegue en servicios separados con comunicación HTTPS y configuración CORS adecuada.

## Consideraciones Técnicas

### Escalabilidad

- **Frontend**: CDN global para carga rápida
- **Backend**: Auto-scaling basado en demanda
- **Base de Datos**: Conexiones optimizadas con pooling
- **Archivos**: Almacenamiento distribuido

### Seguridad

- **HTTPS**: Obligatorio en todas las comunicaciones
- **JWT**: Tokens con expiración configurable
- **CORS**: Configurado para dominios específicos
- **Validación**: Frontend y backend en todas las entradas

### Monitoreo

- **Logs**: Centralizados para análisis
- **Métricas**: Performance y uso del sistema
- **Alertas**: Notificaciones de errores críticos
- **Backup**: Respaldos automáticos de BD

---

**Nota**: Estos diagramas reflejan la arquitectura final del sistema según las especificaciones técnicas definidas.
