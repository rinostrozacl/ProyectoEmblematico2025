# Sistema de Agendamiento - Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

> **Centro de Atención de Vinculación con el Medio**  
> Santo Tomás - Puerto Montt, Chile

## 🎯 Descripción del Proyecto

Sistema web integral para la gestión de actividades y citas del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio, diseñado para optimizar la coordinación entre oferentes, socios comunitarios y beneficiarios del servicio.

### Objetivos Principales

- ✅ **Gestión completa** de actividades puntuales y periódicas
- ✅ **Calendario interactivo** con vista semanal/mensual
- ✅ **Sistema de permisos** granular por usuario
- ✅ **Reportería avanzada** con múltiples formatos
- ✅ **Gestión de archivos** sin restricciones
- ✅ **Interfaz responsiva** para todos los dispositivos

## 📁 Estructura de la Documentación

La documentación del proyecto está organizada en **3 carpetas principales**:

### 📖 [General/](./General/)

> **Información general del proyecto y guías de implementación**

- **[📋 README Principal](./General/README.md)** - Visión completa del proyecto
- **[🚀 Guía de Implementación](./General/guia_implementacion.md)** - Instrucciones paso a paso para equipos

### 📋 [Requerimientos/](./Requerimientos/)

> **Especificaciones funcionales y criterios de aceptación**

- **[🎯 Requerimientos Principales](./Requerimientos/requerimientos.md)** - Funcionalidades y especificaciones técnicas
- **[📋 Reglas de Negocio](./Requerimientos/reglas_negocio.md)** - Políticas operacionales específicas
- **[✅ Criterios de Aceptación](./Requerimientos/criterios_aceptacion.md)** - 38 criterios específicos
- **[🔍 Validaciones del Sistema](./Requerimientos/validaciones.md)** - Validaciones por interfaz

### 🎨 [Diseño/](./Diseño/)

> **Arquitectura técnica, interfaces y especificaciones de diseño**

- **[🎨 Especificaciones UX/UI](./Diseño/especificaciones_ux_ui.md)** - Guías de diseño y experiencia
- **[📱 Interfaces del Sistema](./Diseño/interfaces.md)** - 14 pantallas documentadas
- **[🗄️ Estructura de Base de Datos](./Diseño/estructura_db.md)** - Diseño completo de BD
- **[🔌 API Endpoints](./Diseño/api_endpoints.md)** - 30+ endpoints documentados
- **[📊 Sistema de Reportes](./Diseño/reportes_consultas.md)** - 10 tipos de reportes
- **[⚠️ Manejo de Errores](./Diseño/manejo_errores.md)** - Estrategias de error handling
- **[📈 Diagramas del Sistema](./Diseño/diagramas_sistema.md)** - Diagramas técnicos completos

## 🚀 Inicio Rápido

### Para Desarrolladores

1. **📖 Lee el README principal**: [General/README.md](./General/README.md)
2. **🎯 Revisa los requerimientos**: [Requerimientos/requerimientos.md](./Requerimientos/requerimientos.md)
3. **🚀 Sigue la guía de implementación**: [General/guia_implementacion.md](./General/guia_implementacion.md)
4. **🎨 Implementa según el diseño**: [Diseño/especificaciones_ux_ui.md](./Diseño/especificaciones_ux_ui.md)

### Para Project Managers

1. **📋 Revisa criterios de aceptación**: [Requerimientos/criterios_aceptacion.md](./Requerimientos/criterios_aceptacion.md)
2. **📋 Estudia reglas de negocio**: [Requerimientos/reglas_negocio.md](./Requerimientos/reglas_negocio.md)
3. **📊 Planifica con los reportes**: [Diseño/reportes_consultas.md](./Diseño/reportes_consultas.md)

### Para Diseñadores UX/UI

1. **🎨 Revisa especificaciones**: [Diseño/especificaciones_ux_ui.md](./Diseño/especificaciones_ux_ui.md)
2. **📱 Estudia las interfaces**: [Diseño/interfaces.md](./Diseño/interfaces.md)
3. **🔍 Valida con criterios**: [Requerimientos/criterios_aceptacion.md](./Requerimientos/criterios_aceptacion.md)

