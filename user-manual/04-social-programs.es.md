# Gestión de Programas Sociales

La sección de Programas Sociales es el núcleo de Gobify, donde usted gestiona programas de asistencia federales y locales, rastrea beneficiarios, crea solicitudes y genera reportes.

## Acceso a Programas Sociales

1. Haga clic en la pestaña **Programas Sociales** en la navegación principal
2. La lista de programas se carga, mostrando todos los programas disponibles según su rol

[Captura de pantalla: Lista de programas mostrando programas federales y locales]

## Comprensión de los Tipos de Programas

Gobify gestiona dos categorías distintas de programas sociales:

### Programas Federales

**Características:**
- Financiados por el gobierno federal
- Requisitos estandarizados a nivel nacional
- Típicamente presupuestos más grandes
- Requisitos estrictos de cumplimiento
- Etiquetados con insignia "Federal"

**Ejemplos:**
- Programa Federal de Becas
- Apoyo Alimentario Federal
- Pensión para Adultos Mayores

### Programas Locales

**Características:**
- Financiados por gobierno municipal/estatal
- Requisitos específicos de la comunidad
- Más flexibilidad en elegibilidad
- Procesos de aprobación más rápidos
- Etiquetados con insignia "Local"

**Ejemplos:**
- Apoyo a Madres Solteras
- Becas Municipales
- Mejoramiento de Vivienda

### Su Nivel de Acceso

Su rol de usuario determina qué programas puede ver:

| Rol de Usuario | Programas Federales | Programas Locales |
|-----------|-----------------|----------------|
| Solo federal | ✓ Sí | ✗ No |
| Solo local | ✗ No | ✓ Sí |
| Acceso completo | ✓ Sí | ✓ Sí |

## Exploración de Programas Sociales

### Vista de Lista de Programas

[Captura de pantalla: Lista de programas mostrando tarjetas con nombres de programas, tipos y conteos de beneficiarios]

La lista de programas muestra tarjetas o filas para cada programa:

**Información de Tarjeta:**
- Nombre del programa
- Insignia de tipo de programa (Federal/Local)
- Número de beneficiarios activos
- Número de solicitudes pendientes
- Descripción breve
- Botón "Ver Detalles"

### Ordenamiento y Filtrado

**Ordenar Programas:**
- Por nombre (alfabéticamente)
- Por conteo de beneficiarios (más/menos)
- Por tipo (Federal o Local)
- Por estado (Activo, Cerrado, Próximo)

**Filtrar Programas:**
1. Use el menú desplegable de filtros en la parte superior
2. Seleccione criterios:
   - Tipo de programa (Federal/Local)
   - Estado (Activo/Inactivo)
   - Categoría (Educación, Salud, Vivienda, etc.)
3. Ver resultados filtrados

**Buscar Programas:**
1. Escriba en el cuadro de búsqueda
2. La búsqueda encuentra coincidencias en:
   - Nombre del programa
   - Descripción
   - Categoría
3. Los resultados se actualizan en tiempo real

## Visualización de Detalles del Programa

Para ver información completa sobre un programa social:

1. **Haga clic en la tarjeta del programa** o botón "Ver Detalles"
2. **La página de detalles del programa se abre** con información completa

[Captura de pantalla: Página de detalles del programa con pestañas y mapa]

### Secciones de Detalles del Programa

#### Pestaña de Descripción General

**Información General:**
- Nombre completo del programa
- Tipo de programa (Federal/Local)
- Categoría del programa (Educación, Salud, etc.)
- Descripción y objetivos
- Requisitos de elegibilidad
- Documentos requeridos
- Monto o tipo de beneficio
- Duración del programa

**Estadísticas:**
- Beneficiarios totales: 1,247
- Solicitudes activas: 234
- Aprobadas este mes: 156
- Revisiones pendientes: 78
- Utilización de presupuesto: 68%

**Estado del Programa:**
- Abierto para nuevas solicitudes
- Fecha límite de solicitud
- Próxima fecha de revisión

#### Lista de Beneficiarios

