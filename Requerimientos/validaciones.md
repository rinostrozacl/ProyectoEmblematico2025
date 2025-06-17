# Validaciones y Mensajes de Error - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

Este documento define las validaciones que deben implementarse en el sistema y los mensajes de error que deben mostrarse a los usuarios en cada caso.

## Principios Generales

### Presentación de Errores

- Los mensajes de error deben ser claros, concisos y orientados a la solución
- Usar colores e iconos consistentes (rojo para errores, amarillo para advertencias)
- Mostrar errores cerca del campo relacionado
- Para errores generales, usar notificaciones en la parte superior de la página
- Evitar términos técnicos en los mensajes dirigidos al usuario

### Momento de Validación

- Validación en tiempo real para campos críticos (disponibilidad de email, formato de fecha)
- Validación al perder el foco para campos de formato (email, fecha, hora)
- Validación completa al enviar el formulario

## Validaciones por Interfaz

### 1. Login

| Campo      | Validación               | Mensaje de Error                                                       |
| ---------- | ------------------------ | ---------------------------------------------------------------------- |
| Email      | Campo requerido          | "El email es obligatorio"                                              |
| Email      | Formato válido           | "Por favor, introduce un email válido"                                 |
| Contraseña | Campo requerido          | "La contraseña es obligatoria"                                         |
| General    | Credenciales incorrectas | "Email o contraseña incorrectos. Inténtalo de nuevo"                   |
| General    | Usuario no encontrado    | "No existe ninguna cuenta con este email"                              |
| General    | Error de conexión        | "No se pudo conectar con el servidor. Verifica tu conexión a internet" |

### 2. Recuperación de Contraseña

| Campo   | Validación           | Mensaje de Error                                                       |
| ------- | -------------------- | ---------------------------------------------------------------------- |
| Email   | Campo requerido      | "El email es obligatorio"                                              |
| Email   | Formato válido       | "Por favor, introduce un email válido"                                 |
| Email   | Existe en el sistema | "No hay ninguna cuenta asociada a este email"                          |
| General | Email enviado        | "Se ha enviado un email para restablecer tu contraseña" (confirmación) |
| General | Error al enviar      | "No se pudo enviar el email. Inténtalo más tarde"                      |

### 3. Registro de Usuario (Administrador)

| Campo                | Validación                     | Mensaje de Error                                                                     |
| -------------------- | ------------------------------ | ------------------------------------------------------------------------------------ |
| Nombre               | Campo requerido                | "El nombre es obligatorio"                                                           |
| Nombre               | Longitud mínima (3 caracteres) | "El nombre debe tener al menos 3 caracteres"                                         |
| Email                | Campo requerido                | "El email es obligatorio"                                                            |
| Email                | Formato válido                 | "Por favor, introduce un email válido"                                               |
| Email                | No existe en el sistema        | "Ya existe una cuenta con este email"                                                |
| Rol                  | Campo requerido                | "El rol es obligatorio"                                                              |
| Contraseña           | Campo requerido                | "La contraseña es obligatoria"                                                       |
| Contraseña           | Longitud mínima (6 caracteres) | "La contraseña debe tener al menos 6 caracteres"                                     |
| Contraseña           | Complejidad                    | "La contraseña debe incluir al menos una letra mayúscula, una minúscula y un número" |
| Confirmar Contraseña | Coincide con contraseña        | "Las contraseñas no coinciden"                                                       |

### 4. Crear Actividad

| Campo                    | Validación                       | Mensaje de Error                                                             |
| ------------------------ | -------------------------------- | ---------------------------------------------------------------------------- |
| Nombre                   | Campo requerido                  | "El nombre de la actividad es obligatorio"                                   |
| Nombre                   | Longitud máxima (100 caracteres) | "El nombre no puede exceder los 100 caracteres"                              |
| Tipo de Actividad        | Campo requerido                  | "El tipo de actividad es obligatorio"                                        |
| Periodicidad             | Campo requerido                  | "La periodicidad es obligatoria"                                             |
| Fecha (Puntual)          | Campo requerido                  | "La fecha es obligatoria"                                                    |
| Fecha (Puntual)          | Fecha futura                     | "La fecha debe ser posterior a hoy"                                          |
| Fecha Inicio (Periódica) | Campo requerido                  | "La fecha de inicio es obligatoria"                                          |
| Fecha Inicio (Periódica) | Fecha futura                     | "La fecha de inicio debe ser posterior a hoy"                                |
| Fecha Fin (Periódica)    | Mayor que fecha inicio           | "La fecha de fin debe ser posterior a la fecha de inicio"                    |
| Hora                     | Formato válido                   | "La hora debe tener un formato válido (HH:MM)"                               |
| Hora                     | Rango horario (8:00-20:00)       | "La hora debe estar entre las 8:00 y las 20:00"                              |
| Lugar                    | Campo requerido                  | "El lugar es obligatorio"                                                    |
| Oferentes                | Al menos uno seleccionado        | "Debe seleccionar al menos un oferente"                                      |
| Socio Comunitario        | Campo requerido                  | "El socio comunitario es obligatorio"                                        |
| Beneficiarios            | Al menos uno seleccionado        | "Debe seleccionar al menos un beneficiario"                                  |
| Cupo                     | Valor numérico positivo          | "El cupo debe ser un número positivo"                                        |
| Cupo                     | No excede capacidad del lugar    | "El cupo excede la capacidad del lugar seleccionado"                         |
| Archivos                 | Tamaño máximo (10MB)             | "El archivo no puede superar los 10MB"                                       |
| Archivos                 | Formato permitido                | "Formato de archivo no permitido. Sube un archivo PDF, DOC, DOCX, JPG o PNG" |

### 5. Modificar Actividad

| Campo                                        | Validación        | Mensaje de Error                                         |
| -------------------------------------------- | ----------------- | -------------------------------------------------------- |
| [Mismas validaciones que en Crear Actividad] |                   |                                                          |
| Actividad                                    | No está cancelada | "No se puede modificar una actividad cancelada"          |
| Actividad                                    | No ha pasado      | "No se puede modificar una actividad que ya ha ocurrido" |

### 6. Cancelar Actividad

| Campo     | Validación                      | Mensaje de Error                                        |
| --------- | ------------------------------- | ------------------------------------------------------- |
| Actividad | Seleccionada                    | "Debe seleccionar una actividad para cancelar"          |
| Actividad | No está cancelada               | "Esta actividad ya está cancelada"                      |
| Actividad | No ha pasado                    | "No se puede cancelar una actividad que ya ha ocurrido" |
| Motivo    | Campo requerido                 | "El motivo de cancelación es obligatorio"               |
| Motivo    | Longitud mínima (10 caracteres) | "El motivo debe tener al menos 10 caracteres"           |

### 7. Reagendar Actividad

| Campo          | Validación                      | Mensaje de Error                                                        |
| -------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Actividad/Cita | Seleccionada                    | "Debe seleccionar una actividad/cita para reagendar"                    |
| Actividad/Cita | No está cancelada               | "No se puede reagendar una actividad/cita cancelada"                    |
| Actividad/Cita | No ha pasado                    | "No se puede reagendar una actividad/cita que ya ha ocurrido"           |
| Motivo         | Campo requerido                 | "El motivo del cambio es obligatorio"                                   |
| Motivo         | Longitud mínima (10 caracteres) | "El motivo debe tener al menos 10 caracteres"                           |
| Nueva Fecha    | Campo requerido                 | "La nueva fecha es obligatoria"                                         |
| Nueva Fecha    | Fecha futura                    | "La nueva fecha debe ser posterior a hoy"                               |
| Nueva Hora     | Formato válido                  | "La hora debe tener un formato válido (HH:MM)"                          |
| Nueva Hora     | Rango horario (8:00-20:00)      | "La hora debe estar entre las 8:00 y las 20:00"                         |
| Lugar y Hora   | Disponibilidad                  | "El lugar seleccionado no está disponible en la fecha y hora indicadas" |

### 8. Adjuntar Información

| Campo       | Validación                       | Mensaje de Error                                                             |
| ----------- | -------------------------------- | ---------------------------------------------------------------------------- |
| Actividad   | Seleccionada                     | "Debe seleccionar una actividad"                                             |
| Archivo     | Campo requerido                  | "Debe seleccionar un archivo para subir"                                     |
| Archivo     | Tamaño máximo (10MB)             | "El archivo no puede superar los 10MB"                                       |
| Archivo     | Formato permitido                | "Formato de archivo no permitido. Sube un archivo PDF, DOC, DOCX, JPG o PNG" |
| Descripción | Longitud máxima (200 caracteres) | "La descripción no puede exceder los 200 caracteres"                         |

### 9. Mantenedores (General)

| Campo       | Validación                       | Mensaje de Error                                                   |
| ----------- | -------------------------------- | ------------------------------------------------------------------ |
| Nombre      | Campo requerido                  | "El nombre es obligatorio"                                         |
| Nombre      | Longitud máxima (100 caracteres) | "El nombre no puede exceder los 100 caracteres"                    |
| Nombre      | No duplicado                     | "Ya existe un registro con este nombre"                            |
| Eliminación | No tiene relaciones              | "No se puede eliminar porque está siendo utilizado en actividades" |