## 🛠️ Stack Tecnológico

### **Backend**

- **Node.js + Express** - API RESTful
- **MySQL 8.0+** - Base de datos relacional
- **Prisma** - ORM para gestión de base de datos
- **JWT** - Autenticación y autorización
- **Multer** - Gestión de archivos sin límites

### **Frontend (Opciones)**

- **Next.js** (React - Recomendado)
- **Nuxt.js** (Vue.js)
- **Angular** (Framework completo)

### **Características Clave**

- **FullCalendar** - Calendario interactivo con drag & drop
- **Responsive Design** - Adaptable a todos los dispositivos
- **Sistema de Permisos** - Granular por usuario (sin roles)
- **Reportes Avanzados** - PDF, Excel, CSV, JSON
- **Validaciones Completas** - Frontend y backend

## 📊 Métricas del Proyecto

| Aspecto                     | Cantidad | Estado           |
| --------------------------- | -------- | ---------------- |
| **Interfaces de Usuario**   | 14       | ✅ Documentadas  |
| **API Endpoints**           | 30+      | ✅ Especificados |
| **Criterios de Aceptación** | 38       | ✅ Definidos     |
| **Tablas de Base de Datos** | 11       | ✅ Diseñadas     |
| **Tipos de Reportes**       | 10       | ✅ Especificados |
| **Mantenedores**            | 6        | ✅ Planificados  |
| **Diagramas Técnicos**      | 7        | ✅ Creados       |

## 📝 Pautas de Evaluación

### 🎯 **Metodología de Evaluación Objetiva**

La evaluación se basa **exclusivamente** en el cumplimiento de los **38 Criterios de Aceptación (CA)** documentados en [criterios_aceptacion.md](./Requerimientos/criterios_aceptacion.md). Cada criterio es **binario**: funciona completamente según especificación = ✅ | no funciona o funciona parcialmente = ❌

---

### 🔍 **Revisión de Avance (50% del proyecto)**

**Primera Nota del Proyecto (mínimo 11 CA para nota 4.0)**

> **Importante**: Cada criterio debe funcionar COMPLETAMENTE. No hay puntos parciales. Un criterio que funciona a medias cuenta como ❌ No Cumplido.

#### **Módulo 1: Autenticación (7 criterios)**

| Criterio  | Descripción              | Verificación Objetiva                                                       |
| --------- | ------------------------ | --------------------------------------------------------------------------- |
| **CA-01** | Login exitoso            | Usuario registrado ingresa credenciales correctas → redirigido a calendario |
| **CA-02** | Login fallido            | Credenciales incorrectas → mensaje "Credenciales incorrectas"               |
| **CA-03** | Campos vacíos login      | Formulario vacío → mensajes error específicos por campo                     |
| **CA-04** | Recuperación exitosa     | Email registrado → mensaje "Se ha enviado un correo"                        |
| **CA-05** | Email no registrado      | Email inexistente → mensaje "El correo no está registrado"                  |
| **CA-06** | Registro público exitoso | Datos válidos → cuenta creada + permisos básicos + redirección              |
| **CA-07** | Email único              | Email existente → mensaje "Este email ya está registrado"                   |

#### **Módulo 2: Gestión Básica de Actividades (9 criterios)**

