# Criterios de Aceptación - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Metodología de Criterios de Aceptación

### Formato Estándar

Cada criterio de aceptación sigue el formato:

```
DADO [contexto inicial]
CUANDO [acción del usuario]
ENTONCES [resultado esperado]
```

### Definición de "Completado"

Una funcionalidad se considera completada cuando:

- Todos los criterios de aceptación han sido implementados
- Las pruebas manuales confirman el comportamiento esperado
- Las validaciones de frontend y backend funcionan correctamente
- Los mensajes de error están implementados según especificación
- La funcionalidad es responsive en dispositivos móviles y desktop

## 1. Sistema de Autenticación

### Historia: Login de Usuario

#### Criterios de Aceptación:

**CA-01**: Login exitoso

```
DADO que soy un usuario registrado
CUANDO ingreso email y contraseña correctos
ENTONCES debo ser redirigido al calendario principal
Y mi sesión debe quedar activa
```

**CA-02**: Login fallido

```
DADO que soy un usuario registrado
CUANDO ingreso credenciales incorrectas
ENTONCES debo ver el mensaje "Credenciales incorrectas"
Y debo permanecer en la página de login
```

**CA-03**: Campos vacíos

```
DADO que estoy en la página de login
CUANDO intento enviar el formulario con campos vacíos
ENTONCES debo ver mensajes de error específicos para cada campo
Y el botón de envío debe permanecer deshabilitado
```

### Historia: Recuperación de Contraseña

#### Criterios de Aceptación:

**CA-04**: Solicitud de recuperación exitosa

```
DADO que soy un usuario registrado
CUANDO ingreso mi email en recuperación de contraseña
ENTONCES debo recibir un correo con instrucciones
Y debo ver el mensaje "Se ha enviado un correo con instrucciones"
```

**CA-05**: Email no registrado

```
DADO que ingreso un email no registrado
CUANDO solicito recuperación de contraseña
ENTONCES debo ver el mensaje "El correo no está registrado"
```

### Historia: Registro de Usuario

#### Criterios de Aceptación:

**CA-06**: Registro público exitoso

```
DADO que soy una persona nueva en el sistema
CUANDO completo el formulario de registro con datos válidos
ENTONCES mi cuenta debe crearse con permisos básicos
Y debo recibir confirmación de registro exitoso
Y debo ser redirigido al calendario principal
```

**CA-07**: Validación de email único

```
DADO que intento registrarme con un email ya existente
CUANDO envío el formulario de registro
ENTONCES debo ver el mensaje "Este email ya está registrado"
Y el registro no debe procesarse
```

## 2. Gestión de Actividades

### Historia: Crear Actividad

#### Criterios de Aceptación:

**CA-08**: Crear actividad puntual exitosa

```
DADO que tengo permisos para crear actividades
CUANDO completo el formulario con datos válidos para actividad puntual
ENTONCES la actividad debe crearse en la base de datos
Y debo ver el mensaje "Actividad creada exitosamente"
Y debo ser redirigido al calendario
```

**CA-09**: Crear actividad periódica exitosa

```
DADO que tengo permisos para crear actividades
CUANDO completo el formulario para actividad periódica con fechas de inicio y fin
ENTONCES deben crearse todas las citas según la periodicidad seleccionada
Y cada cita debe respetar las fechas y horarios especificados
```

**CA-10**: Validación de campos obligatorios

```
DADO que estoy creando una actividad
CUANDO intento guardar sin completar campos obligatorios
ENTONCES debo ver mensajes de error específicos para cada campo faltante
Y la actividad no debe guardarse
```

**CA-11**: Validación de conflictos de horario

```
DADO que estoy creando una actividad
CUANDO selecciono un lugar y horario ya ocupado
ENTONCES debo ver el mensaje "El lugar [nombre] ya está ocupado el [fecha] de [hora] a [hora]"
Y debo recibir sugerencias de horarios/lugares alternativos
```

### Historia: Modificar Actividad

#### Criterios de Aceptación:

**CA-12**: Modificación exitosa

```
DADO que tengo permisos para modificar una actividad
CUANDO actualizo la información y guardo los cambios
ENTONCES los datos deben actualizarse en la base de datos
Y debo ver el mensaje "Actividad actualizada exitosamente"
```

**CA-13**: Restricción por permisos

```
DADO que no tengo permisos para modificar actividades de otros usuarios
CUANDO intento editar una actividad que no creé
ENTONCES debo ver el mensaje "No tiene permisos para modificar esta actividad"
```

**CA-14**: Validación de actividad completada

```
DADO que intento modificar una actividad con estado "Completada"
CUANDO trato de guardar cambios
ENTONCES debo ver el mensaje "No se puede modificar una actividad completada"
```

### Historia: Cancelar Actividad

#### Criterios de Aceptación:

**CA-15**: Cancelación exitosa

