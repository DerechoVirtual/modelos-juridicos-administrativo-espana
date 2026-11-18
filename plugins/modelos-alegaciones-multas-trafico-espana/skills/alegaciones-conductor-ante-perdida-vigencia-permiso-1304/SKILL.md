---
name: alegaciones-conductor-ante-perdida-vigencia-permiso-1304
description: "Redacta el escrito «Alegaciones del conductor ante la pérdida de vigencia del permiso por perder todos los puntos» (formulario 1304 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del conductor ante la pérdida de vigencia del permiso por perder todos los puntos

> Formulario 1304 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] FECHA (5 veces)
- [ ] Nº
- [ ] AÑO
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO] clase»; «… ellas hubiera correspondido, por cuanto»; «…onadores y puntos asignados, así como en»; «…, en el centro autorizado»; «…ecialmente las señaladas con los números»; «… especialmente la anotada en el apartado»; «…tos que se acompañan, así como la prueba»; «…, para acreditar que»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 37 del Real Decreto 818/2009
- Real Decreto Legislativo 6/2015
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

### Formulario 1304 · Alegaciones del conductor ante la pérdida de vigencia del permiso por perder todos los puntos

- Año del modelo: 2006
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 15 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA PROVINCIAL DE TRÁFICO DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P. [C.P.] ante la Jefatura Provincial de Tráfico, como mejor proceda comparece y

DICE

Que, con fecha [FECHA], ha recibido la notificación de un acuerdo de fecha [FECHA], por medio del cual se inicia el procedimiento para declarar la pérdida de vigencia del permiso o licencia de conducir número [Nº]/[AÑO] clase [COMPLETAR], del que es titular el interesado, como consecuencia de haberse constatado la pérdida de la totalidad de los puntos asignados.

Que a la vista del citado acuerdo de inicio de expediente, y estando en total disconformidad con el mismo, dentro del plazo de diez días concedido al efecto, en aplicación de lo establecido en el artículo 37 del Real Decreto 818/2009, de 8 de mayo, por el que se aprueba el Reglamento General de Conductores, procedo a formular las siguientes

ALEGACIONES

PrimeraQue en el texto del acuerdo no se contiene de forma correcta y completa el enunciado de la relación detallada de las resoluciones firmes en vía administrativa que supuestamente han dado lugar a la pérdida de puntos, con indicación del número de puntos que a cada una de ellas hubiera correspondido, por cuanto [COMPLETAR], lo que determina la incorrección y nulidad del acuerdo de inicio.

SegundaQue a la vista de las infracciones se puede concluir que no se corresponde el enunciado contenido en el acuerdo con las correspondientes resoluciones sancionadoras, lo que no ofrece garantías en términos de defensa legal, teniendo en cuenta que se trata de un expediente que suprime y elimina un derecho fundamental a la libertad de desplazamientos en relación con la pérdida del permiso para conducir, sin resultar acreditada la correspondencia entre las infracciones supuestamente cometidas conforme a sus resoluciones y el listado contenido en el acuerdo, desconexión que se manifiesta en fechas, contenidos sancionadores y puntos asignados, así como en [COMPLETAR], todo lo cual determina la nulidad del acuerdo de inicio.

TerceraQue no se ha computado de forma correcta la asignación de puntos al interesado, ya que no consta la recarga del crédito de puntos lograda mediante el curso de recuperación parcial de puntos seguido con fecha [FECHA], en el centro autorizado [COMPLETAR], y que debió computarse automáticamente, sin que esta parte sea responsable de los fallos del sistema.

CuartaQue las sanciones consignadas en el acuerdo de inicio, especialmente las señaladas con los números [COMPLETAR], no son definitivas y firmes en vías administrativa, por cuanto con fecha [FECHA] fueron recurridas, estando en el momento presente pendiente su resolución sin haberse agotado los plazos legales para considerarlas firmes en vía administrativa.

QuintaQue las asignación de puntos es errónea por cuanto las infracciones señaladas en el listado no tienen atribuida la pérdida de puntos marcada, especialmente la anotada en el apartado [COMPLETAR], conforme al baremo legalmente establecido en el Anexo II del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial.

SextaQue todas y cada una de las afirmaciones contenidas en este escrito de alegaciones son ciertas y así queda acreditado con la documentación que se acompaña o se señala y cuya constancia obra en los archivos y registros mencionados accesibles a la Administración de Tráfico para las debidas comprobaciones conforme a las necesidades probatorias del expediente.

En virtud de lo expuesto, de conformidad con lo establecido en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), y demás normas de general y pertinente aplicación,

SOLICITO

Que se tenga por presentado este escrito de alegaciones dentro del plazo concedido a efecto y, de conformidad con lo manifestado en el mismo, se disponga dejar sin efecto el acuerdo de inicio de expediente para declarar la pérdida de vigencia del permiso/licencia de conducir por puntos a que se hace referencia.

Que en caso de que por la Jefatura de Tráfico no se consideren probadas las alegaciones manifestadas por este interesado, solicito que se disponga la apertura de una fase de pruebas, en la que se acreditarán los hechos alegados, mediante la práctica de la prueba documental, conforme a los documentos que se acompañan, así como la prueba [COMPLETAR], para acreditar que [COMPLETAR], por ser lo que procede en Derecho.

En [LUGAR], a [FECHA].

Firma