| Criterio  | Descripción                    | Verificación Objetiva                                               |
| --------- | ------------------------------ | ------------------------------------------------------------------- |
| **CA-08** | Crear actividad puntual        | Formulario completo → actividad en BD + mensaje éxito + redirección |
| **CA-09** | Crear actividad periódica      | Fechas inicio/fin → todas las citas creadas según periodicidad      |
| **CA-10** | Validación campos obligatorios | Campos faltantes → mensajes error específicos + no guardar          |
| **CA-11** | Conflictos de horario          | Lugar ocupado → mensaje específico + sugerencias alternativas       |
| **CA-12** | Modificación exitosa           | Cambios válidos → actualización BD + mensaje éxito                  |
| **CA-13** | Restricción por permisos       | Sin permisos → mensaje "No tiene permisos para modificar"           |
| **CA-14** | Actividad completada           | Estado "Completada" → mensaje "No se puede modificar"               |
| **CA-15** | Cancelación exitosa            | Con motivo → estado "Cancelada" + citas canceladas + mensaje        |
| **CA-16** | Motivo obligatorio             | Sin motivo → mensaje "Debe proporcionar un motivo"                  |

#### **Módulo 3: Calendario Básico (7 criterios)**

| Criterio  | Descripción              | Verificación Objetiva                                        |
| --------- | ------------------------ | ------------------------------------------------------------ |
| **CA-17** | Carga inicial calendario | Primera carga → vista semanal actual + actividades mostradas |
| **CA-18** | Vista mensual            | Click "Vista Mensual" → formato mensual + indicadores días   |
| **CA-19** | Navegación temporal      | Controles anterior/siguiente → navegación sin límites        |
| **CA-20** | Filtros calendario       | Filtros aplicados → solo actividades que cumplen criterios   |
| **CA-21** | Drag & Drop              | Arrastrar cita → mover horario + confirmación                |
| **CA-22** | Crear desde calendario   | Click celda vacía → formulario + fecha/hora preseleccionada  |
| **CA-23** | Ver detalle              | Click actividad → modal con detalles + opciones              |

#### **Módulo 4: Base de Datos y Estructura (3 criterios)**

| Verificación | Descripción         | Criterio Objetivo                                      |
| ------------ | ------------------- | ------------------------------------------------------ |
| **BD-01**    | Estructura completa | 11 tablas creadas según estructura_db.md               |
| **BD-02**    | Permisos granulares | Tabla permisos_usuario implementada + 13 permisos      |
| **BD-03**    | Datos de prueba     | Mínimo 5 usuarios, 10 actividades, todos los catálogos |

---

### 🏆 **Entrega Final (100% del proyecto)**

**Segunda Nota del Proyecto (mínimo 23 CA para nota 4.0)**

> **Aclaración**: La nota final se calcula según la cantidad de criterios cumplidos. Cada criterio debe cumplirse en su totalidad, sin puntos parciales.

#### **Módulos Adicionales Requeridos**

#### **Módulo 5: Sistema de Permisos (3 criterios)**

| Criterio  | Descripción            | Verificación Objetiva                                                       |
| --------- | ---------------------- | --------------------------------------------------------------------------- |
| **CA-24** | Asignación permisos    | Asignar permiso → guardado en BD + usuario accede solo funciones permitidas |
| **CA-25** | Validación tiempo real | Acceso no autorizado → mensaje "No tiene permisos" + redirección            |
| **CA-26** | Interfaz adaptativa    | Permisos específicos → solo botones/opciones autorizadas visibles           |

#### **Módulo 6: Gestión de Archivos (3 criterios)**

| Criterio  | Descripción        | Verificación Objetiva                                                  |
| --------- | ------------------ | ---------------------------------------------------------------------- |
| **CA-27** | Subida archivo     | Archivo válido → subido a servidor + lista actualizada + mensaje éxito |
| **CA-28** | Múltiples archivos | Varios archivos → todos guardados sin reemplazar + lista completa      |
| **CA-29** | Descarga archivo   | Click archivo → descarga correcta + nombre/extensión original          |

#### **Módulo 7: Mantenedores (3 criterios)**

| Criterio  | Descripción                 | Verificación Objetiva                                                      |
| --------- | --------------------------- | -------------------------------------------------------------------------- |
| **CA-30** | Crear elemento catálogo     | Nuevo elemento → guardado BD + disponible en selectores                    |
| **CA-31** | Validación elementos en uso | Elemento en uso → mensaje "No se puede eliminar" + opción deshabilitar     |
| **CA-32** | Deshabilitar elemento       | Opción "Deshabilitar" → marcado inactivo + no en selectores + en histórico |

