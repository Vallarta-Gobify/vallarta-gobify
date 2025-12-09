# Gestión de Reportes

La sección de Reportes le permite ver, rastrear y gestionar reportes y solicitudes enviados por ciudadanos. Este módulo ayuda a asegurar respuestas oportunas a las necesidades y quejas de los ciudadanos.

## ¿Qué Son los Reportes?

Los reportes son comunicaciones enviadas por ciudadanos que incluyen:
- **Solicitudes de servicio** (ej., solicitudes de asistencia)
- **Quejas** sobre servicios o programas
- **Consultas** sobre estado de programa
- **Problemas** que requieren atención gubernamental
- **Retroalimentación** sobre servicios recibidos
- **Apelaciones** de decisiones

## Acceso a Reportes

1. Haga clic en la pestaña **Reportes** en la navegación principal
2. La lista de reportes se carga mostrando todos los reportes enviados
3. La lista está organizada por fecha de envío (más reciente primero)

[Captura de pantalla: Vista de lista de reportes con filtros de estado]

## Comprensión de la Lista de Reportes

### Tabla de Reportes

La tabla de reportes muestra información clave para evaluación rápida:

**Columnas de la Tabla:**

| Columna | Descripción | Ejemplo |
|--------|-------------|---------|
| **Folio** | Número de referencia del reporte | REP-2025-001234 |
| **Ciudadano** | Nombre del ciudadano | María García López |
| **Tipo** | Tipo de reporte | Solicitud de Apoyo |
| **Categoría** | Categoría del reporte | Programa Social |
| **Fecha** | Fecha de envío | 05/12/2025 14:30 |
| **Estado** | Estado actual | Pendiente |
| **Prioridad** | Nivel de prioridad | Media |
| **Asignado a** | Personal asignado | Juan Pérez |
| **Acciones** | Botones de acción | Ver, Editar |

### Tipos de Reporte

Los reportes se clasifican por tipo:

**Solicitud (Request):**
- Solicitud de asistencia gubernamental
- Solicitud para nuevo programa
- Petición de información
- Solicitud de cita

**Queja (Complaint):**
- Problema de calidad de servicio
- Preocupación sobre comportamiento del personal
- Problema de entrega de programa
- Retraso en procesamiento

**Consulta (Inquiry):**
- Pregunta sobre programa
- Verificación de estado
- Información general
- Necesidad de aclaración

**Incidencia (Incident):**
- Reporte de problema
- Situación de emergencia
- Problema urgente
- Preocupación crítica

**Sugerencia (Suggestion):**
- Idea de mejora
- Retroalimentación sobre servicio
- Mejora de proceso
- Recomendación de programa

**Otro (Other):**
- No encaja en otras categorías
- Circunstancia especial
- Misceláneo

### Categorías de Reporte

Los reportes se organizan además por tema:

- **Programa Social**: Relacionado con programas sociales
- **Documentación**: Problemas relacionados con documentos
- **Atención Ciudadana**: Asuntos de servicio ciudadano
- **Información**: Solicitudes de información
- **Administrativo**: Problemas administrativos
- **Técnico**: Problemas técnicos con el sistema
- **Otro**: Otras categorías

### Tipos de Estado

Cada reporte tiene un estado que indica su estado actual:

| Estado | Color | Significado | Acción Requerida |
|--------|-------|---------|-----------------|
| **Pendiente** | Amarillo | Esperando revisión | Asignar y comenzar revisión |
| **En Revisión** | Azul | Actualmente siendo revisado | Completar evaluación |
| **En Proceso** | Azul Claro | Se está tomando acción | Continuar resolución |
| **Resuelto** | Verde | Resuelto/completado | Cerrar o archivar |
| **Cerrado** | Gris | Cerrado/archivado | No se necesita acción |
| **Cancelado** | Rojo | Cancelado | Documentar razón |

### Niveles de Prioridad

Los reportes se asignan prioridad basada en urgencia:

| Prioridad | Color | Tiempo de Respuesta | Ejemplos |
|----------|-------|---------------|----------|
| **Urgente** | Rojo | Mismo día | Asistencia de emergencia, problemas críticos |
| **Alta** | Naranja | 1-2 días | Suspensión de beneficios, apelaciones importantes |
| **Media** | Amarillo | 3-5 días | Solicitudes estándar, quejas generales |
| **Baja** | Verde | 5-10 días | Sugerencias, consultas generales |

## Búsqueda y Filtrado de Reportes

Encuentre rápidamente reportes específicos usando búsqueda y filtros.

[Captura de pantalla: Barra de búsqueda y opciones de filtro]

### Búsqueda de Reportes

**Buscar por:**

**Número de Folio:**
```
Búsqueda: REP-2025-001234
Resultado: Coincidencia exacta de reporte
```

