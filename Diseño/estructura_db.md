# Estructura de Base de Datos - MySQL

Este documento describe la estructura de la base de datos MySQL para el Sistema de Agendamiento del Proyecto emblemático: Centro Integral Alerce - Vinculación con el medio.

## Modelo Relacional

### Tabla: `usuarios`

Almacena la información de los usuarios del sistema.

```sql
CREATE TABLE usuarios (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL,
  fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  ultimo_acceso TIMESTAMP NULL,
  token_recuperacion VARCHAR(255) NULL,
  token_expiracion TIMESTAMP NULL
);
```

### Tabla: `permisos_usuario`

Almacena los permisos específicos asignados a cada usuario.

```sql
CREATE TABLE permisos_usuario (
  id INT AUTO_INCREMENT PRIMARY KEY,
  usuario_id INT NOT NULL,
  permiso VARCHAR(50) NOT NULL,
  fecha_asignacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  asignado_por INT NULL,
  FOREIGN KEY (usuario_id) REFERENCES usuarios(id) ON DELETE CASCADE,
  FOREIGN KEY (asignado_por) REFERENCES usuarios(id),
  UNIQUE KEY unique_user_permission (usuario_id, permiso)
);
```

**Permisos disponibles**:

- `ver_calendario` - Visualizar calendario
- `crear_actividad_propia` - Crear actividades propias
- `crear_actividad_cualquier` - Crear actividades para cualquier oferente
- `editar_actividad_propia` - Editar actividades propias
- `editar_actividad_cualquier` - Editar cualquier actividad
- `cancelar_actividad_propia` - Cancelar actividades propias
- `cancelar_actividad_cualquier` - Cancelar cualquier actividad
- `reagendar_actividad` - Reagendar actividades
- `gestionar_usuarios` - Crear, editar, eliminar usuarios
- `gestionar_permisos` - Asignar/modificar permisos de usuarios
- `gestionar_mantenedores` - Gestión de catálogos del sistema
- `generar_reportes` - Acceso a sistema de reportes
- `subir_archivos` - Adjuntar archivos a actividades

### Tabla: `tipos_actividad`

Catálogo de tipos de actividades disponibles.

```sql
CREATE TABLE tipos_actividad (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL UNIQUE,
  descripcion TEXT NOT NULL
);
```

### Tabla: `lugares`

Catálogo de lugares donde se pueden realizar actividades.

```sql
CREATE TABLE lugares (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL UNIQUE,
  cupo INT NULL,
  activo BOOLEAN DEFAULT TRUE
);
```

### Tabla: `oferentes`

Catálogo de oferentes de actividades (carreras, etc.).

```sql
CREATE TABLE oferentes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL UNIQUE,
  docente_responsable VARCHAR(100) NOT NULL,
  activo BOOLEAN DEFAULT TRUE
);
```

### Tabla: `socios_comunitarios`

Catálogo de socios comunitarios.

```sql
CREATE TABLE socios_comunitarios (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL UNIQUE,
  activo BOOLEAN DEFAULT TRUE
);
```

### Tabla: `beneficiarios`

Catálogo de beneficiarios del servicio.

```sql
CREATE TABLE beneficiarios (
  id INT AUTO_INCREMENT PRIMARY KEY,
  caracterizacion VARCHAR(200) NOT NULL,
  activo BOOLEAN DEFAULT TRUE
);
```

### Tabla: `proyectos`

Catálogo de proyectos (opcional).

```sql
CREATE TABLE proyectos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL UNIQUE,
  descripcion TEXT NULL,
  fecha_inicio DATE NOT NULL,
  fecha_fin DATE NULL,
  activo BOOLEAN DEFAULT TRUE
);
```

### Tabla: `actividades`

Almacena la información de las actividades.