[Captura de pantalla: Tabla mostrando todos los beneficiarios inscritos en el programa]

**Columnas de la Tabla:**
- Nombre del beneficiario
- CURP
- Folio (número de solicitud)
- Dirección
- Fecha de inscripción
- Estado (Activo, Suspendido, Completado)
- Monto del beneficio
- Fecha del último pago

**Buscar Beneficiarios:**

La búsqueda es extremadamente flexible. Puede buscar por:

1. **Nombre**
   ```
   Búsqueda: Maria Garcia
   Resultados: Todos los beneficiarios llamados Maria Garcia
   ```

2. **Folio (Número de Solicitud)**
   ```
   Búsqueda: 2024-001234
   Resultados: Solicitud específica por número de folio
   ```

3. **Dirección**
   ```
   Búsqueda: Calle Juarez
   Resultados: Todos los beneficiarios que viven en Calle Juarez
   ```

4. **Colonia**
   ```
   Búsqueda: Centro
   Resultados: Todos los beneficiarios en la colonia Centro
   ```

5. **Búsqueda Combinada**
   ```
   Búsqueda: Garcia Centro
   Resultados: Residentes con apellido Garcia en Centro
   ```

**Cómo Funciona la Búsqueda:**
- Busca en todos los campos simultáneamente
- Funcionan las coincidencias parciales
- No distingue entre mayúsculas y minúsculas
- Resultados en tiempo real mientras escribe

#### Vista de Mapa

El mapa interactivo muestra las ubicaciones de los beneficiarios visualmente.

[Captura de pantalla: Mapa Mapbox con marcadores de clúster y pines individuales]

**Características del Mapa:**

**Marcadores de Clúster:**
- Grupos de beneficiarios cercanos aparecen como círculos numerados
- El número indica cuántos beneficiarios hay en esa área
- La intensidad del color muestra densidad (más oscuro = más beneficiarios)

**Acercamiento:**
- Haga clic en un marcador de clúster para acercarse
- Los clústeres se dividen en clústeres más pequeños
- Eventualmente aparecen marcadores individuales

**Marcadores Individuales:**
- Un pin individual representa un beneficiario
- Haga clic en el pin para ver ventana emergente con:
  - Nombre del beneficiario
  - Dirección
  - Número de folio
  - Estado
  - Enlace "Ver Detalles"

**Controles del Mapa:**

[Captura de pantalla: Controles del mapa mostrando botones de zoom y ubicación]

- **Botones +/-**: Acercar y alejar
- **Botón de ubicación**: Recentrar mapa
- **Pantalla completa**: Expandir mapa a pantalla completa
- **Rueda del mouse**: Acercar/alejar
- **Hacer clic y arrastrar**: Desplazarse por el mapa

**Uso del Mapa:**

1. **Encontrar Áreas de Alta Densidad**
   ```
   1. Buscar marcadores de clúster grandes
   2. Estos muestran dónde viven la mayoría de los beneficiarios
   3. Útil para planificar eventos de difusión
   4. Identificar áreas desatendidas
   ```

2. **Localizar Beneficiario Específico**
   ```
   1. Buscar nombre del beneficiario
   2. El mapa se centra automáticamente en su ubicación
   3. El marcador se resalta
   4. Hacer clic para ventana emergente de detalles
   ```

3. **Planificar Visitas de Campo**
   ```
   1. Acercarse a colonia específica
   2. Ver todos los beneficiarios en esa área
   3. Hacer clic en cada marcador para anotar direcciones
   4. Planificar ruta de visita eficiente
   ```

4. **Analizar Distribución Geográfica**
   ```
   1. Alejar para ver toda la ciudad
   2. Notar qué áreas tienen más beneficiarios
   3. Identificar brechas en cobertura
   4. Planificar campañas de inscripción dirigidas
   ```

**Mejores Prácticas del Mapa:**
- Use clústeres para entender patrones de distribución
- Acérquese progresivamente en lugar de saltar al zoom máximo
- Use búsqueda para localizar direcciones específicas rápidamente
- Tome capturas de pantalla para reportes (use modo de pantalla completa)

#### Pestaña de Documentos

Ver y gestionar documentos relacionados con el programa:
- Lineamientos del programa (PDF)
- Formularios de solicitud
- Listas de verificación de documentos requeridos
- Formularios de muestra completados
- Anuncios del programa

## Creación de Nuevas Solicitudes de Programa

Cuando un ciudadano solicita un programa, usted crea una solicitud en el sistema.

### Flujo de Trabajo de Creación de Solicitudes

[Captura de pantalla: Formulario de creación de solicitud paso a paso]

#### Paso 1: Información del Ciudadano

1. **Haga clic en el botón "Nueva Solicitud"** en la página de detalles del programa
2. **Ingrese o busque al ciudadano:**

   **Opción A - Ciudadano Existente:**
   ```
   1. Escribir nombre o CURP en el cuadro de búsqueda
   2. Seleccionar ciudadano del menú desplegable
   3. La información se completa automáticamente
   4. Hacer clic en "Siguiente"
   ```

   **Opción B - Nuevo Ciudadano:**
   ```
   1. Hacer clic en "Registrar Nuevo Ciudadano"
   2. Completar información personal:
      - Nombre completo (como aparece en la identificación)
      - CURP (18 caracteres)
      - Fecha de nacimiento
      - Género
      - Número de teléfono
      - Correo electrónico (si está disponible)
   3. Hacer clic en "Siguiente"
   ```

**Campos Requeridos:**
- Nombre completo (requerido)
- CURP (requerido, validado por formato)
- Fecha de nacimiento (requerido)
- Género (requerido)
- Número de teléfono (requerido, contacto principal)

**Campos Opcionales:**
- Teléfono secundario
- Dirección de correo electrónico
- Ocupación
- Estado civil

**Validación:**
- Formato de CURP verificado automáticamente
- Advertencia de CURP duplicado si ya existe
- Formato de teléfono validado
- Edad calculada desde fecha de nacimiento

#### Paso 2: Información de Dirección

[Captura de pantalla: Formulario de dirección con campos de calle, colonia, código postal]

**Complete la dirección:**

1. **Información de Calle:**
   - Seleccione calle del menú desplegable (busca mientras escribe)
   - O haga clic en "Agregar Nueva Calle" si no se encuentra
   - Ingrese número de calle (exterior)
   - Ingrese número interior (si aplica, ej., apartamento)

2. **Colonia:**
   - Seleccione colonia del menú desplegable
   - O haga clic en "Agregar Nueva Colonia" si no se encuentra
   - Completa automáticamente el código postal cuando está disponible

3. **Detalles Adicionales:**
   - Código postal (CP)
   - Referencias (ej., "entre Hidalgo y Morelos")
   - Puntos de referencia de la colonia

**Consejos:**
- Use búsqueda en menú desplegable de calles: escribir "Jua" encuentra "Calle Juárez"
- Si la dirección no existe, agregue calle/colonia primero (ver guía de Datos Geográficos)
- Proporcione referencias para visitas de campo más fáciles
- Verifique que el código postal coincida con la colonia

#### Paso 3: Información Escolar

**Solo para programas relacionados con educación (ej., programas de becas)**

[Captura de pantalla: Formulario de información escolar]

**Detalles del Estudiante:**
- Nombre de la escuela (seleccionar del menú desplegable)
- Nivel escolar (Primaria, Secundaria, Preparatoria, Universidad)
- Grado/semestre
- Número de identificación del estudiante
- Dirección de la escuela (si es diferente a la de casa)

**Información Académica:**
- Promedio de calificaciones actual
- Porcentaje de asistencia
- Necesidades especiales (si aplica)

**Omitir Este Paso:**
- Si no es un programa educativo, este paso está oculto
- Haga clic en "Siguiente" para continuar

#### Paso 4: Revisar y Enviar

[Captura de pantalla: Pantalla de revisión mostrando toda la información ingresada]

**Revisar Toda la Información:**
- Detalles del ciudadano
- Dirección completa
- Información escolar (si aplica)
- Programa seleccionado
- Lista de verificación de documentos requeridos

