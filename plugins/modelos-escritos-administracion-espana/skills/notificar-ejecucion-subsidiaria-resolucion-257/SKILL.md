---
name: notificar-ejecucion-subsidiaria-resolucion-257
description: "Redacta el escrito «Notificar la ejecución subsidiaria de una resolución administrativa» (formulario 257 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificar la ejecución subsidiaria de una resolución administrativa

> Formulario 0257 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] Nº DE EXPEDIENTE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] FECHA (6 veces)
- [ ] PLAZO
- [ ] Nº DE PROCEDIMIENTO
- [ ] IMPORTE
- [ ] ÓRGANO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…xpediente de referencia, seguido en esta»; «…, con DNI [DNI/NIE] por Debido a»; «…(notificada el»; «…e los daños y perjuicios ocasionados y a»; «…ontencioso-Administrativo, plaza n.º de)»; «…, en la que se obligaba al denunciado a»; «…tificado a través del Boletín Oficial de»; «…de fecha [FECHA] y del tablón de edictos»; «… a bien RESOLVER PRIMERO.- Procédase por»; «…ndole que de conformidad con el artículo»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 44 de la Ley 39/2015
- artículo 102 de la Ley 39/2015

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

### Formulario 0257 · Notificar la ejecución subsidiaria de una resolución administrativa

- Año del modelo: 2016
- Revisión 17-11-2026: 23 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Notificación de ejecución subsidiaria en expediente de denuncia número [Nº DE EXPEDIENTE]

Intentada la notificación sin haberse podido practicar, de la resolución del procedimiento administrativo de ejecución subsidiaria correspondiente al expediente de denuncia que se cita, se hace público el presente anuncio en cumplimiento de lo establecido en el artículo 44 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

Número del expediente:

Denunciado:

Domicilio:

Denunciante:

Visto el expediente de referencia, seguido en esta [COMPLETAR] (Órgano, persona o unidad que adopta la resolución) a D./Dª [NOMBRE Y APELLIDOS], con DNI [DNI/NIE] por

Debido a [COMPLETAR]

Mediante resolución firme de fecha [FECHA] (notificada el [COMPLETAR]), se acordó, por este Centro Directivo, que D abonase la multa, procediera al pago de los daños y perjuicios ocasionados y a [COMPLETAR] en los términos fijados en la Resolución, concediéndole el plazo de [PLAZO] desde el momento en que adquiriese firmeza la misma.

Transcurrido el mismo sin que así lo hiciera, sería ejecutado de forma subsidiaria por la Administración, corriendo los gastos ocasionados a costa del infractor.

Mediante Providencia de fecha [FECHA] dictada por el Tribunal de Instancia (Sección de lo Contencioso-Administrativo, plaza n.º de) [COMPLETAR] en el procedimiento abreviado nº [Nº DE PROCEDIMIENTO], en la que se declara la firmeza de la Sentencia dictada en dichas actuaciones, se desestima el recurso contencioso-administrativo interpuesto contra la Resolución del expediente administrativo sancionador de referencia, de fecha [FECHA], en la que se obligaba al denunciado a [COMPLETAR], concediéndole el plazo de 1 mes desde que la resolución fuese firme.

Con fecha [FECHA] (notificado a través del Boletín Oficial de [COMPLETAR] de fecha [FECHA] y del tablón de edictos [COMPLETAR], al no haber sido posible la notificación en el domicilio del interesado), y una vez transcurridos los plazos concedidos en la resolución mencionada, se requirió al interesado para que procediera a realizar, voluntariamente, los trabajos ordenados o, en otro caso, se procedería a la ejecución subsidiaria de los mismos por este órgano administrativo y a costa del interesado.

El plazo concedido en dicho requerimiento ha transcurrido sin que hasta la fecha se haya acreditado su cumplimiento en la forma indicada.

Considerando que la Administración puede proceder, a través de sus órganos y servicios o por persona distinta, a la ejecución subsidiaria de lo ordenado, cuando se trate de actos que, por no ser personalísimos, puedan ser realizados por persona distinta del obligado y a su costa.

Vistos los antecedentes mencionados y el artículo 102 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, he tenido a bien

RESOLVER

PRIMERO.- Procédase por [COMPLETAR], a la ejecución subsidiaria de lo acordado mediante resolución de [FECHA], dictada por este órgano administrativo, consistente en

SEGUNDO.- Requiérase al interesado el pago de la cuantía de [IMPORTE] euros en concepto de liquidación provisional de los gastos que ocasiona la citada ejecución, según la tasación provisional realizada y a salvo de lo que resulte de la liquidación definitiva.

TERCERO.- Notifíquese la presente resolución al interesado, indicándole que de conformidad con el artículo [COMPLETAR], contra esta resolución, que no agota la vía administrativa, cabe interponer recurso de alzada ante [ÓRGANO], dentro del plazo de UN MES contado a partir del día siguiente a la fecha de notificación.

CUARTO.- Notifíquese con antelación suficiente, la fecha y hora de inicio de la referida ejecución.

Lugar, fecha, sello y firma
