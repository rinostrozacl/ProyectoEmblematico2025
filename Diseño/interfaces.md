# Interfaces del Sistema de Agendamiento - Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

Este documento detalla las interfaces a desarrollar para el Sistema de Agendamiento del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## 1. Login

Pantalla de acceso al sistema.

### Elementos:

- Campo de texto para nombre de usuario (email)
- Campo de contraseña
- Botón "Iniciar Sesión"
- Enlace "Recuperar Contraseña"

### Funcionalidad:

- **Proceso**:
  - Captura de credenciales (email y contraseña)
  - Validación de campos obligatorios
  - Verificación de credenciales contra base de datos MySQL
  - Generación de token JWT para sesión autenticada
  - Redirección a calendario principal

### Diseño:

- Logo del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio en la parte superior
- Formulario centrado en la pantalla
- Diseño limpio y minimalista

## 2. Recuperación de Contraseña

Pantalla para solicitar recuperación de contraseña.

### Elementos:

- Campo de texto para correo electrónico
- Botón "Enviar Email de Recuperación"
- Enlace para volver al login

### Funcionalidad:

- **Descripción**: Formulario para solicitar recuperación de contraseña mediante correo electrónico.
- **Proceso**: Validación de email → Verificación en base de datos → Envío de email con token de recuperación

## 3. Vista de Carga Semanal (Calendario)

Pantalla principal que muestra las citas agendadas en formato de calendario semanal.

### Elementos:

- Calendario semanal con vista de días y horas
- Citas mostradas como bloques en los días/horas correspondientes
- Filtros para tipos de actividad, lugares, etc.
- Botones para navegación entre semanas

### Funcionalidad:

- Visualización de citas por semana
- Navegación entre semanas (anterior/siguiente)
- Filtrado de citas según criterios
- Al hacer clic en una cita, mostrar modal con detalle
- Botón para crear nueva actividad/cita

### Diseño:

- Vista tipo agenda con horas en el eje vertical y días en el horizontal
- Código de colores para diferentes tipos de actividades
- Diseño responsive que se adapta a diferentes dispositivos

## 4. Detalle de Ficha de Actividad

Modal o pantalla que muestra el detalle completo de una actividad y sus citas.

### Elementos:

- Información completa de la actividad:
  - Nombre y tipo
  - Periodicidad
  - Cupo
  - Lugar
  - Fecha y hora (o fechas para actividades periódicas)
  - Oferentes, socio comunitario y beneficiarios
  - Archivos adjuntos (con opción para visualizar/descargar)
- Botones de acción:
  - "Modificar Actividad"
  - "Cancelar Actividad"
  - "Reagendar Actividad"
  - "Adjuntar Información"

### Funcionalidad:

- Visualización de todos los detalles de la actividad
- Acceso a las acciones de modificación, cancelación y reagendamiento
- Visualización y descarga de archivos adjuntos
- Opción para adjuntar nueva información

## 5. Crear Actividad

Formulario para crear una nueva actividad con sus citas.

### Elementos:

- Campos para todos los atributos de la actividad:
  - Nombre (texto)
  - Tipo de actividad (selector)
  - Periodicidad (selector)
  - Cupo (numérico, opcional)
  - Lugar (selector)
  - Oferentes de la actividad (selector múltiple)
  - Socio comunitario (selector)
  - Beneficiarios (selector múltiple)
  - Proyecto (selector, opcional)
  - Archivos adjuntos (carga de archivos)
  - Días de aviso previo (numérico)
- Para actividades puntuales:
  - Fecha (selector de fecha)
  - Hora (selector de hora)
- Para actividades periódicas:
  - Fecha inicio (selector de fecha)
  - Fecha fin (selector de fecha)
  - Selección de días y horas para las citas

### Funcionalidad:

- Validación de campos obligatorios
- Creación de la actividad en base de datos MySQL
- Creación automática de las citas asociadas
- Almacenamiento de archivos adjuntos en servidor
- Mensajes de confirmación/error

