# Diagrama de Flujo del Sistema

El siguiente diagrama muestra el flujo principal de navegación entre las distintas interfaces del sistema:

```mermaid
graph TD
    A[Usuario] -->|Accede| B[Login]
    B -->|Autenticación Exitosa| C[Vista Calendario]
    B -->|Contraseña Olvidada| D[Recuperar Contraseña]
    D -->|Email Enviado| B

    C -->|Ver Detalle| E[Detalle Actividad]
    C -->|Crear Nueva| F[Crear Actividad]
    C -->|Filtrar| Q[Filtros Calendario]
    C -->|Cambiar Vista| R[Vista Semanal/Mensual]

    E -->|Modificar| G[Modificar Actividad]
    E -->|Cancelar| H[Cancelar Actividad]
    E -->|Reagendar| I[Reagendar Actividad]
    E -->|Adjuntar| J[Adjuntar Archivos]

    F -->|Guardar| C
    G -->|Guardar Cambios| C
    H -->|Confirmar Cancelación| C
    I -->|Guardar Nueva Fecha| C
    J -->|Guardar Archivo| E
    Q -->|Aplicar| C
    R -->|Cambiar| C

    C -->|Acceder a Mantenedores| K[Mantenedores]
    K -->|Gestionar Tipos| L[Tipos Actividad]
    K -->|Gestionar Lugares| M[Lugares]
    K -->|Gestionar Oferentes| N[Oferentes]
    K -->|Gestionar Socios| O[Socios Comunitarios]
    K -->|Gestionar Proyectos| P[Proyectos]

    C -->|Generar Reportes| S[Sistema Reportes]
    S -->|Configurar| T[Parámetros Reporte]
    T -->|Exportar| U[Archivo Descarga]

    L -->|Volver| K
    M -->|Volver| K
    N -->|Volver| K
    O -->|Volver| K
    P -->|Volver| K
    U -->|Volver| C

    style B fill:#ffebee
    style C fill:#e8f5e8
    style K fill:#e3f2fd
    style S fill:#fff3e0
```

> **Nota**: Para diagramas técnicos más detallados consulte [Diagramas del Sistema](../Diseño/diagramas_sistema.md)

## Descripción del Flujo

1. El usuario accede al sistema a través de la pantalla de Login.
2. Tras autenticarse correctamente, accede a la Vista de Calendario (pantalla principal).
3. Desde la Vista de Calendario puede:
   - Ver el detalle de una actividad existente
   - Crear una nueva actividad
   - Acceder a los mantenedores
4. Desde el Detalle de Actividad puede:
   - Modificar la actividad
   - Cancelar la actividad
   - Reagendar la actividad
   - Adjuntar nueva información
5. Los mantenedores permiten gestionar los catálogos del sistema:
   - Tipos de actividad
   - Lugares
   - Oferentes
   - Socios comunitarios
   - Proyectos

Este flujo representa las principales interacciones del usuario con el sistema, aunque existen más interacciones detalladas en la documentación de interfaces.
