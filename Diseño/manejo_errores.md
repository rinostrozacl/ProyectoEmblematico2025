# Manejo de Errores y Excepciones - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Estrategia General de Manejo de Errores

### Principios de Diseño

- **Transparencia**: Los errores deben ser claros y comprensibles para el usuario
- **Recuperación**: Siempre que sea posible, ofrecer una ruta de recuperación
- **Logging**: Registrar todos los errores para análisis posterior
- **Consistencia**: Mantener un estilo uniforme en todos los mensajes de error
- **Prevención**: Validaciones proactivas para evitar errores

**Nota**: Los mensajes específicos de validación por interfaz están detallados en [validaciones.md](./validaciones.md). Este documento se enfoca en el manejo técnico y estrategias de recuperación.

## Categorías de Errores

### 1. Errores de Validación de Datos

#### Campos Obligatorios Vacíos

**Comportamiento**:

- Highlight del campo en rojo
- Mensaje específico debajo del campo
- Impedir el envío del formulario

**Mensajes**:

- "El nombre de la actividad es obligatorio"
- "Debe seleccionar un tipo de actividad"
- "La fecha de inicio es requerida"
- "Debe especificar una hora de inicio"

#### Formatos Incorrectos

**Comportamiento**:

- Validación en tiempo real mientras el usuario escribe
- Feedback visual inmediato

**Mensajes**:

- "El formato de correo electrónico no es válido"
- "La fecha debe tener el formato DD/MM/AAAA"
- "La hora debe estar en formato HH:MM"
- "El cupo debe ser un número entero positivo"

#### Rangos de Valores Inválidos

**Comportamiento**:

- Validación inmediata al perder el foco del campo
- Sugerencia de valor correcto

**Mensajes**:

- "La fecha de fin debe ser posterior a la fecha de inicio"
- "La hora de fin debe ser posterior a la hora de inicio"
- "El cupo no puede ser negativo"
- "La fecha no puede ser anterior a hoy"

### 2. Errores de Conflictos de Recursos

#### Conflictos de Horario y Lugar

**Comportamiento**:

- Modal de advertencia con detalles del conflicto
- Opción de ver actividad existente
- Sugerencias de horarios/lugares alternativos

**Mensajes**:

- "El lugar 'Sala de Reuniones' ya está ocupado el Lunes 15/03/2024 de 14:00 a 16:00 por la actividad 'Taller de Comunicación'"
- "Horarios alternativos disponibles en el mismo lugar: 10:00-12:00, 16:00-18:00"
- "Lugares alternativos disponibles en el mismo horario: Auditorio, Sala de Capacitación"

#### Límites de Cupo Excedidos

**Comportamiento**:

- Mensaje de advertencia
- Mostrar cupo actual y límite
- Opción de modificar cupo si tiene permisos

**Mensajes**:

- "No se puede confirmar la actividad. Cupo máximo: 25 personas, solicitado: 30 personas"
- "El lugar 'Auditorio' tiene capacidad para 50 personas, pero se están registrando 60"

### 3. Errores de Permisos y Acceso

#### Permisos Insuficientes

**Comportamiento**:

- Página/modal informativo
- Opción de contactar administrador
- Redirección automática tras 5 segundos

**Mensajes**:

- "No tiene permisos para realizar esta acción. Contacte al administrador del sistema"
- "Su cuenta no tiene permisos para gestionar usuarios"
- "Solo puede modificar actividades que usted ha creado"

#### Sesión Expirada

**Comportamiento**:

- Modal de notificación
- Redirección automática al login
- Preservar datos del formulario cuando sea posible

**Mensajes**:

- "Su sesión ha expirado por seguridad. Por favor, inicie sesión nuevamente"
- "Ha estado inactivo por mucho tiempo. Será redirigido al inicio de sesión"

### 4. Errores de Conectividad y Sistema

#### Errores de Conexión a la Base de Datos

**Comportamiento**:

- Página de error temporal
- Botón "Intentar nuevamente"
- Notificación automática al equipo técnico

**Mensajes**:

- "Error temporal de conexión. Intente nuevamente en unos momentos"
- "No se pudo conectar con el servidor. Verifique su conexión a internet"

#### Errores del Servidor (500)

**Comportamiento**:

- Página de error técnico
- Código de error único para reporte
- Opción de reportar problema

**Mensajes**:

- "Ha ocurrido un error interno del servidor. Código de error: #ERROR-20240315-001"
- "Nuestro equipo técnico ha sido notificado automáticamente"
- "Si el problema persiste, contacte al soporte técnico"

#### Timeouts de Operación

**Comportamiento**:

- Indicador de carga que muestra progreso
- Opción de cancelar operación larga
- Mensaje informativo sobre la demora

**Mensajes**:

- "La operación está tomando más tiempo del esperado..."
- "Procesando archivo de 50MB. Esto puede tomar algunos minutos"
- "Generando reporte con 10,000 registros. Por favor espere..."

## Errores Específicos por Funcionalidad

### Gestión de Actividades

#### Crear Actividad

**Errores Posibles**:

- Nombre duplicado para el mismo oferente
- Selección de fechas pasadas
- Conflictos de recursos

**Mensajes**:

- "Ya existe una actividad con el nombre 'Taller Excel' para el oferente 'Ingeniería'"
- "No se pueden crear actividades en fechas pasadas"
- "El lugar seleccionado no está disponible en el horario indicado"

#### Modificar Actividad

**Errores Posibles**:

- Intentar modificar actividad completada
- Cambios que generan conflictos
- Permisos insuficientes

**Mensajes**:

