---
name: sobreseimiento-denuncia-anonima-trafico-1813
description: "Redacta el escrito «Sobreseimiento de una denuncia anónima de tráfico» (formulario 1813 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Sobreseimiento de una denuncia anónima de tráfico

> Formulario 1813 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…se ha presentado en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 9.2 del Real Decreto 320/1994
- art. 9.2 RD 320/1994

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

### Formulario 1813 · Sobreseimiento de una denuncia anónima de tráfico

- Año del modelo: 2004
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 3 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito por el que se acuerda el sobreseimiento de una denuncia en materia de tráfico y seguridad vial, al no poder ser identificado el denunciante, tal y como viene previsto en el artículo 9.2 del Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, aprobado por Real Decreto 320/1994, de 25 de febrero.

Con fecha [FECHA] se ha presentado en [COMPLETAR] una denuncia sin firma en la que se pone en conocimiento de este órgano administrativo la realización de los siguientes hechos (1):

Realizadas las diligencias oportunas encaminadas a ofrecer al denunciante la oportunidad de subsanar esta deficiencia en los plazos señalados por las normas de procedimiento administrativo común, no ha sido posible su identificación.

Vistos los antecedentes mencionados, de conformidad con el artículo 9.2 del Real Decreto 320/1994 [NOTA DE REVISIÓN (comprobar): Ídem: art. 9.2 RD 320/1994 formalmente vigente, sin equivalente legal. Fuente: RD 320/1994, BOE-A-1994-8985 art. 9.2.], de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, procede dictar el siguiente

ACUERDO:

Se decreta el sobreseimiento de la denuncia anónima referenciada, sin perjuicio de las comprobaciones que sobre los hechos objeto de la misma puedan realizarse por este órgano administrativo y la ulterior tramitación del expediente que en base a los mismos sea procedente.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) Sin perjuicio de que los órganos competentes puedan comprobar los hechos a que se refieran, en los casos en que puedan suponer un riesgo para la seguridad vial, las denuncias de carácter anónimo serán archivadas sin que deban efectuarse ulteriores trámites al respecto (art. 9.2 RD 320/1994). La denuncia anónima no es sólo la que carece de firma, sino la que no se puede identificar al denunciante por faltar su nombre y apellidos, aunque conste una firma o rúbrica ilegibles. Los agentes de la autoridad se pueden identificar con un número, pero los particulares deben dejar constancia de su identidad de forma completa y correcta, de lo contrario la denuncia (anónima a estos efectos) se tendrá por no puesta. En materia de tráfico no son frecuentes las denuncias de particulares, nominativas ni anónimas, por hechos de circulación, lo que entendemos que es debido al carácter fugaz y momentáneo de las infracciones y no por falta de voluntad de denunciar a las personas que conducen de forma agresiva y cometen infracciones que ponen en peligro la seguridad de todos los usuarios de las vías públicas.
