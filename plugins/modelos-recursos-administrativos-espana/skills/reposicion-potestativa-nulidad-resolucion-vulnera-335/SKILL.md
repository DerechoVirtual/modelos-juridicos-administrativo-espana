---
name: reposicion-potestativa-nulidad-resolucion-vulnera-335
description: "Redacta el escrito «Reposición potestativa por nulidad de resolución que vulnera el derecho a la prueba» (formulario 335 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición potestativa por nulidad de resolución que vulnera el derecho a la prueba

> Formulario 0335 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] CALLE (3 veces)
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] Nº
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «… DICE: HECHOS Primero.- Que con fecha de»; «…ruina parcial del edificio situado en la»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 123 y 124 de la Ley 39/2015
- artículo 117.1 de la LPACAP
- art. 47 de la LPACAP
- art. 24 de la CE

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

### Formulario 0335 · Reposición potestativa por nulidad de resolución que vulnera el derecho a la prueba

- Año del modelo: 2013
- Revisión 17-11-2026: 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Sr. Concejal Delegado del Área de Urbanismo del Ayuntamiento de [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], con DNI núm. [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

actuando en su propio nombre y derecho, interpone recurso potestativo de reposición contra el Decreto n.º [Nº] de [COMPLETAR], del Concejal Delegado del Área de Urbanismo del Ayuntamiento de Valverde (Madrid), que declaró en estado de ruina el inmueble ubicado en la calle [CALLE], con la obligación de la propiedad de proceder a su demolición a excepción de sus fachadas a vía pública, comparece y como mejor proceda en Derecho, DICE:

HECHOS

Primero.- Que con fecha de [COMPLETAR] se le ha notificado la mencionada Resolución del Concejal Delegado del Área de Urbanismo del Ayuntamiento de Valverde (Madrid) que declaró en estado de ruina el inmueble ubicado en la calle [CALLE], con la obligación de la propiedad de proceder a su demolición a excepción de sus fachadas a vía pública.

Segundo.- Que en la citada Resolución no se ha entrado a valorar como medio de prueba el dictamen técnico propuesto en el periodo probatorio, que respalda la posición mantenida por este recurrente y que desvirtúa las conclusiones a que ha llegado el técnico municipal para que se declare el edificio en ruina, basándose en el hecho de que es doctrina jurisprudencial consolidada (SSTS 1 abril 1996, Rec. 2401/1992, 27 enero 1998, Rec. 3511/1994, 28 junio 1999, Rec. 3880/1993, y 27 marzo 2000, Rec. 7371/1994, 6 abril 2000, Rec. 7800/1994 y 17 de julio 2000, Rec. 8386/1994), la que atribuye una cierta preferencia a los informes periciales emitidos por los técnicos municipales, ya que considera que están dotados de una presunción de mayor objetividad al estar alejados de los intereses de parte.

Tercero.- Que no considerada ajustada a Derecho la citada resolución, se interpone el presente recurso potestativo de reposición en base a los siguientes

FUNDAMENTOS DE DERECHO

Primero.- El recurso potestativo de reposición se interpone conforme a lo que disponen los artículos 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP) ya que se trata de un acto que pone fin a la vía administrativa.

El recurso se interpone en el plazo de un mes desde la notificación de la resolución, tal como exige el artículo 117.1 de la LPACAP arriba mencionada.

Segundo.- La solicitud de recibimiento a prueba de la recurrente expresaba los puntos sobre los que debía versar la prueba acreditando el informe pericial presentado que las deficiencias detectadas en el edificio cuya ruina parcial se ha declarado, no impiden que el edificio cuente con suficiente autonomía estructural y sea susceptible de ser utilizado y mantenido de forma independiente sin necesidad de proceder a su demolición parcial. Se hace especial referencia a los elementos vinculados directamente a su estabilidad, consolidación estructural, estanqueidad y en general a la seguridad de la construcción y de las personas, tales como la estructura, la cimentación, las fachadas exteriores, interiores y medianeras, las cubiertas, azoteas, voladizos, marquesinas, antenas y demás elementos susceptibles de desprendimiento, así como las redes de saneamiento y distribución de agua, gas y energía eléctrica en baja tensión.

Además se detallan en el informe pericial presentado como medio de prueba con la mayor precisión posible, las obras y demás actuaciones necesarias para mantener el edificio en condiciones adecuadas de seguridad, salubridad, ornato público y habitabilidad según su destino, realizando los trabajos precisos para conservar o reponer dichas condiciones y subsanar las deficiencias advertidas.

Tercero.- Dado que la recurrente pretendía probar la improcedencia de la declaración de la ruina parcial del edificio situado en la [COMPLETAR], la no valoración de la prueba pericial propuesta le ha causado indefensión real y efectiva, ya que la prueba presentada pretende acreditar hechos relevantes para la decisión del asunto, pudiéndose subsanar las deficiencias del edificio mediante otros instrumentos de disciplina urbanística, tales como una orden de ejecución.

Por tanto,

SOLICITA

Que se tenga por presentado este escrito, se sirva admitirlo y tenga por interpuesto recurso potestativo de reposición, y de acuerdo con lo establecido en el art. 47 de la LPACAP, se declare la nulidad de pleno derecho de la resolución que se recurre, toda vez que se ha conculcado el derecho fundamental a la prueba proclamado por el art. 24 de la CE.

En [LUGAR], a [FECHA].

Firmado:
