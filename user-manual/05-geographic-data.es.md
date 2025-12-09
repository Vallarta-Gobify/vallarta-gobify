# Gestión de Datos Geográficos

Las funciones de gestión de datos geográficos en Gobify le ayudan a mantener información precisa de calles y colonias, lo cual es esencial para direcciones de ciudadanos y seguimiento de beneficiarios de programas.

## Por Qué Importan los Datos Geográficos

Los datos geográficos precisos aseguran:
- **Direcciones precisas de ciudadanos** para entrega de programas y visitas de campo
- **Mapeo correcto** de beneficiarios en mapas de programas
- **Datos de ubicación estandarizados** en todo el sistema
- **Búsqueda y filtrado fáciles** por colonia
- **Códigos postales consistentes** y divisiones administrativas

## Acceso a Datos Geográficos

La gestión de datos geográficos se divide en dos secciones:

1. **Calles** - Haga clic en la pestaña **Calles** en la navegación principal
2. **Colonias** - Haga clic en la pestaña **Colonias** en la navegación principal

---

## Gestión de Calles

La sección de Calles le permite ver, buscar, agregar y editar información de calles.

### Vista de Lista de Calles

[Captura de pantalla: Tabla de calles mostrando nombres de calles, tipos y botones de edición]

Cuando abra la sección de Calles, verá una lista paginada de todas las calles en el sistema.

**Columnas de la Tabla:**

| Columna | Descripción | Ejemplo |
|--------|-------------|---------|
| **Nombre** | Nombre de la calle | Juárez |
| **Tipo** | Etiqueta de tipo de calle | Calle |
| **Nombre Completo** | Designación completa de la calle | Calle Juárez |
| **Acciones** | Botones de acción | Editar, Eliminar |

**Etiquetas de Tipo de Calle:**

Las calles se categorizan por tipo, cada una con una etiqueta visual distintiva:

- **Calle** - Más común, calles estándar
- **Avenida** - Vías principales importantes
- **Boulevard** - Caminos amplios e importantes
- **Privada** - Acceso restringido o cerrado
- **Cerrada** - Calles sin salida
- **Callejón** - Pasajes estrechos
- **Camino** - Rutas menos urbanas
- **Andador** - Caminos peatonales

[Captura de pantalla: Etiquetas de tipo de calle con diferentes colores]

Cada tipo tiene una insignia de color para identificación visual rápida.

### Búsqueda de Calles

Use la funcionalidad de búsqueda para encontrar rápidamente calles específicas.

[Captura de pantalla: Barra de búsqueda con ejemplo "Juarez"]

**Métodos de Búsqueda:**

#### Por Nombre
```
Búsqueda: Juarez
Resultados: Todas las calles que contienen "Juarez"
- Calle Juárez
- Avenida Benito Juárez
- Privada Juárez Norte
```

#### Por Tipo
```
Búsqueda: Avenida
Resultados: Todas las calles con tipo "Avenida"
- Avenida Revolución
- Avenida Hidalgo
- Avenida del Mar
```

#### Búsqueda Parcial
```
Búsqueda: Hid
Resultados: Calles que coinciden con nombre parcial
- Calle Hidalgo
- Boulevard Miguel Hidalgo
```

**Características de Búsqueda:**
- Resultados en tiempo real mientras escribe
- No distingue entre mayúsculas y minúsculas
- Busca tanto nombre como tipo
- Resalta términos coincidentes

### Paginación

Las calles se muestran 25 por página para facilitar la navegación.

[Captura de pantalla: Controles de paginación mostrando página 1 de 48]

**Controles de Paginación:**

- **Información de Página**: "Mostrando 1-25 de 1,200 calles"
- **Primera Página**: Botón |◄
- **Anterior**: Botón ◄
- **Números de Página**: 1, 2, 3... (hacer clic para saltar)
- **Siguiente**: Botón ►
- **Última Página**: Botón ►|

**Filas por Página:**
1. Haga clic en el menú desplegable "Filas por página"
2. Seleccione: 10, 25, 50 o 100
3. La tabla se recarga con el nuevo tamaño de página

