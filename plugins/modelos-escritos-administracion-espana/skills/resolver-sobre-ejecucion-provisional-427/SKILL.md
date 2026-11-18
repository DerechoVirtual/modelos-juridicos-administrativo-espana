---
name: resolver-sobre-ejecucion-provisional-427
description: "Redacta el escrito «Resolver sobre la ejecución provisional» (formulario 427 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolver sobre la ejecución provisional

> Formulario 0427 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a que, estimando el recurso, se anuló el»; «…de la»; «…ogarse a la Administración demandada con»; «…ipada de la sentencia podrían devenir en»; «…, así lo acuerdo, ordenando a»; «…mente, se acuerda que el recurrente, don»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0427 · Resolver sobre la ejecución provisional

- Año del modelo: 2012
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AUTO

Iltmo. Sr. [NOMBRE Y APELLIDOS]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Dada cuenta;

ANTECEDENTES DE HECHO

PRIMERO.- En fecha [FECHA] se dictó sentencia por la que, estimando el recurso, se anuló el [COMPLETAR] de la [COMPLETAR], según reza el tenor literal del fallo de dicha sentencia.

SEGUNDO.- En fecha [FECHA] el recurrente solicitó la ejecución provisional de la sentencia, por considerar que se le estaba privando indebidamente desde el momento de la misma de los derechos que en ella se reconocían.

TERCERO.- Habiéndose dado traslado a las partes personadas, se oponen a la ejecución provisional, por las razones que constan en sus respectivos escritos, solicitando de forma subsidiaria que el recurrente preste caución suficiente para garantizar los daños y perjuicios que pudieran irrogarse por la ejecución anticipada de la sentencia.

FUNDAMENTOS JURÍDICOS

PRIMERO.- Dispone el artículo 84.1 de la Ley Reguladora de esta Jurisdicción que las partes favorecidas por la sentencia podrán instar su ejecución provisional, ejecución ésta que sólo es posible evitar si, una vez solicitada, se aprecie que con la misma se pudieran producir situaciones irreversibles o perjuicios de imposible reparación. Siendo así que en el presente supuesto, y conforme ya se advertía en la sentencia recaída en estos Autos, ni constan los graves perjuicios que pudieran irrogarse a la Administración demandada con [COMPLETAR] y por tanto disponer la ejecución provisional de la sentencia, que habrá de llevarse a efecto en el plazo máximo de diez días desde la notificación de esta resolución a la Administración recurrida.

SEGUNDO.- Como quiera que los únicos perjuicios que pudieran derivarse de la ejecución anticipada de la sentencia podrían devenir en [COMPLETAR], se fija la caución, que habrá de prestarse en forma de aval a favor de la Administración o un depósito en metálico de 3.005,06 euros para responder frente a los perjuicios ocasionados al codemandado, en el supuesto de una eventual anulación de esta sentencia por el Tribunal Superior.

Por lo expuesto,

FALLO: Que debiendo estimar la petición de ejecución provisional de la sentencia de fecha [FECHA], así lo acuerdo, ordenando a [COMPLETAR], que reponga al recurrente D./Dña. [NOMBRE Y APELLIDOS], ejecución que habrá de verificarse en el plazo de diez días a contar desde la notificación de esta resolución. Igualmente, se acuerda que el recurrente, don [COMPLETAR], deberá prestar caución en forma de aval bancario o de depósito en metálico en la cuenta de depósitos de este órgano judicial de la cantidad de 3.005,06 euros, ajustándose a lo establecido en el artículo 133 de la Ley Reguladora de esta Jurisdicción.

Contra este Auto cabrá recurso de apelación en un solo efecto ante el Tribunal Superior de Justicia de [LOCALIDAD] y se interpondrá ante este Juzgado dentro de los quince días siguientes al de su notificación, mediante escrito razonado que deberá contener las alegaciones en que se fundamente el recurso.

Así lo mando y firmo, certifico.
