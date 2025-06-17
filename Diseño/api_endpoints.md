# Documentación de la API REST - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

Este documento describe los endpoints disponibles en la API REST para el Sistema de Agendamiento del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## Base URL

```
http://api.centro-alerce.cl/v1
```

Para desarrollo local:

```
http://localhost:3000/api/v1
```

## Autenticación

La API utiliza autenticación basada en JWT (JSON Web Tokens).

Para acceder a los endpoints protegidos, es necesario incluir el token en el encabezado de autorización:

```
Authorization: Bearer <token>
```

### Endpoints de Autenticación

#### Login

```
POST /auth/login
```

**Body:**

```json
{
  "email": "usuario@ejemplo.com",
  "password": "contraseña"
}
```

**Respuesta (200 OK):**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "usuario": {
    "id": 1,
    "nombre": "Nombre Usuario",
    "email": "usuario@ejemplo.com",
    "rol": "admin"
  }
}
```

#### Recuperar Contraseña

```
POST /auth/recuperar-password
```

**Body:**

```json
{
  "email": "usuario@ejemplo.com"
}
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Se ha enviado un correo electrónico con instrucciones para restablecer la contraseña"
}
```

#### Restablecer Contraseña

```
POST /auth/restablecer-password
```

**Body:**

```json
{
  "token": "token-de-recuperacion",
  "password": "nueva-contraseña"
}
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Contraseña restablecida con éxito"
}
```

#### Registro de Usuario

```
POST /auth/register
```

**Body:**

```json
{
  "nombre": "Nuevo Usuario",
  "email": "usuario@ejemplo.com",
  "password": "contraseña"
}
```

**Respuesta (201 Created):**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "usuario": {
    "id": 25,
    "nombre": "Nuevo Usuario",
    "email": "usuario@ejemplo.com",
    "permisos": ["ver_calendario", "crear_actividad_propia"]
  }
}
```

**Errores comunes:**

- **400 Bad Request**: Campos faltantes o inválidos
- **409 Conflict**: Email ya registrado

## Usuarios

### Obtener Usuarios

```
GET /usuarios
```

**Parámetros de consulta:**

- `page`: Número de página (por defecto: 1)
- `limit`: Límite de resultados por página (por defecto: 10)

**Respuesta (200 OK):**

```json
{
  "total": 25,
  "pagina": 1,
  "limite": 10,
  "usuarios": [
    {
      "id": 1,
      "nombre": "Usuario 1",
      "email": "usuario1@ejemplo.com",
      "rol": "admin"
    }
    // ...
  ]
}
```

### Obtener Usuario por ID

```
GET /usuarios/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Usuario 1",
  "email": "usuario1@ejemplo.com",
  "rol": "admin",
  "fecha_creacion": "2024-01-01T12:00:00Z",
  "ultimo_acceso": "2024-01-10T14:30:00Z"
}
```

### Crear Usuario

```
POST /usuarios
```

**Body:**

```json
{
  "nombre": "Nuevo Usuario",
  "email": "nuevo@ejemplo.com",
  "password": "contraseña",
  "rol": "operador"
}
```

**Respuesta (201 Created):**

```json
{
  "id": 26,
  "nombre": "Nuevo Usuario",
  "email": "nuevo@ejemplo.com",
  "rol": "operador"
}
```

### Actualizar Usuario

```
PUT /usuarios/:id
```

**Body:**

```json
{
  "nombre": "Usuario Actualizado",
  "rol": "admin"
}
```

**Respuesta (200 OK):**

```json
{
  "id": 26,
  "nombre": "Usuario Actualizado",
  "email": "nuevo@ejemplo.com",
  "rol": "admin"
}
```

### Eliminar Usuario

```
DELETE /usuarios/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Usuario eliminado con éxito"
}
```

## Tipos de Actividad

### Obtener Tipos de Actividad

```
GET /tipos-actividad
```

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "nombre": "Capacitación",
    "descripcion": "Actividad formativa para desarrollo de habilidades"
  }
  // ...
]
```

### Obtener Tipo de Actividad por ID

```
GET /tipos-actividad/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Capacitación",
  "descripcion": "Actividad formativa para desarrollo de habilidades"
}
```

### Crear Tipo de Actividad

```
POST /tipos-actividad
```

**Body:**

```json
{
  "nombre": "Nuevo Tipo",
  "descripcion": "Descripción del nuevo tipo de actividad"
}
```

**Respuesta (201 Created):**

```json
{
  "id": 10,
  "nombre": "Nuevo Tipo",
  "descripcion": "Descripción del nuevo tipo de actividad"
}
```

### Actualizar Tipo de Actividad

```
PUT /tipos-actividad/:id
```

**Body:**

```json
{
  "nombre": "Tipo Actualizado",
  "descripcion": "Descripción actualizada"
}
```

**Respuesta (200 OK):**

```json
{
  "id": 10,
  "nombre": "Tipo Actualizado",
  "descripcion": "Descripción actualizada"
}
```

### Eliminar Tipo de Actividad

```
DELETE /tipos-actividad/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Tipo de actividad eliminado con éxito"
}
```

## Lugares

### Obtener Lugares

```
GET /lugares
```

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "nombre": "Oficina del centro",
    "cupo": 20,
    "activo": true
  }
  // ...
]
```