- "No se puede modificar una actividad que ya ha sido completada"
- "Los cambios propuestos generan conflicto con 3 actividades existentes"
- "Solo puede modificar actividades que usted ha creado"

#### Cancelar Actividad

**Errores Posibles**:

- Intentar cancelar actividad ya cancelada
- Motivo de cancelación vacío

**Mensajes**:

- "Esta actividad ya se encuentra cancelada"
- "Debe proporcionar un motivo para la cancelación"

### Gestión de Archivos

#### Subida de Archivos

**Errores Posibles**:

- Archivo corrupto
- Error de almacenamiento
- Interrupción de la subida

**Mensajes**:

- "El archivo parece estar corrupto. Intente con otro archivo"
- "Error al guardar el archivo en el servidor. Intente nuevamente"
- "La subida fue interrumpida. ¿Desea reintentar?"

**Comportamiento**:

- Barra de progreso que muestra porcentaje
- Posibilidad de reanudar subidas interrumpidas
- Validación de integridad del archivo

### Gestión de Usuarios

#### Crear Usuario

**Errores Posibles**:

- Email ya registrado
- Contraseña no segura
- Campos obligatorios vacíos

**Mensajes**:

- "El correo electrónico ya está registrado en el sistema"
- "La contraseña debe tener al menos 8 caracteres, incluir mayúsculas, minúsculas y números"
- "Todos los campos marcados con (\*) son obligatorios"

#### Recuperación de Contraseña

**Errores Posibles**:

- Email no registrado
- Error en envío de correo
- Token expirado

**Mensajes**:

- "El correo electrónico no se encuentra registrado en el sistema"
- "No se pudo enviar el correo de recuperación. Intente más tarde"
- "El enlace de recuperación ha expirado. Solicite uno nuevo"

## Manejo de Errores en el Frontend

### Estados de Error en Componentes

#### Formularios

```typescript
interface FormErrorState {
  fieldErrors: { [fieldName: string]: string };
  generalError: string | null;
  isSubmitting: boolean;
}
```

**Comportamiento**:

- Mostrar errores específicos de campo
- Destacar campos con error
- Prevenir múltiples envíos

#### Listas y Tablas

**Estados**:

- Error de carga inicial
- Error en paginación
- Error en filtros

**Mensajes**:

- "Error al cargar los datos. Haga clic aquí para reintentar"
- "Error al cargar la página siguiente"
- "No se pudieron aplicar los filtros seleccionados"

#### Calendario

**Errores Específicos**:

- Error al cargar eventos
- Error al cambiar de vista
- Error en drag & drop

**Mensajes**:

- "Error al cargar las actividades del calendario"
- "No se pudo cambiar a la vista mensual"
- "No se pudo mover la actividad. El horario de destino no está disponible"

### Recuperación Automática

#### Reintentos Automáticos

- Operaciones de lectura: 3 intentos automáticos
- Operaciones de escritura: 1 reintento con confirmación del usuario
- Delay incremental: 1s, 3s, 5s

#### Cache Local

- Mantener datos en localStorage para recuperación
- Sincronización automática cuando se restablece la conexión
- Indicador visual de estado "sin conexión"

## Logging y Monitoreo de Errores

### Información a Registrar

#### Para Errores de Usuario

```json
{
  "timestamp": "2024-03-15T14:30:00Z",
  "userId": 123,
  "action": "crear_actividad",
  "errorType": "validation",
  "errorMessage": "Fecha de inicio requerida",
  "formData": {...},
  "userAgent": "Mozilla/5.0...",
  "sessionId": "abc123"
}
```

#### Para Errores del Sistema

```json
{
  "timestamp": "2024-03-15T14:30:00Z",
  "errorType": "database_connection",
  "errorMessage": "Connection timeout after 30s",
  "stackTrace": "...",
  "serverInfo": {...},
  "affectedUsers": 5,
  "recoveryAction": "connection_retry"
}
```

### Alertas del Sistema

- **Críticas**: Errores que afectan a múltiples usuarios
- **Advertencias**: Errores frecuentes que requieren atención
- **Información**: Eventos importantes del sistema

## Páginas de Error Personalizadas

### Error 404 - Página No Encontrada

**Contenido**:

- Ilustración amigable
- Mensaje explicativo
- Enlaces de navegación principales
- Buscador interno

**Mensaje**:
"La página que busca no existe o ha sido movida. Utilice el menú de navegación o busque lo que necesita"

### Error 500 - Error Interno del Servidor

**Contenido**:

- Mensaje de disculpa
- Código de error único
- Información de contacto técnico
- Estimación de tiempo de resolución

**Mensaje**:
"Estamos experimentando dificultades técnicas temporales. Nuestro equipo ha sido notificado y está trabajando en una solución"

### Error 403 - Acceso Denegado

**Contenido**:

- Explicación del problema de permisos
- Opciones para solicitar acceso
- Información de contacto del administrador

**Mensaje**:
"No tiene los permisos necesarios para acceder a esta sección. Contacte al administrador del sistema para solicitar acceso"

## Estrategias de Recuperación

### Recuperación Automática

- **Reconexión automática**: Para errores de conectividad
- **Reintento de operaciones**: Para errores temporales
- **Sincronización diferida**: Para operaciones offline

### Recuperación Manual

- **Botones de reintento**: En todos los mensajes de error
- **Formularios persistentes**: Guardar datos ingresados
- **Navegación alternativa**: Múltiples rutas para llegar al mismo destino

### Recuperación de Datos

- **Autoguardado**: Para formularios largos
- **Historial de cambios**: Para recuperar versiones anteriores
- **Backup automático**: Para datos críticos