**Antes de Enviar:**
1. **Verifique que toda la información sea correcta**
2. **Revise errores tipográficos en nombres y CURP**
3. **Confirme que la dirección esté completa**
4. **Asegúrese de que todos los campos requeridos estén llenos**

**Enviar Solicitud:**
1. Revisar el resumen
2. Hacer clic en "Enviar Solicitud"
3. El sistema genera número de folio
4. Aparece mensaje de confirmación
5. La solicitud aparece en la lista pendiente

**Número de Folio:**
```
Ejemplo: 2025-FED-001234

Formato: AÑO-TIPO-NÚMERO
- 2025: Año actual
- FED: Federal (o LOC para local)
- 001234: Número secuencial
```

**Guarde este número de folio** - es el identificador único de la solicitud.

### Después de Crear la Solicitud

**Próximos Pasos:**
1. Estado de solicitud: Pendiente
2. Aparece en solicitudes pendientes del programa
3. Espera carga de documentos y revisión
4. Se puede editar antes de la aprobación

**Notificar al Ciudadano:**
- Proporcionar número de folio
- Listar documentos requeridos
- Explicar próximos pasos
- Establecer expectativa para cronograma de revisión

## Edición de Solicitudes Existentes

Puede modificar solicitudes que no han sido finalizadas.

### Cómo Editar una Solicitud

1. **Ir a detalles del programa**
2. **Hacer clic en pestaña Beneficiarios**
3. **Localizar la solicitud** (buscar por folio o nombre)
4. **Hacer clic en el botón "Editar"** (ícono de lápiz)
5. **Aparece el formulario de edición** con la información actual

[Captura de pantalla: Formulario de edición de solicitud con datos prellenados]

### Qué Puede Editar

**Siempre Editable:**
- Información de contacto (teléfono, correo electrónico)
- Detalles de dirección
- Información escolar (si aplica)
- Notas de apoyo

**A Veces Editable:**
- Información personal (si la solicitud está pendiente)
- Estado (puede cambiar desde pendiente)
- Documentos (puede agregar/eliminar)

**Nunca Editable:**
- CURP (identificador único)
- Número de folio (generado por el sistema)
- Fecha de creación
- Fecha de aprobación (una vez aprobada)

### Flujo de Trabajo de Edición

```
1. Hacer clic en "Editar Solicitud"
2. El formulario se carga con datos actuales
3. Hacer cambios necesarios
4. Hacer clic en "Guardar Cambios"
5. Aparece mensaje de confirmación
6. La información actualizada se muestra inmediatamente
```

**Mejores Prácticas:**
- Documentar por qué está editando (en campo de notas)
- Verificar cambios con el ciudadano si es posible
- Verificar que las ediciones no afecten elegibilidad
- Guardar frecuentemente si hace múltiples cambios

## Actualización del Estado de la Solicitud

Gestión del ciclo de vida de una solicitud a través de cambios de estado.

### Estados Disponibles

| Estado | Significado | Próximas Acciones |
|--------|---------|-------------|
| **Pendiente** | Esperando revisión | Cargar documentos, verificar elegibilidad |
| **En Revisión** | Bajo revisión | Completar evaluación |
| **Aprobada** | Aprobado | Activar beneficios, notificar ciudadano |
| **Negada** | Denegado | Agregar razón, notificar ciudadano |
| **Suspendida** | Suspendido | Investigar problema |
| **Completada** | Completado | Archivar, reporte final |

### Cambio de Estado

[Captura de pantalla: Menú desplegable de estado con opciones y campo de razón]

#### Aprobar una Solicitud (Aprobada)

```
1. Revisar detalles de solicitud minuciosamente
2. Verificar que todos los documentos estén cargados
3. Verificar criterios de elegibilidad
4. Hacer clic en "Cambiar Estado"
5. Seleccionar "Aprobada"
6. Agregar notas de aprobación (opcional pero recomendado)
7. Establecer fecha de inicio del beneficio
8. Hacer clic en "Confirmar"
9. El sistema envía notificación de aprobación al ciudadano
```