### Obtener Lugar por ID

```
GET /lugares/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Oficina del centro",
  "cupo": 20,
  "activo": true
}
```

### Crear Lugar

```
POST /lugares
```

**Body:**

```json
{
  "nombre": "Nuevo Lugar",
  "cupo": 15,
  "activo": true
}
```

**Respuesta (201 Created):**

```json
{
  "id": 5,
  "nombre": "Nuevo Lugar",
  "cupo": 15,
  "activo": true
}
```

### Actualizar Lugar

```
PUT /lugares/:id
```

**Body:**

```json
{
  "nombre": "Lugar Actualizado",
  "cupo": 25
}
```

**Respuesta (200 OK):**

```json
{
  "id": 5,
  "nombre": "Lugar Actualizado",
  "cupo": 25,
  "activo": true
}
```

### Eliminar Lugar

```
DELETE /lugares/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Lugar eliminado con éxito"
}
```

## Oferentes

### Obtener Oferentes

```
GET /oferentes
```

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "nombre": "Carrera de Enfermería",
    "docente_responsable": "Juan Pérez",
    "activo": true
  }
  // ...
]
```

### Obtener Oferente por ID

```
GET /oferentes/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Carrera de Enfermería",
  "docente_responsable": "Juan Pérez",
  "activo": true
}
```

### Crear Oferente

```
POST /oferentes
```

**Body:**

```json
{
  "nombre": "Nuevo Oferente",
  "docente_responsable": "María González",
  "activo": true
}
```

**Respuesta (201 Created):**

```json
{
  "id": 8,
  "nombre": "Nuevo Oferente",
  "docente_responsable": "María González",
  "activo": true
}
```

### Actualizar Oferente

```
PUT /oferentes/:id
```

**Body:**

```json
{
  "docente_responsable": "Pedro Sánchez"
}
```

**Respuesta (200 OK):**

```json
{
  "id": 8,
  "nombre": "Nuevo Oferente",
  "docente_responsable": "Pedro Sánchez",
  "activo": true
}
```

### Eliminar Oferente

```
DELETE /oferentes/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Oferente eliminado con éxito"
}
```

## Socios Comunitarios

### Obtener Socios Comunitarios

```
GET /socios-comunitarios
```

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "nombre": "Junta de Vecinos Alerce Sur",
    "activo": true
  }
  // ...
]
```

### Obtener Socio Comunitario por ID

```
GET /socios-comunitarios/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Junta de Vecinos Alerce Sur",
  "activo": true
}
```

### Crear Socio Comunitario

```
POST /socios-comunitarios
```

**Body:**

```json
{
  "nombre": "Nuevo Socio Comunitario",
  "activo": true
}
```

**Respuesta (201 Created):**

```json
{
  "id": 6,
  "nombre": "Nuevo Socio Comunitario",
  "activo": true
}
```

### Actualizar Socio Comunitario

```
PUT /socios-comunitarios/:id
```

**Body:**

```json
{
  "nombre": "Socio Actualizado"
}
```

**Respuesta (200 OK):**

```json
{
  "id": 6,
  "nombre": "Socio Actualizado",
  "activo": true
}
```

### Eliminar Socio Comunitario

```
DELETE /socios-comunitarios/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Socio comunitario eliminado con éxito"
}
```

## Beneficiarios

(Endpoints similares a Socios Comunitarios)

## Proyectos

(Endpoints similares a los anteriores)

## Actividades

### Obtener Actividades

```
GET /actividades
```

**Parámetros de consulta:**

- `page`: Número de página (por defecto: 1)
- `limit`: Límite de resultados por página (por defecto: 10)
- `estado`: Filtrar por estado (opcional: "Programada", "Cancelada", "Completada")
- `fecha_inicio`: Filtrar desde fecha (opcional, formato: YYYY-MM-DD)
- `fecha_fin`: Filtrar hasta fecha (opcional, formato: YYYY-MM-DD)
- `tipo_actividad_id`: Filtrar por tipo de actividad (opcional)

**Respuesta (200 OK):**