```sql
CREATE TABLE actividades (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100) NOT NULL,
  tipo_actividad_id INT NOT NULL,
  periodicidad ENUM('Puntual', 'Periódica') NOT NULL,
  fecha_inicio DATE NOT NULL,
  fecha_fin DATE NULL,
  cupo INT NULL,
  socio_comunitario_id INT NOT NULL,
  proyecto_id INT NULL,
  estado ENUM('Programada', 'Cancelada', 'Completada') NOT NULL DEFAULT 'Programada',
  fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  creado_por INT NOT NULL,
  FOREIGN KEY (tipo_actividad_id) REFERENCES tipos_actividad(id),
  FOREIGN KEY (socio_comunitario_id) REFERENCES socios_comunitarios(id),
  FOREIGN KEY (proyecto_id) REFERENCES proyectos(id),
  FOREIGN KEY (creado_por) REFERENCES usuarios(id)
);
```

### Tabla: `actividades_oferentes`

Tabla de relación muchos a muchos entre actividades y oferentes.

```sql
CREATE TABLE actividades_oferentes (
  actividad_id INT NOT NULL,
  oferente_id INT NOT NULL,
  PRIMARY KEY (actividad_id, oferente_id),
  FOREIGN KEY (actividad_id) REFERENCES actividades(id),
  FOREIGN KEY (oferente_id) REFERENCES oferentes(id)
);
```

### Tabla: `actividades_beneficiarios`

Tabla de relación muchos a muchos entre actividades y beneficiarios.

```sql
CREATE TABLE actividades_beneficiarios (
  actividad_id INT NOT NULL,
  beneficiario_id INT NOT NULL,
  PRIMARY KEY (actividad_id, beneficiario_id),
  FOREIGN KEY (actividad_id) REFERENCES actividades(id),
  FOREIGN KEY (beneficiario_id) REFERENCES beneficiarios(id)
);
```

### Tabla: `citas`

Almacena las citas asociadas a las actividades.

```sql
CREATE TABLE citas (
  id INT AUTO_INCREMENT PRIMARY KEY,
  actividad_id INT NOT NULL,
  lugar_id INT NOT NULL,
  fecha DATE NOT NULL,
  hora_inicio TIME NOT NULL,
  hora_fin TIME NULL,
  estado ENUM('Programada', 'Cancelada', 'Completada') NOT NULL DEFAULT 'Programada',
  motivo_cancelacion TEXT NULL,
  fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  creado_por INT NOT NULL,
  FOREIGN KEY (actividad_id) REFERENCES actividades(id),
  FOREIGN KEY (lugar_id) REFERENCES lugares(id),
  FOREIGN KEY (creado_por) REFERENCES usuarios(id)
);
```

### Tabla: `archivos`

Almacena metadatos de archivos adjuntos a las actividades.

```sql
CREATE TABLE archivos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(255) NOT NULL,
  ruta VARCHAR(255) NOT NULL,
  tipo VARCHAR(100) NOT NULL,
  tamano INT NOT NULL,
  actividad_id INT NOT NULL,
  tipo_adjunto VARCHAR(50) NOT NULL,
  descripcion TEXT NULL,
  fecha_carga TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  cargado_por INT NOT NULL,
  FOREIGN KEY (actividad_id) REFERENCES actividades(id),
  FOREIGN KEY (cargado_por) REFERENCES usuarios(id)
);
```

## Relaciones

- Una **Actividad** puede tener múltiples **Citas** (1:N)
- Una **Actividad** puede tener múltiples **Archivos** (1:N)
- Una **Actividad** tiene un **Tipo de Actividad** específico (N:1)
- Una **Actividad** puede estar relacionada con múltiples **Oferentes** (N:M)
- Una **Actividad** está relacionada con un **Socio Comunitario** específico (N:1)
- Una **Actividad** puede estar relacionada con múltiples **Beneficiarios** (N:M)
- Una **Actividad** puede pertenecer a un **Proyecto** (opcional, N:1)
- Una **Cita** se realiza en un **Lugar** específico (N:1)
- Un **Usuario** puede crear múltiples **Actividades**, **Citas** y cargar múltiples **Archivos** (1:N)

