---
name: personacion-diputacion-provincial-1036
description: "Redacta el escrito «Personación de la Diputación Provincial» (formulario 1036 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Personación de la Diputación Provincial

> Formulario 1036 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD (4 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE DEL SOLICITANTE
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…posición, vía de hecho, mera inactividad»; «…, de»; «…, de [COMPLETAR], por la que»; «…s Corporaciones Locales, en razón de que»; «…urisdiccional contencioso administrativo»

## Elecciones que hay que hacer

- ese Tribunal / esa Sala

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 63.2 de la Ley 7/1985
- art. 219.1 del Real Decreto 2568/1986
- art. 2 de la Ley 7/1985

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

### Formulario 1036 · Personación de la Diputación Provincial

- Año del modelo: 2008
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 15 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]
A LA SALA
 :

AUTOS DE RECURSO CONTENCIOSO ADMINISTRATIVO NUMERO [NÚMERO]

D./Dña. [NOMBRE Y APELLIDOS],

Procurador/a de los Tribunales

Letrado de los Servicios Jurídicos de la Diputación Provincial de [LOCALIDAD], actuando en nombre y representación de la misma según copia de poder que acompaño al presente escrito y que, siendo general para pleitos, solicito su devolución previo testimoniado, ante ese órgano jurisdiccional comparezco y, como mejor proceda en derecho, DIGO

PRIMERO.- Que ante [ELEGIR: ese Tribunal / esa Sala] se siguen los autos de recurso contencioso administrativo nº [Nº DE PROCEDIMIENTO], iniciados a instancia de [NOMBRE DEL SOLICITANTE] contra [ACTO O RESOLUCIÓN], por medio de los cuales se impugna una resolución, disposición, vía de hecho, mera inactividad [COMPLETAR], de [COMPLETAR], por la que [COMPLETAR].

SEGUNDO.- Que mi principal, Diputación Provincial de [LOCALIDAD], posee un evidente interés legítimo en este recurso jurisdiccional, como así cabe obtener del juego de los arts. 19.1 e) y 21.1 b) de la LLCA/98, art. 63.2 de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, y art. 219.1 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Corporaciones Locales, en razón de que [COMPLETAR], ya que el referido interés legítimo aludido en los preceptos citados bien puede ser directo como indirecto, como así lo ha declarado el Tribunal Constitucional, entre otras muchas, en su Sentencia 195/1992, de 16 de noviembre; o incluso cabría que tal interés fuera meramente reflejo, pese a lo cual, incluso en este último caso, habría que garantizar a los potenciales afectados por la resolución judicial a dictar su audiencia previa.

TERCERO.- El apartado e) del inciso 1 del art. 19 de la Ley Reguladora de la Jurisdicción Contencioso Administrativa dispone:

«Están legitimados ante el orden jurisdiccional contencioso administrativo [COMPLETAR]

 las entidades locales territoriales, para impugnar los actos y disposiciones que afecten el ámbito de su autonomía, emanados de las Administraciones del Estado y de las Comunidades Autónomas»

El art. 63.2 de la Ley de Bases de Régimen Local, por su parte, establece:

 «Están igualmente legitimadas en todo caso las Entidades Locales territoriales para la impugnación de las disposiciones y actos de las Administraciones del Estado y de las Comunidades Autónomas que lesionen su autonomía, tal como ésta resulta garantizada por la Constitución y esta Ley».

El art. 219.1 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Corporaciones Locales, finalmente estatuye que:

 «las entidades locales territoriales están legitimadas para impugnar las disposiciones y actos de las Administraciones del Estado y de las Comunidades Autónomas que lesionen su autonomía tal como ésta resulta garantizada por la Constitución y la Ley 7/1985, de 2 de abril»

CUARTO.- Pues bien, aun cuando podría parecer que existiera una cierta limitación a la legitimación de las Corporaciones Locales, respecto de la exigida para el resto de las personas jurídicas, pues para la legitimación de éstas bastaría que ostentasen derechos o intereses legítimos, mientras que para las corporaciones locales será necesario que además los actos o disposiciones que se impugnen afecten al ámbito de su autonomía, de forma que, en una primera interpretación, pudiera predicarse en exclusiva su legitimación para lo que sería un cierto ámbito político de decisión o autonormación (autonomía), lo cierto es que luego esa aparente restricción cede si se ponen en relación los preceptos citados con el art. 2 de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local. En éste se establece que «para la efectividad de la autonomía» garantizada constitucionalmente a las entidades locales, la legislación del Estado y la de las Comunidades Autónomas, reguladora de los distintos sectores de la acción pública, según la distribución constitucional de competencias, deberá asegurar a los Municipios, las Provincias y las Islas su derecho a intervenir en «cuantos asuntos afecten directamente al círculo de sus intereses». Queda, pues, desdibujada la aparente diferencia de tratamiento, al aproximar la misma Ley «la autonomía» al «círculo de los intereses»; pudiendo, por ello, sin violencia, penetrar el sistema de legitimación por puro interés legítimo, aunque, eso sí, siempre que se afecte al círculo de intereses o el ámbito de competencias locales.

Es por todo ello por lo que vengo a personarme en representación de mi principal, Diputación Provincial de [LOCALIDAD] en la posición procesal de codemandado.

Por lo expuesto,

SUPLICO

del Tribunal
de la Sala
 que tenga por evacuado en tiempo y forma este escrito, junto con el poder que lo acompaña, lo admita, y por ello tenga por personada a la Diputación Provincial de [LOCALIDAD] y por parte a la misma en la condición de codemandada, entendiéndose a partir de este momento conmigo las sucesivas actuaciones.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
