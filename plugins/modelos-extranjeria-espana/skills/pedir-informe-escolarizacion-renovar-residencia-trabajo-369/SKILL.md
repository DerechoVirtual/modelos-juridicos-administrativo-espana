---
name: pedir-informe-escolarizacion-renovar-residencia-trabajo-369
description: "Redacta el escrito «Pedir informe de escolarización para renovar residencia y trabajo» (formulario 369 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir informe de escolarización para renovar residencia y trabajo

> Formulario 0369 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Renovación por cuenta ajena: hoy art. 80 RD 1155/2024. Ojo: el art. 159.1 RD 1155/2024 está parcialmente anulado por la STS de 8-7-2026 (BOE 22-9-2026).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NACIONALIDAD
- [ ] DNI/NIE (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A la Consejería de Educación de»; «…ue el interesado es progenitor del menor»; «…, también nacional de»; «…luye copia de la matrícula en el Colegio»; «…4099); STS 8-7-2026 (BOE-A-2026-19632).]»; «…se acredite fehacientemente que el menor»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 1155/2024
- Ley Orgánica 4/2000
- Ley Orgánica 2/2009

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

### Formulario 0369 · Pedir informe de escolarización para renovar residencia y trabajo

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco
- Avisos de la revisión: Renovación por cuenta ajena: hoy art. 80 RD 1155/2024. Ojo: el art. 159.1 RD 1155/2024 está parcialmente anulado por la STS de 8-7-2026 (BOE 22-9-2026).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la Consejería de Educación de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], y titular de autorización de residencia y trabajo con NIE n.º [DNI/NIE], ante este Organismo:

EXPONE

Primero.- Que el interesado es progenitor del menor [COMPLETAR], también nacional de [COMPLETAR], y titular de autorización de residencia con NIE n.º [DNI/NIE]. Se adjunta copia traducida de la partida de nacimiento.

Segundo.- El menor se encuentra en la actualidad accediendo al Sistema de enseñanza pública obligatoria, tal y como impera la legislación vigente. Se incluye copia de la matrícula en el Colegio [COMPLETAR]; sito en la calle [CALLE] n.º [NÚMERO], provincia de [PROVINCIA].

Tercero.- El solicitante pretende renovar su autorización de residencia y trabajo en plazo y forma, de acuerdo con lo establecido en los arts. 64, 71, 80, 86 o 159 y ss del Real Decreto 1155/2024 [NOTA DE REVISIÓN: Numeración correcta: 64 (no lucrativa), 71 (reagrupación), 80 (cuenta ajena), 86 (cuenta propia), 159 y ss. (menores). La STS de 8-7-2026 anuló incisos de los arts. 159.1 («solteras» y la exigencia de no haberse ausentado desde el nacimiento, que se interpreta como residencia efectiva habitual) y 160.1-2. Fuente: RD 1155/2024, arts. 64, 71, 80, 86 y 159 (BOE-A-2024-24099); STS 8-7-2026 (BOE-A-2026-19632).] [COMPLETAR], por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social. Se adjunta copia de la referida autorización.

Cuarto.- Que de acuerdo con la Ley Orgánica 2/2009 de reforma de la Ley Orgánica 4/2000, sobre derechos y libertades de los extranjeros en España y su integracion social, en su artículo 9.4, el extranjero que tenga a su cargo un menor en edad de escolarización obligatoria, deberá acreditarlo mediante informe de las autoridades autonómicas competentes, su solicitud de renovación.

Quinto.- Es por ello, que D./Dña. [NOMBRE Y APELLIDOS], se dirige a este Organismo para que emita informe competente donde se acredite fehacientemente que el menor [COMPLETAR] se encuentra en la actualidad debidamente escolarizado, en aras de solicitar la renovación de su utorización de residencia y trabajo.

En [LUGAR], a [FECHA].

Fdo.:
