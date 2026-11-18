---
name: apelacion-contra-auto-deniega-suspender-expulsion-712
description: "Redacta el escrito «Apelación contra auto que deniega suspender la expulsión (extranjería)» (formulario 712 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra auto que deniega suspender la expulsión (extranjería)

> Formulario 0712 del plugin **Extranjería** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (8 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…iariamente su arraigo, habiendo aportado»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoq…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 80.1.a) de la LJCA
- art. 85.1 de la LJCA
- art. 130 de la LJCA

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

### Formulario 0712 · Apelación contra auto que deniega suspender la expulsión (extranjería)

- Año del modelo: 2009
- Revisión 17-11-2026: 1 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 5 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en el Recurso contencioso administrativo nº [Nº DE PROCEDIMIENTO], interpuesto contra la resolución de fecha [FECHA] de la Subdelegación del Gobierno de [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en derecho, DIGO:

Que habiendo sido notificado del auto de fecha [FECHA], dictada en la presente pieza de medidas cautelares, interpongo contra el citado auto RECURSO DE APELACIÓN en base a los siguientes

HECHOS

PRIMERO.- Por la citada resolución de fecha [FECHA] de la Subdelegación del Gobierno de [LOCALIDAD] se acordó imponer a mi representado, como autor de una infracción del art. de la Ley de Extranjería, la sanción de expulsión de territorio nacional con prohibición de entrada por [Nº] años.

SEGUNDO.- Frente a la citada resolución se interpuso este recurso contencioso-administrativo, habiendo solicitado esta parte en su demanda la suspensión de la ejecución de la orden de expulsión, la cual fue denegada en el auto de fecha [FECHA], notificado a esta parte, en fecha [FECHA], el cual se recurre por medio de este escrito.

ADMISIBILIDAD DEL RECURSO

PRIMERO.- El auto que se recurre es apelable al haberse dictado en un proceso de que el Tribunal conoce en primera instancia, y ser un auto que pone fin a la pieza separada de medidas cautelares, según dispone el art. 80.1.a) de la LJCA.

SEGUNDO.- El recurso cumple los requisitos de tiempo y forma establecidos en el art. 85.1 de la LJCA.

MOTIVOS DE IMPUGNACIÓN

PRIMERO.- Infracción de los artículos 129, 130, siguientes y concordantes de la Ley de Jurisdicción Contencioso-Administrativa.

El presente recurso se articula frente al auto denegando la suspensión de la resolución administrativa impugnada, entendiendo que infringe los preceptos expresados por cuanto que la ejecución de la sanción hace perder la finalidad legítima de este recurso, produciendo perjuicios irreparables a mi representado.

En efecto, en el caso concurren los requisitos del art. 130 de la LJCA, para acordar la suspensión, pues de no adoptarse la medida cautelar, el recurso perdería su finalidad legítima, por cuanto la ejecución de la medida ocasiona perjuicios irreparables a mi representado y al ejecutarse una sanción que no se puede imponer a mi representado, pues la sanción procedente en su caso sería la de multa, sin que resulte perjudicado el interés general.

La jurisprudencia viene aplicando pacíficamente esta doctrina, proclamando reiteradamente que la suspensión de la ejecución de determinaciones administrativas de expulsión de extranjeros del territorio nacional resulta procedente cuando la persona afectada tiene arraigo en España por razón de sus intereses familiares, sociales o económicos, por lo que la ejecución de la orden de expulsión habría de producirle unos perjuicios de difícil reparación, que en parte afectarían a su esfera personal de sus derechos, por lo que en tales casos el perjuicio grave al interés general, que se aprecia cuando no concurren las circunstancias especiales de arraigo, debe ceder ante los perjuicios concretos que la inmediata expulsión producirían al extranjero. Así se recoge en las SSTS de 20 de enero y 20 de marzo de 2001, que indican que cuando una persona afectada por una orden de expulsión tiene arraigo en España, por razón de sus intereses familiares, sociales o económicos, la efectividad de la resolución le ocasiona unos perjuicios de difícil reparación que determinan la procedencia de la suspensión de la expulsión.

Del mismo modo, la patente falta de proporcionalidad de la sanción, que determinaría la procedencia de sustituir al expulsión por multa, con arreglo a la doctrina del Tribunal Supremo recogida, entre otras, en SSTS 19 de abril y 5 de julio de 2007, también determinaría otro motivo de suspensión, en este caso por el hecho de ejecutarse una sanción cuya imposición no sería procedente.

En el presente caso, mi mandante ha justificado indiciariamente su arraigo, habiendo aportado [COMPLETAR], lo cual se ajusta al concepto de arraigo manejado por el Tribunal Supremo como aquellos intereses familiares, económicos y sociales que pueden justificar la permanencia en España. (STS Sala 3ª, sec. 5ª de 17-2-2006). Por tanto, mi representado ha acreditado indiciariamente, en el estrecho margen que permite el incidente cautelar, el arraigo, tal y como la Jurisprudencia del TS lo entiende, aportando pruebas de poseer intereses familiares, económicos y sociales que hacen que la ejecución de la orden de expulsión le ocasione un perjuicio irreparable, perdiendo la finalidad legítima este recurso.

Por estos motivos, solicito de la Sala la revocación del auto, dictando en su lugar resolución donde se adopte la medida cautelar de suspensión interesada por esta parte en su escrito de demanda.

En virtud de todo lo expuesto,

SUPLICO AL TRIBUNAL PARA LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE, que se tenga por presentado este escrito, admitiendo el recurso de apelación contra el auto de fecha [FECHA], y previos los trámites legales preceptivos, elevando las actuaciones a la citada Sala, se dicte resolución revocatoria del citado auto de fecha [FECHA], decretándose en su lugar la medida cautelar de suspensión de la resolución administrativa impugnada.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO AL TRIBUNAL que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

Es Justicia que se pide en [LUGAR], a [FECHA].

Firma Abogado.	Firma Procurador.
