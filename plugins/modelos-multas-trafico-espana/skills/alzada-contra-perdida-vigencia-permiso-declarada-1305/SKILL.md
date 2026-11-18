---
name: alzada-contra-perdida-vigencia-permiso-declarada-1305
description: "Redacta el escrito «Alzada contra la pérdida de vigencia del permiso declarada por la Jefatura Provincial de Tráfico» (formulario 1305 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra la pérdida de vigencia del permiso declarada por la Jefatura Provincial de Tráfico

> Formulario 1305 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (4 veces)
- [ ] Nº
- [ ] AÑO
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ada por el Jefe Provincial de Tráfico de»; «…/[AÑO] clase»; «…cialmente las numeradas en los apartados»; «… ellas hubiera correspondido, por cuanto»; «…onadores y puntos asignados, así como en»; «…, en el centro autorizado»; «…specialmente las señalas con los números»; «… especialmente la anotada en el apartado»

## Párrafos opcionales (9)

Inclúyelos solo si encajan en los hechos:

- Que las infracciones que se contienen en la relación expresada en la resolución por la que se declara la pérdi…
- Que en el texto del acuerdo no se contiene de forma correcta y completa el enunciado de la relación detallada …
- Que a la vista de las infracciones se puede concluir que no se corresponde el enunciado contenido en el acuerd…
- Que no se ha computado de forma correcta la asignación de puntos al interesado, ya que no consta la recarga de…
- Que las sanciones consignadas en el acuerdo de inicio, especialmente las señalas con los números [COMPLETAR], …
- Que la asignación de puntos es errónea por cuanto las infracciones señaladas en el listado no tienen atribuida…
- Que he recibido la notificación de la resolución por la que se comunica la pérdida de vigencia del permiso de …
- Que la resolución por la que se declara la pérdida de vigencia del permiso de conducir no se ha instruido corr…
- Que por parte de la Jefatura de Tráfico se ha dictado la resolución por la que se declara la pérdida del vigen…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto Legislativo 6/2015
- Ley 39/2015
- Real Decreto 818/2009

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

### Formulario 1305 · Alzada contra la pérdida de vigencia del permiso declarada por la Jefatura Provincial de Tráfico

- Año del modelo: 2006
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 9 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA PROVINCIAL DE TRÁFICO DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P. [C.P.] ante el órgano superior de la Jefatura Provincial de Tráfico, como mejor proceda comparece y

DICE

Que en virtud de este escrito interpone RECURSO DE ALZADA contra la resolución de fecha [FECHA], dictada por el Jefe Provincial de Tráfico de [COMPLETAR], en la que se declara la pérdida de vigencia del permiso/licencia de conducir, número [Nº]/[AÑO] clase [COMPLETAR], expedido a favor del interesado, como consecuencia de la supuesta pérdida total del crédito de puntos que tiene asignado conforme al sistema de gestión de autorizaciones para conducir.

Que la citada resolución, por la que se declara la pérdida de vigencia del permiso de conducir, es contraria a Derecho por cuanto vulnera las normas y los principios legales, así como las garantías que corresponden a los interesados en este tipo de procedimientos administrativos, y de modo particular en lo que se refiere a la correcta descripción de las infracciones supuestamente cometidas en relación con el número de puntos asignados para cada una de ellas, y las cuestiones referentes al control del saldo de puntos que corresponden al interesado en relación con el baremo legalmente establecido, todo lo cual hace que la resolución impugnable y debe ser dejada sin efecto conforme a los siguientes

MOTIVOS

[OPCIONAL — incluir si procede]

Que las infracciones que se contienen en la relación expresada en la resolución por la que se declara la pérdida de vigencia del permiso de conducir no fueron en su día notificadas al interesado, especialmente las numeradas en los apartados [COMPLETAR], lo que implica que no pueden ser definitivas y firmes al no haberse notificado previamente al interesado para que pueda ejercer su derecho de defensa contra las mismas, siendo un acto unilateral contrario a Derecho darlas por definitivas y firmes y vía administrativa sin que se haya dado previamente la oportunidad de recurrirlas.

[OPCIONAL — incluir si procede]

Que en el texto del acuerdo no se contiene de forma correcta y completa el enunciado de la relación detallada de las resoluciones firmes en vía administrativa que supuestamente han dado lugar a la pérdida de puntos, con indicación del número de puntos que a cada una de ellas hubiera correspondido, por cuanto [COMPLETAR], lo que determina la incorrección y nulidad del acuerdo de inicio.

