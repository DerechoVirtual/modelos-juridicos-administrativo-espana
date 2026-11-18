---
name: apelacion-contra-sentencia-confirma-expulsion-714
description: "Redacta el escrito «Apelación contra sentencia que confirma una expulsión (extranjería)» (formulario 714 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra sentencia que confirma una expulsión (extranjería)

> Formulario 0714 del plugin **Extranjería** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA (7 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…dablemente su arraigo, habiendo aportado»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoq…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 81 de la LJCA
- art. 85.1 de la LJCA
- arts. 53.1.a), 55, 57 y 58 de la LO 4/2000

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

### Formulario 0714 · Apelación contra sentencia que confirma una expulsión (extranjería)

- Año del modelo: 2009
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 párrafos opcionales señalados; 14 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 5 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], cuya representación tengo acreditada en el Recurso contencioso administrativo nº [Nº DE PROCEDIMIENTO]/[AÑO], interpuesto contra la resolución de fecha [FECHA] de la Subdelegación del Gobierno de [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que habiendo sido notificado del auto de fecha [FECHA], dictada en la presente pieza de medidas cautelares, interpongo contra el citado auto RECURSO DE APELACIÓN en base a los siguientes

HECHOS

PRIMERO.- Esta parte interpuso recurso contencioso-administrativo contra la resolución de fecha [FECHA]. de la Subdelegación del Gobierno de [LOCALIDAD]. en la que se acordaba imponer a mi representado, como autor de una infracción del art. de la Ley de Extranjería, la sanción de expulsión de territorio nacional con prohibición de entrada por [Nº] años.

SEGUNDO.- Seguidos los trámites legales, el proceso fue resuelto en la instancia por sentencia de fecha [FECHA], notificada a esta parte, en fecha [FECHA], la cual se recurre por medio de este escrito.

ADMISIBILIDAD DEL RECURSO

PRIMERO.- El auto que se recurre es apelable al haberse dictado en un proceso de que el Tribunal conoce en primera instancia, y tratarse de un proceso de cuantía indeterminada, según dispone el art. 81 de la LJCA.

SEGUNDO.- El recurso cumple los requisitos de tiempo y forma establecidos en el art. 85.1 de la LJCA.

MOTIVOS DE IMPUGNACIÓN

PRIMERO.- Infracción de los arts. 53.1.a), 55, 57 y 58 de la LO 4/2000, de 11 de enero, del principio de proporcionalidad y de la doctrina jurisprudencial que los interpreta.

La sentencia de instancia infringe dichos preceptos por cuanto no tiene en cuenta que la sanción prevista para la infracción de estancia irregular cometida por mi representado es la multa y, si bien el artículo 57 de la citada Ley permite expulsar al extranjero con la consiguiente prohibición de entrada, la jurisprudencia ha reiterado que la Administración debe justificar tal elección de la sanción más grave en virtud de las circunstancias concurrentes, pero, en este caso, al tratarse meramente de una estancia ilegal por carecer de autorización, el principio de proporcionalidad impide que se le imponga la sanción más grave.

En este caso, además, mi representado ha justificado indudablemente su arraigo, habiendo aportado [COMPLETAR], lo cual se ajusta al concepto de arraigo manejado por el Tribunal Supremo como aquellos intereses familiares, económicos y sociales que pueden justificar la permanencia en España. Por tanto, mi representado ha acreditado su arraigo, tal y como la Jurisprudencia del TS lo entiende, aportando pruebas de poseer intereses familiares, económicos y sociales, lo que hace que la sanción de expulsión impuesta sea totalmente desproporcionada.

Por estos motivos, solicito de la Sala la revocación de la sentencia, y la estimación de la demanda interpuesta por esta parte.

En virtud de todo lo expuesto,

SUPLICO AL TRIBUNAL PARA LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE, que se tenga por presentado este escrito, admitiendo el recurso de apelación contra la sentencia de fecha [FECHA], y previos los trámites legales preceptivos, elevando las actuaciones a la citada Sala, se dicte sentencia por la que, dando lugar a la apelación, se revoque la sentencia de instancia y se estime las pretensiones deducidas en nuestro escrito de demanda con los pronunciamientos inherentes.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO AL TRIBUNAL que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

Es Justicia que se pide en [LUGAR], a [FECHA].

Firma Abogado.	Firma Procurador.