### 10. Tipos de Actividad (Mantenedor)

| Campo       | Validación                       | Mensaje de Error                                     |
| ----------- | -------------------------------- | ---------------------------------------------------- |
| Nombre      | Campo requerido                  | "El nombre del tipo de actividad es obligatorio"     |
| Nombre      | No duplicado                     | "Ya existe un tipo de actividad con este nombre"     |
| Descripción | Campo requerido                  | "La descripción es obligatoria"                      |
| Descripción | Longitud máxima (500 caracteres) | "La descripción no puede exceder los 500 caracteres" |

### 11. Lugares (Mantenedor)

| Campo  | Validación              | Mensaje de Error                      |
| ------ | ----------------------- | ------------------------------------- |
| Nombre | Campo requerido         | "El nombre del lugar es obligatorio"  |
| Nombre | No duplicado            | "Ya existe un lugar con este nombre"  |
| Cupo   | Valor numérico positivo | "El cupo debe ser un número positivo" |

### 12. Oferentes (Mantenedor)

| Campo               | Validación      | Mensaje de Error                        |
| ------------------- | --------------- | --------------------------------------- |
| Nombre              | Campo requerido | "El nombre del oferente es obligatorio" |
| Nombre              | No duplicado    | "Ya existe un oferente con este nombre" |
| Docente Responsable | Campo requerido | "El docente responsable es obligatorio" |

### 13. Socios Comunitarios (Mantenedor)

| Campo  | Validación      | Mensaje de Error                                 |
| ------ | --------------- | ------------------------------------------------ |
| Nombre | Campo requerido | "El nombre del socio comunitario es obligatorio" |
| Nombre | No duplicado    | "Ya existe un socio comunitario con este nombre" |

### 14. Beneficiarios (Mantenedor)

| Campo           | Validación                       | Mensaje de Error                                         |
| --------------- | -------------------------------- | -------------------------------------------------------- |
| Caracterización | Campo requerido                  | "La caracterización es obligatoria"                      |
| Caracterización | Longitud máxima (200 caracteres) | "La caracterización no puede exceder los 200 caracteres" |

### 15. Proyectos (Mantenedor)

| Campo        | Validación             | Mensaje de Error                                          |
| ------------ | ---------------------- | --------------------------------------------------------- |
| Nombre       | Campo requerido        | "El nombre del proyecto es obligatorio"                   |
| Nombre       | No duplicado           | "Ya existe un proyecto con este nombre"                   |
| Fecha Inicio | Campo requerido        | "La fecha de inicio es obligatoria"                       |
| Fecha Fin    | Mayor que fecha inicio | "La fecha de fin debe ser posterior a la fecha de inicio" |

## Validaciones de Sistema

### Conflictos de Agenda

| Escenario            | Validación               | Mensaje de Error                                             |
| -------------------- | ------------------------ | ------------------------------------------------------------ |
| Lugar ocupado        | Verificar disponibilidad | "El lugar ya está reservado para esta fecha y hora"          |
| Actividad simultánea | Verificar solapamiento   | "Ya existe otra actividad programada para esta fecha y hora" |

### Permisos y Autenticación

| Escenario            | Validación                  | Mensaje de Error                                             |
| -------------------- | --------------------------- | ------------------------------------------------------------ |
| Sesión expirada      | Verificar token             | "Tu sesión ha expirado. Por favor, inicia sesión nuevamente" |
| Acceso no autorizado | Verificar permisos          | "No tienes permisos para realizar esta acción"               |
| Operación prohibida  | Verificar reglas de negocio | "Esta operación no está permitida"                           |

## Buenas Prácticas para el Manejo de Errores

1. **Validación en Capas**:

   - Validar en el frontend para retroalimentación inmediata
   - Validar en el backend para garantizar la integridad de los datos
   - Implementar validaciones a nivel de base de datos para consistencia

2. **Errores Amigables**:

   - Traducir errores técnicos a mensajes comprensibles
   - Ofrecer soluciones cuando sea posible
   - Mantener un tono constructivo y no culpabilizador

3. **Gestión de Fallos de Red**:

   - Detectar problemas de conectividad
   - Permitir reintento de operaciones
   - Almacenar temporalmente datos en caso de fallos

4. **Registro de Errores**:
   - Registrar errores graves para su análisis
   - Incluir información contextual (no sensible)
   - Facilitar la depuración sin comprometer la privacidad del usuario