**Nombre del Ciudadano:**
```
Búsqueda: Maria Garcia
Resultados: Todos los reportes de Maria Garcia
```

**Palabras Clave:**
```
Búsqueda: beca
Resultados: Todos los reportes que mencionan "beca"
```

### Filtrado de Reportes

Aplique filtros para reducir la lista:

**Por Estado:**
```
1. Hacer clic en menú desplegable de filtro "Estado"
2. Seleccionar uno o más estados:
   - Pendiente (para ver qué necesita atención)
   - En Revisión (para ver en qué se está trabajando)
   - Resuelto (para revisar reportes completados)
3. La lista se actualiza para mostrar solo estados seleccionados
```

**Por Tipo, Categoría, Prioridad:**
Similar al filtrado por estado, seleccione de los menús desplegables

**Por Rango de Fechas:**
```
1. Hacer clic en filtro "Rango de Fechas"
2. Seleccionar:
   - Hoy
   - Esta semana
   - Este mes
   - Rango personalizado
3. Aplicar filtro
```

## Visualización de Detalles del Reporte

Ver información completa sobre un reporte específico.

[Captura de pantalla: Vista de detalles del reporte con todas las secciones de información]

### Secciones de Detalles del Reporte

#### Información del Encabezado
- Número de folio (ID único)
- Estado actual con insignia de color
- Nivel de prioridad
- Fecha y hora de envío
- Última actualización
- Miembro del personal asignado (si hay)

#### Información del Ciudadano
- Nombre completo del ciudadano (enlace clicable al perfil)
- CURP
- Número de teléfono
- Dirección de correo electrónico
- Dirección completa
- Lista de programas inscritos

#### Contenido del Reporte
- Tipo y categoría del reporte
- Asunto/título
- Descripción completa (como fue escrita por el ciudadano)
- Método de envío
- Preferencia de idioma

#### Documentos Adjuntos
- Lista de archivos adjuntos
- Acciones: Ver, Descargar

#### Historial de Estado
Línea de tiempo completa mostrando:
- Envío original
- Asignación a personal
- Cambios de estado
- Resolución
- Cierre

#### Notas del Personal
Comunicación interna entre personal (no visible para ciudadano)

#### Comunicaciones con Ciudadano
Registro de correos electrónicos, SMS y notificaciones enviadas

## Gestión del Estado del Reporte

Actualice el estado mientras procesa reportes.

### Cambio de Estado del Reporte

```
1. Abrir detalles del reporte
2. Hacer clic en botón "Cambiar Estado"
3. Seleccionar nuevo estado del menú desplegable
4. Agregar notas requeridas explicando el cambio
5. Hacer clic en "Actualizar Estado"
6. El estado cambia inmediatamente
7. Se envía notificación al ciudadano (si está configurado)
8. El cambio se registra en el historial
```

### Flujo de Trabajo de Estado

**Flujo Típico:**
```
Pendiente (enviado)
    ↓
En Revisión (personal asignado, revisando)
    ↓
En Proceso (se está tomando acción)
    ↓
Resuelto (problema resuelto)
    ↓
Cerrado (archivado, sin acción adicional)
```

### Cuándo Usar Cada Estado

**Pendiente:** Reporte recién enviado, esperando revisión inicial

**En Revisión:** Asignado a miembro del personal, siendo investigado

**En Proceso:** Plan de acción determinado, trabajando activamente en resolución

**Resuelto:** Problema ha sido abordado, ciudadano satisfecho

**Cerrado:** No se necesita más acción, archivado para registros

**Cancelado:** Reporte duplicado, envío inválido, ciudadano retiró solicitud

### Notas Requeridas para Cambios de Estado

Siempre agregue notas explicando:
- ¿Qué acción se tomó?
- ¿Por qué se eligió este estado?
- ¿Cuál es el siguiente paso?
- ¿Cómo se notificó al ciudadano?
- ¿Se necesita algún seguimiento?

## Asignación de Reportes

Distribuya reportes al personal apropiado para manejo.

### Asignación de un Reporte

```
1. Abrir detalles del reporte
2. Hacer clic en botón "Asignar"
3. Seleccionar miembro del personal del menú desplegable
4. Agregar nota de asignación (opcional pero recomendado)
5. Hacer clic en "Asignar"
6. El miembro del personal recibe notificación
7. El reporte aparece en su carga de trabajo
```

### Mejores Prácticas de Asignación

**Asignar Basado En:**
- Experiencia del personal (programas, servicios)
- Carga de trabajo actual (distribuir balance)
- Habilidades de idioma (si se necesita)
- Disponibilidad
- Prioridad del reporte

## Respuesta a Reportes

Comuníquese con ciudadanos sobre sus reportes.

### Envío de Mensajes