## Índices Recomendados

Para optimizar las consultas frecuentes, se recomiendan los siguientes índices:

```sql
-- Índices para búsquedas frecuentes
CREATE INDEX idx_citas_fecha ON citas(fecha, hora_inicio);
CREATE INDEX idx_citas_actividad ON citas(actividad_id, fecha);
CREATE INDEX idx_actividades_estado ON actividades(estado, fecha_inicio);
CREATE INDEX idx_archivos_actividad ON archivos(actividad_id, tipo_adjunto);
```

## Procedimientos Almacenados

### Verificación de Disponibilidad de Lugar

```sql
DELIMITER //
CREATE PROCEDURE verificar_disponibilidad_lugar(
  IN p_lugar_id INT,
  IN p_fecha DATE,
  IN p_hora_inicio TIME,
  IN p_hora_fin TIME,
  IN p_cita_id INT
)
BEGIN
  DECLARE v_ocupado INT;

  -- Verificar si existe otra cita en el mismo lugar, fecha y rango de horas (excluyendo la cita actual si se está editando)
  SELECT COUNT(*) INTO v_ocupado
  FROM citas
  WHERE lugar_id = p_lugar_id
    AND fecha = p_fecha
    AND estado = 'Programada'
    AND (
      (hora_inicio <= p_hora_inicio AND hora_fin >= p_hora_inicio) OR
      (hora_inicio <= p_hora_fin AND hora_fin >= p_hora_fin) OR
      (hora_inicio >= p_hora_inicio AND hora_fin <= p_hora_fin)
    )
    AND (p_cita_id IS NULL OR id != p_cita_id);

  -- Retornar resultado (0 = disponible, 1 = ocupado)
  SELECT v_ocupado AS ocupado;
END //
DELIMITER ;
```

### Creación de Citas para Actividades Periódicas

```sql
DELIMITER //
CREATE PROCEDURE crear_citas_periodicas(
  IN p_actividad_id INT,
  IN p_lugar_id INT,
  IN p_fecha_inicio DATE,
  IN p_fecha_fin DATE,
  IN p_hora_inicio TIME,
  IN p_hora_fin TIME,
  IN p_dias_semana VARCHAR(20), -- Formato: '1,2,3,4,5,6,7' (lunes a domingo)
  IN p_usuario_id INT
)
BEGIN
  DECLARE v_fecha_actual DATE;
  DECLARE v_dia_semana INT;
  DECLARE v_dias_array VARCHAR(20);

  SET v_fecha_actual = p_fecha_inicio;
  SET v_dias_array = CONCAT(',', p_dias_semana, ',');

  -- Iterar sobre el rango de fechas
  WHILE v_fecha_actual <= p_fecha_fin DO
    -- Obtener el día de la semana (1=lunes, 7=domingo)
    SET v_dia_semana = DAYOFWEEK(v_fecha_actual) % 7 + 1;

    -- Verificar si este día de la semana está incluido
    IF LOCATE(CONCAT(',', v_dia_semana, ','), v_dias_array) > 0 THEN
      -- Crear la cita
      INSERT INTO citas (actividad_id, lugar_id, fecha, hora_inicio, hora_fin, creado_por)
      VALUES (p_actividad_id, p_lugar_id, v_fecha_actual, p_hora_inicio, p_hora_fin, p_usuario_id);
    END IF;

    -- Avanzar al siguiente día
    SET v_fecha_actual = DATE_ADD(v_fecha_actual, INTERVAL 1 DAY);
  END WHILE;
END //
DELIMITER ;
```

## Triggers

### Actualizar Estado de Citas al Cancelar Actividad

```sql
DELIMITER //
CREATE TRIGGER tr_actividad_cancelada
AFTER UPDATE ON actividades
FOR EACH ROW
BEGIN
  IF NEW.estado = 'Cancelada' AND OLD.estado != 'Cancelada' THEN
    UPDATE citas
    SET estado = 'Cancelada',
        motivo_cancelacion = CONCAT('Cancelada automáticamente al cancelar la actividad')
    WHERE actividad_id = NEW.id
      AND estado = 'Programada';
  END IF;
END //
DELIMITER ;
```

