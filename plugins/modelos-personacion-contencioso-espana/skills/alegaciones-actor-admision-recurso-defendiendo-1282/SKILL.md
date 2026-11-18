---
name: alegaciones-actor-admision-recurso-defendiendo-1282
description: "Redacta el escrito «Alegaciones del actor en la admisión del recurso defendiendo la competencia del órgano» (formulario 1282 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del actor en la admisión del recurso defendiendo la competencia del órgano

> Formulario 1282 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…arse incompetente el Tribunal o Tribunal»; «… del proceso. Por lo expresado, SOLICITA»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 51.4 de la Ley 29/1998
- arts. 8 a 14 de la LJCA
- art. 51.6 de la LJCA

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

### Formulario 1282 · Alegaciones del actor en la admisión del recurso defendiendo la competencia del órgano

- Año del modelo: 2008
- Revisión 17-11-2026: 1 rangos de artículos despegados («25 a31» → «25 a 31»); 1 desplegables convertidos en elección en blanco; 6 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AUTOS DE RECURSO NUMERO [Nº DE PROCEDIMIENTO]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], parte actora en el recurso contencioso administrativo que al margen queda reseñado, representación que tengo oportunamente acreditada, ante ese órgano jurisdiccional comparezco y, como mejor proceda en derecho, DIGO

Que al amparo del art. 51.4 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa (en adelante, LJCA), el órgano judicial al que tengo el honor de dirigirme me ha dado traslado para que en plazo de diez días alegue sobre la eventual concurrencia de causa de inadmisibilidad del recurso por incompetencia.

Que el citado artículo dispone que el juzgado o Sala, previa reclamación y examen del expediente administrativo, si lo considera necesario, declarará no haber lugar a la admisión del recurso cuando constare de modo inequívoco y manifiesto la concurrencia de incompetencia en el Tribunal .

Que esta parte defiende la plena admisibilidad del recurso formulado y en concreto la competencia del órgano jurisdiccional al amparo de lo establecido en los arts. 8 a 14 de la LJCA.

Que, además, de concurrir algún defecto de incompetencia, realidad que esta parte niega según lo acabado de exponer, en todo caso no posee las cualidades de «inequívoco y manifiesto» exigidas por el inciso 1 del citado precepto de la Ley para la inadmisión del recurso en el presente momento procesal.

Finalmente, que en caso de estimarse incompetente el Tribunal o Tribunal [COMPLETAR], por imperativo del art. 51.6 de la LJCA deberá resolverlo en forma de Auto y seguidamente remitir las actuaciones al órgano de la jurisdicción que estime competente para que ante él siga el curso del proceso.

Por lo expresado,

SOLICITA [COMPLETAR]

que dicte resolución de admisión del presente recurso y acuerde la continuación del procedimiento por sus trámites hasta sentencia, y, subsidiariamente, declare cuál es el órgano competente y remita las actuaciones para que ante él continúe en forma el curso de los autos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
