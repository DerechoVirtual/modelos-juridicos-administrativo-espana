---
name: pedir-administracion-ejecutar-acto-firme-903
description: "Redacta el escrito «Pedir a la Administración ejecutar un acto firme» (formulario 903 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir a la Administración ejecutar un acto firme

> Formulario 0903 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.
- **Criterio de Hacienda y del TEAC** → `buscar_consultas_hacienda` → `leer_consulta_hacienda`; `buscar_doctrina_teac` → `leer_resolucion_teac`.

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
- [ ] CALLE
- [ ] DNI/NIE
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de la ciudad de»; «…) según poder,»; «…tificó acto administrativo en materia de»; «…e dio lugar al expediente administrativo»; «…98, de 13 de julio. Lugar, fecha y firma»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 38 y 39 de la Ley 39/2015
- artículo 29.2 LJCA
- artículo 29.2 de la Ley 29/1998

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

### Formulario 0903 · Pedir a la Administración ejecutar un acto firme

- Año del modelo: 2009
- Revisión 17-11-2026: 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS] con domicilio en la calle [CALLE] de la ciudad de [COMPLETAR] (además, en su caso, teléfono y/o correo electrónico) con DNI [DNI/NIE] comparece en su propio nombre (o en representación de [NOMBRE DEL REPRESENTADO/A]) según poder, [COMPLETAR]) y como mejor proceda en Derecho, DIGO:

PRIMERO.- El día [FECHA] se me notificó acto administrativo en materia de [COMPLETAR], en el que se estimaba plenamente la reclamación presentada en su día y que dio lugar al expediente administrativo [COMPLETAR]. Contra dicho acto administrativo no se interpuso recurso alguno y por lo tanto devino firme.

SEGUNDO.- Como consecuencia de la firmeza del acto, a tenor de lo que se dispone en los artículos 38 y 39 de la Ley 39/2015, de 1 de octubre, dicho acto produce plenos efectos jurídicos, pues al ser firme vincula a la Administración Pública que debe proceder a su ejecución, pues en caso contrario, se producen al interesado perjuicios considerables.

TERCERO.- El acto administrativo, una vez alcanzada su firmeza legalmente, debe cumplirse por parte de la Administración Pública autora de la misma, pues en caso contrario se produce una quiebra del principio de seguridad jurídica y de legalidad, así como del principio de que nadie puede ir en contra de sus propios actos.

En este sentido, el artículo 29.2 LJCA señala que cuando la Administración no ejecute sus actos firmes podrán los afectados solicitar su ejecución, y si ésta no se produce en el plazo de un mes desde tal petición, podrán los solicitantes formular recurso contencioso-administrativo, que se tramitará por el procedimiento abreviado.

Por todo lo cual,

SOLICITO

que se tenga por presentado este escrito, junto con los documentos que se acompañan, y que se proceda a la ejecución inmediata del acto administrativo firme, que se ha citado con anterioridad, teniendo en cuenta que esta solicitud es a los efectos prevenidos en el artículo 29.2 de la Ley 29/1998, de 13 de julio.

Lugar, fecha y firma [COMPLETAR]

ÓRGANO, UNIDAD O CARGO ADMINISTRATIVO AL QUE SE DIRIGE EL ESCRITO