**Lista de Verificación de Aprobación:**
- [ ] Todos los documentos requeridos enviados
- [ ] Información verificada (CURP, dirección, etc.)
- [ ] Cumple criterios de elegibilidad
- [ ] Sin inscripción duplicada
- [ ] Presupuesto disponible
- [ ] Autoridad de aprobación confirmada

#### Denegar una Solicitud (Negada)

```
1. Determinar razón de denegación
2. Hacer clic en "Cambiar Estado"
3. Seleccionar "Negada"
4. REQUERIDO: Agregar razón de denegación
5. Seleccionar categoría de denegación:
   - No cumple elegibilidad
   - Documentación incompleta
   - Inscripción duplicada
   - Presupuesto no disponible
   - Otro (especificar)
6. Hacer clic en "Confirmar"
7. El sistema envía notificación de denegación
```

**Importante**: Siempre proporcione razones claras y específicas de denegación. Los ciudadanos tienen derecho a entender por qué se denegó su solicitud.

#### Suspender una Solicitud (Suspendida)

Usar cuando un problema temporal necesita resolución:

```
1. Identificar el problema (ej., documentos faltantes)
2. Cambiar estado a "Suspendida"
3. Agregar razón detallada de suspensión
4. Establecer fecha de seguimiento
5. Notificar al ciudadano de la acción requerida
6. Reanudar cuando se resuelva el problema
```

**Razones Comunes de Suspensión:**
- Documentos faltantes o vencidos
- Verificación de dirección necesaria
- Información adicional pendiente
- Congelación temporal del presupuesto
- Investigación requerida

### Flujo de Trabajo de Cambio de Estado

**Proceso General:**
```
1. Abrir detalles de solicitud
2. Hacer clic en el botón "Actualizar Estado"
3. Seleccionar nuevo estado del menú desplegable
4. Completar razón/notas requeridas
5. Agregar cualquier información de apoyo
6. Revisar cambio de estado
7. Hacer clic en "Confirmar"
8. El estado se actualiza inmediatamente
9. Se envía notificación automática (si está configurado)
10. El cambio de estado se registra en el historial
```

**Historial de Estados:**
- Todos los cambios de estado se registran
- Muestra quién hizo el cambio
- Muestra cuándo ocurrió el cambio
- Muestra la razón proporcionada
- Crea registro de auditoría

## Exportación de Datos del Programa

Genere reportes y exporte datos de beneficiarios para análisis o documentación.

### Exportar a PDF

Las exportaciones PDF son ideales para reportes oficiales e impresión.

[Captura de pantalla: Diálogo de exportación PDF con opciones y barra de progreso]

#### Características de Exportación PDF

**Qué se Incluye:**
- Encabezado del programa con logo
- Nombre y detalles del programa
- Fecha y hora de exportación
- Lista de beneficiarios (tabla formateada)
- Resumen de estadísticas
- Números de página
- Formato profesional

**Cómo Exportar PDF:**

```
1. Abrir detalles del programa
2. Hacer clic en el botón "Exportar"
3. Seleccionar "Exportar a PDF"
4. Aparece modal de generación de PDF
5. Configurar opciones:
   - Incluir estadísticas: Sí/No
   - Incluir mapa: Sí/No
   - Rango de fechas: Todo el tiempo / Personalizado
   - Filtro de estado: Todo / Solo activos
6. Hacer clic en "Generar PDF"
7. La barra de progreso muestra el estado de generación
8. La descarga comienza automáticamente cuando se completa
```

**Seguimiento de Progreso:**

[Captura de pantalla: Barra de progreso mostrando "Generando PDF... 68%"]

La barra de progreso muestra el estado en tiempo real:
- "Preparando datos..." (0-20%)
- "Formateando documento..." (20-60%)
- "Generando páginas..." (60-90%)
- "Finalizando PDF..." (90-100%)
- "¡Descarga lista!" (100%)

