# Reglas de Negocio - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Gestión de Conflictos de Agendamiento

### Conflictos de Lugar y Horario

- **Regla**: No se puede agendar una actividad en el mismo lugar y horario si ya existe otra cita programada
- **Comportamiento**: El sistema debe mostrar un mensaje indicando que el lugar está ocupado en ese horario
- **Validación**: Verificar disponibilidad tanto al crear como al reagendar una cita
- **Mensaje**: "El lugar [nombre del lugar] ya está ocupado el [fecha] de [hora inicio] a [hora fin]"

### Resolución de Conflictos

- **Sugerencia automática**: El sistema puede sugerir horarios disponibles en el mismo lugar
- **Lugares alternativos**: Mostrar lugares disponibles en el mismo horario
- **Vista de disponibilidad**: Permitir ver la disponibilidad del lugar en una vista de calendario

## Políticas de Cancelación

### Cancelación de Actividades

- **Sin restricción temporal**: Las actividades pueden cancelarse en cualquier momento, sin límite de tiempo previo
- **Motivo obligatorio**: Se debe proporcionar un motivo de cancelación
- **Estado de la actividad**: Cambiar estado a "Cancelada" (no eliminar del sistema)
- **Citas asociadas**: Todas las citas de la actividad deben cancelarse automáticamente

### Cancelación de Citas Individuales

- **Sin restricción temporal**: Las citas pueden cancelarse en cualquier momento
- **Motivo obligatorio**: Se debe registrar el motivo de cancelación
- **Actividades periódicas**: Al cancelar una cita de actividad periódica, solo esa instancia se cancela

## Políticas de Reagendamiento

### Reagendamiento de Actividades

- **Sin límite**: No hay restricción en la cantidad de reagendamientos permitidos
- **Motivo obligatorio**: Se debe proporcionar un motivo para el reagendamiento
- **Validación de disponibilidad**: Verificar que el nuevo horario/lugar esté disponible
- **Historial**: Mantener registro de reagendamientos previos

### Reagendamiento de Citas

- **Flexibilidad total**: Sin límites de tiempo o cantidad de reagendamientos
- **Validación cruzada**: Verificar disponibilidad del lugar y horario destino
- **Notificación**: El cambio debe quedar registrado en el sistema

## Gestión de Cupos

### Control de Capacidad

- **Cupo lleno**: No se permite registrar participantes adicionales cuando se alcanza el cupo máximo
- **Mensaje de cupo lleno**: "Esta actividad ha alcanzado su cupo máximo de [número] participantes"
- **Sin lista de espera**: No se implementará sistema de lista de espera
- **Cupo opcional**: Si no se define cupo, se considera capacidad ilimitada

### Modificación de Cupos

- **Reducción de cupo**: Se puede reducir el cupo solo si no hay participantes que excedan el nuevo límite
- **Aumento de cupo**: Se puede aumentar sin restricciones
- **Cupo en lugares**: Los lugares pueden tener cupo propio que debe respetarse

## Gestión de Archivos

### Políticas de Archivos Adjuntos

- **Sin límite de tamaño**: No hay restricción en el tamaño de archivos
- **Sin límite de tipos**: Se permiten todos los tipos de archivo
- **Sin límite de cantidad**: No hay restricción en la cantidad de archivos por actividad
- **Almacenamiento permanente**: Los archivos se mantienen indefinidamente

### Gestión de Archivos

- **Reemplazo**: Se pueden agregar archivos adicionales sin reemplazar existentes
- **Eliminación**: Los archivos pueden eliminarse individualmente
- **Versionado**: Si se sube un archivo con el mismo nombre, mantener ambas versiones

## Comportamientos del Calendario

### Vista Predeterminada

- **Vista inicial**: Semana actual al ingresar al sistema
- **Cambio de vista**: Permitir alternar entre vista semanal y mensual
- **Navegación**: Sin límites temporales para navegación hacia atrás o adelante

### Filtros del Calendario

- **Filtro por fecha**: Rango de fechas específico
- **Filtro por tipo de actividad**: Mostrar solo tipos seleccionados
- **Filtro por lugar**: Mostrar solo actividades en lugares específicos
- **Filtro por oferente**: Mostrar solo actividades de oferentes específicos
- **Combinación de filtros**: Permitir múltiples filtros simultáneos

