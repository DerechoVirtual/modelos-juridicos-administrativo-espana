---
name: reposicion-contra-multa-trafico-309
description: "Redacta el escrito «Reposición contra multa de tráfico» (formulario 309 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra multa de tráfico

> Formulario 0309 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] CALLE
- [ ] NÚMERO
- [ ] C.P.
- [ ] DNI/NIE
- [ ] ÓRGANO
- [ ] FECHA (5 veces)
- [ ] Nº DE EXPEDIENTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A»; «…DE»; «…, número [NÚMERO], CP [C.P.], de»; «…, ante [ÓRGANO] de»; «…por una presunta infracción del artículo»; «…de»; «…ecurrente por una presunta infracción de»; «…n virtud de todo lo expuesto, SOLICITO A»; «…DE»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Prescripción / Caducidad / Concurrencia de sanciones / Falta de competencia — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 112, 123 y 124 de la Ley 39/2015
- artículo 82 del Real Decreto Legislativo 339/1990
- art. 96 del Real Decreto Legislativo 6/2015
- artículo 123 de la Ley 39/2015
- artículos 47 y 48 de la Ley 39/2015
- artículo 47.1 a) de la Ley 39/2015
- artículo 53.2 de la Constitución
- artículo 77.2 de la Ley 39/2015
- artículo 24 de la Constitución
- artículo 53.2 b) de la Ley 39/2015
- art. 77.4 de la Ley 39/2015
- artículo 13 del Real Decreto 320/1994
- artículo 47 de la Ley 39/2015
- artículo 81.4 del Real Decreto Legislativo 339/1990
- art. 95 del Real Decreto Legislativo 6/2015
- artículo 25.1 de la Constitución
- artículo 27.1 de la Ley 40/2015

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

### Formulario 0309 · Reposición contra multa de tráfico

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A [COMPLETAR] DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en la C/ [CALLE], número [NÚMERO], CP [C.P.], de [COMPLETAR], y provisto de DNI número [DNI/NIE], ante [ÓRGANO] de [COMPLETAR] comparezco y como mejor proceda en derecho, DIGO:

Que con fecha [FECHA] se me ha notificado la resolución sancionadora dictada en el Expediente número [Nº DE EXPEDIENTE], por una presunta infracción del artículo [COMPLETAR] de [COMPLETAR], y no estando conforme con la misma, dentro del plazo conferido y en forma legal, por medio del presente escrito, interpongo recurso de reposición con base en los antecedentes de hecho y fundamentos de derecho siguientes.

ANTECEDENTES DE HECHO

Primero.-Con fecha [FECHA] se formuló por los Agentes de la Autoridad una denuncia contra el recurrente por una presunta infracción de [COMPLETAR]

Segundo.- Con fecha [FECHA] el que suscribe presentó escrito de alegaciones manifestando que los hechos imputados no se correspondían con la realidad, tal como consta en el expediente, pues lo que realmente aconteció fue que

Por tanto, dichos hechos no son constitutivos de la infracción administrativa que se imputa, ya que no concurren los elementos ni los requisitos necesarios de la misma.

En tiempo legal se propuso la práctica de los medios de prueba pertinentes para acreditar la veracidad de lo manifestado por esta parte, pero el Instructor del expediente

Tercero.- Con fecha [FECHA], y tras dictarse propuesta de resolución se concedió trámite de audiencia, sin haberse practicado todas las pruebas propuestas por el recurrente, causándose indefensión, y en el escrito de alegaciones volví a reiterar la solicitud de práctica de tales pruebas.

En la propuesta de resolución dictada por el instructor no se tiene en consideración ninguna de las alegaciones formuladas por el recurrente y sin motivación alguna se rechaza la práctica de la prueba interesada. La resolución que es objeto del presente recurso confirma íntegramente la propuesta de resolución del órgano instructor.

Cuarto.- En el presente expediente se han vulnerado derechos fundamentales del recurrente, lo que determina la nulidad del mismo, y además se han infringido los principios que rigen la potestad sancionadora, las normas del procedimiento administrativo aplicable y los preceptos reguladores del tráfico, circulación de vehículos a motor y seguridad vial, como analizo en los siguientes

FUNDAMENTOS DE DERECHO

Primero.- El presente recurso de reposición se interpone al amparo de lo dispuesto en los artículos 112, 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, así como del artículo 82 del Real Decreto Legislativo 339/1990, de 2 de marzo, que aprueba la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: El RDLeg 339/1990 está derogado; basta citar el art. 96 del TR LSV (RDLeg 6/2015), que ya figura entre paréntesis: reposición potestativa en un mes. Fuente: RDLeg 6/2015, art. 96 (BOE-A-2015-11722).](art. 96 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial).

Segundo.- Es competente para resolver este recurso el mismo Órgano que dictó la resolución impugnada, tal como impone el artículo 123 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

Tercero.- El artículo 124 de la citada norma establece que el plazo para interponer el recurso es de un mes si el acto es expreso y de tres meses en caso de silencio de la Administración. El plazo máximo para dictar y notificar la resolución será de un mes.

Cuarto.- Fondo del recurso.

A) CON CARÁCTER PREVIO:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Prescripción / Caducidad / Concurrencia de sanciones / Falta de competencia — el texto de cada opción no venía en el formulario original]

B) La resolución recurrida es nula de pleno derecho, y subsidiariamente anulable, por ser de aplicación los artículos 47 y 48 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, que establece los supuestos en que los actos administrativos son nulos de pleno derecho y anulables.

