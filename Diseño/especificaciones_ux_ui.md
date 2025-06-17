# Especificaciones UX/UI - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Paleta de Colores Institucional

### Colores Primarios

- **Azul Institucional**: #003366 (Azul oscuro Santo Tomás)
- **Azul Secundario**: #0066CC (Azul medio)
- **Azul Claro**: #E6F2FF (Para fondos y highlights)

### Colores de Estado

- **Éxito**: #28A745 (Verde)
- **Advertencia**: #FFC107 (Amarillo)
- **Error**: #DC3545 (Rojo)
- **Información**: #17A2B8 (Cian)

### Colores de Actividades (Código de colores para calendario)

- **Capacitación**: #FF6B6B (Coral)
- **Taller**: #4ECDC4 (Turquesa)
- **Charlas**: #45B7D1 (Azul claro)
- **Atenciones**: #96CEB4 (Verde menta)
- **Operativo**: #FFEAA7 (Amarillo claro)
- **Práctica profesional**: #DDA0DD (Violeta claro)
- **Diagnóstico**: #F4A460 (Arena)

## Tipografía

### Fuentes

- **Principal**: "Roboto", Arial, sans-serif
- **Secundaria**: "Open Sans", Arial, sans-serif
- **Monospace**: "Courier New", monospace (para códigos/IDs)

### Jerarquía Tipográfica

- **H1**: 2.5rem (40px) - Títulos principales
- **H2**: 2rem (32px) - Títulos de sección
- **H3**: 1.75rem (28px) - Subtítulos
- **H4**: 1.5rem (24px) - Títulos de componentes
- **Body**: 1rem (16px) - Texto principal
- **Caption**: 0.875rem (14px) - Texto secundario

## Responsive Breakpoints

### Dispositivos Soportados

- **Desktop**: 1200px y superior
- **Laptop**: 992px - 1199px
- **Tablet**: 768px - 991px
- **Mobile**: 576px - 767px
- **Small Mobile**: 575px y menor

### Comportamientos Responsivos

#### Calendario

- **Desktop/Laptop**: Vista semanal completa con 7 días
- **Tablet**: Vista semanal con scroll horizontal
- **Mobile**: Vista diaria con navegación por swipe

#### Formularios

- **Desktop/Laptop**: 2-3 columnas según contenido
- **Tablet**: 2 columnas máximo
- **Mobile**: 1 columna, campos apilados verticalmente

#### Tablas

- **Desktop/Laptop**: Tabla completa
- **Tablet/Mobile**: Scroll horizontal o vista de tarjetas

## Flujos de Navegación

### Flujo Principal del Usuario

1. **Login** → Dashboard/Calendario
2. **Calendario** → Ver actividad → Detalle/Editar/Eliminar
3. **Crear Actividad** → Formulario → Confirmación → Calendario
4. **Mantenedores** → Lista → Crear/Editar → Confirmación → Lista

### Breadcrumbs

- Siempre visible en la parte superior
- Formato: `Inicio > Sección > Subsección`
- Clickeable para navegación rápida

### Navegación Secundaria

- Menú lateral colapsible en desktop
- Menú hamburguesa en mobile
- Accesos rápidos a funciones principales

## Estados de la Aplicación

### Estados de Carga (Loading States)

- **Skeleton screens** para contenido principal
- **Spinners** para acciones rápidas (botones)
- **Progress bars** para cargas de archivos
- **Shimmer effect** para listas y tarjetas

### Estados de Error

- **Error de conexión**: Mensaje con botón "Reintentar"
- **Error de validación**: Highlight en campos con mensaje específico
- **Error 404**: Página personalizada con navegación de regreso
- **Error 500**: Página de error con contacto de soporte

### Estados de Éxito

- **Notificación toast** para acciones exitosas
- **Confirmación modal** para acciones críticas
- **Iconos de check** para validaciones en tiempo real

### Estados Vacíos

- **Sin datos**: Ilustración + mensaje + acción primaria
- **Búsqueda sin resultados**: Sugerencias de búsqueda alternativa
- **Filtros sin resultados**: Opción para limpiar filtros

## Componentes de Interfaz

### Botones

#### Jerarquía

- **Primario**: Azul institucional, texto blanco
- **Secundario**: Borde azul, texto azul, fondo transparente
- **Terciario**: Solo texto azul, sin bordes
- **Destructivo**: Rojo, texto blanco