```
DADO que tengo permisos para cancelar actividades
CUANDO cancelo una actividad proporcionando un motivo
ENTONCES el estado debe cambiar a "Cancelada"
Y todas las citas asociadas deben cancelarse automáticamente
Y debo ver el mensaje "Actividad cancelada exitosamente"
```

**CA-16**: Motivo obligatorio

```
DADO que estoy cancelando una actividad
CUANDO intento cancelar sin proporcionar un motivo
ENTONCES debo ver el mensaje "Debe proporcionar un motivo para la cancelación"
Y la cancelación no debe procesarse
```

## 3. Gestión del Calendario

### Historia: Vista de Calendario

#### Criterios de Aceptación:

**CA-17**: Carga inicial del calendario

```
DADO que accedo al calendario por primera vez
CUANDO la página carga completamente
ENTONCES debo ver la vista semanal de la semana actual
Y las actividades deben mostrarse en sus fechas y horarios correspondientes
```

**CA-18**: Cambio de vista semanal a mensual

```
DADO que estoy en la vista semanal
CUANDO hago clic en el botón "Vista Mensual"
ENTONCES debo ver el calendario en formato mensual
Y los días con actividades deben mostrarse con indicadores visuales
```

**CA-19**: Navegación temporal

```
DADO que estoy en cualquier vista del calendario
CUANDO uso los controles de navegación (anterior/siguiente)
ENTONCES debo poder navegar sin límites hacia el pasado o futuro
Y las actividades deben cargarse correctamente para cada período
```

**CA-20**: Filtros del calendario

```
DADO que estoy en el calendario
CUANDO aplico filtros por tipo de actividad, lugar u oferente
ENTONCES solo deben mostrarse las actividades que cumplan los criterios seleccionados
Y debo poder combinar múltiples filtros simultáneamente
```

### Historia: Interacciones del Calendario

#### Criterios de Aceptación:

**CA-21**: Drag & Drop para reagendar

```
DADO que tengo permisos para reagendar
CUANDO arrastro una cita a otro horario/día válido
ENTONCES la cita debe moverse al nuevo horario
Y debo ver una confirmación del cambio
```

**CA-22**: Crear actividad desde calendario

```
DADO que tengo permisos para crear actividades
CUANDO hago clic en una celda vacía del calendario
ENTONCES debo ver el formulario de crear actividad
Y la fecha/hora deben estar pre-seleccionadas según la celda clickeada
```

**CA-23**: Ver detalle de actividad

```
DADO que hay actividades en el calendario
CUANDO hago clic en una actividad existente
ENTONCES debo ver un modal con todos los detalles de la actividad
Y debo tener acceso a las opciones de editar/cancelar/reagendar
```

## 4. Sistema de Permisos

### Historia: Gestión de Permisos de Usuario

#### Criterios de Aceptación:

**CA-24**: Asignación de permisos

```
DADO que tengo permisos para gestionar usuarios
CUANDO asigno permisos específicos a un usuario
ENTONCES esos permisos deben guardarse en la base de datos
Y el usuario debe tener acceso solo a las funciones permitidas
```

**CA-25**: Validación de permisos en tiempo real

```
DADO que un usuario tiene permisos limitados
CUANDO intenta acceder a una función no autorizada
ENTONCES debo ver el mensaje "No tiene permisos para realizar esta acción"
Y debo ser redirigido a una página autorizada
```

**CA-26**: Interface adaptativa por permisos

```
DADO que un usuario tiene permisos específicos
CUANDO navega por el sistema
ENTONCES solo debe ver botones y opciones para las funciones autorizadas
Y las funciones no autorizadas no deben mostrarse en la interfaz
```

## 5. Gestión de Archivos

### Historia: Adjuntar Archivos

#### Criterios de Aceptación:

**CA-27**: Subida exitosa de archivo

```
DADO que estoy creando o editando una actividad
CUANDO adjunto un archivo válido
ENTONCES el archivo debe subirse al servidor
Y debe mostrarse en la lista de archivos adjuntos
Y debo ver el mensaje "Archivo adjuntado exitosamente"
```

**CA-28**: Múltiples archivos

```
DADO que tengo una actividad existente
CUANDO adjunto múltiples archivos
ENTONCES todos los archivos deben guardarse sin reemplazar los existentes
Y debo ver una lista completa de todos los archivos adjuntos
```

**CA-29**: Descarga de archivos

```
DADO que hay archivos adjuntos a una actividad
CUANDO hago clic en un archivo
ENTONCES el archivo debe descargarse correctamente
Y debe mantener su nombre y extensión original
```

## 6. Mantenedores

### Historia: Gestión de Catálogos

#### Criterios de Aceptación:

**CA-30**: Crear elemento de catálogo

```
DADO que tengo permisos para gestionar mantenedores
CUANDO creo un nuevo elemento (lugar, tipo de actividad, etc.)
ENTONCES el elemento debe guardarse en la base de datos
Y debe aparecer disponible en los selectores correspondientes
```

