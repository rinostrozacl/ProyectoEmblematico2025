# Reportes y Consultas - Sistema de Agendamiento Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio

## Reportes Operacionales

### 1. Reporte de Actividades por Período

**Propósito**: Obtener un listado de todas las actividades programadas en un rango de fechas.

**Parámetros**:

- Fecha inicio (obligatorio)
- Fecha fin (obligatorio)
- Tipo de actividad (opcional)
- Estado de actividad (opcional: programada, cancelada, completada)
- Lugar (opcional)

**Información incluida**:

- Nombre de la actividad
- Tipo de actividad
- Fecha y hora de cada cita
- Lugar
- Oferente(s)
- Socio comunitario
- Estado actual
- Cupo (si aplica)

### 2. Reporte de Ocupación de Lugares

**Propósito**: Analizar el uso y ocupación de los diferentes lugares disponibles.

**Parámetros**:

- Período de análisis (mes, trimestre, semestre, año)
- Lugar específico (opcional)

**Información incluida**:

- Nombre del lugar
- Cupo máximo
- Total de horas utilizadas
- Porcentaje de ocupación
- Días de mayor/menor uso
- Tipos de actividades más frecuentes

### 3. Reporte de Actividades por Oferente

**Propósito**: Seguimiento de las actividades realizadas por cada oferente/carrera.

**Parámetros**:

- Período de consulta
- Oferente específico (opcional)

**Información incluida**:

- Nombre del oferente
- Docente responsable
- Cantidad de actividades programadas
- Cantidad de actividades completadas
- Cantidad de actividades canceladas
- Total de horas de actividad
- Tipos de actividad más realizados

### 4. Reporte de Cancelaciones y Reagendamientos

**Propósito**: Análisis de cambios y cancelaciones para identificar patrones y mejoras.

**Parámetros**:

- Período de análisis
- Tipo de evento (cancelaciones, reagendamientos, o ambos)

**Información incluida**:

- Fecha original vs fecha modificada
- Motivo del cambio
- Cantidad de días de anticipación
- Frecuencia por oferente
- Frecuencia por tipo de actividad
- Impacto en recursos (lugares liberados/ocupados)

## Reportes de Gestión

### 5. Dashboard Ejecutivo

**Propósito**: Vista resumen para toma de decisiones gerenciales.

**Información incluida**:

- Total de actividades del mes actual
- Comparativo con mes anterior
- Lugares más utilizados
- Oferentes más activos
- Tasa de cancelaciones
- Proyección de actividades futuras (próximos 30 días)

### 6. Reporte de Socios Comunitarios

**Propósito**: Seguimiento de la colaboración con socios comunitarios.

**Parámetros**:

- Período de análisis
- Socio comunitario específico (opcional)

**Información incluida**:

- Nombre del socio comunitario
- Cantidad de actividades colaborativas
- Tipos de actividad más frecuentes
- Oferentes que más colaboran
- Beneficiarios atendidos
- Frecuencia de colaboración

### 7. Reporte de Utilización por Proyecto

**Propósito**: Seguimiento de actividades agrupadas por proyecto.

**Parámetros**:

- Proyecto específico (opcional)
- Estado del proyecto (activo, completado, etc.)

**Información incluida**:

- Nombre del proyecto
- Fechas de inicio y fin del proyecto
- Actividades asociadas
- Progreso del proyecto (actividades completadas vs programadas)
- Recursos utilizados
- Oferentes participantes

## Reportes de Análisis

### 8. Análisis de Tendencias Temporales

**Propósito**: Identificar patrones de uso por días, semanas, meses.

**Información incluida**:

- Días de la semana más activos
- Horarios de mayor demanda
- Estacionalidad mensual
- Tendencias anuales
- Comparativos año a año

### 9. Reporte de Eficiencia de Recursos

**Propósito**: Optimización del uso de lugares y horarios.

**Información incluida**:

- Lugares subutilizados
- Franjas horarias con baja ocupación
- Conflictos de horarios más frecuentes
- Recomendaciones de optimización
- Análisis de capacidad vs demanda

### 10. Reporte de Participación por Beneficiarios

**Propósito**: Análisis del impacto en diferentes grupos de beneficiarios.

**Parámetros**:

- Tipo de beneficiario
- Período de análisis

**Información incluida**:

- Caracterización de beneficiarios
- Cantidad de actividades dirigidas a cada grupo
- Tipos de actividad más solicitados
- Distribución temporal de actividades
- Cobertura geográfica

## Métricas e Indicadores

### Indicadores Clave de Rendimiento (KPIs)

#### Operacionales

- **Tasa de ocupación de lugares**: (Horas utilizadas / Horas disponibles) × 100
- **Tasa de cancelación**: (Actividades canceladas / Total actividades) × 100
- **Tasa de reagendamiento**: (Actividades reagendadas / Total actividades) × 100
- **Tiempo promedio de anticipación para cancelaciones**
- **Utilización promedio de cupos**: (Participantes reales / Cupos totales) × 100

