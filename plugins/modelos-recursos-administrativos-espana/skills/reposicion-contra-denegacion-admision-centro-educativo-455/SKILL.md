---
name: reposicion-contra-denegacion-admision-centro-educativo-455
description: "Redacta el escrito «Reposición contra denegación de admisión en un centro educativo» (formulario 455 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra denegación de admisión en un centro educativo

> Formulario 0455 del plugin **Recursos administrativos** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD (3 veces)
- [ ] TELÉFONO
- [ ] FECHA (4 veces)
- [ ] CALLE
- [ ] Nº (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…vincial de la Consejería de Educación de»; «…itidos para cursar estudios de Educación»; «…en el año académico»; «…dministrativa impugnada incluye al menor»; «…ndiente al Distrito educativo del Centro»; «…nueva vivienda (acompaño como documentos»; «…, lo que determina la admisión del menor»; «…para la admisión del alumnado. SEGUNDO.-»; «…TERCERO.-»; «…timando el recurso y admitiendo al menor»; «…como alumno del curso»; «…de Educación»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112.1 de la Ley 39/2015
- artículos 121 y 122 de la Ley 39/2015

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, MASC si es una demanda civil).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0455 · Reposición contra denegación de admisión en un centro educativo

- Año del modelo: 2012
- Revisión 17-11-2026: 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, con D.N.I. y con domicilio a efectos de notificaciones sito en [LOCALIDAD], y con teléfono [TELÉFONO] (además, en su caso, fax y/o correo electrónico), comparece y como mejor proceda, DICE:

Que en fecha [FECHA] he sido notificado de la resolución de la Delegación Provincial de la Consejería de Educación de [COMPLETAR] de fecha [FECHA], por la que se publica la relación de alumnos admitidos y no admitidos para cursar estudios de Educación [COMPLETAR] en el año académico [COMPLETAR], y de conformidad con lo prevenido en el art. 112.1 de la Ley 39/2015, por medio del presente escrito interpongo RECURSO DE REPOSICIÓN (en su caso se interpondría alzada al amparo de los artículos 121 y 122 de la Ley 39/2015) en base a los siguientes MOTIVOS:

PRIMERO.- La resolución administrativa impugnada incluye al menor [COMPLETAR], hijo del recurrente, en la relación de alumnos no admitidos al no haberse puntuado el apartado correspondiente al "domicilio" por falta de residencia efectiva en el domicilio que se hizo constar en la solicitud.

La resolución infringe los criterios normativamente predeterminados acerca de la valoración del domicilio, en los cuales se dispone que el domicilio se acreditará mediante certificación expedida por el Ayuntamiento respectivo y que se considerará como domicilio el habitual de convivencia de los padres, madres o tutores legales del alumnado o, en su caso, el del alumnado de bachillerato si vive en domicilio distinto de los de aquéllos. Cuando los padres, madres o tutores legales vivan en domicilios diferentes, se considerará como domicilio el de la persona con quien conviva el alumno o alumna y tenga atribuida la guarda y custodia del mismo.

El recurrente acreditó su domicilio en la calle [CALLE], correspondiente al Distrito educativo del Centro [COMPLETAR], mediante certificación de empadronamiento expedida por el Ayuntamiento de [LOCALIDAD], siendo el domicilio a la fecha de la solicitud

Posteriormente, en fecha [FECHA], la familia se trasladó al domicilio sito en [LOCALIDAD], zona de influencia del mismo Centro educativo, al haber finalizado el contrato de alquiler en el anterior inmueble y haber adquirido una nueva vivienda (acompaño como documentos [COMPLETAR] contrato de arrendamiento del anterior inmueble, contrato de compraventa de la nueva vivienda y certificación de empadronamiento del Ayuntamiento).

En fecha posterior al traslado de domicilio, se realizó un Acta de Comprobación Domiciliaria por la Policía Local en la que se hacía constar que el domicilio se encontraba deshabitado y que no coincidía el domicilio alegado en solicitud de admisión del menor en el centro, lo cual determina a la Administración a la que me dirijo a no puntuar el concepto de domicilio, lo que implica la no admisión del menor.

Dicha actuación infringe las normas anteriormente expresadas en orden al domicilio por cuanto que, en primer lugar, se refieren exclusivamente al domicilio en el momento de la solicitud que indudablemente era el que se hizo constar en la solicitud de admisión y hasta el día [FECHA] en que se produjo el cambio de domicilio; ello no se ve contradicho por el Acta de Comprobación Domiciliaria realizada por la Policía, en la cual se ponía de manifiesto que dicho piso se encontraba deshabitado, toda vez que dicha Acta tiene fecha posterior al cambio de domicilio. En segundo lugar, en ningún momento se exige al solicitante que notifique a la Administración el cambio de domicilio. Y, por último, el nuevo domicilio se incluye en el área de influencia del Centro educativo.

En consecuencia, solicitamos que se anule la resolución impugnada en este extremo, otorgando la puntuación de [Nº] puntos por domicilio en la zona de influencia del Centro, lo que determina la admisión del menor [COMPLETAR], al ser su puntuación global de [Nº] puntos, superior a la que se ha fijado para la admisión del alumnado.

SEGUNDO.- [COMPLETAR]

TERCERO.- [COMPLETAR]

Por todo lo expuesto,

SOLICITO tenga por presentado este escrito, junto con los documentos que se acompañan, y por interpuesto recurso de reposición contra [ACTO O RESOLUCIÓN] y, en virtud de las alegaciones contenidas en el mismo y previos los trámites legales, dicte resolución estimando el recurso y admitiendo al menor [COMPLETAR] como alumno del curso [COMPLETAR] de Educación [COMPLETAR] en el Centro [COMPLETAR], curso académico

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del recurrente

A LA DELEGACIÓN PROVINCIAL DE LA CONSEJERÍA DE EDUCACIÓN DE [COMPLETAR]