**Consejos de Navegación:**
- Use búsqueda para reducir resultados en lugar de paginar a través de miles
- Salte a número de página específico para rangos conocidos
- Aumente filas por página para sesiones de edición masiva

### Agregar una Nueva Calle

Cuando una calle no existe en el sistema, puede agregarla.

[Captura de pantalla: Botón "Agregar Nueva Calle" y formulario]

**Cómo Agregar una Calle:**

```
1. Hacer clic en el botón "Agregar Nueva Calle" (arriba a la derecha)
2. Aparece el formulario Agregar Calle
3. Completar campos requeridos:
   - Nombre de calle (requerido)
   - Tipo de calle (requerido)
4. Completar campos opcionales:
   - Nombres alternativos
   - Notas
5. Hacer clic en "Guardar"
6. La nueva calle aparece en la lista inmediatamente
7. Disponible para uso en direcciones de ciudadanos
```

**Campos del Formulario Agregar Calle:**

**Nombre de Calle** (requerido)
- Ingrese el nombre base sin designación de tipo
- Ejemplo: Ingrese "Juárez" no "Calle Juárez"
- Use capitalización apropiada
- Evite abreviaturas

**Tipo de Calle** (requerido)
- Seleccione del menú desplegable:
  - Calle
  - Avenida
  - Boulevard
  - Privada
  - Cerrada
  - Callejón
  - Camino
  - Andador
  - Otro (Other)

**Nombres Alternativos** (opcional)
- Variaciones comunes del nombre de la calle
- Nombres anteriores
- Apodos locales
- Ejemplo: "Benito Juárez" para "Juárez"

**Notas** (opcional)
- Información adicional
- Puntos de referencia en la calle
- Características especiales
- Ejemplo: "Calle comercial principal en Centro"

**Reglas de Validación:**
- El nombre de la calle no puede estar vacío
- Debe seleccionar un tipo de calle
- El sistema verifica duplicados (advierte si existe nombre similar)
- Máximo 200 caracteres para nombre

**Ejemplo de Entrada:**
```
Nombre: Revolución
Tipo: Avenida
Nombres Alternativos: Av. Revolución, Revolución Norte
Notas: Corre de norte a sur a través de Centro y Zona Romántica
```

**Después de Agregar:**
- Calle inmediatamente disponible en menús desplegables de direcciones
- Aparece en resultados de búsqueda de calles
- Se puede editar si es necesario
- Disponible para todos los usuarios

### Edición de Calles Existentes

Corrija errores o actualice información de calles en línea.

[Captura de pantalla: Botón de edición y campos de edición en línea]

**Cómo Editar:**

```
1. Localizar calle en la lista (usar búsqueda si es necesario)
2. Hacer clic en el botón "Editar" (ícono de lápiz)
3. Los campos se vuelven editables en línea
4. Hacer cambios:
   - Actualizar nombre
   - Cambiar tipo
   - Modificar notas
5. Hacer clic en "Guardar" (ícono de marca de verificación)
6. O hacer clic en "Cancelar" (ícono X) para descartar
7. Los cambios se guardan inmediatamente
8. Se muestra información actualizada
```

**Edición en Línea:**

La edición ocurre directamente en la fila de la tabla:

**Antes de Editar:**
```
Juárez | Calle | Calle Juárez | [Editar] [Eliminar]
```

**Durante la Edición:**
```
[Juarez___] [▼Calle] [Guardar ✓] [Cancelar ✗]
```

**Después de Guardar:**
```
Benito Juárez | Avenida | Avenida Benito Juárez | [Editar] [Eliminar]
```

**Qué Puede Editar:**
- Nombre de la calle
- Tipo de calle
- Nombres alternativos
- Notas

**Qué No Puede Editar:**
- ID de la calle (referencia interna del sistema)
- Fecha de creación
- Número de direcciones que usan esta calle (solo vista)

**Mejores Prácticas de Edición:**
1. Verificar que el cambio sea necesario
2. Revisar errores tipográficos antes de guardar
3. Asegurar que el tipo describe con precisión la calle
4. Actualizar nombres alternativos si cambia el nombre principal
5. Documentar razón en notas si es un cambio importante

**Ediciones Comunes:**
- Corregir errores ortográficos
- Actualizar nombres oficiales de calles
- Cambiar designación de tipo (ej., Calle → Avenida)
- Agregar nombres alternativos faltantes
- Estandarizar capitalización

### Eliminación de Calles

Elimine calles que son duplicadas o ingresadas por error.

**Cómo Eliminar:**

```
1. Localizar calle a eliminar
2. Hacer clic en el botón "Eliminar" (ícono de papelera)
3. Aparece diálogo de confirmación:
   "¿Está seguro de que desea eliminar esta calle?"
   "Esta acción no se puede deshacer."
4. Verificar que el nombre de la calle sea correcto
5. Hacer clic en "Confirmar Eliminación"
6. La calle se elimina de la lista
```

**Advertencias Importantes:**

**No Se Puede Eliminar Si:**
- La calle se usa en direcciones de ciudadanos
- La calle aparece en registros de beneficiarios de programas
- La calle se referencia en reportes

**Antes de Eliminar:**
1. Buscar ciudadanos con esta dirección
2. Verificar que no haya registros activos que usen esta calle
3. Considerar editar en lugar de eliminar
4. Verificar si es un duplicado (fusionar datos primero)

**Ejemplo de Mensaje de Error:**
```
No se puede eliminar la calle "Calle Juárez"
Actualmente usada en 247 direcciones de ciudadanos.
Por favor reasigne direcciones antes de eliminar.
```

**Flujo de Trabajo de Eliminación Segura:**
```
1. Verificar que la calle tenga cero usos
2. Verificar que no sea solo un error tipográfico (editar en su lugar)
3. Confirmar que sea verdaderamente un duplicado
4. Eliminar solo el duplicado
5. Mantener la entrada principal/correcta
```

---

## Gestión de Colonias

La sección de Colonias gestiona información de colonias o distritos.

### Vista de Lista de Colonias

[Captura de pantalla: Tabla de colonias mostrando nombres de colonias y códigos postales]

Similar a las calles, las colonias se muestran en una lista paginada y con búsqueda.

**Columnas de la Tabla:**

| Columna | Descripción | Ejemplo |
|--------|-------------|---------|
| **Nombre** | Nombre de colonia | Centro |
| **Código Postal** | Código postal | 48300 |
| **Municipio** | Municipio | Puerto Vallarta |
| **Número de Residentes** | Conteo de residentes | 1,247 |
| **Acciones** | Botones de acción | Editar, Eliminar |

### Búsqueda de Colonias

[Captura de pantalla: Barra de búsqueda de colonias con ejemplo "Centro"]

**Funcionalidad de Búsqueda:**

#### Por Nombre
```
Búsqueda: Centro
Resultados: Todas las colonias con "Centro" en el nombre
- Centro
- Centro Norte
- Residencial del Centro
```

#### Por Código Postal
```
Búsqueda: 48300
Resultados: Colonias con código postal 48300
- Centro
- Zona Romántica
- Emiliano Zapata
```

#### Por Municipio
```
Búsqueda: Puerto Vallarta
Resultados: Todas las colonias en Puerto Vallarta
```

**Consejos de Búsqueda:**
- Comience a escribir para resultados instantáneos
- Busque código postal para área específica
- Use nombres parciales para resultados más amplios
- Limpie búsqueda para ver lista completa

### Agregar una Nueva Colonia

Agregue colonias que aún no estén en el sistema.

[Captura de pantalla: Formulario Agregar Colonia con campos requeridos]

**Cómo Agregar:**

```
1. Hacer clic en el botón "Agregar Nueva Colonia"
2. Completar el formulario:
   - Nombre de colonia (requerido)
   - Código postal (requerido)
   - Municipio (requerido)
   - Información adicional (opcional)
3. Hacer clic en "Guardar"
4. La nueva colonia aparece en la lista
5. Disponible en formularios de direcciones inmediatamente
```

**Campos del Formulario Agregar Colonia:**

**Nombre de Colonia** (requerido)
- Nombre oficial de la colonia
- Use capitalización apropiada
- Ejemplo: "Zona Romántica"

**Código Postal (CP)** (requerido)
- Código postal de 5 dígitos
- Ejemplo: 48380
- Validación: Debe ser exactamente 5 dígitos