```
1. Abrir detalles del reporte
2. Hacer clic en botón "Enviar Mensaje"
3. Elegir método de comunicación:
   - Correo electrónico
   - SMS
   - Notificación del sistema
4. Seleccionar plantilla (opcional)
5. Componer mensaje
6. Vista previa
7. Enviar
8. El mensaje se registra en historial de comunicaciones
```

### Plantillas de Mensaje

**Solicitud Recibida:**
```
Asunto: Reporte Recibido - Folio {FOLIO}

Estimado/a {NOMBRE},

Hemos recibido su reporte con folio {FOLIO}. Su solicitud
está siendo procesada y le contactaremos pronto con una
actualización.

Atentamente,
[Departamento]
```

**En Revisión:**
```
Asunto: Su Reporte Está en Revisión - Folio {FOLIO}

Estimado/a {NOMBRE},

Le informamos que su reporte está actualmente en revisión.
Esperamos proporcionarle una respuesta en {DIAS} días hábiles.
```

**Resuelto:**
```
Asunto: Reporte Resuelto - Folio {FOLIO}

Estimado/a {NOMBRE},

Su reporte ha sido resuelto. [Detalles de la resolución]

Si tiene preguntas, contáctenos.
```

## Tareas Comunes de Gestión de Reportes

### Tarea: Procesar Nuevo Reporte

```
1. Navegar a sección Reportes
2. Filtrar: Estado = Pendiente
3. Ordenar: Prioridad (Urgente primero)
4. Hacer clic en primer reporte pendiente
5. Revisar detalles y adjuntos
6. Asignar a personal apropiado (o a sí mismo)
7. Cambiar estado a En Revisión
8. Agregar notas de evaluación inicial
9. Enviar reconocimiento al ciudadano
10. Establecer recordatorio de seguimiento
```

### Tarea: Limpiar Cola de Pendientes

```
1. Filtrar: Estado = Pendiente
2. Para cada reporte:
   a. Revisión rápida
   b. Asignar a personal
   c. Establecer prioridad
   d. Agregar notas de triaje
3. Meta: Todos los reportes asignados al final del día
```

### Tarea: Seguimiento de Reportes En Proceso

```
1. Filtrar: Estado = En Proceso
2. Filtrar: Asignado a = Yo
3. Revisar cada reporte:
   a. Verificar fecha de última actividad
   b. Si >3 días, actualizar ciudadano
   c. Agregar notas de progreso
   d. Mover a Resuelto si está completo
```

### Tarea: Generar Resumen de Reporte Semanal

```
1. Filtrar: Rango de Fechas = Esta semana
2. Filtrar: Estado = Resuelto
3. Exportar a Excel
4. Analizar:
   - Total resueltos
   - Por tipo
   - Por categoría
   - Tiempo promedio de resolución
5. Compartir con supervisor
```

## Mejores Prácticas

### Rutina Diaria

**Mañana:**
1. Verificar reportes pendientes
2. Revisar prioridades urgentes
3. Responder envíos nocturnos
4. Planear carga de trabajo del día

**Durante el Día:**
1. Procesar reportes en orden de prioridad
2. Actualizar estados regularmente
3. Comunicarse con ciudadanos
4. Documentar todas las acciones

**Fin del Día:**
1. Actualizar todos los reportes en proceso
2. Asegurar que no queden elementos urgentes pendientes
3. Preparar prioridades de mañana
4. Registrar estadísticas diarias

### Estándares de Calidad

**Para Todos los Reportes:**
- Reconocer dentro de 24 horas
- Actualizar estado al menos semanalmente
- Documentar todas las acciones
- Mantener comunicación profesional
- Resolver dentro de plazos publicados

## Solución de Problemas

### No Puede Ver Detalles del Ciudadano

**Verificar:**
- Permisos de usuario
- El registro del ciudadano aún existe
- El enlace es correcto
- Problemas del navegador (intentar actualizar)

### El Mensaje No Se Envía

**Verificar:**
- La dirección de correo electrónico es válida
- El formato del número de teléfono es correcto
- El servicio de correo del sistema funciona
- Intentar método de comunicación alternativo

### El Reporte Está Atascado en Estado

**Revisar:**
- Última acción tomada
- ¿Qué bloquea el progreso?
- ¿Necesita reasignarse?
- ¿Escalar a supervisor?

## Próximos Pasos

Ahora que entiende la gestión de reportes:

- **[Consejos y Trucos](08-tips-and-tricks.md)**: Flujos de trabajo avanzados y consejos de eficiencia
- **[Gestión de Ciudadanos](03-managing-citizens.md)**: Vincule gestión de ciudadanos con reportes
- **[Programas Sociales](04-social-programs.md)**: Conecte reportes con solicitudes de programas

---

**Consejo Profesional**: Cree filtros guardados para sus vistas de reportes más comunes (ej., "Mis Urgentes", "Asignación Pendiente", "Resueltos Esta Semana"). Muchos sistemas le permiten marcar estas vistas filtradas para acceso con un clic.
