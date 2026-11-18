---
name: alegaciones-conducir-sin-autorizacion-administrativa-598
description: "Redacta el escrito «Alegaciones por conducir sin la autorización administrativa» (formulario 598 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones por conducir sin la autorización administrativa

> Formulario 0598 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] NÚMERO (5 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA JEFATURA PROVINCIAL DE TRÁFICO DON»; «…y domicilio»; «…cho, DIGO: Que en relación al expediente»; «…l indicado vehículo, puesto que la clase»

## Elecciones que hay que hacer

- Inexistencia de infracción o comisión de otra infracción diferente

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 77 k) del Real Decreto Legislativo 6/2015
- arts. 59 y 61 del Real Decreto Legislativo 6/2015
- art. 75 c) del Real Decreto Legislativo 6/2015

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

### Formulario 0598 · Alegaciones por conducir sin la autorización administrativa

- Año del modelo: 2011
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA PROVINCIAL DE TRÁFICO

DON [COMPLETAR], mayor de edad, con DNI [DNI/NIE] y domicilio [COMPLETAR] en [LOCALIDAD], ante el órgano mencionado comparezco y, como mejor proceda en Derecho, DIGO:

Que en relación al expediente [COMPLETAR] formulo, en tiempo y forma oportuno, las siguientes ALEGACIONES

PRIMERA.- Los hechos objeto del expediente al que me refiero han sido calificados como "conducir un vehículo careciendo de la autorización administrativa correspondiente", infracción que el art. 77 k) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, califica como infracción muy grave.

[ELEGIR: Inexistencia de infracción o comisión de otra infracción diferente]

SEGUNDA.- Los hechos objeto del presente procedimiento consisten en que, en el día y hora señalados, conducía el vehículo indicado en la denuncia.

Como titular de la autorización administrativa para conducir con número [NÚMERO] estoy habilitado, conforme a lo establecido en los arts. 59 y 61 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, para conducir.

Cuestión distinta es que en ese momento no pudiera mostrar al Agente de la autoridad el permiso, cuestión que, en la práctica, es irrelevante dado que los medios técnicos de los que se dispone permiten la comprobación (incluso instantánea) de la existencia de una determinada autorización y vigencia de la misma, lo que supone que, en el presente caso, no se ha cometido infracción alguna.

SEGUNDA.- Los hechos objeto del presente procedimiento consisten en que, en el día y hora señalados, conducía el vehículo indicado en la denuncia.

Como titular de la autorización administrativa para conducir con número [NÚMERO] estoy habilitado, conforme a lo establecido en los arts. 59 y 61 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, para conducir el vehículo que conducía.

Cuestión distinta es que en ese momento no pudiera mostrar al Agente de la autoridad el permiso, cuestión que, en la práctica, es irrelevante dado que los medios técnicos de los que se dispone permiten la comprobación (incluso instantánea) de la existencia de un determinado permiso o licencia, así como sus clases y vigencia. Ello supone que, en el presente caso, no se ha cometido infracción alguna.

SEGUNDA.- Los hechos objeto del presente procedimiento consisten en que, en el día y hora señalados, conducía el vehículo indicado en la denuncia.

Como titular de la autorización administrativa para conducir con número [NÚMERO] estoy habilitado, conforme a lo establecido en los arts. 59 y 61 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, para conducir el vehículo que conducía.

Cuestión distinta es que en esa fecha la referida autorización administrativa estuviera caducada, pero puesto que, tal y como se puede comprobar, soy titular de autorización administrativa que habilita para la conducción de ese tipo de vehículo, no es posible la comisión de la infracción que se me imputa.

Teniendo en cuenta que, tal y como establece el art. 13.3 del Reglamento General de Conductores, "el titular de un permiso o licencia de conducción caducados podrá solicitar su prórroga acompañando los documentos a que se refiere el apartado anterior" y que de esos documentos únicamente la no aportación del "informe de aptitud psicofísica emitido por un centro de reconocimiento de conductores autorizado" sería causa suficiente para denegar la prórroga de la autorización, la obtención del referido informe de aptitud psicofísica en este momento (copia del cual se acompaña al presente escrito) demuestra que, materialmente, no se ha trasgredido norma alguna, puesto que se cumple con todos los requisitos que nuestro ordenamiento exige para conducir vehículos

SEGUNDA.- Los hechos objeto del presente procedimiento consisten en que, en el día y hora señalados, conducía el vehículo indicado en la denuncia.

Como titular de la autorización administrativa para conducir con número [NÚMERO] estoy habilitado, conforme a lo establecido en los arts. 59 y 61 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, para conducir el vehículo que conducía.

Cuestión distinta es que en esa fecha la referida autorización administrativa estuviera caducada, pero puesto que, tal y como se puede comprobar, soy titular de autorización administrativa que habilita para la conducción de ese tipo de vehículo, no es posible la comisión de la infracción que se me imputa.

Teniendo en cuenta que, tal y como establece el art. 13.3 del Reglamento General de Conductores, "el titular de un permiso o licencia de conducción caducados podrá solicitar su prórroga acompañando los documentos a que se refiere el apartado anterior" y que, a la fecha de presentación de este escrito, ya se ha solicitado y obtenido la prórroga de vigencia de la autorización que habilita la conducción de vehículos, ello es la prueba más palpable de que no se ha trasgredido norma alguna, puesto que al momento de la denuncia se cumplía, materialmente, con todos los requisitos que nuestro ordenamiento exige para conducir vehículos

SEGUNDA.- Los hechos objeto del presente procedimiento consisten en que, en el día y hora señalados, conducía el vehículo indicado en la denuncia.

Como titular de la autorización administrativa para conducir con número [NÚMERO] estoy habilitado para conducir el indicado vehículo, puesto que la clase [COMPLETAR], de la que soy titular, me autoriza a conducir vehículos de esas características.

Cuestión distinta es que en ese momento no pudiera mostrar al Agente de la autoridad el permiso pero, dado que tal y como se puede comprobar soy titular de autorización administrativa que habilita para la conducción de ese tipo de vehículo, no es posible la comisión de la infracción que se me imputa.

En todo caso los hechos objeto del presente expediente serían susceptibles de ser calificados como incumplimiento, por parte del conductor de un vehículo, de la obligación de "llevar consigo su permiso o licencia válidos para conducir", conducta que, en todo caso, merecerá la calificación de infracción leve ya que, conforme a lo establecido en el art. 75 c) del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial son infracciones leves “incumplir las normas contenidas en esta ley que no se califiquen expresamente como infracciones graves o muy graves en los artículos siguientes”.

Por lo anteriormente expuesto, SOLICITO:

Que, habiendo por presentado este escrito, se sirva admitirlo, tenga por formulada la precedente alegación y, tras los trámites legales pertinentes, resuelva el archivo del expediente administrativo, ya que es de Justicia que pido en [LUGAR], a [FECHA].

Firma
