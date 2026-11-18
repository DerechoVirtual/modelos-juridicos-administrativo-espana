---
name: personacion-codemandado-privado-1892
description: "Redacta el escrito «Personación de codemandado privado» (formulario 1892 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Personación de codemandado privado

> Formulario 1892 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…ado en concepto de codemandado junto con»

## Elecciones que hay que hacer

- al Procurador / a la Procuradora

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA OPCIÓN Y REDACTARLA: En el supuesto de que optase por personarse representado por Procurador/a y acompañando poderes / En el supuesto de que optase por personarse en nombre propio y hacer una designa apud acta — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En el supuesto de que optase por personarse representado por Procurador/a / En el supuesto de que optase por personarse en nombre propio / Si se optase por presentar la demanda representado por Letrado/a — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

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

### Formulario 1892 · Personación de codemandado privado

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 1 desplegables convertidos en elección en blanco; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 1 párrafos opcionales señalados; 5 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de personación de un sujeto privado codemandado junto a la Administración en un proceso contencioso-administrativo ordinario relacionado con la responsabilidad derivada de la utilización de vehículos a motor.

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

[ELEGIR UNA OPCIÓN Y REDACTARLA: En el supuesto de que optase por personarse representado por Procurador/a y acompañando poderes / En el supuesto de que optase por personarse en nombre propio y hacer una designa apud acta — el texto de cada opción no venía en el formulario original]

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[ELEGIR UNA OPCIÓN Y REDACTARLA: En el supuesto de que optase por personarse representado por Procurador/a / En el supuesto de que optase por personarse en nombre propio / Si se optase por presentar la demanda representado por Letrado/a — el texto de cada opción no venía en el formulario original]

Que por medio del presente escrito, notificado en el plazo de los cinco días siguientes a la adopción de la resolución por la que se acuerda remitir el expediente y, dentro del plazo de nueve días al efecto conferido, por tener interés en la resolución del pleito, COMPAREZCO EN EL RECURSO CONTENCIOSO-ADMINISTRATIVO referenciado en calidad de codemandado.

En su virtud,

A LA SALA
AL TRIBUNAL
  (1)

SUPLICO

Que, teniendo por presentado este escrito con el documento que se acompaña y sus copias, lo admita, me tenga por comparecido y parte en el recurso contencioso-administrativo referenciado en concepto de codemandado junto con [COMPLETAR], disponiendo que se entiendan conmigo las sucesivas actuaciones y notificaciones.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO

Que designo para mi representación [ELEGIR: al Procurador / a la Procuradora] de los Tribunales D./Dña. [NOMBRE Y APELLIDOS] (solo para el supuesto de que el recurso se encabezara en nombre propio. Si se trata de un recurso presentado ante un órgano unipersonal es potestativa la representación por Procurador/a no obstante, de tratarse de una actuación ante un órgano colegiado, es obligatoria su intervención).

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) El Tribunal o Tribunal notificará a cuantos aparezcan como interesados de la existencia del recurso administrativo interpuesto, y les emplazará para que se personen como demandados en el plazo de nueve días (art. 49 de la Ley procesal).

En los recursos contra las decisiones adoptadas por los órganos administrativos a los que corresponde resolver los recursos especiales y las reclamaciones en materia de contratación a que se refiere la legislación de Contratos del Sector Público se emplazará como parte demandada a las personas, distintas del recurrente, que hubieren comparecido en el recurso administrativo, para que puedan personarse como demandados en el plazo de nueve días.

El efecto de no comparecer en plazo es el de la preclusión. En concreto, reseñar que si los demandados legalmente emplazados se personaran posteriormente al plazo concedido, se les tendrá por parte para los plazos no precluidos. Si no se personaren oportunamente continuará el procedimiento por sus trámites, sin que haya lugar a practicarles, en estrados o en cualquier otra forma, notificaciones de clase alguna (art. 50).

Si quien desea comparecer es la aseguradora de responsabilidad civil de la Administración Pública, para mantener la competencia de la jurisdicción contencioso-administrativa puede indicar que comparece como parte codemandada, sin que peligre la competencia de la jurisdicción contencioso-administrativa.

Si se pretendiera accionar exclusivamente contra la compañía aseguradora (y no contra la Administración Pública) en ejercicio de la acción directa del artículo 76 de la Ley de Contrato de Seguro, la jurisdicción competente sería la civil.