**CA-31**: Validación de elementos en uso

```
DADO que un elemento está siendo usado en actividades activas
CUANDO intento eliminarlo
ENTONCES debo ver el mensaje "No se puede eliminar. Elemento en uso"
Y debo tener la opción de deshabilitarlo en su lugar
```

**CA-32**: Deshabilitar elemento

```
DADO que un elemento está en uso pero necesito deshabilitarlo
CUANDO selecciono la opción "Deshabilitar"
ENTONCES el elemento debe marcarse como inactivo
Y no debe aparecer en futuros selectores
Y debe mantenerse en registros históricos
```

## 7. Reportes y Consultas

### Historia: Generación de Reportes

#### Criterios de Aceptación:

**CA-33**: Generar reporte de actividades por período

```
DADO que tengo permisos para generar reportes
CUANDO selecciono un rango de fechas y genero el reporte
ENTONCES debo recibir un archivo con todas las actividades del período
Y el archivo debe incluir toda la información especificada
```

**CA-34**: Filtros en reportes

```
DADO que estoy generando un reporte
CUANDO aplico filtros específicos (tipo, lugar, oferente)
ENTONCES el reporte debe incluir solo los datos que cumplan los criterios
Y los filtros aplicados deben reflejarse en el nombre del archivo
```

**CA-35**: Múltiples formatos de exportación

```
DADO que tengo un reporte listo
CUANDO selecciono el formato de exportación (Excel, PDF, CSV)
ENTONCES debo recibir el archivo en el formato solicitado
Y el contenido debe ser consistente entre formatos
```

## 8. Manejo de Errores

### Historia: Gestión de Errores del Sistema

#### Criterios de Aceptación:

**CA-36**: Error de conectividad

```
DADO que se pierde la conexión a internet
CUANDO intento realizar una acción en el sistema
ENTONCES debo ver el mensaje "Error de conexión. Intente nuevamente"
Y debo tener un botón "Reintentar" disponible
```

**CA-37**: Error de validación en tiempo real

```
DADO que estoy completando un formulario
CUANDO ingreso datos inválidos en un campo
ENTONCES debo ver feedback visual inmediato (campo en rojo)
Y debo ver el mensaje de error específico debajo del campo
```

**CA-38**: Recuperación automática de sesión

```
DADO que mi sesión expira mientras trabajo
CUANDO intento realizar una acción
ENTONCES debo ver una notificación de sesión expirada
Y debo ser redirigido al login manteniendo el contexto cuando sea posible
```

## Escenarios de Prueba por Funcionalidad

### Pruebas de Integración

#### Escenario 1: Flujo completo de creación de actividad

1. Login como usuario con permisos
2. Navegar al calendario
3. Crear nueva actividad puntual
4. Verificar que aparece en el calendario
5. Adjuntar archivo a la actividad
6. Modificar la actividad
7. Generar reporte que incluya la actividad

#### Escenario 2: Gestión de conflictos

1. Crear actividad en lugar y horario específico
2. Intentar crear segunda actividad en mismo lugar/horario
3. Verificar mensaje de conflicto
4. Aceptar sugerencia de horario alternativo
5. Confirmar que ambas actividades se crearon correctamente

#### Escenario 3: Flujo de permisos

1. Crear usuario con permisos limitados
2. Login como ese usuario
3. Verificar que solo ve funciones autorizadas
4. Intentar acceder a función no autorizada
5. Verificar mensaje de error y redirección

### Criterios de Rendimiento

#### Tiempos de Respuesta Esperados

- **Carga inicial del calendario**: Máximo 3 segundos
- **Cambio de vista (semanal/mensual)**: Máximo 1 segundo
- **Guardado de actividad**: Máximo 2 segundos
- **Subida de archivo (hasta 10MB)**: Máximo 30 segundos
- **Generación de reporte**: Máximo 10 segundos

#### Capacidad del Sistema

- **Usuarios simultáneos**: Mínimo 20 usuarios
- **Actividades por mes**: Mínimo 1000 actividades
- **Archivos por actividad**: Sin límite técnico
- **Tamaño total de archivos**: Limitado por espacio en servidor

### Criterios de Accesibilidad

#### Navegación por Teclado

- Todos los elementos interactivos deben ser accesibles via Tab
- El orden de navegación debe ser lógico e intuitivo
- Los focus indicators deben ser claramente visibles

#### Compatibilidad con Screen Readers

- Todos los formularios deben tener labels apropiados
- Las imágenes informativas deben tener alt text
- La estructura de headings debe ser jerárquica y correcta

#### Responsive Design

- Funcionalidad completa en dispositivos móviles (576px+)
- Elementos táctiles mínimo 44px x 44px
- Texto legible sin zoom en dispositivos móviles
