---
name: alegaciones-multa-titular-sin-detener-vehiculo-ni-318
description: "Redacta el escrito «Alegaciones: multa al titular sin detener el vehículo ni requerirle identificar al conductor» (formulario 318 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones: multa al titular sin detener el vehículo ni requerirle identificar al conductor

> Formulario 0318 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A»; «…DE»; «…número [NÚMERO] CP [C.P.] de»; «…, ante [ÓRGANO] de»; «…horas del día [FECHA] de»; «…r infringido, presuntamente, el artículo»; «…de»; «…uncia, pues en tal momento me encontraba»; «…En virtud de lo expuesto, SOLICITO A»; «…DE»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: MEDIOS DE PRUEBA / A) Estar los agentes ocupados con otro usuario / B) Por circunstancias del tráfico / C) Por factores meteorológicos adversos / D)Por obras / E) En todo caso — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 89 del Real Decreto Legislativo 6/2015
- artículo 95 del Real Decreto Legislativo 6/2015
- artículo 77 de la Ley 39/2015
- artículo 10.2 del Real Decreto 320/1994

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

### Formulario 0318 · Alegaciones: multa al titular sin detener el vehículo ni requerirle identificar al conductor

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 23 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (COMPLETAR)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A [COMPLETAR] DE [COMPLETAR]

D./Dª [NOMBRE Y APELLIDOS] mayor de edad, con domicilio en la C/ [CALLE] número [NÚMERO] CP [C.P.] de [COMPLETAR] y provisto de DNI número [DNI/NIE], ante [ÓRGANO] de [COMPLETAR] comparezco y, como mejor proceda en derecho, DIGO:

Que con fecha [FECHA] se me ha notificado la denuncia formulada a las [Nº] horas del día [FECHA] de [COMPLETAR] de [AÑO] contra el conductor del vehículo marca [MARCA/MODELO] modelo [MARCA/MODELO] matrícula [MATRÍCULA] del cual es titular el compareciente, por haber infringido, presuntamente, el artículo [COMPLETAR] de [COMPLETAR] y cometer los siguientes hechos:

Que por tales hechos se sigue contra el compareciente el expediente número [Nº DE EXPEDIENTE] y no estando conforme con la denuncia ni con la sanción que se pretende imponer, dentro del plazo conferido y en forma legal, por medio del presente escrito formulo las siguientes

ALEGACIONES

Con carácter previo, niego que el compareciente fuera el conductor del vehículo denunciado en el día y hora de la denuncia, pues en tal momento me encontraba [COMPLETAR]

Que ignoro por qué el agente denunciante no detuvo el vehículo en el momento de cometerse la presunta infracción, pues en el escrito que ahora se me notifica no se realiza ninguna descripción detallada de los motivos que impidieron la notificación instantánea al conductor del vehículo, tal y como ordena, como norma general, el artículo art. 89 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, que establece que será causa legal que justifica la notificación de la denuncia en momento posterior el hecho de formularse la misma en circunstancias en que la detención del vehículo pueda originar un riesgo para la circulación o cuando la denuncia se formule estando el vehículo estacionado, y el conductor no esté presente, o cuando el agente denunciante se encuentre realizando tareas de vigilancia y control de tráfico y carezca de medios para proceder a la persecución del vehículo. En el caso que nos ocupa no concurre ninguno de dichos supuestos que justifican la notificación posterior, no se describe ningún riesgo concreto, las circunstancias meteorológicas eran óptimas y la circulación fluida y el conductor estuvo hablando con el agente denunciante.

En dicho precepto se incluyen también los supuestos en los que la Autoridad haya tenido conocimiento de los hechos a través de medios de captación y reproducción de imágenes, pero en el boletín no se indican dichos medios ni sus características técnicas.

Con tales normas, el Legislador ha querido que la notificación de las denuncias en el acto sea la norma general, y ello es así porque la notificación personal y en el mismo momento de cometerse la presunta infracción es la principal oportunidad de defensa que tiene el eventual infractor, en cuanto le permite apreciar in situ las concretísimas circunstancias concurrentes en el hecho que podrían explicar o justificar la supuesta infracción, no sólo a juicio del denunciado, sino incluso a juicio del propio denunciante, y por ello, sólo si concurren razones justificadas, que habrá de probar el Agente denunciante, será válida la notificación posterior, pues en caso contrario la denuncia será nula.

Que al amparo de lo dispuesto en el artículo 95 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, y en el artículo 77 de la Ley 39/2015, de 1 de octubre, [NOTA DE REVISIÓN (comprobar): Prueba en el procedimiento sancionador de tráfico: art. 95.2 TR LSV y, supletoriamente, art. 77 LPAC. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 95; Ley 39/2015 art. 77.] y para evitar indefensión, interesa al derecho de esta parte se practiquen y se dé traslado de los siguientes

[ELEGIR UNA OPCIÓN Y REDACTARLA: MEDIOS DE PRUEBA / A) Estar los agentes ocupados con otro usuario / B) Por circunstancias del tráfico / C) Por factores meteorológicos adversos / D)Por obras / E) En todo caso — el texto de cada opción no venía en el formulario original]

En virtud de lo expuesto,

SOLICITO A [COMPLETAR] DE [COMPLETAR] Que tenga por presentado este escrito en tiempo y forma legales, se digne admitirlo, así como por efectuadas las alegaciones contenidas en el mismo y, a su tenor, acuerde el archivo del expediente incoado, por carecer de validez la denuncia formulada conforme dispone el artículo 10.2 del Real Decreto 320/1994, de 25 de febrero, que aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, en relación con los artículos 87 y 89.2.a) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: Los arts. 75 y 81.3 citados son de la ley antigua (hoy 75 = infracciones leves; 81 no tiene apartado 3). La notificación posterior exige que el agente indique los motivos concretos (art. 89.2.a TR LSV); el art. 10.2 RD 320/1994 (formalmente vigente) añade la invalidez de la denuncia. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 87 y 89.2; RD 320/1994, BOE-A-1994-8985 art. 10.2.] y, en caso contrario, acuerde la práctica de los medios de prueba que se proponen, dando traslado de su resultado al compareciente, para evitar indefensión.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
