# Gestión de Ciudadanos

La sección de Ciudadanos es su base de datos integral para gestionar información ciudadana, rastrear inscripciones en programas y ver reportes de ciudadanos. Esta guía cubre todas las funciones de gestión de ciudadanos.

## Acceso a la Gestión de Ciudadanos

1. Haga clic en la pestaña **Ciudadanos** en la navegación principal
2. La lista de ciudadanos se carga, mostrando todos los ciudadanos registrados

[Captura de pantalla: Vista de lista de ciudadanos con barra de búsqueda y tabla de datos]

**Nota**: La carga inicial puede tardar unos segundos cuando se manejan más de 10,000 registros de ciudadanos.

## Comprensión de la Tabla de Ciudadanos

La tabla de ciudadanos usa AG Grid, un potente sistema de cuadrícula de datos que maneja grandes conjuntos de datos eficientemente.

### Columnas de la Tabla

Por defecto, verá estas columnas:

| Columna | Descripción | Ejemplo |
|--------|-------------|---------|
| **Nombre** | Nombre completo | María García López |
| **CURP** | ID único del ciudadano | GAML850615MDFRRR04 |
| **Fecha de Nacimiento** | Fecha de nacimiento | 15/06/1985 |
| **Género** | Género | Femenino |
| **Teléfono** | Número de teléfono | 322-123-4567 |
| **Email** | Dirección de correo electrónico | maria.garcia@email.com |
| **Dirección** | Dirección completa | Calle Juárez 123, Centro |
| **Colonia** | Colonia | Centro |
| **Programas** | Conteo de programas inscritos | 3 programas |
| **Reportes** | Conteo de reportes enviados | 2 reportes |
| **Acciones** | Botones de acción | Ver, Editar, Eliminar |

### Características de la Tabla

**Columnas Ordenables:**
- Haga clic en cualquier encabezado de columna para ordenar ascendente
- Haga clic nuevamente para ordenar descendente
- Haga clic una tercera vez para eliminar el ordenamiento

**Columnas Redimensionables:**
- Pase el mouse sobre el borde entre encabezados de columna
- Haga clic y arrastre para redimensionar

**Encabezado Fijo:**
- Mientras se desplaza hacia abajo, la fila de encabezado permanece visible
- Siempre sabrá qué columna está viendo

## Búsqueda de Ciudadanos

La funcionalidad de búsqueda le permite encontrar rápidamente ciudadanos específicos.

[Captura de pantalla: Barra de búsqueda con ejemplo de búsqueda "Maria Garcia"]

### Métodos de Búsqueda

#### Por Nombre
```
Búsqueda: Maria Garcia
Resultados: Todos los ciudadanos con "Maria" o "Garcia" en su nombre
```

**Consejos:**
- Nombres parciales funcionan (ej., "Mar" encuentra Maria, Mariana, Marco)
- La búsqueda no distingue entre mayúsculas y minúsculas
- La búsqueda verifica primer nombre, segundo nombre y apellidos

#### Por CURP
```
Búsqueda: GAML850615
Resultados: Ciudadanos con CURP coincidente
```

**Consejos:**
- Puede ingresar CURP parcial
- Excelente para identificación exacta
- La búsqueda de CURP no distingue entre mayúsculas y minúsculas

#### Búsqueda Combinada
```
Búsqueda: Garcia Centro
Resultados: Ciudadanos con apellido Garcia que viven en la colonia Centro
```

**Cómo Funciona:**
- La búsqueda busca en múltiples campos simultáneamente
- Encuentra registros que coinciden con cualquier término de búsqueda
- Búsquedas más específicas producen menos resultados más relevantes

### Flujo de Trabajo de Búsqueda

1. **Haga clic en el cuadro de búsqueda** en la parte superior de la tabla de ciudadanos
2. **Escriba su término de búsqueda** (nombre, CURP o dirección)
3. **Los resultados se actualizan automáticamente** mientras escribe
4. **Limpie la búsqueda** haciendo clic en el ícono X o eliminando todo el texto

