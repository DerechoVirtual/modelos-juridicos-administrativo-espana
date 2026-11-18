---
name: reposicion-contra-denegacion-beca-estudios-458
description: "Redacta el escrito «Reposición contra denegación de beca de estudios» (formulario 458 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra denegación de beca de estudios

> Formulario 0458 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…la resolución de la Dirección General de»; «… beca solicitada para cursar estudios de»; «…en el año académico»; «…le que el recurrente, con una familia de»; «…nte datos que contradigan los documentos»; «…e se fijan en la convocatoria. SEGUNDO.-»; «…del recurrente A LA DIRECCIÓN GENERAL DE»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112.1 de la Ley 39/2015
- artículos 121 y 122 de la Ley 35/2015
- Ley 24/2005
- Real Decreto 1721/2007
- Real Decreto 1000/2012

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

### Formulario 0458 · Reposición contra denegación de beca de estudios

- Año del modelo: 2012
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, con D.N.I. y con domicilio a efectos de notificaciones sito en [LOCALIDAD], y con teléfono (además, en su caso, fax y/o correo electrónico), comparece y como mejor proceda, DICE:

Que en fecha [FECHA] he sido notificado de la resolución de la Dirección General de [COMPLETAR] de fecha [FECHA] denegando la beca solicitada para cursar estudios de [COMPLETAR] en el año académico [COMPLETAR], y de conformidad con lo prevenido en el art. 112.1 de la Ley 39/2015, por medio del presente escrito interpongo RECURSO DE REPOSICIÓN (en su caso se interpondría alzada al amparo de los artículos 121 y 122 de la Ley 35/2015) en base a los siguientes MOTIVOS:

PRIMERO.- La resolución administrativa impugnada infringe lo dispuesto en la disposición adicional novena de la Ley 24/2005, de 18 de noviembre, de reforma para el impulso de la productividad, y normativa de desarrollo, estableciendo dicha disposición adicional que las becas y ayudas al estudio que se convoquen para seguir estudios reglados y para las que no se fije un número determinado de beneficiarios se concederán de forma directa a todos los estudiantes que se encuentren en las condiciones que determinen las correspondientes convocatorias, precepto éste que resulta desarrollado por el Real Decreto 1721/2007, de 21 de diciembre, que fijó un nuevo régimen de las becas y ayudas al estudio personalizadas, modificando el anteriormente vigente de gestión centralizada y regulando, con carácter básico, los parámetros precisos para asegurar la igualdad en el acceso a las citadas becas y ayudas al estudio sin detrimento de las competencias normativas y de ejecución de las comunidades autónomas.

De acuerdo a dicho normativo, el Real Decreto 1000/2012, de 29 de junio, fijó los umbrales de renta y patrimonio familiar y las cuantías de las becas y ayudas al estudio del Ministerio de Educación, Cultura y Deporte para el curso 2012-2013, las cuales fueron desarrolladas por la Resolución de 2 de agosto de 2012, de la Secretaria de Estado, cuyo artículo 27 determina los umbrales de renta familiar, calculados conforme a lo dispuesto en los artículos 24 a 26 de la misma Resolución.

Pues bien, de acuerdo a tales umbrales, es indudable que el recurrente, con una familia de [COMPLETAR] miembros, no supera los establecidos en dicha normativa básica, la cual resulta infringida por la resolución recurrida, que contiene una motivación inexacta, ya que no obran en el expediente datos que contradigan los documentos [COMPLETAR] aportados por el recurrente, ni se ha procedido al cruce de datos con la AEAT que avalen la superación de los umbrales de renta o de patrimonio. De ahí que haya de concluirse en que no queda en modo alguno justificado el motivo esgrimido para la denegación y que la resolución recurrida adolece de una falta absoluta de motivación ya que no concreta en qué elemento concurre la apreciación de que no se cumplen los requisitos de carácter económico, ya sea en la renta o en el patrimonio o en ambos y ni siquiera indica cual de los umbrales de patrimonio es el que en su caso se sobrepasa.

Por lo demás, he cumplido escrupulosamente sus obligaciones en el procedimiento, puesto que fui requerido en dos ocasiones para la aportación de diferente documentación, requerimientos que fueron cumplimentados ya que se aportaron las certificaciones del INEM y de la Seguridad Social, donde consta claramente el cumplimiento de los requisitos económicos establecidos en las normas antes citadas.

Por ello, se solicita la estimación del recurso, reconociendo el derecho a la beca solicitada dentro de los parámetros económicos que se fijan en la convocatoria.

SEGUNDO.- [COMPLETAR]

Por todo lo expuesto,

SOLICITO tenga por presentado recurso de reposición y, en virtud de las alegaciones contenidas en el mismo y previos los trámites legales, dicte resolución estimando el recurso y reconociendo el derecho del recurrente a la percepción de la beca solicitada.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del recurrente

A LA DIRECCIÓN GENERAL DE [COMPLETAR]
