# Requerimientos del Sistema de Agendamiento - Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Descripción General

El Sistema de Agendamiento para el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio tiene como objetivo gestionar las citas de las diversas actividades que se desarrollan en el centro. Este documento detalla los requerimientos funcionales y técnicos del sistema.

## Requerimientos Funcionales

### 1. Gestión de Actividades

- Crear actividades puntuales (con una sola cita) o periódicas (con múltiples citas)
- Asignar tipos, lugares, oferentes, socios comunitarios y beneficiarios a las actividades
- Establecer cupos para las actividades (opcional)
- Adjuntar archivos a las actividades (sin límites de tamaño, tipo o cantidad)
- Modificar, cancelar o reagendar actividades
- Agrupar actividades en proyectos (opcional)

### 2. Gestión de Citas

- Asociar citas a actividades
- Asignar fecha, hora y lugar a cada cita
- Visualizar citas en formato de calendario semanal
- Acceder a detalles de la actividad desde una cita
- Cancelar o reagendar citas

### 3. Sistema de Usuarios

- Autenticación mediante usuario y contraseña
- Recuperación de contraseña a través de correo electrónico
- Registro público abierto para cualquier usuario
- Creación de usuarios adicionales desde dentro del sistema (opcional)
- Asignación de permisos específicos por usuario

### 4. Sistema de Permisos

- Asignación de permisos específicos por usuario
- Control de acceso a funcionalidades según permisos asignados
- Gestión de usuarios y sus permisos correspondientes

### 5. Mantenedores

- Gestionar catálogos de:
  - Tipos de actividad
  - Lugares
  - Oferentes de actividad
  - Socios comunitarios
  - Proyectos

### 6. Gestión de Archivos

- Adjuntar archivos a las actividades
- Visualizar o descargar archivos adjuntos
- Adjuntar información de comunicaciones posteriormente

## Requerimientos Técnicos

### 1. Arquitectura

- Aplicación web responsive
- Almacenamiento en MySQL
- Autenticación mediante usuario/contraseña con JWT

### 2. Seguridad

- Sistema cerrado, no accesible públicamente
- Autenticación obligatoria para todas las funciones
- Protección de datos sensibles

### 3. Interfaces

- Interfaz de usuario intuitiva y amigable
- Diseño responsivo para diferentes dispositivos
- Cumplimiento de estándares de accesibilidad

### 4. Rendimiento

- Tiempos de respuesta rápidos
- Optimización para conexiones lentas
- Carga eficiente de datos

## Entidades del Sistema

### Actividad

- Nombre
- Tipo de actividad (relación)
- Periodicidad (puntual o periódica con rango de fechas)
- Cupo (opcional)
- Oferentes de la actividad (relación)
- Socio comunitario (relación)
- Beneficiarios del servicio (relación)
- Proyecto (relación, opcional)
- Archivos adjuntos

### Cita

- Actividad (relación)
- Lugar (relación)
- Fecha
- Hora

### Tipo de Actividad

- Nombre
- Descripción
- Valores predefinidos: Capacitación, Taller, Charlas, Atenciones, Operativo en oficina, Operativo rural, Operativo, Práctica profesional, Diagnóstico

### Periodicidad

- Nombre
- Valores predefinidos: Puntual, Periódica (rango de fechas)

### Lugares

- Nombre
- Cupo (opcional)
- Valores predefinidos: Oficina del centro, Lugares del territorio

### Oferentes de la Actividad

- Nombre
- Docente responsable
- Valores predefinidos: Carreras (IP, CFT, Universidad) + 1 docente responsable por carrera

### Socio Comunitario

- Nombre

### Beneficiarios del Servicio

- Caracterización (por definir)

### Proyectos (Opcional)

- Nombre

## Lista de Interfaces del Sistema

### 1. Login (`/login`)

**Descripción**: Pantalla de acceso al sistema con autenticación de usuarios.
**Elementos**: Campo email, campo contraseña, botón "Iniciar Sesión", enlace "Recuperar Contraseña"
**Proceso**: Validación de credenciales → Generación de JWT → Redirección a calendario principal

### 2. Recuperación de Contraseña (`/forgot-password`)

**Descripción**: Formulario para solicitar recuperación de contraseña vía email.
**Elementos**: Campo email, botón "Enviar Email de Recuperación", enlace a login
**Proceso**: Validación de email → Generación de token → Envío de correo → Confirmación

### 3. Registro de Usuario (`/register`)

**Descripción**: Formulario para registro público de nuevos usuarios en el sistema.
**Elementos**: Campos nombre, email, contraseña, confirmar contraseña
**Proceso**: Validación de datos → Creación de usuario → Asignación de permisos básicos → Login automático

### 4. Dashboard/Calendario Principal (`/dashboard`, `/`)

**Descripción**: Vista principal con calendario semanal/mensual de actividades.
**Elementos**: Calendario interactivo, filtros, botones navegación, botón crear actividad
**Proceso**: Carga de actividades → Aplicación de filtros → Renderizado de calendario → Interacciones (click, drag&drop)

### 5. Crear Actividad (`/activities/create`)

**Descripción**: Formulario completo para crear nuevas actividades puntuales o periódicas.
**Elementos**: Todos los campos de actividad, selector de periodicidad, carga de archivos
**Proceso**: Validación de campos → Verificación de conflictos → Creación de actividad → Generación de citas → Redirección a calendario

### 6. Editar Actividad (`/activities/:id/edit`)

**Descripción**: Formulario pre-llenado para modificar actividades existentes.
**Elementos**: Mismos campos que crear, pre-poblados con datos actuales
**Proceso**: Carga de datos existentes → Validación de cambios → Verificación de conflictos → Actualización → Confirmación

### 7. Detalle de Actividad (`/activities/:id`)

**Descripción**: Vista completa de información de una actividad específica.
**Elementos**: Todos los detalles de la actividad, archivos adjuntos, botones de acción
**Proceso**: Carga de información → Verificación de permisos → Mostrar opciones disponibles

### 8. Cancelar Actividad (`/activities/:id/cancel`)

**Descripción**: Formulario para cancelar una actividad con justificación.
**Elementos**: Información de actividad, campo motivo, botones confirmar/cancelar
**Proceso**: Validación de motivo → Cambio de estado → Cancelación de citas asociadas → Confirmación

### 9. Reagendar Actividad (`/activities/:id/reschedule`)

**Descripción**: Formulario para cambiar fecha/hora de actividad o cita.
**Elementos**: Datos actuales, nuevos selectores fecha/hora, campo motivo
**Proceso**: Validación de nueva fecha → Verificación de disponibilidad → Actualización → Confirmación

### 10. Gestión de Usuarios (`/users`)

**Descripción**: Lista y gestión de usuarios del sistema.
**Elementos**: Tabla de usuarios, botones crear/editar/eliminar, filtros de búsqueda
**Proceso**: Carga de usuarios → Aplicación de filtros → Gestión de permisos

### 11. Crear/Editar Usuario (`/users/create`, `/users/:id/edit`)

**Descripción**: Formulario para gestión de usuarios y asignación de permisos.
**Elementos**: Campos de usuario, checkboxes de permisos específicos
**Proceso**: Validación de datos → Verificación de email único → Asignación de permisos → Creación/actualización

### 12. Mantenedores (`/maintenance`)

**Descripción**: Panel de gestión de catálogos del sistema.
**Sub-rutas**:

- `/maintenance/activity-types` - Tipos de Actividad
- `/maintenance/places` - Lugares
- `/maintenance/providers` - Oferentes
- `/maintenance/community-partners` - Socios Comunitarios
- `/maintenance/beneficiaries` - Beneficiarios
- `/maintenance/projects` - Proyectos

### 13. Reportes (`/reports`)

**Descripción**: Panel de generación y visualización de reportes.
**Elementos**: Selectores de tipo de reporte, filtros, botones de exportación
**Proceso**: Selección de parámetros → Generación de reporte → Exportación en formato seleccionado

### 14. Adjuntar Archivos (`/activities/:id/attachments`)

**Descripción**: Interfaz para gestión de archivos adjuntos a actividades.
**Elementos**: Lista de archivos existentes, área de subida, campo descripción
**Proceso**: Selección de archivos → Validación → Subida → Actualización de lista

## Rutas de la API Sugeridas

### Autenticación

- `POST /auth/login` - Iniciar sesión
- `POST /auth/logout` - Cerrar sesión
- `POST /auth/forgot-password` - Solicitar recuperación
- `POST /auth/reset-password` - Restablecer contraseña
- `POST /auth/register` - Registro inicial (solo si no hay usuarios)

### Usuarios

- `GET /users` - Listar usuarios
- `POST /users` - Crear usuario
- `GET /users/:id` - Obtener usuario
- `PUT /users/:id` - Actualizar usuario
- `DELETE /users/:id` - Eliminar usuario
- `PUT /users/:id/permissions` - Actualizar permisos