**Municipio** (requerido)
- Seleccione del menú desplegable
- Ejemplo: Puerto Vallarta
- O escriba para buscar municipios

**Estado**
- Usualmente se completa automáticamente basado en el municipio
- Ejemplo: Jalisco

**Información Adicional** (opcional)
- Límites de la colonia
- Puntos de referencia notables
- Características locales
- Notas administrativas

**Validación:**
- Nombre de colonia requerido
- Código postal debe ser de 5 dígitos
- Municipio requerido
- Verificación de duplicados advierte de nombres similares

**Ejemplo de Entrada:**
```
Nombre: 5 de Diciembre
Código Postal: 48350
Municipio: Puerto Vallarta
Estado: Jalisco
Info: Área residencial al sur de Centro, cerca del aeropuerto
```

### Edición de Colonias

Actualice información de colonias existentes.

[Captura de pantalla: Edición en línea para colonia]

**Cómo Editar:**

```
1. Encontrar colonia (usar búsqueda si es necesario)
2. Hacer clic en el botón "Editar"
3. Los campos se vuelven editables en línea
4. Actualizar información:
   - Corregir ortografía del nombre
   - Actualizar código postal
   - Modificar municipio
   - Agregar notas
5. Hacer clic en "Guardar" para confirmar
6. O "Cancelar" para descartar cambios
```

**Actualizaciones Comunes:**
- Corregir errores de código postal
- Actualizar nombres oficiales de colonias
- Agregar información adicional
- Corregir asignaciones de municipio
- Estandarizar formatos de nombres

**Ejemplo de Edición en Línea:**

**Antes:**
```
Centro | 48300 | Puerto Vallarta | [Editar]
```

**Durante la Edición:**
```
[Centro_____] [48300_] [▼Puerto Vallarta] [✓] [✗]
```

**Después:**
```
Centro | 48300 | Puerto Vallarta | [Editar]
```

### Eliminación de Colonias

Elimine colonias duplicadas o incorrectas.

**Cómo Eliminar:**

```
1. Localizar colonia en la lista
2. Hacer clic en el botón "Eliminar"
3. Aparece mensaje de confirmación
4. Verificar que sea seguro eliminar
5. Hacer clic en "Confirmar"
6. Se elimina la colonia
```

**Consideraciones Importantes:**

**No Se Puede Eliminar Si:**
- Ciudadanos tienen direcciones en esta colonia
- Programas muestran beneficiarios en esta colonia
- Registros activos referencian esta colonia

**Mensaje de Error:**
```
No se puede eliminar la colonia "Centro"
Actualmente asignada a 3,428 direcciones de ciudadanos.
Por favor reasigne direcciones antes de eliminar.
```

**Seguro para Eliminar:**
- Entrada nueva sin usos
- Duplicado confirmado
- Ingresada por error
- Datos de prueba

**Antes de Eliminar:**
1. Verificar conteo de residentes (debe ser 0)
2. Buscar ciudadanos en esta colonia
3. Verificar que sea un duplicado
4. Fusionar datos a la colonia correcta si es necesario

---

## Uso de Datos Geográficos en la Práctica

### Al Crear Direcciones de Ciudadanos

**Flujo de Trabajo:**
```
1. Comenzar a crear/editar ciudadano
2. Llegar a sección de dirección
3. Campo de calle: El menú desplegable carga todas las calles
4. Escribir para buscar: "Jua" muestra calles que comienzan con "Jua"
5. Seleccionar: "Calle Juárez"
6. Campo de colonia: El menú desplegable carga todas las colonias
7. Escribir para buscar: "Cen" muestra colonias que comienzan con "Cen"
8. Seleccionar: "Centro"
9. Código postal: Se completa automáticamente "48300" (basado en Centro)
10. Completar campos de dirección restantes
```

**Si Falta Calle/Colonia:**
```
1. Notar que el menú desplegable no tiene la calle/colonia necesaria
2. Hacer clic en el enlace "Agregar Nuevo"
3. Aparece formulario de agregar rápido
4. Ingresar detalles de calle/colonia
5. Guardar
6. Regresar al formulario de ciudadano
7. Nueva calle/colonia ahora disponible en menú desplegable
8. Seleccionar y continuar
```