#### Estados

- **Default**: Estado normal
- **Hover**: Darkening del color base (10%)
- **Active**: Pressed effect con sombra interna
- **Disabled**: 50% opacidad, cursor not-allowed

### Formularios

#### Campos de Entrada

- **Borde**: 1px solid #E0E0E0
- **Focus**: Borde azul institucional, sombra sutil
- **Error**: Borde rojo, mensaje de error debajo
- **Disabled**: Fondo gris claro, texto gris

#### Validación en Tiempo Real

- **Válido**: Icono check verde a la derecha
- **Inválido**: Icono X rojo con mensaje
- **En proceso**: Spinner mientras valida

### Tablas

#### Estructura

- **Header**: Fondo gris claro, texto en negrita
- **Filas alternadas**: Zebra striping para mejor legibilidad
- **Hover**: Highlight sutil de fila
- **Selección**: Checkbox en primera columna

#### Funcionalidades

- **Ordenamiento**: Iconos de flecha en headers clickeables
- **Paginación**: Controles en parte inferior
- **Búsqueda**: Campo de búsqueda en parte superior

## Accesibilidad

### Contraste

- **Mínimo**: 4.5:1 para texto normal
- **Mejorado**: 7:1 para textos importantes
- **Elementos no textuales**: 3:1 mínimo

### Navegación por Teclado

- **Tab order**: Lógico y predecible
- **Focus indicators**: Visible en todos los elementos interactivos
- **Skip links**: Para navegación rápida al contenido principal

### Screen Readers

- **Alt text**: Para todas las imágenes informativas
- **ARIA labels**: Para botones e iconos sin texto
- **Headings**: Estructura jerárquica correcta

### Tamaños de Toque

- **Mínimo**: 44px x 44px para elementos táctiles
- **Espaciado**: 8px mínimo entre elementos clickeables

## Interacciones y Microanimaciones

### Transiciones

- **Duración estándar**: 200ms
- **Easing**: ease-in-out para la mayoría
- **Hover effects**: 100ms para respuesta inmediata

### Animaciones de Página

- **Fade in**: Para modales y overlays
- **Slide**: Para paneles laterales
- **Scale**: Para tooltips y dropdowns

### Feedback Táctil

- **Button press**: Ligera escala hacia abajo (0.95)
- **Card hover**: Elevación con sombra
- **Link hover**: Subrayado animado

## Componentes del Calendario

### Vista Semanal

- **Grid**: 7 columnas (días) x filas dinámicas (horas)
- **Citas**: Bloques con color según tipo de actividad
- **Hover**: Tooltip con información básica
- **Click**: Abrir modal de detalle

### Vista Mensual

- **Grid**: 7 x 6 (semanas máximo en un mes)
- **Indicadores**: Puntos de color para días con actividades
- **Navegación**: Flechas para mes anterior/siguiente

### Interacciones de Arrastrar y Soltar

- **Visual feedback**: Sombra y transparencia durante el arrastre
- **Drop zones**: Highlight de zonas válidas para soltar
- **Validación**: Feedback inmediato si el drop no es válido

## Mensajes y Notificaciones

### Toast Notifications

- **Posición**: Esquina superior derecha
- **Duración**: 5 segundos (éxito/info), 8 segundos (error)
- **Acción**: Botón X para cerrar manualmente

### Modales de Confirmación

- **Overlay**: Fondo semi-transparente oscuro
- **Centrado**: Tanto horizontal como vertical
- **Escape**: Cerrar con ESC o click fuera del modal

### Tooltips

- **Activación**: Hover en desktop, tap en mobile
- **Posición**: Inteligente para evitar salirse de pantalla
- **Contenido**: Máximo 2 líneas de texto

## Iconografía

### Biblioteca de Iconos

- **Biblioteca**: Feather Icons o similares (consistencia)
- **Tamaño estándar**: 24px para interfaz general
- **Tamaño pequeño**: 16px para elementos compactos
- **Tamaño grande**: 48px para estados vacíos

### Iconos Específicos del Sistema

- **Calendario**: Para vistas y navegación temporal
- **Usuario**: Para gestión de usuarios y permisos
- **Configuración**: Para mantenedores y configuración
- **Archivo**: Para gestión de documentos adjuntos
- **Notificación**: Para alertas y mensajes del sistema