**Nota de Rendimiento**: La búsqueda en más de 10,000 registros está optimizada y devuelve resultados rápidamente.

## Visualización de Detalles de Ciudadano

Para ver información completa sobre un ciudadano:

1. **Localice al ciudadano** usando búsqueda o desplazamiento
2. **Haga clic en el botón "Ver"** (ícono de ojo) en la columna Acciones
3. **El panel de detalles del ciudadano se abre** mostrando el perfil completo

[Captura de pantalla: Vista de detalles del ciudadano con todas las secciones de información]

### Secciones de Vista de Detalles

#### Información Personal
- Nombre legal completo
- CURP (ID Único de Ciudadano)
- Fecha de nacimiento y edad
- Género
- Estado civil
- Ocupación

#### Información de Contacto
- Número de teléfono principal
- Teléfono secundario (si está disponible)
- Dirección de correo electrónico
- Método de contacto preferido

#### Detalles de Dirección
- Nombre y número de calle
- Número interior (si aplica)
- Colonia
- Código postal
- Municipio
- Estado
- Dirección completa formateada

#### Programas Sociales Inscritos

[Captura de pantalla: Lista de programas mostrando nombre del programa, tipo, estado, fecha de inscripción]

**La Tabla Muestra:**
- Nombre del programa (ej., "Programa Federal de Becas")
- Tipo de programa (Federal o Local)
- Estado de inscripción (Activo, Pendiente, Completado)
- Fecha de inscripción
- Estado de solicitud
- Monto del beneficio (si aplica)

**Acciones:**
- Haga clic en cualquier nombre de programa para ver detalles completos del programa
- Ver historial de beneficios para ese ciudadano
- Ver documentos asociados con la inscripción

#### Reportes de Ciudadanos

[Captura de pantalla: Lista de reportes enviados por el ciudadano]

**La Tabla Muestra:**
- Tipo de reporte (ej., "Solicitud de Apoyo", "Queja")
- Fecha de envío
- Estado actual (Pendiente, En Proceso, Resuelto)
- Miembro del personal asignado (si hay)
- Nivel de prioridad

**Acciones:**
- Haga clic en cualquier reporte para ver detalles completos
- Ver historial de reportes y cambios de estado
- Ver documentos o fotos adjuntas

#### Historial de Actividad
- Cambios recientes al registro del ciudadano
- Inscripciones y cambios en programas
- Envíos de reportes
- Actualizaciones de estado

## Personalización de Columnas de la Tabla

Gobify le permite personalizar qué columnas ve y su orden.

### Mostrar/Ocultar Columnas

1. **Haga clic en el ícono del menú de columnas** (tres puntos o ícono de cuadrícula cerca de la barra de búsqueda)
2. **Aparece la lista de columnas** con casillas de verificación
3. **Marque/desmarque columnas** para mostrarlas u ocultarlas
4. **Sus preferencias se guardan** automáticamente

[Captura de pantalla: Menú de personalización de columnas con casillas de verificación]

**Columnas Comúnmente Ocultas:**
- Email (si no se necesita para su trabajo)
- Números de teléfono secundarios
- Campos de dirección detallados (si solo necesita colonia)

**Columnas Comúnmente Visibles:**
- Nombre, CURP (siempre recomendado)
- Conteo de programas
- Conteo de reportes
- Información de contacto principal

### Reorganización de Columnas

1. **Haga clic y mantenga** en un encabezado de columna
2. **Arrastre a la izquierda o derecha** a la posición deseada
3. **Suelte el mouse** para soltar la columna en la nueva ubicación
4. **El orden se guarda** para sesiones futuras

### Restablecer a Predeterminado

Si su personalización se vuelve confusa:

1. Haga clic en el ícono del menú de columnas
2. Seleccione "Restablecer a Predeterminado" o "Restaurar Predeterminados"
3. Las columnas vuelven al diseño original

## Operaciones Masivas

Cuando necesite trabajar con múltiples ciudadanos a la vez, use operaciones masivas.

### Selección de Múltiples Ciudadanos

**Seleccionar Ciudadanos Individuales:**
1. Marque la casilla de verificación al inicio de cada fila de ciudadano
2. Las filas seleccionadas se resaltan
3. El conteo de ciudadanos seleccionados aparece en la parte superior

[Captura de pantalla: Tres ciudadanos seleccionados con contador mostrando "3 seleccionados"]

**Seleccionar Todos los Visibles:**
1. Marque la casilla de verificación en el encabezado de la tabla
2. Todos los ciudadanos en la página actual se seleccionan
3. O use la opción "Seleccionar Todo" si está disponible

**Seleccionar Rango:**
1. Haga clic en la casilla del primer ciudadano
2. Mantenga presionada la tecla Shift
3. Haga clic en la casilla del último ciudadano
4. Todos los ciudadanos entre ambos se seleccionan

### Acciones Masivas Disponibles

Una vez que haya seleccionado múltiples ciudadanos:

#### Exportar Seleccionados
- Haga clic en el botón "Exportar"
- Elija formato (Excel, CSV, PDF)
- La descarga contiene solo ciudadanos seleccionados

#### Imprimir Seleccionados
- Haga clic en el botón "Imprimir"
- La vista previa de impresión muestra la lista de ciudadanos seleccionados
- Útil para registros físicos

#### Asignar a Programa
- Haga clic en el botón "Asignar a Programa"
- Seleccione qué programa
- Se inicia la inscripción masiva
- Revisar y confirmar

#### Enviar Notificación
- Haga clic en "Enviar Notificación"
- Elija plantilla de notificación
- Envíe correo electrónico o SMS a ciudadanos seleccionados
- Útil para actualizaciones de programas

### Deseleccionar Ciudadanos

- Haga clic en las casillas de verificación individuales nuevamente para deseleccionar
- Haga clic en la casilla del encabezado para deseleccionar todos
- Haga clic en el botón "Limpiar Selección" si está disponible

## Exportación de Datos de Ciudadanos

Exporte datos de ciudadanos para reportes, análisis o registros.

### Opciones de Exportación

[Captura de pantalla: Menú de exportación mostrando opciones de formato]

#### Exportación Excel (.xlsx)
**Mejor Para:** Análisis de datos, crear reportes, compartir con usuarios de Excel

**Contiene:**
- Todas las columnas visibles en la vista actual
- Datos formateados
- Múltiples hojas si se exportan datos relacionados (programas, reportes)

**Cómo Hacerlo:**
1. Haga clic en el botón "Exportar"
2. Seleccione "Excel (.xlsx)"
3. El archivo se descarga automáticamente
4. Abra en Microsoft Excel o software similar

#### Exportación CSV (.csv)
**Mejor Para:** Importar a otros sistemas, respaldos de base de datos, compatibilidad universal

**Contiene:**
- Todos los datos en formato separado por comas
- Sin formato, solo datos crudos
- Se puede abrir en Excel o editores de texto

**Cómo Hacerlo:**
1. Haga clic en el botón "Exportar"
2. Seleccione "CSV (.csv)"
3. El archivo se descarga automáticamente
4. Abra en Excel, Numbers o Google Sheets

#### Exportación PDF (.pdf)
**Mejor Para:** Impresión, reportes oficiales, distribución de solo lectura

**Contiene:**
- Tabla formateada con todas las columnas visibles
- Diseño profesional
- Encabezados y pies de página con fecha/hora
- Números de página

**Cómo Hacerlo:**
1. Haga clic en el botón "Exportar"
2. Seleccione "PDF (.pdf)"
3. El archivo se descarga automáticamente
4. Abra en lector de PDF o imprima

### Flujo de Trabajo de Exportación

**Exportar Vista Actual:**
```
1. Aplicar cualquier filtro o búsqueda
2. Personalizar columnas para mostrar solo lo que necesita
3. Hacer clic en "Exportar"
4. Elegir formato
5. La descarga se completa
```