### Mantenimiento de Calidad de Datos

**Mantenimiento Regular:**

**Semanal:**
- Revisar calles/colonias recién agregadas
- Verificar duplicados
- Verificar códigos postales
- Estandarizar nomenclatura

**Mensual:**
- Auditar entradas no usadas
- Limpiar datos de prueba
- Actualizar basado en fuentes oficiales
- Documentar cambios importantes

**Trimestral:**
- Verificar con datos oficiales del servicio postal
- Actualizar asignaciones de municipio
- Revisar y fusionar duplicados
- Generar reporte de calidad

**Verificaciones de Calidad:**

**Para Calles:**
- [ ] Nombre escrito correctamente
- [ ] Tipo asignado apropiadamente
- [ ] Sin duplicados
- [ ] Nombres alternativos agregados
- [ ] Usada en al menos una dirección

**Para Colonias:**
- [ ] Código postal oficial verificado
- [ ] Municipio correcto
- [ ] Sin duplicados
- [ ] Límites claros
- [ ] Referenciada en direcciones

### Tareas Comunes de Datos Geográficos

#### Tarea: Agregar una Nueva Calle desde Registro de Ciudadano

```
1. Recibir registro de ciudadano
2. Ciudadano vive en "Calle Nueva" (no está en sistema)
3. Hacer clic en pestaña Calles
4. Hacer clic en "Agregar Nueva Calle"
5. Ingresar:
   Nombre: Nueva
   Tipo: Calle
6. Guardar
7. Regresar al formulario de ciudadano
8. Seleccionar "Calle Nueva" del menú desplegable
9. Completar dirección
```

#### Tarea: Corregir Error de Tipo de Calle

```
1. Notar "Calle Revolución" debería ser "Avenida Revolución"
2. Ir a sección Calles
3. Buscar: "Revolucion"
4. Hacer clic en "Editar" en la calle
5. Cambiar Tipo: Calle → Avenida
6. Agregar nota: "Tipo corregido según designación oficial"
7. Guardar
8. El sistema actualiza todas las referencias automáticamente
```

#### Tarea: Fusionar Colonias Duplicadas

```
1. Descubrir duplicados:
   - "5 de Diciembre"
   - "5 De Diciembre" (diferente capitalización)
2. Verificar uso:
   - Primera: 234 ciudadanos
   - Segunda: 12 ciudadanos
3. Determinar cuál mantener (primera, más uso)
4. Para cada ciudadano en segunda colonia:
   - Editar registro de ciudadano
   - Cambiar colonia a primera versión
   - Guardar
5. Una vez que segunda colonia tenga 0 uso:
   - Eliminar el duplicado
6. Solo queda versión principal
```

#### Tarea: Actualizar Códigos Postales

```
1. Recibir actualización oficial de código postal
2. Ir a sección Colonias
3. Buscar colonia afectada
4. Hacer clic en "Editar"
5. Actualizar código postal: Antiguo → Nuevo
6. Agregar nota: "Actualizado según SEPOMEX 2025"
7. Guardar
8. Todas las direcciones reflejan automáticamente el nuevo código
```

## Integración con Otros Módulos

### Calles/Colonias en Gestión de Ciudadanos

Al ver perfiles de ciudadanos:
- La dirección completa muestra nombres de calle y colonia
- Hacer clic en calle/colonia para ver todos los ciudadanos en esa ubicación
- Filtrar ciudadanos por colonia
- El mapa muestra límites de colonia (si está configurado)

### Datos Geográficos en Programas Sociales

Mapas de beneficiarios de programas:
- Agrupar por colonia
- Codificar por color según densidad de colonia
- Filtrar lista de programas por colonia
- Generar reportes por colonia

### Reportes por Geografía

Los reportes se pueden filtrar por:
- Calles específicas
- Colonias particulares
- Rangos de códigos postales
- Todo el municipio

## Mejores Prácticas

### Convenciones de Nomenclatura

**Calles:**
- Use nombres oficiales de registros de la ciudad
- Capitalice apropiadamente: "Juárez" no "JUAREZ" o "juarez"
- No incluya tipo en nombre: "Juárez" no "Calle Juárez"
- Agregue acentos donde sea apropiado: "Revolución" no "Revolucion"

**Colonias:**
- Use nombres oficiales del servicio postal
- Coincida con designaciones SEPOMEX
- Incluya direcciones cardinales si es oficial: "Centro Norte"
- Evite abreviaturas: "Fraccionamiento" no "Fracc."

### Precisión de Datos

**Verificar Antes de Agregar:**
1. Verificar fuentes oficiales (ciudad, servicio postal)
2. Confirmar ortografía
3. Validar código postal
4. Buscar entradas similares existentes

**Fuentes para Consultar:**
- SEPOMEX (Servicio Postal Mexicano) catálogo oficial
- Planes de desarrollo urbano municipal
- Google Maps (para referencia, no única fuente)
- Directorio oficial de calles de la ciudad

### Prevención de Duplicados

**Antes de Agregar Nuevo:**
1. Buscar exhaustivamente
2. Probar variaciones: "5 de Diciembre", "5 Diciembre", "Cinco de Diciembre"
3. Verificar errores ortográficos comunes
4. Revisar entradas agregadas recientemente

**Cuando Encuentre Duplicados:**
1. Determinar cuál es correcto/más completo
2. Notar conteo de uso para cada uno
3. Migrar datos a versión principal
4. Eliminar duplicado solo cuando sea seguro

## Solución de Problemas

### Calle/Colonia No Aparece en Menú Desplegable

**Soluciones:**
1. Actualizar la página
2. Limpiar búsqueda e intentar de nuevo
3. Verificar que se guardó (revisar lista)
4. Verificar ortografía en búsqueda de menú desplegable
5. Agregarla si verdaderamente falta

### No Se Puede Eliminar Calle/Colonia

**Razón:**
- Aún en uso por direcciones de ciudadanos
- Referenciada en registros de programas

**Resolución:**
```
1. Buscar todos los ciudadanos que usan esta calle/colonia
2. Decidir si las entradas deben actualizarse o si la eliminación es incorrecta
3. Si verdaderamente es un duplicado, actualizar todos los ciudadanos para usar versión correcta
4. Una vez que el conteo de uso llegue a 0, se permite la eliminación
5. O mantener entrada si está realmente en uso (no eliminar)
```

### El Código Postal No Coincide

**Verificar:**
1. Verificar con catálogo oficial SEPOMEX
2. Actualizar código postal de colonia si es incorrecto
3. O reasignar ciudadano a colonia correcta
4. Documentar fuente del código postal correcto

### Demasiados Resultados de Búsqueda

**Refinar Búsqueda:**
1. Usar términos más específicos
2. Incluir código postal en búsqueda
3. Agregar nombre de municipio
4. Usar frase exacta si es posible

## Referencia Rápida

### Tipos Comunes de Calles

| Español | Inglés | Uso |
|---------|---------|-------|
| Calle | Street | Calles estándar |
| Avenida | Avenue | Vías principales |
| Boulevard | Boulevard | Vías amplias |
| Privada | Private | Calles cerradas/privadas |
| Cerrada | Closed | Calles sin salida |
| Callejón | Alley | Pasajes estrechos |
| Camino | Road | Rutas menos urbanas |
| Andador | Walkway | Caminos peatonales |

### Atajos de Teclado
- **Tab**: Moverse entre campos del formulario
- **Enter**: Enviar búsqueda
- **Esc**: Cancelar edición en línea
- **Ctrl/Cmd + F**: Búsqueda rápida en página

## Próximos Pasos

Ahora que entiende los datos geográficos:

- **[Escáner QR](06-qr-scanner.md)**: Acceso rápido a información de ciudadanos
- **[Reportes](07-reports.md)**: Gestione reportes de ciudadanos
- **[Consejos y Trucos](08-tips-and-tricks.md)**: Flujos de trabajo avanzados y atajos

---

**Consejo Profesional**: Cuando los ciudadanos llamen preguntando sobre programas, tener direcciones precisas significa que puede encontrarlos rápidamente y verificar su inscripción. Mantenga los datos geográficos limpios para operaciones fluidas.