[OPCIONAL — incluir si procede]

Que a la vista de las infracciones se puede concluir que no se corresponde el enunciado contenido en el acuerdo con las correspondientes resoluciones sancionadoras, lo que no ofrece garantías en términos de defensa legal, teniendo en cuenta que se trata de un expediente que suprime y elimina un derecho fundamental a la libertad de desplazamientos en relación con la pérdida del permiso para conducir, sin resultar acreditada la correspondencia entre las infracciones supuestamente cometidas conforme a sus resoluciones y el listado contenido en el acuerdo, desconexión que se manifiesta en fechas, contenidos sancionadores y puntos asignados, así como en [COMPLETAR], todo lo cual determina la nulidad del acuerdo de inicio.

[OPCIONAL — incluir si procede]

Que no se ha computado de forma correcta la asignación de puntos al interesado, ya que no consta la recarga del crédito de puntos lograda mediante el curso de recuperación parcial de puntos seguido con fecha [FECHA], en el centro autorizado [COMPLETAR], y que debió computarse automáticamente, sin que esta parte sea responsable de los fallos del sistema.

[OPCIONAL — incluir si procede]

Que las sanciones consignadas en el acuerdo de inicio, especialmente las señalas con los números [COMPLETAR], no son definitivas y firmes en vía administrativa, por cuanto con fecha [FECHA] fueron recurridas, estando en el momento presente pendiente su resolución sin haberse agotado los plazos legales para considerarlas firmes en vía administrativa.

[OPCIONAL — incluir si procede]

Que la asignación de puntos es errónea por cuanto las infracciones señaladas en el listado no tienen atribuida la pérdida de puntos marcada, especialmente la anotada en el apartado [COMPLETAR], conforme al baremo legalmente establecido en el Anexo II del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV).

[OPCIONAL — incluir si procede]

Que he recibido la notificación de la resolución por la que se comunica la pérdida de vigencia del permiso de conducir sin haberse dado previamente la oportunidad de formular alegaciones dentro del plazo de diez días establecido reglamentariamente a efectos de poder manifestar los motivos por los que se considera contrario a Derecho la pérdida de vigencia del permiso, lo que ocasiona indefensión al interesado y la consiguiente nulidad de la resolución del expediente.

[OPCIONAL — incluir si procede]

Que la resolución por la que se declara la pérdida de vigencia del permiso de conducir no se ha instruido correctamente por parte de la Jefatura de Tráfico, ya que las comprobaciones efectuadas del saldo de puntos no han seguido ningún protocolo de control homologado, ni se han expedido los certificados previos e informes preceptivos para fundamentar la resolución, la cual, además no está debidamente validada, registrada y notificada.

[OPCIONAL — incluir si procede]

Que por parte de la Jefatura de Tráfico se ha dictado la resolución por la que se declara la pérdida del vigencia del permiso de conducir, sin haber acordado previamente la apertura de un período de prueba de las alegaciones manifestadas por este interesado, así como sin haber dictado resolución motivada por la que se denieguen las pruebas propuestas para la correcta instrucción del expediente, lo que determina un vicio de nulidad e indefensión especialmente cualificado que determina la estimación del recurso de alzada.

Que de conformidad con lo establecido en los artículos 112 y Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, se presenta este recurso de alzada, en el plazo de un mes concedido al efecto, que puede interponerse tanto ante el órgano competente para resolverlo como ante el propio órgano autor del acto.

En virtud de lo expuesto, conforme a lo previsto en el TR LTCVMSV, en relación con el Real Decreto 818/2009, de 8 de mayo, por el que se aprueba el Reglamento General de Conductores, y las demás normas de general y pertinente aplicación,

SOLICITA

Que se tenga por presentado este RECURSO DE ALZADA en tiempo y forma, se admita a trámite, y de conformidad con lo manifestado en el mismo se proceda a su estimación total, dejando sin efecto la resolución impugnada en la que se declara la pérdida de vigencia del permiso/licencia de conducir referenciado, por ser contraria a Derecho en los términos expresados anteriormente.

Que hasta que se proceda a la resolución de este recurso de alzada se proceda a la suspensión de la ejecutividad de la resolución impugnada, a efectos de no ocasionar daños y perjuicios al interesado que, en su caso, podrían dar lugar a responsabilidad patrimonial de la Administración autora del acto en razón de su vulneración del ordenamiento jurídico y mal funcionamiento del servicio público.

En [LUGAR], a [FECHA].

Firma