#### **Módulo 8: Reportes (3 criterios)**

| Criterio  | Descripción         | Verificación Objetiva                                               |
| --------- | ------------------- | ------------------------------------------------------------------- |
| **CA-33** | Reporte por período | Rango fechas → archivo con actividades del período                  |
| **CA-34** | Filtros reportes    | Filtros aplicados → datos que cumplen criterios + filtros en nombre |
| **CA-35** | Múltiples formatos  | Seleccionar formato → archivo en formato correcto                   |

#### **Módulo 9: Manejo de Errores (3 criterios)**

| Criterio  | Descripción            | Verificación Objetiva                                                    |
| --------- | ---------------------- | ------------------------------------------------------------------------ |
| **CA-36** | Error conectividad     | Sin conexión → mensaje "Error de conexión" + botón "Reintentar"          |
| **CA-37** | Validación tiempo real | Datos inválidos → feedback visual inmediato + mensaje específico         |
| **CA-38** | Recuperación sesión    | Sesión expirada → notificación + redirección login + contexto preservado |

---

### 📊 **Sistema de Calificación Objetiva**

#### **Tabla Revisión de Avance (18 CA disponibles)**

| CA Cumplidos | Porcentaje | Nota    | Descripción                               |
| ------------ | ---------- | ------- | ----------------------------------------- |
| **18 CA**    | 100%       | 7.0     | Excelente - Todos los criterios de avance |
| **16-17 CA** | 89-94%     | 6.0-6.5 | Muy bueno - Casi completo                 |
| **14-15 CA** | 78-83%     | 5.0-5.5 | Bueno - Funcionalidades principales       |
| **11-13 CA** | 61-72%     | 4.0-4.5 | Suficiente - Cumple mínimo (60%)          |
| **< 11 CA**  | < 61%      | 1.0-3.9 | Insuficiente - No alcanza el 60%          |

#### **Tabla Entrega Final (38 CA disponibles)**

| CA Cumplidos | Porcentaje | Nota    | Descripción                                |
| ------------ | ---------- | ------- | ------------------------------------------ |
| **37-38 CA** | 97-100%    | 6.5-7.0 | Excelente - Sistema prácticamente completo |
| **33-36 CA** | 87-95%     | 5.5-6.4 | Muy bueno - Sistema avanzado               |
| **29-32 CA** | 76-84%     | 4.5-5.4 | Bueno - Sistema funcional                  |
| **23-28 CA** | 61-74%     | 4.0-4.4 | Suficiente - Cumple mínimo (60%)           |
| **< 23 CA**  | < 61%      | 1.0-3.9 | Insuficiente - No alcanza el 60%           |

### 📋 **Proceso de Evaluación**

#### **Revisión de Avance (Nota 1)**

1. **Demo en vivo**: 15 minutos por equipo
2. **Verificación CA**: Evaluador comprueba los criterios implementados (máximo 18 disponibles)
3. **Checklist binario**: ✅ Funciona completamente | ❌ No funciona/parcial
4. **Nota 1**: Según tabla de avance (11 CA = nota 4.0, 18 CA = nota 7.0)

#### **Entrega Final (Nota 2)**

1. **Demo completa**: 20 minutos por equipo
2. **Verificación exhaustiva**: Todos los 38 CA evaluados
3. **Checklist binario**: ✅ Funciona completamente | ❌ No funciona/parcial
4. **Nota 2**: Según tabla final (23 CA = nota 4.0, 38 CA = nota 7.0)

### 📅 **Fechas y Modalidad**

- **Revisión de Avance**: [Fecha a definir] - Demo + Nota 1 (mínimo 11 CA para aprobar)
- **Entrega Final**: [Fecha a definir] - Demo + Nota 2 (mínimo 23 CA para aprobar)
- **Modalidad**: Presencial, cada equipo demuestra en vivo su sistema funcionando

**Nota Importante**: La evaluación es **100% objetiva**. Cada criterio se evalúa de forma binaria (funciona completamente o no funciona). La nota final se calcula según la cantidad total de criterios cumplidos usando la tabla de rangos.

## ✅ Estado del Proyecto

### 🟢 **Documentación Completa** (100%)

- [x] Requerimientos funcionales y técnicos
- [x] Arquitectura y stack tecnológico definido
- [x] Diseño UX/UI con paleta institucional
- [x] Base de datos con 11 tablas relacionadas
- [x] API REST con 30+ endpoints
- [x] Sistema de validaciones por interfaz
- [x] Manejo integral de errores
- [x] 38 criterios de aceptación específicos

### 🎯 **Listo para Desarrollo**

El proyecto cuenta con documentación técnica que permite:

1. **Comenzar desarrollo inmediatamente**
2. **Implementar sin ambigüedades**
3. **Validar cumplimiento con criterios específicos**
4. **Seguir buenas prácticas de desarrollo**

## 🎨 Características del Sistema

### 🗓️ **Gestión de Actividades**

- Actividades puntuales y periódicas
- Asignación de recursos (lugares, oferentes, beneficiarios)
- Estados: Programada, Cancelada, Completada
- Gestión de cupos opcional

### 📅 **Calendario Interactivo**

- Vista semanal (default) y mensual
- Drag & Drop para reagendamiento
- Filtros avanzados multi-criterio
- Código de colores por tipo
- Click directo para crear

### 👥 **Sistema de Usuarios**

- Registro inicial público (solo primer admin)
- Permisos granulares por usuario
- Sin roles predefinidos
- Autenticación JWT segura

### 📁 **Gestión de Archivos**

- **Sin límites** de tamaño, tipo o cantidad
- Adjuntar a cualquier actividad
- Metadatos y descripciones
- Descarga y visualización

### 📊 **Reportes y Analytics**

- 10 tipos de reportes operacionales
- Exportación en múltiples formatos
- Dashboard ejecutivo con KPIs
- Filtros personalizables

## 🏢 Información Institucional

### Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

- **Ubicación**: Alerce, Puerto Montt, Chile
- **Institución**: Santo Tomás
- **Función**: Centro de Atención de Vinculación con el Medio
- **Objetivo**: Coordinar actividades con la comunidad

### Contexto Académico

- **Asignatura**: Desarrollo Web
- **Modalidad**: Equipos de 4-5 estudiantes
- **Duración**: 3 semanas de desarrollo
- **Entregables**: Sistema funcional

## 📞 Contacto y Soporte

### Para Consultas Técnicas

- **Profesores**: Asignatura Desarrollo Web
- **Institución**: Santo Tomás Puerto Montt
- **Documentación**: Carpetas organizadas en este repositorio

### Para Consultas del Centro

- **Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio**
- **Santo Tomás Puerto Montt**

---

## 🔗 Enlaces Directos

| Tipo de Usuario      | Documentación Recomendada                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **👨‍💻 Desarrollador** | [Requerimientos](./Requerimientos/requerimientos.md) → [Guía](./General/guia_implementacion.md) → [API](./Diseño/api_endpoints.md)                |
| **🎨 Diseñador**     | [UX/UI](./Diseño/especificaciones_ux_ui.md) → [Interfaces](./Diseño/interfaces.md) → [Criterios](./Requerimientos/criterios_aceptacion.md)        |
| **📋 PM**            | [Criterios](./Requerimientos/criterios_aceptacion.md) → [Reglas](./Requerimientos/reglas_negocio.md) → [Reportes](./Diseño/reportes_consultas.md) |
| **🏗️ Arquitecto**    | [README](./General/README.md) → [Base de Datos](./Diseño/estructura_db.md) → [API](./Diseño/api_endpoints.md)                                     |

---

**Desarrollado para el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio**  
_Santo Tomás - Puerto Montt, Chile_  
© 2024 - Documentación Completa ✅