### Interacciones del Calendario

- **Drag & Drop**: Permitir arrastrar y soltar citas para reagendar
- **Click para crear**: Click en celda vacía del calendario para crear nueva actividad
- **Click en cita**: Abrir modal con detalles de la actividad
- **Navegación táctil**: Soporte para swipe en dispositivos móviles

## Gestión de Datos Maestros

### Datos Iniciales del Sistema

- **Sin datos precargados**: El sistema inicia sin datos maestros predefinidos
- **Configuración inicial**: El primer usuario debe configurar los catálogos básicos
- **Datos mínimos requeridos**: Al menos un lugar y un tipo de actividad para poder crear actividades

### Eliminación de Datos Maestros

- **No eliminación física**: Los elementos con referencias activas no pueden eliminarse
- **Deshabilitación**: Los elementos en uso pueden deshabilitarse para evitar su uso futuro
- **Validación de integridad**: Verificar referencias antes de permitir eliminación
- **Recuperación**: Los elementos deshabilitados pueden reactivarse

### Mantenimiento de Integridad

- **Referencias futuras**: Lugares con citas futuras no pueden eliminarse
- **Referencias históricas**: Mantener integridad con datos históricos
- **Cascada controlada**: Al deshabilitar un elemento padre, consultar sobre elementos dependientes

## Sistema de Permisos

### Asignación de Permisos

- **Por usuario**: Cada usuario tiene permisos específicos asignados individualmente
- **Sin roles predefinidos**: No hay perfiles o roles estándar
- **Granularidad**: Permisos específicos por funcionalidad

### Permisos Disponibles

- **Gestión de usuarios**: Crear, editar, eliminar usuarios
- **Gestión de actividades**: Crear, editar, eliminar, reagendar actividades
- **Gestión de citas**: Crear, editar, eliminar, reagendar citas
- **Mantenedores**: Gestión de catálogos (lugares, tipos, oferentes, etc.)
- **Visualización**: Acceso a diferentes vistas del calendario
- **Reportes**: Acceso a reportes y exportaciones

### Control de Acceso

- **Validación por acción**: Verificar permisos antes de cada operación
- **Interface adaptativa**: Mostrar solo opciones para las que el usuario tiene permisos
- **Auditoría**: Registrar acciones realizadas por cada usuario

## Registro de Usuarios

### Registro Público

- **Registro abierto**: Cualquier persona puede registrarse en el sistema
- **Permisos básicos**: Los nuevos usuarios reciben permisos básicos de visualización
- **Sin restricciones**: No hay límites en la cantidad de usuarios que se pueden registrar

### Permisos Iniciales

- **Permisos por defecto**: Usuarios nuevos reciben permisos básicos (visualización de calendario, crear actividades propias)
- **Escalamiento de permisos**: Los administradores pueden asignar permisos adicionales posteriormente
- **Flexibilidad**: Los permisos pueden modificarse en cualquier momento

### Creación de Usuarios Adicional

- **Opción dual**: Los usuarios pueden registrarse públicamente O ser creados desde el sistema
- **Por usuarios autorizados**: Solo usuarios con permiso "Gestión de usuarios" pueden crear otros usuarios
- **Asignación manual**: Los permisos pueden asignarse manualmente durante la creación

## Validaciones de Integridad

### Validaciones Temporales

- **Fecha de inicio**: No puede ser anterior a la fecha actual (para nuevas actividades)
- **Fecha de fin**: Debe ser posterior a la fecha de inicio (actividades periódicas)
- **Horarios**: Hora de fin debe ser posterior a hora de inicio
- **Coherencia de fechas**: En actividades periódicas, las citas deben estar dentro del rango definido

### Validaciones de Recursos

- **Disponibilidad de lugar**: Verificar que el lugar esté disponible en el horario solicitado
- **Cupo de lugar**: No exceder la capacidad máxima del lugar
- **Cupo de actividad**: No exceder el cupo definido para la actividad

### Validaciones de Datos

- **Campos obligatorios**: Verificar que todos los campos requeridos estén completos
- **Formatos**: Validar formatos de email, teléfono, etc.
- **Rangos**: Verificar que los valores numéricos estén dentro de rangos válidos