```json
{
  "total": 42,
  "pagina": 1,
  "limite": 10,
  "actividades": [
    {
      "id": 1,
      "nombre": "Taller de primeros auxilios",
      "tipo_actividad": {
        "id": 2,
        "nombre": "Taller"
      },
      "periodicidad": "Puntual",
      "fecha_inicio": "2024-08-15",
      "estado": "Programada"
    }
    // ...
  ]
}
```

### Obtener Actividad por ID

```
GET /actividades/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "nombre": "Taller de primeros auxilios",
  "tipo_actividad": {
    "id": 2,
    "nombre": "Taller"
  },
  "periodicidad": "Puntual",
  "fecha_inicio": "2024-08-15",
  "fecha_fin": null,
  "cupo": 20,
  "socio_comunitario": {
    "id": 1,
    "nombre": "Junta de Vecinos Alerce Sur"
  },
  "proyecto": null,
  "estado": "Programada",
  "fecha_creacion": "2024-07-01T10:00:00Z",
  "creado_por": {
    "id": 1,
    "nombre": "Administrador"
  },
  "oferentes": [
    {
      "id": 1,
      "nombre": "Carrera de Enfermería"
    }
  ],
  "beneficiarios": [
    {
      "id": 3,
      "caracterizacion": "Adultos mayores"
    }
  ],
  "citas": [
    {
      "id": 1,
      "fecha": "2024-08-15",
      "hora_inicio": "10:00",
      "hora_fin": "12:00",
      "lugar": {
        "id": 1,
        "nombre": "Oficina del centro"
      },
      "estado": "Programada"
    }
  ],
  "archivos": [
    {
      "id": 1,
      "nombre": "programa_taller.pdf",
      "tipo": "application/pdf",
      "fecha_carga": "2024-07-01T10:05:00Z"
    }
  ]
}
```

### Crear Actividad

```
POST /actividades
```

**Body:**

```json
{
  "nombre": "Nueva Actividad",
  "tipo_actividad_id": 2,
  "periodicidad": "Puntual",
  "fecha_inicio": "2024-03-20",
  "fecha_fin": null,
  "cupo": 25,
  "oferentes": [1, 3],
  "socio_comunitario_id": 2,
  "beneficiarios": [1, 2],
  "proyecto_id": 1
}
```

**Respuesta (201 Created):**

```json
{
  "id": 43,
  "nombre": "Nueva Actividad",
  "mensaje": "Actividad creada con éxito"
}
```

### Actualizar Actividad

```
PUT /actividades/:id
```

**Body:**

```json
{
  "nombre": "Actividad Actualizada",
  "cupo": 20
}
```

**Respuesta (200 OK):**

```json
{
  "id": 43,
  "nombre": "Actividad Actualizada",
  "mensaje": "Actividad actualizada con éxito"
}
```

### Cancelar Actividad

```
POST /actividades/:id/cancelar
```

**Body:**

```json
{
  "motivo_cancelacion": "Falta de asistentes confirmados"
}
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Actividad cancelada con éxito"
}
```

## Citas

### Obtener Citas

```
GET /citas
```

**Parámetros de consulta:**