## 6. Modificar Actividad

Formulario similar a "Crear Actividad" pero pre-llenado con la información existente.

### Elementos:

- Los mismos elementos que en "Crear Actividad", con valores preexistentes
- Botón "Guardar Cambios"
- Botón "Cancelar" (vuelve sin guardar cambios)

### Funcionalidad:

- Carga de la información actual de la actividad
- Validación de campos obligatorios
- Actualización de la actividad en base de datos MySQL
- Actualización de las citas asociadas si es necesario
- Mensajes de confirmación/error

## 7. Cancelar Actividad

Pantalla para cancelar una actividad y todas sus citas.

### Elementos:

- Selector de actividad a cancelar (si se accede desde el menú)
- Campo de texto para ingresar el motivo de la cancelación
- Botón "Cancelar Actividad"
- Botón "Volver" (sin realizar la cancelación)

### Funcionalidad:

- Confirmación antes de cancelar (diálogo de confirmación)
- Registro del motivo de cancelación
- Actualización del estado de la actividad y sus citas en base de datos MySQL
- Mensaje de confirmación tras cancelación exitosa

## 8. Reagendar Actividad

Pantalla para cambiar la fecha/hora de una actividad puntual o de una cita específica.

### Elementos:

- Selector de actividad/cita a reagendar (si se accede desde el menú)
- Campo de texto para ingresar el motivo del cambio
- Selector de nueva fecha
- Selector de nueva hora
- Botón "Guardar Nueva Fecha"
- Botón "Volver" (sin realizar cambios)

### Funcionalidad:

- Validación de la nueva fecha/hora
- Actualización de la cita en base de datos MySQL
- Mensaje de confirmación tras reagendamiento exitoso

## 9. Adjuntar Información de Comunicaciones

Pantalla para adjuntar archivos adicionales a una actividad.

### Elementos:

- Selector de actividad (si se accede desde el menú)
- Componente de carga de archivos
- Campo para descripción del archivo (opcional)
- Botón "Guardar Archivo"
- Botón "Volver" (sin guardar)

### Funcionalidad:

- Almacenamiento de archivos en servidor
- Registro de la metadata del archivo en base de datos MySQL
- Validación de tamaño y tipo de archivo
- Mensaje de confirmación tras carga exitosa

## 10. Mantenedores

Conjunto de pantallas para administrar los catálogos del sistema.

### Elementos por cada entidad (Tipos de actividad, Lugares, Oferentes, etc.):

- Tabla con listado de elementos existentes
- Botón "Crear Nuevo"
- Botones de "Editar" y "Eliminar" por cada elemento
- Formulario para crear/editar con los campos correspondientes a cada entidad

### Funcionalidad:

- Visualización de elementos existentes
- Creación de nuevos elementos
- Edición de elementos existentes
- Eliminación de elementos (con confirmación)
- Validación de referencias (no permitir eliminar elementos en uso)

## Componentes Comunes

### Barra de Navegación Superior

- Logo del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio
- Menú desplegable con acceso a las diferentes secciones
- Nombre del usuario actual
- Botón de cierre de sesión

### Pie de Página

- Información de contacto del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio
- Año de desarrollo
- Versión del sistema

### Mensajes y Notificaciones

- Componente para mostrar mensajes de éxito, error o advertencia
- Notificaciones de sistema (alertas de actividades próximas)

## Consideraciones de Diseño

- Paleta de colores institucional de Santo Tomás
- Diseño responsive para adaptarse a diferentes dispositivos
- Interfaces intuitivas y fáciles de usar
- Consistencia en elementos de diseño a lo largo de toda la aplicación
- Feedback visual para acciones del usuario

## Observaciones para el Desarrollo

- Priorizar la usabilidad y experiencia de usuario
- Implementar validaciones del lado del cliente para mejorar la experiencia
- Asegurar que todas las interfaces sean accesibles
- Optimizar el rendimiento, especialmente en la carga de datos y archivos
