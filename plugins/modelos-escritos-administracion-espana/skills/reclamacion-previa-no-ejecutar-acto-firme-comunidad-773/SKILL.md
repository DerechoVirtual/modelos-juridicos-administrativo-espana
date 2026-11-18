---
name: reclamacion-previa-no-ejecutar-acto-firme-comunidad-773
description: "Redacta el escrito «Reclamación previa por no ejecutar un acto firme (Comunidad Valenciana)» (formulario 773 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamación previa por no ejecutar un acto firme (Comunidad Valenciana)

> Formulario 0773 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (5 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] SU
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE
- [ ] NÚMERO DE LA CALLE
- [ ] FECHA (3 veces)
- [ ] PLAZO
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…actividad, de ejecución de la resolución»; «…, en virtud de la cual requirió a»; «…, titular de la parcela»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 29.2 de la LJCA

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

### Formulario 0773 · Reclamación previa por no ejecutar un acto firme (Comunidad Valenciana)

- Año del modelo: 2009
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NÚMERO DE LA CALLE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL AYUNTAMIENTO DE [LOCALIDAD]

DON/DOÑA [NOMBRE Y APELLIDOS] en [SU] propio nombre y derecho/en representación de ….., con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], c/ [CALLE] núm. [NÚMERO DE LA CALLE] ante el Ayuntamiento de [LOCALIDAD] comparezco y, como mejor en derecho proceda, DIGO:Que por medio del presente escrito vengo a formular solicitud, frente a inactividad, de ejecución de la resolución [COMPLETAR] dictada por el Ayuntamiento de [LOCALIDAD], sobre la base de las siguientes,

ALEGACIONES

Primero.- El Ayuntamiento al que me dirijo dictó resolución, en fecha [FECHA], en virtud de la cual requirió a [COMPLETAR], titular de la parcela [COMPLETAR], a restaurar la legalidad urbanística, todo ello con fundamento en el art. 250 y ss. del Decreto Legislativo 1/2021, de 18 de junio, del Consell de aprobación del texto refundido de la Ley de ordenación del territorio, urbanismo y paisaje.

En concreto, el acto mencionado ordenó la demolición de una caseta ubicada en la parcela.

Segundo.- Ha transcurrido desde el dictado de la resolución un plazo de [PLAZO], no habiéndose recurrido el acto administrativo, ni ejecutado el mismo.

Nos encontramos, por consiguiente, ante un acto o resolución firme y una inejecución del mismo por la Administración.

Tercero.- De conformidad con lo establecido en el art. 29.2 de la LJCA, en el supuesto de inactividad de la Administración para la ejecución de un acto firme, los afectados estarán facultados para solicitar su ejecución.

Por consiguiente, formulo solicitud al Ayuntamiento de [LOCALIDAD] a fin de que ejecute la resolución de [FECHA] advirtiendo de que en el caso de que no se ejecutase en el plazo de 1 mes se deducirá recurso contencioso-administrativo.

Por lo expuesto,

SOLICITO AL AYUNTAMIENTO DE [LOCALIDAD] que, habiendo por presentado este escrito, se sirva admitirlo, tenga por formulada solicitud a fin de que ejecute la resolución consistente en [DESCRIBIR], advirtiendo de que en el caso de que no se ejecutase en el plazo de 1 mes, se deducirá recurso contencioso-administrativo, es de Justicia que pido en [LUGAR], a [FECHA].
