---
name: acuerdo-declaracion-lesividad-1302
description: "Redacta el escrito «Acuerdo de declaración de lesividad» (formulario 1302 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo de declaración de lesividad

> Formulario 1302 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] FECHA (3 veces)
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…expediente»; «…recaída en el expediente»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 82 de la Ley 39/2015
- art. 48 de la Ley 39/2015
- art. 107 de la Ley 39/2015

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

### Formulario 1302 · Acuerdo de declaración de lesividad

- Año del modelo: 2006
- Revisión 17-11-2026: 5 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

ACUERDO DE DECLARACIÓN ADMINISTRATIVA DE LESIVIDAD

Visto el expediente instruido en orden a la declaración de lesividad de la licencia otorgada por resolución de fecha [FECHA] expediente [COMPLETAR] y RESULTANDO los siguientes,

ANTECEDENTES

I.- Por resolución de la Alcaldía de fecha [FECHA] recaída en el expediente [COMPLETAR], le fue otorgada a D. licencia (especificar el tipo de licencia de que se trata).

II.- El otorgamiento de la licencia en cuestión incide, conforme a los informes de los Servicios Técnicos Municipales, en grave infracción del ordenamiento jurídico (especificar la infracción en que se ha incurrido).

III.- Instruido expediente por resolución de fecha [FECHA] han sido evacuados informes por parte del Jefe del Servicio Municipal, en cuyo ámbito administrativo se otorgó la licencia. Se le ha otorgado al interesado el correspondiente trámite de audiencia y vista en el expediente, a tenor del art. 82 de la Ley 39/2015 de procedimiento administrativo común de las administraciones publicas, poniéndose de manifiesto que no han transcurrido cuatro años desde el momento del otorgamiento de la licencia cuya lesividad se pretende y la incoación de este procedimiento.

Tampoco ha operado la caducidad del procedimiento que nos ocupa, pues desde la adopción del acuerdo de iniciación del procedimiento al día de la adopción de esta resolución, no han transcurrido tres meses.

Vistos los anteriores antecedentes y considerando los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO Las Administraciones Públicas pueden declarar lesivos para el interés público los actos favorables para los interesados, que resulten anulables conforme al art. 48 de la Ley 39/2015, a fin de proceder a su anterior impugnación ante el orden jurisdiccional contencioso-administrativo.

SEGUNDO El acuerdo de lesividad se puede adoptar en el plazo máximo de cuatro años, contado desde la fecha en que fue adoptado el acto administrativo, exige la incoación de expediente y evacuar el trámite de audiencia y vista del interesado.

La duración del expediente para declarar la lesividad no puede superar el plazo de tres meses, caso contrario operará la caducidad del mismo.

TERCERO La declaración previa de lesividad se refiere exclusivamente a actos declarativos de derechos que sean anulables por haber incurrido en cualquier infracción del ordenamiento jurídico y la Administración autora entienda que los mismos son contrarios al interés público (interés que no tiene porque ser necesariamente de carácter económico).

La declaración de lesividad debe realizarse por el órgano competente, que en el caso de la Administración Local, lo es el Pleno de la Corporación, en los términos del art. 107 de la Ley 39/2015.

Esta declaración de lesividad debe adoptarse, como se ha indicado en el apartado anterior, en el plazo máximo de cuatro años y, a partir de la adopción del acuerdo, correrá el plazo de dos meses para interponer el correspondiente recurso contencioso-administrativo (art. 46.5 LJ).

El procedimiento, en sede jurisdiccional, se inicia directamente con la demanda en la que se "fijará con precisión la persona o personas demandadas y su sede o domicilio si constara", y se deberá acompañar la declaración de lesividad y el expediente administrativo (art. 45.4 LJ).

Los demandados deberán ser emplazados personalmente por el plazo de nueve días (art. 49.6 LJ).

Vistos los artículos citados y demás de pertinente aplicación, el Pleno del Ayuntamiento

ACUERDA

1.- Declarar lesivo al interés público el acto administrativo a que anteriormente se ha hecho referencia.

2.- Proceder a su impugnación por la vía jurisdiccional, ordenando a los Servicios Jurídicos de este Ayuntamiento que procedan en los términos que resultan de los arts. 45.4, 19.2 y 43 de la Ley Reguladora de la Jurisdicción Contencioso-Administrativa, en concordancia con el art. 107 de la Ley 39/2015.

3.- Notifíquese a los interesados en el expediente el acuerdo aquí adoptado.
