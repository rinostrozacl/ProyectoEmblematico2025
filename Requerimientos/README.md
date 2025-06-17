# Requerimientos del Sistema - Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

Esta carpeta contiene toda la documentación de requerimientos funcionales y técnicos del Sistema de Agendamiento para el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## 📋 Documentos de Requerimientos

### [🎯 Requerimientos Principales](./requerimientos.md)

**Documento principal** que contiene:

- Requerimientos funcionales completos
- Requerimientos técnicos y de arquitectura
- Lista detallada de 14 interfaces del sistema
- Rutas sugeridas para frontend y backend
- Validaciones del sistema
- Procesos paso a paso
- Entidades del sistema

### [📋 Reglas de Negocio](./reglas_negocio.md)

**Políticas operacionales específicas**:

- Gestión de conflictos de agendamiento
- Políticas de cancelación y reagendamiento
- Gestión de cupos y capacidades
- Comportamientos del calendario
- Sistema de permisos granular
- Gestión de datos maestros

### [✅ Criterios de Aceptación](./criterios_aceptacion.md)

**38 criterios específicos** organizados por funcionalidad:

- Sistema de autenticación (7 criterios)
- Gestión de actividades (9 criterios)
- Gestión del calendario (7 criterios)
- Sistema de permisos (3 criterios)
- Gestión de archivos (3 criterios)
- Mantenedores (3 criterios)
- Reportes y consultas (3 criterios)
- Manejo de errores (3 criterios)

### [🔍 Validaciones del Sistema](./validaciones.md)

**Especificaciones detalladas de validación**:

- Validaciones por interfaz (15 interfaces)
- Mensajes de error específicos
- Validaciones de sistema y seguridad
- Principios generales de presentación

## 🎯 Resumen Ejecutivo

### Objetivo del Sistema

Desarrollar un sistema web para la gestión integral de actividades y citas del Centro de Atención de Vinculación con el Medio ubicado en Alerce, Puerto Montt, Chile.

### Funcionalidades Principales

| Módulo            | Descripción                                      | Criterios |
| ----------------- | ------------------------------------------------ | --------- |
| **Autenticación** | Login, recuperación contraseña, registro inicial | 7         |
| **Actividades**   | CRUD completo, estados, periodicidad             | 9         |
| **Calendario**    | Vista semanal/mensual, drag & drop, filtros      | 7         |
| **Permisos**      | Sistema granular por usuario                     | 3         |
| **Archivos**      | Sin límites, gestión completa                    | 3         |
| **Mantenedores**  | 6 catálogos del sistema                          | 3         |
| **Reportes**      | 10 tipos, múltiples formatos                     | 3         |
| **Errores**       | Manejo integral, recuperación                    | 3         |

### Stack Tecnológico

- **Backend**: Node.js + Express + MySQL + JWT
- **Frontend**: Next.js / Nuxt.js / Angular (a elección)
- **Base de Datos**: MySQL 8.0+
- **Autenticación**: JWT sin roles predefinidos

## 📊 Métricas del Proyecto

### Alcance Técnico

- **14 Interfaces** de usuario definidas
- **30+ Endpoints** de API REST
- **38 Criterios** de aceptación específicos
- **6 Mantenedores** de catálogos
- **10 Reportes** operacionales
- **15 Validaciones** por interfaz

### Capacidad del Sistema

- **Usuarios simultáneos**: 20+ usuarios
- **Volumen mensual**: 1,000+ actividades
- **Archivos**: Sin límites de tamaño/tipo/cantidad
- **Navegadores**: Chrome, Firefox, Safari, Edge

## 🔗 Enlaces Relacionados

### Documentación de Diseño

- [🎨 Especificaciones UX/UI](../Diseño/especificaciones_ux_ui.md)
- [🗄️ Estructura de Base de Datos](../Diseño/estructura_db.md)
- [🔌 API Endpoints](../Diseño/api_endpoints.md)
- [📱 Interfaces del Sistema](../Diseño/interfaces.md)

### Documentación General

- [📖 README Principal](../General/README.md)
- [🚀 Guía de Implementación](../General/guia_implementacion.md)

## ✅ Estado de Completitud

### Documentación de Requerimientos

- [x] **Requerimientos funcionales** - Completo
- [x] **Requerimientos técnicos** - Completo
- [x] **Lista de interfaces** - 14 interfaces documentadas
- [x] **Rutas del sistema** - Frontend y backend
- [x] **Reglas de negocio** - Políticas específicas
- [x] **Criterios de aceptación** - 38 criterios detallados
- [x] **Validaciones** - 15 interfaces validadas
- [x] **Procesos de negocio** - 5 procesos principales

### Nivel de Detalle

- **Requerimientos**: 10/10 - Completamente especificados
- **Criterios**: 10/10 - Formato Gherkin, casos específicos
- **Validaciones**: 10/10 - Mensajes y comportamientos definidos
- **Reglas**: 10/10 - Políticas operacionales claras

## 🎯 Uso de Esta Documentación

### Para Desarrolladores

1. **Comenzar con**: [requerimientos.md](./requerimientos.md) - Visión completa
2. **Implementar según**: [criterios_aceptacion.md](./criterios_aceptacion.md) - Casos específicos
3. **Validar con**: [validaciones.md](./validaciones.md) - Mensajes y comportamientos
4. **Seguir políticas**: [reglas_negocio.md](./reglas_negocio.md) - Reglas operacionales

### Para Project Managers

1. **Planificar con**: Criterios de aceptación (38 items)
2. **Validar cumplimiento**: Cada criterio tiene formato verificable
3. **Gestionar alcance**: Requerimientos claramente definidos
4. **Controlar calidad**: Validaciones específicas documentadas

### Para Stakeholders

1. **Entender funcionalidad**: Requerimientos funcionales
2. **Revisar reglas**: Políticas de negocio específicas
3. **Aprobar criterios**: Casos de aceptación detallados
4. **Validar diseño**: Flujos y procesos documentados

---

**Nota**: Toda la documentación está interconectada. Se recomienda leer los requerimientos principales primero, luego profundizar en las reglas de negocio y criterios de aceptación según la necesidad específica del desarrollo.

_Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio - Santo Tomás Puerto Montt_
