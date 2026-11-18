---
name: resolver-expediente-nulidad-acto-124
description: "Redacta el escrito «Resolver el expediente de nulidad de un acto» (formulario 124 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolver el expediente de nulidad de un acto

> Formulario 0124 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] FECHA (7 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ministración dictó resolución por la que»; «…, el Consejo de Estado»; «…e pleno Derecho, prevista en el apartado»; «…sto, de acuerdo con el Consejo de Estado»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 106 de la LPACAP
- artículo 102.4 de la LPACAP
- artículos 32.2 y 34.1 de la Ley 40/2015

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

### Formulario 0124 · Resolver el expediente de nulidad de un acto

- Año del modelo: 2017
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente número:

Interesados:

Procedimiento:

Asunto: RESOLUCIÓN

VISTO el procedimiento de revisión de oficio para la declaración de nulidad de pleno Derecho del acto dictado en fecha [FECHA], sobre [DESCRIBIR], y de conformidad con los siguientes

ANTECEDENTES DE HECHO

PRIMERO.- Con fecha [FECHA], esta Administración dictó resolución por la que [COMPLETAR]. Dicha resolución definitiva en vía administrativa fue notificada en forma a los interesados.

SEGUNDO.- Con fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] presentó escrito ante esta Administración por el que se solicitaba la declaración de nulidad de la citada resolución.

TERCERO.- Admitida a trámite dicha solicitud e instruido el correspondiente procedimiento, con fecha [FECHA], el Consejo de Estado [COMPLETAR] dictaminó favorablemente la declaración de nulidad sometida a consulta y la indemnización de los daños y perjuicios producidos.

CUARTO.- En el presente procedimiento se han observado los trámites legales, así como el plazo máximo de seis meses desde su inicio para dictar la presente resolución, de conformidad con lo establecido en el artículo 106.5 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

FUNDAMENTOS DE DERECHO

PRIMERO.- Esta Administración Pública, siguiendo el parecer del órgano instructor del procedimiento, y de conformidad con el dictamen del Consejo de Estado, es competente para declarar la nulidad de pleno Derecho del acto dictado en fecha [FECHA], sobre el expediente administrativo relativo a [DESCRIBIR], de acuerdo con lo dispuesto en el art. 106 de la LPACAP.

SEGUNDO.- De las actuaciones practicadas resulta probado que el acto administrativo objeto de revisión ha incurrido en causa de nulidad de pleno Derecho, prevista en el apartado [COMPLETAR], del art. 47.1 de la citada LPACAP, consistente en [DESCRIBIR], por lo que procede la sanción de nulidad radical o absoluta de dicho acto administrativo.

TERCERO.- De acuerdo con lo dispuesto en el artículo 102.4 de la LPACAP, este órgano administrativo competente establece como indemnización por daños y perjuicios que procede reconocer a D./Dña. [NOMBRE Y APELLIDOS], el derecho a percibir la cuantía de [IMPORTE]. euros, que son los efectivamente ocasionados e indemnizables por la ilegalidad del acto dañoso y la responsabilidad derivada del mismo, según preceptúan los artículos 32.2 y 34.1 de la Ley 40/2015 de Régimen Jurídico del Sector Publico.

En atención a todo lo expuesto, de acuerdo con el Consejo de Estado [COMPLETAR],

RESUELVO

Primero.- DECLARAR la nulidad de pleno Derecho del acto dictado por esta Administración Pública, en fecha [FECHA], sobre el expediente administrativo de referencia.

Segundo.- RECONOCER a D./Dña. [NOMBRE Y APELLIDOS] el derecho a percibir una indemnización por los daños y perjuicios ocasionados en la cantidad total de [IMPORTE] euros.

Contra la presente resolución, que pone fin a la vía administrativa, se podrá interponer recurso potestativo de reposición ante este mismo órgano en el plazo de UN MES, contar desde el día siguiente al de la recepción de su notificación, o interponer recurso contencioso-administrativo, ante [ÓRGANO], en el plazo de DOS MESES, contados desde el día siguiente a la notificación o publicación de la misma, sin perjuicio de que los interesados puedan ejercitar cualquier otro recurso que estimen procedente.

En [LUGAR], a [FECHA].

Firma del titular del órgano administrativo competente