### Actividades

- `GET /activities` - Listar actividades (con filtros)
- `POST /activities` - Crear actividad
- `GET /activities/:id` - Obtener actividad
- `PUT /activities/:id` - Actualizar actividad
- `DELETE /activities/:id` - Eliminar actividad
- `POST /activities/:id/cancel` - Cancelar actividad
- `POST /activities/:id/reschedule` - Reagendar actividad

### Citas

- `GET /appointments` - Listar citas (calendario)
- `POST /appointments` - Crear cita
- `PUT /appointments/:id` - Actualizar cita
- `DELETE /appointments/:id` - Eliminar cita
- `POST /appointments/:id/reschedule` - Reagendar cita

### Archivos

- `POST /activities/:id/files` - Subir archivo
- `GET /activities/:id/files` - Listar archivos
- `GET /files/:id` - Descargar archivo
- `DELETE /files/:id` - Eliminar archivo

### Mantenedores

- `GET /activity-types` - Tipos de actividad
- `POST /activity-types` - Crear tipo
- `PUT /activity-types/:id` - Actualizar tipo
- `DELETE /activity-types/:id` - Eliminar tipo
- Similar para: `/places`, `/providers`, `/community-partners`, `/beneficiaries`, `/projects`

### Reportes

- `GET /reports/activities` - Reporte de actividades
- `GET /reports/occupancy` - Reporte de ocupación
- `GET /reports/providers` - Reporte por oferente
- `GET /reports/cancellations` - Reporte de cancelaciones

## Validaciones del Sistema

### Validaciones de Frontend

- **Tiempo real**: Email válido, formato de fecha/hora, campos numéricos
- **Al perder foco**: Verificación de duplicados, rangos válidos
- **Al enviar**: Validación completa de formulario, campos obligatorios

### Validaciones de Backend

- **Seguridad**: Validación de permisos, autenticación JWT
- **Integridad**: Verificación de conflictos de horario, capacidad de lugares
- **Reglas de negocio**: Estados válidos, fechas futuras, motivos obligatorios

### Mensajes de Error Específicos

- **Campos obligatorios**: "El [campo] es obligatorio"
- **Formatos**: "El formato de [campo] no es válido"
- **Conflictos**: "El lugar ya está ocupado en [fecha] de [hora] a [hora]"
- **Permisos**: "No tiene permisos para realizar esta acción"
- **Estados**: "No se puede [acción] una actividad [estado]"

## Procesos Principales del Sistema

### Proceso de Autenticación

1. Usuario ingresa credenciales
2. Sistema valida formato
3. Verificación contra base de datos
4. Generación de JWT si es válido
5. Redirección a dashboard
6. Manejo de errores específicos

### Proceso de Creación de Actividad

1. Selección de tipo de actividad
2. Completar información básica
3. Selección de periodicidad
4. Configuración de fechas/horarios
5. Validación de disponibilidad
6. Selección de recursos (lugar, oferentes, etc.)
7. Carga de archivos opcionales
8. Validación completa
9. Creación de actividad y citas asociadas
10. Confirmación y redirección

### Proceso de Cancelación

1. Selección de actividad a cancelar
2. Verificación de permisos
3. Validación de estado (no cancelada/completada)
4. Ingreso de motivo obligatorio
5. Confirmación del usuario
6. Cambio de estado en base de datos
7. Cancelación automática de citas asociadas
8. Notificación de confirmación

### Proceso de Reagendamiento

1. Selección de actividad/cita
2. Verificación de permisos y estado
3. Ingreso de motivo del cambio
4. Selección de nueva fecha/hora
5. Verificación de disponibilidad del lugar
6. Validación de conflictos
7. Actualización en base de datos
8. Confirmación del cambio

### Proceso de Gestión de Permisos

1. Selección de usuario
2. Visualización de permisos actuales
3. Modificación de permisos específicos
4. Validación de coherencia
5. Actualización en base de datos
6. Aplicación inmediata en sesión activa

## Observaciones Adicionales

- El sistema debe ser desarrollado por equipos de 4-5 estudiantes de la asignatura Desarrollo Web
- La implementación debe seguir buenas prácticas de desarrollo
- Se debe documentar adecuadamente el código y crear manuales de usuario
- Todas las rutas deben implementar middleware de autenticación excepto login y registro inicial
- Los formularios deben incluir protección CSRF
- Implementar rate limiting en endpoints críticos
- Todas las operaciones de escritura deben registrarse en logs de auditoría