- `fecha_inicio`: Filtrar desde fecha (opcional, formato: YYYY-MM-DD)
- `fecha_fin`: Filtrar hasta fecha (opcional, formato: YYYY-MM-DD)
- `actividad_id`: Filtrar por actividad (opcional)
- `lugar_id`: Filtrar por lugar (opcional)
- `estado`: Filtrar por estado (opcional: "Programada", "Cancelada", "Completada")

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "actividad": {
      "id": 1,
      "nombre": "Taller de primeros auxilios"
    },
    "lugar": {
      "id": 1,
      "nombre": "Oficina del centro"
    },
    "fecha": "2024-08-15",
    "hora_inicio": "10:00",
    "hora_fin": "12:00",
    "estado": "Programada"
  }
  // ...
]
```

### Obtener Citas por Semana

```
GET /citas/semana
```

**Parámetros de consulta:**

- `fecha`: Fecha de la semana (formato: YYYY-MM-DD)

**Respuesta (200 OK):**

```json
{
  "semana": {
    "inicio": "2024-08-12",
    "fin": "2024-08-18"
  },
  "citas": [
    {
      "id": 1,
      "actividad": {
        "id": 1,
        "nombre": "Taller de primeros auxilios"
      },
      "lugar": {
        "id": 1,
        "nombre": "Oficina del centro"
      },
      "fecha": "2024-08-15",
      "hora_inicio": "10:00",
      "hora_fin": "12:00",
      "estado": "Programada"
    }
    // ...
  ]
}
```

### Obtener Cita por ID

```
GET /citas/:id
```

**Respuesta (200 OK):**

```json
{
  "id": 1,
  "actividad": {
    "id": 1,
    "nombre": "Taller de primeros auxilios"
  },
  "lugar": {
    "id": 1,
    "nombre": "Oficina del centro"
  },
  "fecha": "2024-08-15",
  "hora_inicio": "10:00",
  "hora_fin": "12:00",
  "estado": "Programada",
  "motivo_cancelacion": null,
  "fecha_creacion": "2024-07-01T10:00:00Z",
  "creado_por": {
    "id": 1,
    "nombre": "Administrador"
  }
}
```

### Reagendar Cita

```
POST /citas/:id/reagendar
```

**Body:**

```json
{
  "fecha": "2024-08-20",
  "hora_inicio": "15:00",
  "hora_fin": "17:00",
  "lugar_id": 2,
  "motivo": "Conflicto con otra actividad"
}
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Cita reagendada con éxito",
  "cita": {
    "id": 1,
    "fecha": "2024-08-20",
    "hora_inicio": "15:00",
    "hora_fin": "17:00",
    "lugar": {
      "id": 2,
      "nombre": "Sala de reuniones"
    }
  }
}
```

### Cancelar Cita

```
POST /citas/:id/cancelar
```

**Body:**

```json
{
  "motivo_cancelacion": "Docente no disponible"
}
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Cita cancelada con éxito"
}
```

## Archivos

### Subir Archivo

```
POST /archivos
```

**Form-data:**

- `archivo`: El archivo a subir
- `actividad_id`: ID de la actividad relacionada
- `tipo_adjunto`: Tipo de adjunto (documento, comunicación, etc.)
- `descripcion`: Descripción del archivo (opcional)

**Respuesta (201 Created):**

```json
{
  "id": 10,
  "nombre": "documento.pdf",
  "tipo": "application/pdf",
  "tamano": 154321,
  "url": "/uploads/actividades/1/documento.pdf",
  "mensaje": "Archivo subido con éxito"
}
```

### Obtener Archivos por Actividad

```
GET /actividades/:id/archivos
```

**Respuesta (200 OK):**

```json
[
  {
    "id": 1,
    "nombre": "programa_taller.pdf",
    "tipo": "application/pdf",
    "tamano": 245678,
    "url": "/uploads/actividades/1/programa_taller.pdf",
    "tipo_adjunto": "documento",
    "descripcion": "Programa del taller",
    "fecha_carga": "2024-07-01T10:05:00Z",
    "cargado_por": {
      "id": 1,
      "nombre": "Administrador"
    }
  }
  // ...
]
```

### Descargar Archivo

```
GET /archivos/:id/descargar
```

**Respuesta:** El archivo se descarga directamente

### Eliminar Archivo

```
DELETE /archivos/:id
```

**Respuesta (200 OK):**

```json
{
  "mensaje": "Archivo eliminado con éxito"
}
```

## Alertas

### Obtener Alertas del Día

```
GET /alertas
```

**Respuesta (200 OK):**

```json
[
  {
    "cita_id": 5,
    "actividad_id": 3,
    "actividad": "Charla de nutrición",
    "tipo_actividad": "Charla",
    "lugar": "Auditorio",
    "fecha": "2024-07-15",
    "hora_inicio": "14:00",
    "socio_comunitario": "Centro de adultos mayores"
  }
  // ...
]
```

## Códigos de Error

La API utiliza los siguientes códigos de estado HTTP:

- `200 OK`: La solicitud se completó con éxito
- `201 Created`: El recurso se creó con éxito
- `400 Bad Request`: Solicitud incorrecta (datos inválidos)
- `401 Unauthorized`: No autenticado o token expirado
- `403 Forbidden`: No tiene permisos para acceder al recurso
- `404 Not Found`: El recurso no existe
- `409 Conflict`: Conflicto al intentar crear/actualizar (ej. nombre duplicado)
- `422 Unprocessable Entity`: La solicitud es correcta pero no se puede procesar (ej. regla de negocio violada)
- `500 Internal Server Error`: Error del servidor

Ejemplo de respuesta de error:

```json
{
  "error": "Validación fallida",
  "detalles": {
    "nombre": "El nombre es obligatorio",
    "fecha_inicio": "La fecha debe ser posterior a hoy"
  }
}
```

## Notas Adicionales

- Todos los endpoints que requieren autenticación deben incluir el token JWT en el encabezado de autorización.
- Las fechas se manejan en formato ISO 8601 (YYYY-MM-DD).
- Las horas se manejan en formato 24 horas (HH:MM).
- Para endpoints que retornan listas extensas, se recomienda utilizar paginación.