**Exportaciones Grandes:**
- Programas con más de 1,000 beneficiarios pueden tardar 30-60 segundos
- No cierre el navegador durante la generación
- Verá el porcentaje de progreso
- Puede continuar trabajando en otra pestaña

#### Opciones de Exportación PDF

**Rango de Fechas:**
- Todo el tiempo: Historial completo
- Año actual: Inscripciones de este año
- Mes actual: Inscripciones recientes
- Personalizado: Especificar fechas de inicio y fin

**Filtro de Estado:**
- Todos los estados: Lista completa
- Solo activos: Actualmente inscritos
- Pendientes: Esperando aprobación
- Aprobados: Todas las solicitudes aprobadas
- Personalizado: Selección de múltiples estados

**Incluir Mapa:**
- Sí: Agrega captura de pantalla del mapa al PDF
- No: Reporte solo de texto (más rápido, archivo más pequeño)

### Exportar a Excel

Las exportaciones Excel proporcionan datos para análisis y manipulación.

[Captura de pantalla: Botón de exportación Excel y opciones]

#### Cómo Exportar Excel:

```
1. Abrir detalles del programa
2. Hacer clic en el botón "Exportar"
3. Seleccionar "Exportar a Excel"
4. El archivo se genera (usualmente rápido)
5. La descarga comienza automáticamente
6. Abrir en Excel, Numbers o Google Sheets
```

**Qué se Incluye:**

**Hoja 1: Beneficiarios**
- Toda la información de beneficiarios
- Columnas: Nombre, CURP, Dirección, Estado, Fechas, etc.
- Formateado como tabla con filtros

**Hoja 2: Estadísticas** (si está disponible)
- Resumen del programa
- Tendencias de inscripción
- Desglose de estado
- Utilización del presupuesto

**Hoja 3: Documentos** (si está disponible)
- Lista de verificación de documentos por beneficiario
- Estado de carga
- Reporte de documentos faltantes

#### Estructura de Datos de Excel

**Encabezados de Columna:**
| Columna | Descripción |
|--------|-------------|
| Folio | Número de solicitud |
| Nombre | Nombre completo |
| CURP | ID de ciudadano |
| Dirección | Dirección completa |
| Colonia | Colonia |
| Teléfono | Número de teléfono |
| Email | Dirección de correo electrónico |
| Fecha Inscripción | Fecha de inscripción |
| Estado | Estado actual |
| Monto | Monto del beneficio |

**Uso de la Exportación Excel:**

1. **Filtrar Datos:**
   - Hacer clic en encabezado de columna
   - Usar herramientas de filtro de Excel
   - Ordenar por cualquier columna

2. **Crear Tablas Dinámicas:**
   - Analizar por colonia
   - Contar por estado
   - Sumar montos de beneficios

3. **Generar Gráficos:**
   - Tendencias de inscripción
   - Distribución geográfica
   - Desglose de estado

4. **Calcular Estadísticas:**
   - Monto promedio de beneficio
   - Tasas de aprobación
   - Tiempos de procesamiento

### Mejores Prácticas de Exportación

**Antes de Exportar:**
1. Aplicar filtros necesarios (rango de fechas, estado)
2. Limpiar datos (asegurar que no haya ediciones pendientes)
3. Verificar parámetros del reporte
4. Verificar espacio disponible en disco

**Gestión de Archivos:**
- Nombrar archivos descriptivamente: `becas_federal_dic2025.pdf`
- Almacenar en carpetas organizadas por mes/año
- Respaldar reportes importantes
- Eliminar exportaciones antiguas regularmente

**Seguridad de Datos:**
- Los archivos exportados contienen información personal
- Proteger con contraseña archivos Excel sensibles
- No enviar por correo a destinatarios no autorizados
- Seguir políticas de datos organizacionales

**Exportaciones Grandes:**
- Programas con más de 5,000 beneficiarios: Usar Excel (más rápido)
- Reportes oficiales: Usar PDF (profesional)
- Análisis de datos: Usar Excel (manipulable)
- Revisión rápida: Usar PDF (legible)

## Carga de Documentos

Adjunte documentos de apoyo a solicitudes de programas.

