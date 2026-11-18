---
name: notificar-inculpado-inicio-sancionador-acordado-oficio-208
description: "Redacta el escrito «Notificar al inculpado el inicio del sancionador acordado de oficio» (formulario 208 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificar al inculpado el inicio del sancionador acordado de oficio

> Formulario 0208 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] FECHA (3 veces)
- [ ] ÓRGANO O PERSONA
- [ ] ACTO O RESOLUCIÓN
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en su condición de titular de»; «…ráfico, ha tenido noticia de que por don»; «…rativa de conformidad con en el artículo»; «…uridad Vial, en relación con el artículo»; «…s hechos descritos, que se instruirá por»; «…, con la asistencia de»; «…euros, además de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 86.1 del Real Decreto Legislativo 6/2015
- Real Decreto 1428/2003
- Ley 39/2015

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

### Formulario 0208 · Notificar al inculpado el inicio del sancionador acordado de oficio

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 llamadas a nota sin texto retiradas; 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Por el/la Ilmo./Ilma. Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS], en su condición de titular de [COMPLETAR], órgano competente para resolver los procedimientos en materia de tráfico, con esta fecha y en el asunto de referencia, se ha dictado el siguiente acuerdo de iniciación de expediente sancionador:

"Mediante escrito de fecha [FECHA], formulado por [ÓRGANO O PERSONA], este órgano administrativo competente en materia de sanciones de tráfico, ha tenido noticia de que por don [COMPLETAR], con fecha [FECHA], se han realizado los siguientes hechos:

Los hechos descritos en el párrafo anterior pueden ser constitutivos de infracción administrativa de conformidad con en el artículo [COMPLETAR] del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, en relación con el artículo [COMPLETAR], del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación.

En su virtud, de conformidad con las previsiones del artículo 86.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: Incoación de oficio: art. 86.1 TR LSV. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 86.1.], y la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, he tenido a bien dictar el siguiente

ACUERDO:

PRIMERO.- Iniciar de oficio expediente sancionador contra [ACTO O RESOLUCIÓN] por los hechos descritos, que se instruirá por [COMPLETAR], con la asistencia de [COMPLETAR] para las funciones de secretaría del expediente y que podrán ser recusados de conformidad con las previsiones de la legislación sobre procedimiento administrativo común.

SEGUNDO.- Sin perjuicio de lo que resulte de la instrucción, por la realización de la infracción mencionada corresponde una multa de [IMPORTE] euros, además de [COMPLETAR] como sanciones complementarias.

TERCERO.- Dese traslado de este acuerdo de iniciación de expediente sancionador al instructor del mismo y notifíquese al inculpado para que en el plazo de quince días [NOTA DE REVISIÓN (comprobar): El TR LSV da 20 días naturales para alegar tras la notificación de la denuncia (art. 95.1); en la incoación de oficio sin denuncia conviene usar ese mismo plazo. NO VERIFICADO que la DGT aplique otro en este supuesto. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 86 y 95.1.] realice las alegaciones e informaciones que estime convenientes, y, en su caso, proponer prueba concretando los medios de que pretende valerse.

Lo que notifico a usted, en cuanto inculpado en el citado procedimiento administrativo sancionador haciéndole las siguientes manifestaciones:

Con independencia de la posibilidad de presentar alegaciones, informaciones y pruebas en el plazo de quince días antes mencionado, por el inculpado, en cualquier momento del procedimiento, se puede tener acceso al expediente, para conocer el estado de su tramitación y obtener copias de los documentos contenidos en el mismo.

En caso de no presentar alegaciones sobre el contenido de este acuerdo de iniciación en el plazo antes mencionado, la iniciación notificada podrá ser considerada propuesta de resolución, ya que contiene un pronunciamiento preciso sobre la responsabilidad imputada y sus consecuencias jurídicas.

Asimismo, y con anterioridad a que se acuerde la apertura del trámite de audiencia, los interesados podrán formular alegaciones y aportar los documentos que estimen convenientes.

Una vez recibida la notificación de este acuerdo de incoación, si el infractor reconoce su responsabilidad, se podrá resolver el procedimiento con la imposición de la sanción que proceda.

El pago de la multa propuesta, en cualquier momento anterior a la resolución, podrá implicar igualmente la terminación del procedimiento, sin perjuicio de la posibilidad de interponer los recursos procedentes.

Si por el inculpado se procede al pago de la sanción, podrá beneficiarse de una reducción de del 20 por 100 sobre la cuantía de la sanción propuesta inicialmente.

En [LUGAR], a [FECHA].

Firmado:
