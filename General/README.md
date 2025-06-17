# Sistema de Agendamiento - Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Descripción del Proyecto

Sistema web para la gestión integral de actividades y citas del Centro de Atención de Vinculación con el Medio ubicado en Alerce, Puerto Montt, Chile, perteneciente a Santo Tomás.

### Objetivos del Sistema

- **Gestión de Actividades**: Crear y administrar actividades puntuales y periódicas
- **Calendario Interactivo**: Visualización y gestión de citas en formato calendario
- **Control de Recursos**: Gestión de lugares, oferentes, socios comunitarios y beneficiarios
- **Sistema de Permisos**: Control granular de acceso por usuario
- **Reportería Avanzada**: Generación de reportes operacionales y de gestión
- **Gestión de Archivos**: Adjuntar y gestionar documentos por actividad

## Arquitectura del Sistema

### Stack Tecnológico

**Backend:**

- **Node.js + Express**: API RESTful
- **MySQL**: Base de datos relacional
- **Prisma**: ORM para gestión de base de datos
- **JWT**: Autenticación y autorización
- **Multer**: Gestión de archivos
- **Resend**: Envío de correos (recuperación de contraseña)

**Frontend (Opciones):**

- **Next.js**: Framework React (recomendado)
- **Nuxt.js**: Framework Vue.js
- **Angular**: Framework completo

**Componentes UI:**

- **FullCalendar**: Vista de calendario interactivo
- **Bootstrap/Tailwind**: Framework CSS
- **Axios**: Cliente HTTP para API

### Características Técnicas

- ✅ **Responsive Design**: Adaptable a todos los dispositivos
- ✅ **PWA Ready**: Preparado para aplicación web progresiva
- ✅ **Drag & Drop**: Reagendamiento intuitivo en calendario
- ✅ **Filtros Avanzados**: Múltiples criterios de búsqueda
- ✅ **Exportación Múltiple**: PDF, Excel, CSV, JSON
- ✅ **Gestión de Estados**: Loading, error y success states
- ✅ **Validación en Tiempo Real**: Frontend y backend
- ✅ **Seguridad Avanzada**: JWT, CSRF, Rate Limiting

## Estructura de la Documentación

```
centro_vinculacion/
├── General/
│   ├── README.md                    # Este archivo - visión general
│   └── guia_implementacion.md       # Guía para equipos de desarrollo
├── Requerimientos/
│   ├── README.md                    # Índice de requerimientos
│   ├── requerimientos.md            # Requerimientos funcionales y técnicos
│   ├── reglas_negocio.md           # Políticas y reglas operacionales
│   ├── criterios_aceptacion.md     # Criterios de aceptación (38 criterios)
│   └── validaciones.md             # Validaciones del sistema
├── Diseño/
│   ├── README.md                    # Índice de diseño
│   ├── especificaciones_ux_ui.md    # Guías de diseño y UX
│   ├── interfaces.md               # Interfaces del sistema
│   ├── estructura_db.md            # Diseño de base de datos
│   ├── api_endpoints.md            # Documentación de API REST
│   ├── reportes_consultas.md       # Sistema de reportes
│   └── manejo_errores.md           # Estrategias de manejo de errores
├── mockups/                         # Diagramas y mockups
└── .ia/                            # Gestión del proyecto (IA)
```

## Información del Proyecto

### Contexto Académico

- **Institución**: Santo Tomás - Puerto Montt, Chile
- **Asignatura**: Desarrollo Web
- **Equipos**: 4-5 estudiantes por equipo
- **Centro**: Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

### Alcance del Desarrollo

- **Duración estimada**: 6 semanas
- **Usuarios objetivo**: Personal del centro, oferentes, coordinadores
- **Capacidad**: Mínimo 20 usuarios simultáneos
- **Volumen**: 1000+ actividades por mes

## Enlaces Rápidos

### Para Desarrolladores

- 📋 [Requerimientos Completos](../Requerimientos/requerimientos.md)
- 🎨 [Guías de Diseño](../Diseño/especificaciones_ux_ui.md)
- 🗄️ [Estructura de Base de Datos](../Diseño/estructura_db.md)
- 🔌 [API Endpoints](../Diseño/api_endpoints.md)
- 🚀 [Guía de Implementación](./guia_implementacion.md)

### Para Diseñadores

- 🎨 [Especificaciones UX/UI](../Diseño/especificaciones_ux_ui.md)
- 📱 [Interfaces del Sistema](../Diseño/interfaces.md)
- 🎯 [Criterios de Aceptación](../Requerimientos/criterios_aceptacion.md)

### Para Project Managers

- 📊 [Criterios de Aceptación](../Requerimientos/criterios_aceptacion.md)
- 📋 [Reglas de Negocio](../Requerimientos/reglas_negocio.md)
- 📈 [Sistema de Reportes](../Diseño/reportes_consultas.md)

## Características Principales

### 🗓️ Gestión de Actividades

- Actividades puntuales y periódicas
- Asignación de recursos (lugares, oferentes, beneficiarios)
- Gestión de cupos y capacidades
- Estados: Programada, Cancelada, Completada

### 👥 Sistema de Usuarios

- Registro público abierto para cualquier usuario
- Permisos granulares por usuario (sin roles predefinidos)
- Autenticación JWT segura
- Recuperación de contraseña por email

### 📅 Calendario Interactivo

- Vista semanal y mensual
- Drag & Drop para reagendamiento
- Filtros avanzados (fecha, tipo, lugar, oferente)
- Código de colores por tipo de actividad
- Click para crear desde calendario

### 📁 Gestión de Archivos

- Sin límites de tamaño, tipo o cantidad
- Adjuntar documentos a actividades
- Descarga y visualización de archivos
- Metadatos y descripciones

### 📊 Reportes y Análisis

- 10 tipos de reportes operacionales
- KPIs y métricas del sistema
- Exportación en múltiples formatos
- Dashboard ejecutivo
- Análisis de tendencias

### 🔧 Mantenedores

- Tipos de actividad
- Lugares y capacidades
- Oferentes y docentes responsables
- Socios comunitarios
- Beneficiarios del servicio
- Proyectos (opcional)

## Requerimientos del Sistema

### Técnicos

- **Node.js**: v16+
- **MySQL**: v8.0+
- **Memoria RAM**: 4GB mínimo
- **Espacio disco**: 10GB mínimo (archivos adjuntos)
- **Conexión**: Banda ancha estable

### Navegadores Soportados

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Estado de Desarrollo

### ✅ Documentación Completa

- [x] Requerimientos funcionales y técnicos
- [x] Reglas de negocio específicas
- [x] 38 criterios de aceptación detallados
- [x] Especificaciones UX/UI completas
- [x] Estructura de base de datos
- [x] API REST documentada
- [x] Sistema de validaciones
- [x] Manejo de errores
- [x] Guías de implementación

### 🚀 Listo para Desarrollo

El proyecto cuenta con documentación técnica completa que permite a los equipos de desarrollo:

1. Comenzar implementación inmediatamente
2. Entender todos los requerimientos
3. Seguir las especificaciones de diseño
4. Implementar validaciones y manejo de errores
5. Cumplir con criterios de aceptación definidos

## Contacto y Soporte

Para consultas sobre el proyecto:

- **Profesores**: Asignatura Desarrollo Web
- **Institución**: Santo Tomás Puerto Montt
- **Centro**: Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

---

**Desarrollado para el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio**  
Santo Tomás - Puerto Montt, Chile  
© 2024