### Cómo Cargar Documentos

[Captura de pantalla: Interfaz de carga de documentos con área de arrastrar y soltar]

```
1. Abrir detalles de solicitud
2. Hacer clic en pestaña "Documentos"
3. Hacer clic en el botón "Cargar Documento"
4. Seleccionar tipo de documento del menú desplegable:
   - ID oficial (INE/Pasaporte)
   - Comprobante de domicilio
   - Acta de nacimiento
   - Certificado CURP
   - Comprobante de inscripción escolar
   - Otro
5. Hacer clic en "Elegir Archivo" o arrastrar archivo al área de carga
6. Esperar a que se complete la carga
7. El documento aparece en la lista
```

### Tipos de Archivo Admitidos

**Documentos:**
- PDF (.pdf) - Formato preferido
- Imágenes: JPEG (.jpg), PNG (.png)
- Word (.doc, .docx)
- Excel (.xls, .xlsx) - Para datos de apoyo

**Límites de Tamaño de Archivo:**
- Archivo individual máximo: 10 MB
- Recomendado: Menos de 5 MB
- Comprimir archivos grandes antes de cargar

### Gestión de Documentos Cargados

**La Lista de Documentos Muestra:**
- Tipo de documento
- Nombre del archivo
- Fecha de carga
- Cargado por (nombre del personal)
- Tamaño del archivo
- Acciones (Ver, Descargar, Eliminar)

**Acciones de Documento:**

**Ver Documento:**
1. Hacer clic en ícono "Ver" (ojo)
2. El documento se abre en nueva pestaña
3. Los PDF se muestran en el navegador
4. Las imágenes se muestran en tamaño completo

**Descargar Documento:**
1. Hacer clic en ícono "Descargar"
2. El archivo se guarda en su computadora
3. Se preserva el nombre de archivo original

**Eliminar Documento:**
1. Hacer clic en ícono "Eliminar" (papelera)
2. Aparece diálogo de confirmación
3. Confirmar eliminación
4. El documento se elimina de la solicitud

**Reemplazar Documento:**
1. Eliminar documento incorrecto
2. Cargar documento corregido
3. Seleccionar mismo tipo de documento
4. El archivo nuevo reemplaza al antiguo

### Lista de Verificación de Documentos

Antes de aprobar una solicitud, verifique:

- [ ] Todos los documentos requeridos cargados
- [ ] Los documentos son legibles y completos
- [ ] La información coincide con los datos de la solicitud
- [ ] Los documentos están vigentes (no vencidos)
- [ ] Los archivos se abren sin errores
- [ ] No faltan páginas

## Tareas Comunes de Gestión de Programas

### Tarea: Inscribir Nuevo Beneficiario

```
1. Navegar a detalles del programa
2. Hacer clic en "Nueva Solicitud"
3. Buscar/ingresar información del ciudadano
4. Completar formulario de dirección
5. Agregar información escolar (si aplica)
6. Revisar y enviar
7. Anotar número de folio
8. Cargar documentos requeridos
9. Revisar y aprobar cuando esté listo
```

### Tarea: Procesar Solicitudes Pendientes

```
1. Abrir detalles del programa
2. Filtrar por estado "Pendiente"
3. Hacer clic en primera solicitud pendiente
4. Revisar toda la información
5. Verificar documentos cargados
6. Verificar elegibilidad
7. Cambiar estado a Aprobada/Negada
8. Agregar notas explicando decisión
9. Pasar a siguiente solicitud pendiente
10. Repetir hasta limpiar cola
```

### Tarea: Generar Reporte Mensual

```
1. Abrir detalles del programa
2. Aplicar filtro de fecha: Este mes
3. Aplicar filtro de estado: Aprobada
4. Hacer clic en "Exportar a PDF"
5. Incluir estadísticas: Sí
6. Generar y descargar
7. Revisar PDF
8. Archivar en carpeta de reportes mensuales
9. Compartir con supervisor si se requiere
```

### Tarea: Encontrar Beneficiarios en una Colonia