#### De Calidad

- **Cumplimiento de programación**: (Actividades completadas / Actividades programadas) × 100
- **Satisfacción de usuarios**: Basado en feedback (futuro)
- **Eficiencia de recursos**: Relación costo-beneficio de uso de lugares

#### De Crecimiento

- **Tendencia mensual de actividades**: Crecimiento mes a mes
- **Nuevos socios comunitarios**: Cantidad de nuevas alianzas por período
- **Diversificación de oferentes**: Distribución de actividades entre oferentes
- **Expansión de beneficiarios**: Nuevos grupos atendidos

### Métricas de Sistema

- **Tiempo de respuesta de la aplicación**
- **Disponibilidad del sistema**
- **Usuarios activos por período**
- **Frecuencia de uso por usuario**

## Formatos de Exportación

### Formatos Disponibles

#### Excel (XLSX)

- **Uso**: Reportes detallados con múltiples hojas
- **Ventajas**: Permite análisis adicional, gráficos, filtros
- **Incluye**: Datos tabulares, resúmenes, gráficos básicos

#### PDF

- **Uso**: Reportes ejecutivos y presentaciones
- **Ventajas**: Formato profesional, fácil distribución
- **Incluye**: Resúmenes ejecutivos, gráficos, tablas formateadas

#### CSV

- **Uso**: Integración con otros sistemas, análisis externos
- **Ventajas**: Formato universal, fácil importación
- **Incluye**: Datos en formato tabular simple

#### JSON

- **Uso**: Integración con APIs y sistemas externos
- **Ventajas**: Estructura de datos programática
- **Incluye**: Datos estructurados para procesamiento automático

### Configuración de Exportación

- **Selección de campos**: Permitir elegir qué columnas exportar
- **Filtros aplicados**: Mantener filtros activos en la exportación
- **Formato de fechas**: Configuración regional
- **Separadores**: Configuración para CSV (coma, punto y coma)

## Consultas Dinámicas

### Constructor de Consultas

**Propósito**: Permitir a usuarios avanzados crear consultas personalizadas.

**Funcionalidades**:

- Selección de tablas (actividades, citas, lugares, oferentes)
- Filtros dinámicos por cualquier campo
- Agrupaciones y agregaciones
- Ordenamiento personalizado
- Guardar consultas frecuentes

### Consultas Predefinidas Frecuentes

#### Consulta 1: Actividades de la Semana

```sql
-- Actividades programadas para los próximos 7 días
SELECT nombre, tipo_actividad, fecha, hora_inicio, lugar
FROM actividades_vista
WHERE fecha BETWEEN CURDATE() AND DATE_ADD(CURDATE(), INTERVAL 7 DAY)
ORDER BY fecha, hora_inicio
```

#### Consulta 2: Lugares Disponibles en Horario

```sql
-- Lugares disponibles en un horario específico
SELECT l.nombre, l.cupo
FROM lugares l
WHERE l.id NOT IN (
  SELECT c.lugar_id
  FROM citas c
  WHERE c.fecha = '2024-03-15'
  AND c.hora_inicio <= '14:00'
  AND c.hora_fin >= '13:00'
)
```

#### Consulta 3: Resumen Mensual por Oferente

```sql
-- Actividades por oferente en el mes actual
SELECT o.nombre, COUNT(*) as total_actividades
FROM oferentes o
JOIN actividades_oferentes ao ON o.id = ao.oferente_id
JOIN actividades a ON ao.actividad_id = a.id
JOIN citas c ON a.id = c.actividad_id
WHERE MONTH(c.fecha) = MONTH(CURDATE())
GROUP BY o.id, o.nombre
ORDER BY total_actividades DESC
```

## Automatización de Reportes

### Reportes Programados

- **Frecuencia**: Diaria, semanal, mensual, trimestral
- **Destinatarios**: Lista de correos configurables
- **Formato**: PDF para reportes ejecutivos, Excel para análisis detallado
- **Contenido**: Reportes estándar predefinidos

### Alertas Automáticas

- **Ocupación alta**: Cuando un lugar supera 80% de ocupación
- **Cancelaciones frecuentes**: Cuando un oferente supera umbral de cancelaciones
- **Conflictos detectados**: Cuando se detectan problemas de programación

## Configuración de Acceso a Reportes

### Permisos por Tipo de Reporte

- **Reportes operacionales**: Usuarios con permiso `generar_reportes`
- **Reportes de gestión**: Usuarios con permiso `generar_reportes` y `gestionar_mantenedores`
- **Reportes financieros**: Usuarios con permisos específicos para reportes financieros
- **Consultas dinámicas**: Usuarios con permisos avanzados de reportes

### Configuración de Filtros por Usuario

- **Limitación por oferente**: Usuarios pueden ver solo sus actividades según permisos
- **Limitación por lugar**: Restricción a lugares específicos según permisos asignados
- **Limitación temporal**: Acceso solo a períodos autorizados según configuración de usuario