**Exportar Ciudadanos Seleccionados:**
```
1. Seleccionar ciudadanos específicos usando casillas de verificación
2. Hacer clic en "Exportar Seleccionados"
3. Elegir formato
4. La descarga contiene solo ciudadanos seleccionados
```

**Exportar Todos los Ciudadanos:**
```
1. Limpiar cualquier filtro o selección
2. Hacer clic en "Exportar Todo" (puede requerir confirmación)
3. Elegir formato
4. Esperar la generación (puede tomar tiempo para más de 10,000 registros)
5. La descarga se completa
```

### Mejores Prácticas de Exportación

**Antes de Exportar:**
- Aplicar filtros necesarios para reducir el tamaño de datos
- Personalizar columnas para incluir solo información necesaria
- Verificar que los criterios de búsqueda/filtro sean correctos

**Nomenclatura de Archivos:**
- Las exportaciones típicamente se nombran automáticamente con fecha/hora
- Ejemplo: `ciudadanos_2025-12-08_14-30.xlsx`
- Renombre los archivos descargados para organización

**Exportaciones Grandes:**
- Las exportaciones de más de 10,000 registros pueden tardar 10-30 segundos
- No cierre el navegador mientras se genera la exportación
- Verá un indicador de progreso o notificación

**Privacidad de Datos:**
- Los archivos exportados contienen información personal sensible
- Almacene de forma segura
- Siga las políticas de protección de datos de su organización
- Elimine cuando ya no sea necesario

## Paginación

Con miles de ciudadanos, los datos se dividen en páginas para mejorar el rendimiento.

### Comprensión de la Paginación

[Captura de pantalla: Controles de paginación mostrando "Mostrando 1-25 de 12,456 ciudadanos"]

**La Visualización Muestra:**
- Rango de página actual (ej., "1-25")
- Conteo total de ciudadanos (ej., "de 12,456")
- Número de página actual
- Conteo total de páginas

### Navegación de Páginas

**Controles de Página:**
- **Primera Página**: Haga clic en el botón |◄
- **Página Anterior**: Haga clic en el botón ◄
- **Página Siguiente**: Haga clic en el botón ►
- **Última Página**: Haga clic en el botón ►|
- **Página Específica**: Ingrese número de página o use menú desplegable

**Saltar a Página:**
1. Haga clic en el campo de número de página
2. Escriba el número de página deseado
3. Presione Enter
4. La página se carga inmediatamente

### Filas por Página

Cambie cuántos ciudadanos se muestran por página:

1. Busque el menú desplegable "Filas por página"
2. Haga clic para ver opciones (usualmente 10, 25, 50, 100)
3. Seleccione su preferencia
4. La tabla se recarga con el nuevo tamaño de página

**Elegir Tamaño de Página:**
- **10-25 filas**: Mejor para revisión detallada, computadoras más lentas
- **50 filas**: Buen balance de velocidad y visibilidad
- **100 filas**: Desplazamiento rápido, requiere buena conexión a Internet

**Nota de Rendimiento**: Los tamaños de página más grandes cargan más datos, lo que puede tardar un poco más en conexiones lentas.

## Tareas Comunes de Gestión de Ciudadanos

### Tarea: Encontrar un Ciudadano Específico

```
1. Hacer clic en la pestaña Ciudadanos
2. Hacer clic en el cuadro de búsqueda
3. Escribir nombre o CURP del ciudadano
4. Hacer clic en "Ver" en el ciudadano correcto
5. Revisar perfil completo
```

### Tarea: Verificar Programas Inscritos de un Ciudadano

```
1. Buscar y ver ciudadano
2. Desplazarse a la sección "Programas Sociales Inscritos"
3. Revisar lista de programas
4. Hacer clic en cualquier nombre de programa para detalles
```

### Tarea: Exportar Ciudadanos en una Colonia

```
1. Hacer clic en el cuadro de búsqueda
2. Escribir nombre de colonia (ej., "Centro")
3. Los resultados muestran solo residentes de Centro
4. Hacer clic en "Exportar"
5. Seleccionar formato (Excel recomendado)
6. Descargar y abrir archivo
```

