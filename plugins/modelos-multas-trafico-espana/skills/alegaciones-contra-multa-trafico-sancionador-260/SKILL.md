---
name: alegaciones-contra-multa-trafico-sancionador-260
description: "Redacta el escrito «Alegaciones contra multa de tráfico en sancionador» (formulario 260 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones contra multa de tráfico en sancionador

> Formulario 0260 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE EXPEDIENTE
- [ ] FECHA
- [ ] IMPORTE
- [ ] LOCALIDAD
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procedimiento»; «…, he sido denunciado por»; «…secuencia de una infracción del artículo»; «… sanción propuesta, formula el siguiente»; «…ivos por los que se impone la sanción de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 89 del Real Decreto Legislativo 6/2015
- art. 13 de la LPACAP

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

### Formulario 0260 · Alegaciones contra multa de tráfico en sancionador

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 9 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente nº [Nº DE EXPEDIENTE]

Procedimiento [COMPLETAR]

I.- Que con fecha [FECHA], he sido denunciado por [COMPLETAR] por lo que se impone una multa de [IMPORTE], como consecuencia de una infracción del artículo [COMPLETAR]

II.- Que no hallándose conforme con los hechos que se le imputan, ni con la sanción propuesta, formula el siguiente [COMPLETAR] (escrito de alegaciones o descargos, recurso ordinario, de alzada, recurso de reposición), que fundamento en las siguientes

ALEGACIONES

PRIMERA.- Que la descripción de los hechos imputados en este expediente no se corresponde con la realidad, por lo cuanto que de las pruebas que se solicitan se podrá observar la invalidez de la sanción imputada, negamos pues la veracidad de la infracción imputada.

El abajo firmante, manifiesta que en el día y, aproximadamente, a la hora señalada, circuló (o no circuló) por el lugar que se indica, pero que acostumbra a respetar todas las normas, disposiciones y limitaciones establecidas, por lo que considera poco probable que circulara a tal velocidad, lo que induce a pensar que existe algún error en la medición del cinemómetro.

En este sentido, cabe recordar que la STSJ Castilla-La Mancha núm. 91/2003 (Sala de lo Contencioso-Administrativo, Sección 2), de 8 febrero, establece:

En cuanto a las dudas vertidas respecto al cinemómetro utilizado se ha de resaltar que, en un supuesto como el presente en el que el agente denunciante recoge en el boletín los datos emanados de un aparato cinemómetro habrá de atenderse a la credibilidad que ofrezcan esos aparatos en sus mediciones técnicas para considerar probadas las mismas, y a tal efecto resulta esencial la identificación del concreto cinemómetro empleado para verificar, en su caso, su buen funcionamiento. En el presente supuesto, el agente denunciante consignó en el boletín que se trataba del aparato Multanova Radar 6F, y entregó fotocopia de verificación emitida por el Centro Español de Metrología que acredita la idoneidad del aparato cinemómetro utilizado, pues dicho certificado, expedido el día 9 de junio de 1997, prueba la conformidad para su cometido durante un año (con lo que estaba vigente el día de la denuncia, -14.10.97-), y en el que se indica el mismo número de antena y modelo que el consignado en la fotografía obrante en el expediente. Por lo que respecta a la falta de validez de la fotocopia que le fue entregada del certificado del Centro Español de Metrología está cotejado con el original según se lee en el sello estampado en el mismo con fecha 1.6.97 firmado por don Juan Pablo, y, no es por tanto, una simple fotocopia sin valor probatorio alguno como afirma la parte recurrente.

SEGUNDA Los Agentes actuantes no la han cumplido con sus obligaciones toda vez que dice el artículo 89 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido [NOTA DE REVISIÓN: El RDLeg 6/2015 aprueba un texto refundido (el «texto articulado» era el RDLeg 339/1990, derogado). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 (título oficial).] de la Ley sobre Tráfico, Circulación de Vehículos a Motor y de Seguridad Vial que las denuncias de carácter obligatorio formuladas por Agentes de la Autoridad, se notificarán en el acto al denunciado, y no consta que se dé alguna de las excepciones previstas por la norma para omitir tal obligación.

De la normativa anteriormente citada se deduce la obligación del Agente de parar al conductor o justificar las razones por las que no se hizo, lo que se incumple en el presente expediente y procede la nulidad del mismo.

No se puede cargar a esta parte con las consecuencias de un incumplimiento de la normativa por parte del denunciante o denunciantes, ni por su falta de eficiencia ni tampoco por un deficiente montaje de su servicio.

TERCERA. Falta de motivación de la sanción.

En la denuncia apenas se exponen los hechos objeto de la misma y no permiten conocer los motivos por los que se impone la sanción de [COMPLETAR]

La STSJ Castilla-La Mancha núm. 91/2003 (Sala de lo Contencioso-Administrativo, Sección 2), de 8 febrero, establece:

Aplicando la doctrina reiterada por la Sala al presente supuesto, al no haber sido reflejada situación de peligro, ni en el boletín de denuncia, ni en la resolución sancionadora, ni en la que resuelve el recurso ordinario, (sólo una mera referencia al genérico y potencial peligro del exceso de velocidad), y, por tanto no habiendo sido concretados los fundamentos que han servido de base para imponer dicha sanción, en aras al derecho de defensa del recurrente, resulta obligada la anulación de la sanción de privación del permiso de conducir.

Por todo ello:

SOLICITA, se sirva admitir el presente escrito, tener por hechas las manifestaciones contenidas en el mismo, previas las manifestaciones oportunas y demás trámites de rigor, y a su tenor acuerde dejar sin efecto la denuncia y la sanción anunciada.

PRIMER OTROSI DIGO.- Que para la correcta y completa determinación de los hechos imputados y sus circunstancias relevantes es preciso que se tenga a bien admitir y practicar los siguientes MEDIOS DE PRUEBA, dándose copia del expediente y de las pruebas realizadas a esta parte en cumplimiento de lo establecido en el art. 13 de la LPACAP.

I.- Que se una al expediente la fotografía del cinemómetro que motivó la denuncia.

II.- Que se una al expediente certificación de la última revisión efectuada al cinemómetro que se utilizó para hacer la fotografía, refrendada por el Sr. Secretario del expediente.

III.- Que se una al expediente fotocopia legalizada por el Instructor sobre las características del cinemómetro y error que admite.

IV.- Que se una al expediente una certificación en la que se haga constar que el denunciante estaba el día de la denuncia en acto de servicio en el lugar en donde se produjo la supuesta infracción.

V.- Informe del Agente de la Autoridad sobre las características de la vía y determinación de cómo puede afectar concretamente a la circulación, la notificación de la infracción al que suscribe.

VI.- Que se adjunte por parte de esta jefatura los siguientes documentos relacionados con la infracción que se le imputa a esta parte:

Certificado del organismo competente en materia de tráfico, en el que se determine que volumen de tráfico se produjo en la zona donde presuntamente se produjo la infracción.

VII.- Determinación del lugar donde fue instalado el conjunto que sirvió para detectar la presunta infracción, pues como es debido para que la medición sea correcta, resulta preciso que dicho conjunto esté situado en un plano horizontal con un desnivel máximo del 4% y que, asimismo, se encuentre situado a una distancia de más de 50 metros de un objeto fijo.

SUPLICO: que teniendo por articulada la prueba propuesta acordar lo procedente para la práctica de la misma.

JEFATURA PROVINCIAL DE TRÁFICO DE [LOCALIDAD]
