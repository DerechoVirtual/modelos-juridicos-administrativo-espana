---
name: acta-manifestaciones-reagrupacion-familiar-comunitaria-376
description: "Redacta el escrito «Acta de manifestaciones para reagrupación familiar comunitaria» (formulario 376 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de manifestaciones para reagrupación familiar comunitaria

> Formulario 0376 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Si el ciudadano de la Unión es español sin libre circulación previa, rige el régimen de los arts. 93-99 RD 1155/2024 (DT 3.ª y 4.ª).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NACIONALIDAD (3 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] DNI/NIE (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A DE MANIFESTACIONES COMPARECIENTES Doña»; «…yor de edad, casada, empleada, vecina de»; «…y NIE X-....; su esposo don»; «…u esposo, que el hijo menor de la esposa»; «…r ante el Consulado General de España en»; «…os citados familiares en la localidad de»; «…a Representación Diplomática Española en»; «…efectos ante las autoridades españolas y»; «…a Representación Diplomática Española en»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 240/2007

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

### Formulario 0376 · Acta de manifestaciones para reagrupación familiar comunitaria

- Año del modelo: 2013
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco
- Avisos de la revisión: Si el ciudadano de la Unión es español sin libre circulación previa, rige el régimen de los arts. 93-99 RD 1155/2024 (DT 3.ª y 4.ª).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

MINUTA DE ACTA DE MANIFESTACIONES

COMPARECIENTES

Doña [COMPLETAR], de nacionalidad [NACIONALIDAD], mayor de edad, casada, empleada, vecina de [COMPLETAR] calle [CALLE], con Pasaporte en vigor n.º [NÚMERO] y NIE X-....; su esposo don [COMPLETAR], de nacionalidad española, comercial, con DNI n.º [DNI/NIE], e idéntico domicilio.

ACTA DE MANIFESTACIONES PARA REAGRUPACIÓN FAMILIAR RÉGIMEN COMUNITARIO

I

Que es intención de la compareciente, de nacionalidad [NACIONALIDAD] y de su esposo, que el hijo menor de la esposa [COMPLETAR], soltero, de nacionalidad [NACIONALIDAD], con pasaporte n.º [DNI/NIE], nacido en [LOCALIDAD], el día [FECHA], actualmente residente en [LOCALIDAD], calle [CALLE], se reagrupe familiarmente con los comparecientes en España.

II

Que a los efectos de la reagrupación familiar manifiestan que el hijo de la compareciente depende económicamente y vive a las exclusivas expensas de los comparecientes, siendo inicial y actualmente objeto de la reagrupación que el hijo de la compareciente pueda desarrollar sus estudios y formación en España.

III

Que, con la finalidad de que el hijo de la compareciente pueda solicitar ante el Consulado General de España en [COMPLETAR] el correspondiente visado consular por reagrupación familiar en régimen comunitario de conformidad con lo prevenido en los artículos 2 y siguientes del Real Decreto 240/2007, de 16 de febrero, sobre entrada y permanencia en España de nacionales de Estados miembros de las Comunidades Europeas, hacen constar expresamente: Que siendo intención de los comparecientes reagrupar a los citados familiares en la localidad de [COMPLETAR], y para que surta efectos ante las Autoridades Gubernativas españolas y, en su caso, ante la Representación Diplomática Española en [COMPLETAR], en cuantos trámites de documentación de su residencia fueren precisos, solicitud de visado consular de residencia régimen comunitario, en su caso, su exención, se comprometen y obligan:

a) A sufragar de su peculio particular todos cuantos gastos originen tanto su traslado a España como su retorno a su país de origen, en su momento pertinente o antes si así lo exigieren por cualquier circunstancia las Autoridades españolas.

b) A mantenerle y cuidarle durante su permanencia en España como lo hiciera un buen padre de familia, haciéndose cargo de todos los gastos que pudiera ocasionar por razón de sus estudios, manutención, vestido, asistencia médica, farmacéutica, hospitalaria, viajes y cualquier otro concepto que pudiera surgir como consecuencia de su residencia en España por reagrupación familiar.

c) A reparar cuantos daños y perjuicios cause durante su permanencia en España.

d) Hacen constar los requerientes que tienen ingresos suficientes para garantizar los compromisos contraídos por las presentes manifestaciones y declaran que las responsabilidades antes mencionadas cesarán solamente en el caso de que dicha persona ya no estuviera bajo su tutela y cuidado y se encontrara fuera de territorio español.

IV

Las anteriores manifestaciones las efectúan bajo su personal responsabilidad con la finalidad de que surtan efectos ante las autoridades españolas y [COMPLETAR] encargadas del control de fronteras y la Representación Diplomática Española en [COMPLETAR], en la tramitación de los preceptivos visados de reagrupación familiar en régimen comunitario; y cualquier otro trámite que se derive de la legislación española e internacional sobre extranjeros.
