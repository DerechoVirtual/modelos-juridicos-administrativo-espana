---
name: auto-falta-jurisdiccion-contencioso-administrativa-favor-1766
description: "Redacta el escrito «Auto de falta de jurisdicción contencioso-administrativa a favor de la jurisdicción civil» (formulario 1766 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Auto de falta de jurisdicción contencioso-administrativa a favor de la jurisdicción civil

> Formulario 1766 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA

## Elecciones que hay que hacer

- una / varias

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 9.1 y 22 de la LOPJ
- art. 9.4 de la Ley Orgánica 6/1985
- art. 1 de la Ley 29/1998
- art. 5.3 de la Ley 29/1998
- art. 5.3 LJCA
- artículo 102 del Real Decreto-ley 6/2023

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

### Formulario 1766 · Auto de falta de jurisdicción contencioso-administrativa a favor de la jurisdicción civil

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 1 desplegables convertidos en elección en blanco; 1 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Auto por el que el órgano jurisdiccional contencioso-administrativo, previa audiencia de las partes y el Ministerio Fiscal, acuerda la falta de jurisdicción del orden contencioso administrativo, por corresponder al Orden Civil de la jurisdicción el conocimiento de las pretensiones y el archivo de las actuaciones.

Actualizado conforme al RDL 6/2023, vigente desde el 20 de marzo de 2024.

AUTO

En [LUGAR], a [FECHA].

HECHOS

Que habiéndose apreciado que el objeto del presente recurso pudiera no ser competencia de esta Jurisdicción Contencioso-Administrativa, se dio traslado a las partes y al Ministerio Fiscal por diez días para que formulasen las alegaciones que estimaran pertinentes, lo que hicieron en debida forma.

RAZONAMIENTO JURÍDICO

Que, de conformidad con las normas atributivas de la jurisdicción contenidas en los arts. 9.1 y 22 de la LOPJ, el presente procedimiento debe ser atribuido al conocimiento de la Jurisdicción Civil, al dirimirse [ELEGIR: una / varias] pretensión/es de derecho privado y no tratarse, por tanto, de pretensiones dirigidas contra una Administración Pública por actividad sujeta a Derecho Administrativo en los términos previstos en el art. 9.4 de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial (en adelante LOPJ) y art. 1 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa (en adelante, LJCA), por lo que procede declararlo de esa manera y acordar el archivo de las presentes actuaciones.

LA SALA
EL TRIBUNAL
 ACUERDA

Declarar la falta de jurisdicción del orden contencioso administrativo, por corresponder al Orden Civil de la jurisdicción el conocimiento de las pretensiones, y acordar el archivo de las presentes actuaciones.

Conforme al art. 5.3 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa, si la parte demandante se personare ante el Orden Civil en el plazo de un mes desde la notificación del presente Auto, se entenderá haberlo efectuado en la fecha en que se inició el plazo para interponer el recurso contencioso-administrativo, si hubiere formulado éste siguiendo las indicaciones de la notificación del acto o ésta fuese defectuosa (1).

Notifíquese la presente resolución a las partes haciéndoles saber que contra la misma cabe recurso de reposición. En el caso de interponer este recurso, será necesario realizar el previo depósito de 25 euros en la cuenta de Depósitos y Consignaciones conforme a lo previsto en la Disposición Adicional 15ª de la LOPJ.

Lo acuerda la Sala y firman los Ilmos. Sres. del margen.

Firma del Juez/a:

NOTAS DEL FORMULARIO

(1) Ha de tenerse presente que el art. 5.3 LJCA y para los procedimientos incoados con posterioridad al 20 de marzo de 2024, establece, de conformidad con la redacción dada al mismo por el apartado uno del artículo 102 del Real Decreto-ley 6/2023, de 19 de diciembre, por el que se aprueban medidas urgentes para la ejecución del Plan de Recuperación, Transformación y Resiliencia en materia de servicio público de justicia, función pública, régimen local y mecenazgo que "si la nueva demanda que se formule ante el juzgado o tribunal competente del orden jurisdiccional indicado en la referida resolución se presenta en el plazo de un mes desde que fuera notificada, se entenderá presentada en la fecha en que se inició el plazo para interponer el recurso contencioso-administrativo, si se hubiere formulado éste siguiendo las indicaciones de la notificación del acto o ésta fuese defectuosa. Al objeto de acreditar tales extremos la parte interesada podrá solicitar testimonio de los particulares necesarios al órgano judicial que haya dictado la resolución a que se refiere el apartado anterior".
