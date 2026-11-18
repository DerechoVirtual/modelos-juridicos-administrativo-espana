---
name: pedir-revocar-devolucion-arraigo-390
description: "Redacta el escrito «Pedir revocar la devolución por arraigo» (formulario 390 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir revocar la devolución por arraigo

> Formulario 0390 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DEL GOBIERNO EN»; «…cia por circunstancias excepcionales por»

## Elecciones que hay que hacer

- DELEGACIÓN / SUBDELEGACION
- sin que hasta la fecha se haya dictado sentencia / habiéndose dictado sentencia desestimatoria de la demanda interpuesta

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 23.8 Real Decreto 1155/2024

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

### Formulario 0390 · Pedir revocar la devolución por arraigo

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 2 desplegables convertidos en elección en blanco; 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: DELEGACIÓN / SUBDELEGACION] DEL GOBIERNO EN [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD] con NIE/Pasaporte n.º [DNI/NIE] y domicilio en [LOCALIDAD] en la calle [CALLE], ante esta Delegación comparece y

EXPONE

Primero.- Que con fecha [FECHA] le fue notificada la resolución por la que se decretaba su devolución del territorio español con prohibición de entrada en el mismo por [Nº] años.

Segundo.- Que dicha sanción se impuso por la entrada ilegal en territorio español.

Tercero.- Que la resolución mencionada no fue ejecutada hasta la fecha.

Cuarto.- Que ha presentado solicitud de residencia por circunstancias excepcionales por [COMPLETAR] con fecha [FECHA].

Quinto.- El artículo 23.8 Real Decreto 1155/2024 [NOTA DE REVISIÓN (comprobar): Correcto si se trata de una resolución de devolución no ejecutada: el 23.8 prevé su revocación cuando procede conceder la residencia por circunstancias excepcionales. Si fuera una orden de expulsión, el 23.8 no es aplicable; no he verificado el precepto equivalente para la expulsión. Fuente: RD 1155/2024, art. 23.8 (BOE-A-2024-24099).], de 19 de noviembre establece que:

«Cuando en el marco de un procedimiento relativo a autorizaciones de residencia por circunstancias excepcionales, se comprobase que consta contra el solicitante una resolución de devolución no ejecutada, ésta será revocada, siempre que del análisis de la solicitud derive la procedencia de la concesión de la autorización de residencia por circunstancias excepcionales.

En caso de que el órgano competente para resolver sobre la solicitud de autorización no fuera el mismo que dictó la resolución de devolución a revocar, instará de oficio su revocación al órgano competente para ello. En el escrito por el que se inste la revocación se hará constar el tipo de autorización solicitada y expresa mención a la procedencia de la concesión de la misma, por cumplimiento de los requisitos exigibles para ello, salvo el relativo a la existencia de la resolución de devolución no ejecutada.»

Sexto.- Que presentó recurso contencioso-administrativo contra la resolución que decretó su devolución, [ELEGIR: sin que hasta la fecha se haya dictado sentencia / habiéndose dictado sentencia desestimatoria de la demanda interpuesta], lo que, según ha establecido la DGI en varias comunicaciones, no es obstáculo para proceder a la revocación de la resolución recurrida.

Por lo expuesto,

SOLICITA

Que en la tramitación de su autorización de residencia por circunstancias excepcionales sea aplicado el procedimiento previsto en el citado artículo y se proceda a revocar la orden de devolución decretada, o que se solicite dicha revocación del órgano competente para ello.

En [LUGAR], a [FECHA].

Fdo.:
