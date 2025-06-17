# Guía de Implementación - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

Esta guía proporciona las instrucciones y recomendaciones para los equipos de estudiantes que desarrollarán el Sistema de Agendamiento para el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## Objetivos del Proyecto

Desarrollar un sistema web que permita:

1. Gestionar las actividades que se realizan en el Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio
2. Agendar citas para estas actividades
3. Administrar catálogos de información relacionada

## Equipos de Trabajo

- Equipos de 4-5 estudiantes
- Roles sugeridos:
  - Líder de proyecto
  - Desarrollador 1
  - Desarrollador 2
  - Especialista 3
  - Especialista 4

## Tecnologías a Utilizar

### Backend

- **Node.js + Express**: Framework para desarrollar la API RESTful
- **MySQL**: Sistema de gestión de base de datos relacional
- **Prisma**: ORM obligatorio para gestión de base de datos
- **JWT**: Para manejo de autenticación y sesiones
- **Multer**: Para manejo de carga de archivos
- **Resend**: Para envío de correos electrónicos (recuperación de contraseña)

### Frontend (a elección del equipo)

- **Nuxt.js**: Framework basado en Vue.js para aplicaciones universales
- **Angular**: Framework completo para desarrollo de aplicaciones web
- **Next.js**: Framework React para aplicaciones renderizadas en servidor

### Componentes UI

- Bibliotecas recomendadas según el framework elegido:
  - Bootstrap
  - Tailwind CSS
  - Material UI / PrimeNG / Vuetify (según framework)
- **FullCalendar**: Para la vista de calendario
- **Axios o Fetch**: Para peticiones HTTP a la API (a elección del equipo)

## Pasos para la Implementación

### 1. Configuración del Entorno de Desarrollo

1. Crear **dos repositorios Git separados**:
   - `centro-vinculacion-backend` (API con Node.js + Express + Prisma)
   - `centro-vinculacion-frontend` (interfaz con Angular/Next.js/Nuxt.js)
2. Configurar el entorno de desarrollo:
   - Instalar Node.js y NPM
   - Instalar MySQL
   - Configurar variables de entorno (.env) en cada proyecto
3. Estructurar cada proyecto independientemente:
   - Backend: API RESTful con su propio package.json y dependencias
   - Frontend: Aplicación web con su propio package.json y dependencias

### 2. Implementación de la Base de Datos

1. Configurar Prisma y generar el schema basado en estructura_db.md
2. Ejecutar migraciones de Prisma para crear las tablas en MySQL
3. Configurar datos iniciales (seeds) usando Prisma
4. Crear usuario de base de datos con permisos adecuados

### 3. Implementación del Backend (API)

1. Estructurar la API con Express y Prisma:
   - Rutas (routes)
   - Controladores (controllers)
   - Cliente Prisma configurado
   - Middlewares
   - Utilidades (utils)
2. Implementar autenticación JWT
3. Desarrollar endpoints para todas las entidades usando Prisma
4. Implementar validaciones de entrada
5. Configurar manejo de archivos
6. Configurar Resend para envío de correos de recuperación

### 4. Implementación del Frontend

1. Configurar el framework elegido (Next.js, Nuxt, o Angular)
2. Implementar componentes reutilizables:
   - Formularios con validación
   - Tablas de datos con paginación
   - Componente de calendario
3. Desarrollar las interfaces según las especificaciones
4. Implementar sistema de autenticación
5. Conectar con la API mediante peticiones HTTP (usando Axios o Fetch)

### 5. Pruebas y Optimización

1. Realizar pruebas de funcionalidad
2. Optimizar consultas a la base de datos
3. Implementar caché donde sea apropiado
4. Verificar la experiencia de usuario
5. Probar en diferentes dispositivos (responsividad)

### 6. Despliegue

1. Preparar entornos de producción separados:
   - Servidor para la API backend (puede ser VPS, Railway, Heroku, etc.)
   - Servicio para el frontend (Vercel, Netlify, GitHub Pages, etc.)
2. Desplegar la base de datos MySQL (PlanetScale, Railway, AWS RDS, etc.)
3. Desplegar la API Node.js como servicio independiente
4. Desplegar el frontend apuntando a la URL de la API
5. Configurar CORS en el backend para permitir el dominio del frontend

### 7. Documentación

1. Documentar el código
2. Crear manual de usuario
3. Documentar la API (usando Swagger o similar)
4. Registrar decisiones técnicas importantes

## Estructura de Proyectos Separados

### **Proyecto Backend** (`centro-vinculacion-backend`)

```
centro-vinculacion-backend/
├── config/
├── controllers/
├── middleware/
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   └── seed.js
├── routes/
├── uploads/
├── utils/
├── .env
├── .gitignore
├── app.js
├── package.json
└── README.md
```

### **Proyecto Frontend** (`centro-vinculacion-frontend`)

```
centro-vinculacion-frontend/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── hooks/ (si es React/Next.js)
│   ├── stores/ (si es Vue/Nuxt o Angular)
│   └── assets/
├── .env
├── .gitignore
├── package.json
├── README.md
└── [archivos de configuración del framework]
```

## Recomendaciones Técnicas

### MySQL y API con Prisma

- Utilizar transacciones de Prisma para operaciones que afectan múltiples tablas
- Implementar paginación usando los métodos take y skip de Prisma
- Aprovechar el sistema de tipos de Prisma para mayor seguridad
- Implementar manejo de errores detallado
- Utilizar Prisma Client para todas las operaciones de base de datos

### Seguridad

- Almacenar contraseñas cifradas (bcrypt)
- Validar todas las entradas del usuario
- Implementar protección contra inyección SQL
- Utilizar HTTPS en producción
- Implementar rate limiting para la API
- Configurar CORS adecuadamente para permitir comunicación entre dominios separados

### Desarrollo Frontend

- Separar lógica de presentación (componentes)
- Implementar manejo centralizado de estado (Context API, Redux, Pinia, etc.)
- Utilizar lazy loading para optimizar carga
- Validar formularios tanto en cliente como en servidor
- Manejar estados de carga y errores de forma consistente

## Entregables Esperados

1. **Dos repositorios Git separados**:
   - Backend con API completa y documentada
   - Frontend con todas las interfaces implementadas
2. **Documentación de la API** (Swagger/OpenAPI recomendado)
3. **README detallado en cada proyecto** con instrucciones de instalación
4. **Sistema desplegado y funcionando** (ambos proyectos en producción)
5. **Presentación final** mostrando la arquitectura separada

## Cronograma Sugerido

| Semana | Actividades                                                     |
| ------ | --------------------------------------------------------------- |
| 1      | Configuración del entorno y base de datos. Diseño de interfaces |
| 2      | Implementación de autenticación y estructura base de la API     |
| 3      | Desarrollo de vista calendario y creación de actividades        |
| 4      | Implementación de mantenedores y gestión de archivos            |
| 5      | Finalización de funcionalidades y pruebas                       |
| 6      | Documentación y presentación final                              |

## Recursos Adicionales

### Documentación Oficial

- [Node.js](https://nodejs.org/en/docs/)
- [Express](https://expressjs.com/)
- [MySQL](https://dev.mysql.com/doc/)
- [Prisma](https://www.prisma.io/docs) (obligatorio)
- [JWT](https://jwt.io/)
- Documentación del framework frontend elegido:

  - [Nuxt.js](https://nuxtjs.org/docs/)
  - [Angular](https://angular.io/docs)
  - [Next.js](https://nextjs.org/docs)

### Bibliotecas Útiles

- [FullCalendar](https://fullcalendar.io/) para vista de calendario
- [date-fns](https://date-fns.org/) para manipulación de fechas
- [Joi](https://joi.dev/) o [express-validator](https://express-validator.github.io/) para validaciones
- [Multer](https://github.com/expressjs/multer) para manejo de archivos
- [Resend](https://resend.com/docs) para envío de correos
- [Axios](https://axios-http.com/docs/intro) para peticiones HTTP (alternativa a Fetch nativo)

## Evaluación

El proyecto será evaluado considerando:

- Funcionalidad completa según requerimientos
- Calidad del código y buenas prácticas
- Diseño e implementación de la base de datos
- Experiencia de usuario e interfaz gráfica
- Documentación y presentación final

## Contacto para Consultas

Para dudas o consultas sobre la implementación, contactar a los profesores de la asignatura Desarrollo Web.
