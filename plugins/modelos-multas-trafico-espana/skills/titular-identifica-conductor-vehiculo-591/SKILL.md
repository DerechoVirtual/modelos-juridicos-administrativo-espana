---
name: titular-identifica-conductor-vehiculo-591
description: "Redacta el escrito «Titular que identifica al conductor del vehículo» (formulario 591 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Titular que identifica al conductor del vehículo

> Formulario 0591 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] HORA
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA JEFATURA PROVINCIAL DE TRÁFICO DON»; «…y domicilio»; «…cho, DIGO: Que en relación al expediente»; «…ndatario/conductor habitual del vehículo»; «…del presente expediente, es propiedad de»; «…del presente expediente, es propiedad de»; «…le había dejado utilizar el vehículo era»; «…le había dejado utilizar el vehículo era»; «…tinatario del requerimiento efectuado es»; «…nducción son los siguientes: con permiso»; «…con permiso»; «…con permiso [COMPLETAR] con permiso»; …

## Elecciones que hay que hacer

- Identificación del conductor del vehículo

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 11.2 Real Decreto Legislativo 6/2015
- art. 11.1 a) del Real Decreto Legislativo 6/2015
- art. 11.3 del Real Decreto Legislativo 6/2015
- art. 11.4 del Real Decreto Legislativo 6/2015
- art. 111.1 a) del Real Decreto Legislativo 6/2015

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

### Formulario 0591 · Titular que identifica al conductor del vehículo

- Año del modelo: 2011
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA PROVINCIAL DE TRÁFICO

DON [COMPLETAR], mayor de edad, con DNI [DNI/NIE] y domicilio [COMPLETAR] en [LOCALIDAD], ante el órgano mencionado comparezco y, como mejor proceda en Derecho, DIGO:

Que en relación al expediente [COMPLETAR] formulo, en tiempo y forma oportuno, las siguientes ALEGACIONES

PRIMERA.- Habiendo sido requerido, como titular/arrendatario/conductor habitual del vehículo [COMPLETAR], a fin de identificar el conductor del mismo el día [FECHA] a la hora [HORA] procedo a cumplimentar el requerimiento efectuado.

[ELEGIR: Identificación del conductor del vehículo]

SEGUNDA.- Que aunque, efectivamente, el destinatario del requerimiento efectuado es titular del vehículo objeto del presente expediente, también lo es que, para ese vehículo, consta designado, conforme establecen el art. 11.2 y en el apartado 2 del Anexo I del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, conductor habitual.

Así pues, habiendo comunicado al Registro de Vehículos de la Dirección General de Tráfico el conductor habitual del mismo en los términos establecidos la consecuencias es que, tal y como determina el último inciso del art. 11.2 Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial se trata de un supuesto en que "el titular quedará exonerado de las obligaciones anteriores, que se trasladarán al conductor habitual".

Por lo anteriormente expuesto no me corresponde cumplir con el requerimiento de "facilitar a la Administración la identificación del conductor del vehículo en el momento de ser cometida una infracción".

SEGUNDA.- Que aunque, efectivamente, el vehículo objeto del presente expediente, es propiedad de [COMPLETAR], se trata de una empresa dedicada al alquiler de vehículos sin conductor. En este caso, la Ley de Tráfico distingue entre conductores con permiso nacional (y que, por lo tanto figuran inscritos en el Registro de Conductores e Infractores) y conductores habilitados para conducir por otro tipo de autorización.

Tratándose, como es el caso, de un conductor habilitado por permiso nacional es suficiente con "incluir el número del permiso o licencia de conducción que permita la identificación en el Registro de Conductores e Infractores".

Se adjunta al presente escrito la copia del contrato de arrendamiento, documento en el que figuran todos los datos que permiten identificar al arrendatario del vehículo en le fecha que se dice cometida la infracción y con cuyo envío se cumple con el requerimiento efectuado.

SEGUNDA.- Que aunque, efectivamente, el vehículo objeto del presente expediente, es propiedad de [COMPLETAR], se trata de una empresa dedicada al alquiler de vehículos sin conductor. En este caso, la Ley de Tráfico distingue entre conductores con permiso nacional (y que, por lo tanto figuran inscritos en el Registro de Conductores e Infractores) y conductores habilitados para conducir por otro tipo de autorización.

Tratándose, como es el caso, de este segundo supuesto, y conforme a lo establecido en el inciso final del segundo párrafo del art. 11.1 a) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, en este caso, cuando el titular fuese una empresa de alquiler de vehículos sin conductor y el conductor no figurase inscrito en el Registro de Conductores e Infractores "la copia de la autorización administrativa podrá sustituirse por la copia del contrato de arrendamiento", documento que se adjunta al presente escrito y con cuyo envío se cumple con el requerimiento efectuado.