```
1. Abrir detalles del programa
2. Hacer clic en pestaña de mapa
3. Acercarse a colonia objetivo
4. Observar marcadores de clúster
5. Hacer clic en clúster para ver individuos
6. O usar búsqueda: Escribir nombre de colonia
7. La lista se filtra para mostrar solo esa área
8. Exportar si es necesario para visitas de campo
```

### Tarea: Actualizar Estados de Múltiples Beneficiarios

```
1. Revisar lista de beneficiarios
2. Para cada uno que requiera cambio de estado:
3. Hacer clic en el botón "Editar"
4. Actualizar estado con razón
5. Guardar cambios
6. Pasar al siguiente beneficiario
7. Verificar que todos los cambios se guardaron
8. Generar reporte actualizado
```

## Consejos para Gestión Eficiente de Programas

### Flujo de Trabajo Diario

**Rutina Matutina:**
1. Revisar conteo de solicitudes pendientes
2. Verificar aprobaciones urgentes
3. Responder consultas de ciudadanos
4. Procesar documentos cargados durante la noche

**Rutina de Procesamiento:**
1. Ordenar por fecha de envío (más antiguo primero)
2. Procesar en lotes de 10-20
3. Tomar descansos entre lotes
4. Verificar dos veces las aprobaciones antes de confirmar

**Fin del Día:**
1. Completar cualquier revisión iniciada
2. Actualizar notas de solicitudes
3. Generar resumen de actividad diaria
4. Planear prioridades del día siguiente

### Aseguramiento de Calidad

**Antes de Aprobar:**
- Leer solicitud completa cuidadosamente
- Verificar CURP con ID oficial
- Verificar que la dirección exista en el sistema
- Confirmar autenticidad de documentos
- Verificar inscripciones duplicadas

**Documentación:**
- Siempre agregar notas explicando decisiones
- Documentar conversaciones telefónicas con ciudadanos
- Anotar cualquier circunstancia especial
- Registrar requisitos de seguimiento

### Comunicación

**Con Ciudadanos:**
- Proporcionar número de folio inmediatamente
- Explicar próximos pasos claramente
- Establecer expectativas realistas de cronograma
- Documentar todas las interacciones

**Con el Equipo:**
- Compartir casos complejos con supervisor
- Reportar problemas del sistema prontamente
- Coordinar en días de alto volumen
- Compartir mejores prácticas

## Solución de Problemas

### El Mapa No Carga

**Soluciones:**
1. Actualizar la página
2. Verificar conexión a Internet
3. Permitir permisos de ubicación si se solicita
4. Probar navegador diferente
5. Limpiar caché del navegador

### La Exportación PDF Falla

**Intentar:**
1. Reducir rango de fechas (menos registros)
2. Deshabilitar opción "Incluir Mapa"
3. Verificar espacio disponible en disco
4. Intentar exportación Excel en su lugar
5. Contactar TI si el problema persiste

### No Puede Encontrar Beneficiario en la Búsqueda

**Verificar:**
1. La ortografía es correcta
2. Intentar búsqueda parcial de nombre
3. Buscar por número de folio en su lugar
4. Verificar si se seleccionó programa incorrecto
5. Verificar que el beneficiario exista en el sistema

### La Carga Falla

**Verificar:**
1. Tamaño de archivo menor a 10 MB
2. Tipo de archivo es compatible
3. Conexión a Internet estable
4. El navegador no está bloqueando ventanas emergentes
5. Almacenamiento suficiente en el servidor

## Próximos Pasos

Ahora que entiende los programas sociales:

- **[Datos Geográficos](05-geographic-data.md)**: Gestione calles y colonias
- **[Escáner QR](06-qr-scanner.md)**: Acceso rápido a información de beneficiarios
- **[Reportes](07-reports.md)**: Maneje reportes de ciudadanos

---

**Consejo Profesional**: Mantenga una hoja de cálculo de números de folio frecuentemente usados para referencia rápida. Incluya nombre del ciudadano, folio, programa y estado para búsquedas fáciles durante llamadas telefónicas.