### Actualizar Último Acceso de Usuario

```sql
DELIMITER //
CREATE TRIGGER tr_actualizar_ultimo_acceso
BEFORE UPDATE ON usuarios
FOR EACH ROW
BEGIN
  IF NEW.ultimo_acceso IS NULL THEN
    SET NEW.ultimo_acceso = CURRENT_TIMESTAMP;
  END IF;
END //
DELIMITER ;
```

## Vistas

### Vista de Próximas Citas

```sql
CREATE VIEW v_proximas_citas AS
SELECT
  c.id,
  a.nombre AS actividad,
  ta.nombre AS tipo_actividad,
  l.nombre AS lugar,
  c.fecha,
  c.hora_inicio,
  c.hora_fin,
  sc.nombre AS socio_comunitario,
FROM citas c
JOIN actividades a ON c.actividad_id = a.id
JOIN tipos_actividad ta ON a.tipo_actividad_id = ta.id
JOIN lugares l ON c.lugar_id = l.id
JOIN socios_comunitarios sc ON a.socio_comunitario_id = sc.id
WHERE c.estado = 'Programada'
  AND c.fecha >= CURDATE()
ORDER BY c.fecha, c.hora_inicio;
```

### Vista de Actividades del Día

```sql
CREATE VIEW v_actividades_dia AS
SELECT
  c.id AS cita_id,
  a.id AS actividad_id,
  a.nombre AS actividad,
  ta.nombre AS tipo_actividad,
  l.nombre AS lugar,
  c.fecha,
  c.hora_inicio,
  c.hora_fin,
  sc.nombre AS socio_comunitario
FROM citas c
JOIN actividades a ON c.actividad_id = a.id
JOIN tipos_actividad ta ON a.tipo_actividad_id = ta.id
JOIN lugares l ON c.lugar_id = l.id
JOIN socios_comunitarios sc ON a.socio_comunitario_id = sc.id
WHERE c.estado = 'Programada'
  AND c.fecha = CURDATE()
ORDER BY c.hora_inicio;
```

## Datos Iniciales

Se recomienda cargar datos iniciales para los catálogos:

```sql
-- Tipos de actividad predefinidos
INSERT INTO tipos_actividad (nombre, descripcion) VALUES
('Capacitación', 'Actividad formativa para desarrollo de habilidades'),
('Taller', 'Actividad práctica grupal'),
('Charla', 'Presentación informativa'),
('Atención', 'Atención personalizada a beneficiarios'),
('Operativo en oficina', 'Operativo realizado en las oficinas del centro'),
('Operativo rural', 'Operativo realizado en zonas rurales'),
('Operativo', 'Operativo general'),
('Práctica profesional', 'Actividad de práctica para estudiantes'),
('Diagnóstico', 'Evaluación inicial de necesidades');

-- Lugares predefinidos
INSERT INTO lugares (nombre, cupo) VALUES
('Oficina del centro', 20),
('Sala de reuniones', 15),
('Auditorio', 100);

-- Usuario administrador inicial
INSERT INTO usuarios (nombre, email, password) VALUES
('Administrador', 'admin@centro-alerce.cl', '$2a$10$...');
```

## Notas para la Implementación

1. Las contraseñas deben almacenarse cifradas (ejemplo usando bcrypt)
2. Implementar validaciones de integridad referencial y unicidad en la API
3. Utilizar transacciones para operaciones que modifican múltiples tablas
4. Considerar implementar soft delete para registros históricos
5. Configurar respaldos automáticos de la base de datos

Esta estructura relacional permite implementar todas las funcionalidades requeridas para el sistema de agendamiento, manteniendo la integridad de los datos y optimizando las consultas frecuentes.