### Tarea: Revisar Reportes Recientes

```
1. Ver detalles del ciudadano
2. Desplazarse a la sección "Reportes"
3. Ver lista de reportes enviados
4. Hacer clic en reporte para ver detalles
5. Verificar estado y personal asignado
```

### Tarea: Crear Lista de Contactos para un Programa

```
1. Aplicar filtro de programa o búsqueda
2. Personalizar columnas: Mostrar Nombre, Teléfono, Email
3. Ocultar columnas innecesarias
4. Exportar a Excel
5. Usar exportación para campaña de llamadas/correos
```

## Solución de Problemas

### La Tabla No Carga

**Soluciones:**
1. Actualizar la página (F5)
2. Verificar conexión a Internet
3. Limpiar caché del navegador
4. Probar un navegador diferente
5. Contactar TI si el problema persiste

### La Búsqueda No Devuelve Resultados

**Verificar:**
1. La ortografía es correcta
2. No está buscando información que no existe
3. Intente búsqueda parcial (menos letras)
4. Limpie cualquier filtro aplicado
5. Elimine la búsqueda y comience de nuevo

### Rendimiento Lento

**Optimizar:**
1. Reducir filas por página (usar 25 en lugar de 100)
2. Aplicar filtros para reducir conjunto de datos
3. Cerrar otras pestañas del navegador
4. Verificar velocidad de conexión a Internet
5. Evitar exportar todos los registros a la vez

### La Exportación Falla

**Intentar:**
1. Reducir tamaño de datos (aplicar filtros primero)
2. Seleccionar menos columnas
3. Exportar en lotes más pequeños
4. Probar formato diferente (CSV en lugar de Excel)
5. Verificar espacio disponible en disco

## Mejores Prácticas

### Operaciones Diarias

1. **Usar Búsqueda Eficientemente**: Escriba términos específicos en lugar de desplazarse
2. **Personalice su Vista**: Oculte columnas que nunca usa
3. **Verifique Antes de Exportar**: Revise filtros y selecciones
4. **Verificaciones Regulares de Datos**: Asegúrese de que la información ciudadana esté actualizada

### Calidad de Datos

1. **Reporte Errores**: Si encuentra información incorrecta, repórtela
2. **Verifique Duplicados**: Esté atento a registros de ciudadanos duplicados
3. **Verifique CURP**: Asegúrese de que el CURP coincida con registros gubernamentales
4. **Actualice Información de Contacto**: Mantenga teléfono y correo electrónico actualizados

### Seguridad

1. **Cierre Sesión**: Siempre cierre sesión cuando termine
2. **Asegure Exportaciones**: Proteja archivos descargados con contraseñas
3. **Comparta con Cuidado**: Solo exporte datos que está autorizado a compartir
4. **Bloqueo de Pantalla**: Bloquee su computadora cuando se aleje

## Referencia Rápida

### Atajos de Teclado
- **Ctrl/Cmd + F**: Búsqueda rápida
- **Tab**: Navegar entre campos
- **Enter**: Abrir ciudadano seleccionado
- **Esc**: Cerrar vista de detalles

### Filtros Comunes
- Por colonia: Escribir nombre de colonia
- Por programa: Escribir nombre de programa
- Por estado: Usar menú desplegable de estado si está disponible
- Por rango de fechas: Usar selectores de fecha para inscripciones

## Próximos Pasos

Ahora que puede gestionar ciudadanos:

- **[Programas Sociales](04-social-programs.md)**: Aprenda a inscribir ciudadanos en programas
- **[Datos Geográficos](05-geographic-data.md)**: Entienda calles y colonias
- **[Reportes](07-reports.md)**: Procese reportes de ciudadanos eficientemente

---

**Consejo Profesional**: Cree una lista de "favoritos" exportando un pequeño archivo Excel de ciudadanos con los que trabaja frecuentemente. Téngalo a mano para consultas rápidas de CURP o contacto.