SEGUNDA.- Que aunque, efectivamente, el destinatario del requerimiento efectuado es titular del vehículo objeto del presente expediente, también lo es que, este vehículo es objeto de un arrendamiento a largo plazo.

Que la existencia de ese contrato de arrendamiento a largo plazo, así como el arrendatario, ha sido comunicado al Registro de Vehículos de la Dirección General de Tráfico en los términos establecidos en el art. 11.3 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, por lo que la obligación de facilitar a la Administración la identificación del conductor del vehículo en el momento de ser cometida una infracción "corresponderán al arrendatario a largo plazo del vehículo, en el supuesto de que hubiese constancia de éste en el Registro de Vehículos".

Por lo anteriormente expuesto no me corresponde cumplir con el requerimiento de "facilitar a la Administración la identificación del conductor del vehículo en el momento de ser cometida una infracción".

SEGUNDA.- Que aunque, efectivamente, el destinatario del requerimiento efectuado es titular del vehículo objeto del presente expediente, también lo es que, este vehículo es objeto de un arrendamiento a largo plazo.

Que aunque la existencia de ese contrato de arrendamiento a largo plazo no ha sido comunicado al Registro de Vehículos de la Dirección General de Tráfico en los términos establecidos en el art. 11.4 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial se aprovecha este trámite para proceder a la comunicación del contrato de arrendamiento y del arrendatario.

Se adjunta al presente escrito el referido contrato de arrendamiento, con cuyo envío se cumple con el requerimiento efectuado

SEGUNDA.- El citado día y hora la persona a la que le había dejado utilizar el vehículo era [COMPLETAR] con permiso de conducción número [NÚMERO] y con la comunicación de estos datos se cumple con el requerimiento efectuado.

SEGUNDA.- El citado día y hora la persona a la que le había dejado utilizar el vehículo era [COMPLETAR] con permiso de conducción número [NÚMERO]

Tratándose de un permiso expedido fuera del territorio nacional, y tal y como establece el párrafo segundo del art. 11.1 a) Párrafo segundo del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, se adjunta al presente escrito "copia de la autorización administrativa", y con cuyo envío se cumple con el requerimiento efectuado.

SEGUNDA.- Que aunque, efectivamente, el destinatario del requerimiento efectuado es [COMPLETAR] del vehículo objeto del presente expediente, también lo es que, ese vehículo es utilizado indistintamente por una serie de personas vinculadas por razones familiares/profesionales.

Las personas que conforman este grupo y los datos del permiso de conducción son los siguientes:

 con permiso [COMPLETAR]

 con permiso [COMPLETAR]

 con permiso [COMPLETAR]

 con permiso [COMPLETAR]

Con la comunicación de estos datos a la Administración se cumple con el requerimiento efectuado.

SEGUNDA.- Que el destinatario del requerimiento efectuado es [COMPLETAR] del vehículo objeto del presente expediente y no le consta el uso del vehículo el día y hora indicado.

Que en esa fecha el titular ni hizo uso del vehículo ni autorizó a persona alguna el uso del mismo. Por ello, y caso de haberse utilizado el referido vehículo. Habría sido sin la autorización de su titular y, por lo tanto, en contra de mi voluntad, lo que pongo en su conocimiento a los efectos del requerimiento efectuado.

Además, y conforme a los establecido en el art. 111.1 a) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial el [COMPLETAR] no es responsable subsidiarios en caso de impago de la multa impuesta al conductor en el caso de "robo, hurto o cualquier otro uso en el que quede acreditado que el vehículo fue utilizado en contra de su voluntad".

SEGUNDA.- Que el destinatario del requerimiento efectuado es [COMPLETAR] del vehículo objeto del presente expediente.

Que en la fecha indicada el vehículo fue sustraído, hecho que fue puesto en conocimiento de la autoridad mediante la formulación de la correspondiente denuncia, documento que se adjunta al presente escrito.

Además, y conforme a los establecido en el art. 111.1 a) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial el [COMPLETAR] no es responsable subsidiarios en caso de impago de la multa impuesta al conductor en el caso de "robo, hurto o cualquier otro uso en el que quede acreditado que el vehículo fue utilizado en contra de su voluntad".

Por lo anteriormente expuesto, SOLICITO:

Que, habiendo por presentado este escrito, se sirva admitirlo, tenga por formulada la precedente alegación y, tras los trámites legales pertinentes, resuelva el archivo del expediente administrativo, ya que es de Justicia que pido en [LUGAR], a [FECHA].

Firma