Así, alegamos en primer lugar la infracción del artículo 47.1 a) de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, que señala que “son nulos de pleno derecho los actos de las Administraciones Públicas que lesionen los derechos y libertades susceptibles de amparo constitucional”.

El artículo 53.2 de la Constitución Española recoge los derechos y libertades susceptibles de recurso de amparo ante el Tribunal Constitucional, como son los reconocidos en el artículo 14 y la sección primera del capítulo II del título I, y dentro de la mencionada sección primera se encuentran los artículos 24 y 25, que garantizan y reconocen el derecho a la defensa, a la presunción de inocencia y el principio de legalidad y tipicidad.

Pues bien, en el caso que nos ocupa, claramente se han vulnerado los derechos fundamentales recogidos en los artículos 24 y 25 de nuestra Constitución, y en lugar de tomar como premisa del procedimiento administrativo la inocencia del denunciado, se considera a éste culpable ab initio, sin darle siquiera la oportunidad de probar los descargos alegados y sin practicarse tampoco prueba de cargo bastante para concretar la responsabilidad de la presunta infracción cometida.

Así, aunque el artículo 77.2 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, establece que “cuando la Administración no tenga por ciertos los hechos alegados por los interesados o la naturaleza del procedimiento lo exija, el instructor del mismo acordará la apertura de un período de prueba”, y pese a que el número 3 del mismo artículo señale que “el instructor del procedimiento sólo podrá rechazar las pruebas propuestas por los interesados cuando sean manifiestamente improcedentes o innecesarias, mediante resolución motivada”, lo cierto es que el instructor no rechazó las pruebas propuestas por el hoy recurrente mediante resolución motivada. Esta actuación ocasiona auténtica indefensión vulnerándose, entre otros, el artículo 24 de la Constitución Española.

En relación con dicho precepto constitucional, se infringe artículo 53.2 b) de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas dispone que “los procedimientos sancionadores respetarán la presunción de no existencia de responsabilidad administrativa mientras no se demuestre lo contrario”, y en el art. 77.4 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, establece que “los documentos formalizados por los funcionarios a los que se reconoce la condición de autoridad y en los que, observándose los requisitos legales correspondientes se recojan los hechos constatados por aquéllos harán prueba de éstos salvo que se acredite lo contrario. En el presente expediente, no sólo no se ha aportado la prueba de cargo del denunciante, sino que nada se ha acordado respecto a la propuesta por el recurrente.

El artículo 13 del Real Decreto 320/1994, de 25 de febrero, que aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, también señala que “el instructor del procedimiento sólo podrá rechazar mediante resolución motivada las pruebas propuestas por los interesados, cuando sean improcedentes”.

Por otro lado, la letra e) del número 1 del artículo 47 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, dice que “los actos de las Administraciones Públicas son nulos de pleno derecho en los casos siguientes: los dictados prescindiendo total y absolutamente del procedimiento legalmente establecido”, y en el expediente origen del presente Recurso no sólo se ha prescindido de practicar toda la prueba de descargo propuesta por el recurrente sin haberse dictado resolución motivada al respecto, sino que también se vulnera el trámite previsto en el artículo 81.4 del Real Decreto Legislativo 339/1990, de 2 de marzo, por el que se aprueba el Texto Articulado de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, (art. 95 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial), pues cuando el denunciado niega los hechos reflejados en la denuncia y aporta datos nuevos o distintos de los inicialmente constatados, ha de darse traslado al denunciante para que emita informe en el plazo máximo de quince días, documento del que no se ha dado traslado a esta parte, y tras dictarse propuesta de resolución tampoco se ha respetado el trámite de audiencia, ni se han determinado correctamente los hechos y los responsables de los mismos, por no hablar de la ausencia absoluta de motivación de la resolución que recurrimos, con lo cual no sólo no se han respetado los principios y las normas que regulan la potestad sancionadora de la Administración, sino que tales normas y principios se han vulnerado sistemáticamente, lo que conlleva la declaración de invalidez absoluta de todo el expediente y de la resolución sancionadora dictada.

Finalmente, hago constar que los hechos imputados al recurrente no son constitutivos de la infracción administrativa que se pretende, vulnerándose el principio de tipicidad consagrado en el artículo 25.1 de la Constitución, pues nadie puede ser sancionado por acciones u omisiones que en el momento de producirse no sean constitutivas de infracción administrativa según la legislación vigente en aquel momento, y en el caso que nos ocupa es evidente que la Administración hace una interpretación extensiva de la norma sancionadora, ya que los hechos presuntamente cometidos no están descritos en el tipo que sirve de fundamento a la sanción impuesta.

Por ello, además de vulnerarse el precepto constitucional mencionado anteriormente, se infringe el artículo 27.1 de la Ley 40/2015, de 1 de octubre, del Régimen Jurídico del Sector Público, el cual establece que sólo constituyen infracciones administrativas las vulneraciones del Ordenamiento Jurídico previstas como tales infracciones por una Ley, y expresamente prohíbe, en su número 4, la aplicación analógica de las normas definidoras de infracciones y sanciones.

En virtud de todo lo expuesto,

SOLICITO A [COMPLETAR] DE [COMPLETAR]: Que tenga por presentado este escrito en tiempo y forma legales y por interpuesto recurso de reposición contra la resolución de fecha [FECHA], dictada en el expediente sancionador número [Nº DE EXPEDIENTE], para que en su día se dicte resolución declarando la nulidad de la resolución impugnada y el archivo de todas las actuaciones practicadas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
