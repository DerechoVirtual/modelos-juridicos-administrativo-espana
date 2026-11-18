---
name: internamiento-extranjeros-reforma-apelacion-contra-auto-393
description: "Redacta el escrito «Internamiento de extranjeros: reforma y apelación contra el auto» (formulario 393 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Internamiento de extranjeros: reforma y apelación contra el auto

> Formulario 0393 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA
- [ ] ... (11 veces)
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DE»; «…, abogado colegiado»; «…de»; «…entro de Internamiento de Extranjeros de»; «…CIONES: I Como declaró ante el Tribunal,»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 17.1 de la Constitución

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

### Formulario 0393 · Internamiento de extranjeros: reforma y apelación contra el auto

- Año del modelo: 2013
- Revisión 17-11-2026: 7 campos de relleno marcados en blanco; 8 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL TRIBUNAL DE 1.ª INSTANCIA E INSTRUCCIÓN N.º [NÚMERO] DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], abogado colegiado [COMPLETAR], en nombre y representación de D. [NOMBRE Y APELLIDOS], ante este Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha [FECHA] de [COMPLETAR] de 200 se dictó Auto por el que se autorizaba el internamiento de D. [NOMBRE Y APELLIDOS] en el Centro de Internamiento de Extranjeros de [COMPLETAR], como medida cautelar durante un plazo no superior a cuarenta días.

Que mediante el presente escrito formulo RECURSO DE REFORMA Y SUBSIDIARIAMENTE RECURSO DE APELACIÓN contra el mencionado Auto, conforme a lo prevenido en la Ley de Enjuiciamiento Criminal, y en base a las siguientes ALEGACIONES:

I

Como declaró ante el Tribunal, [COMPLETAR] reside en España desde 1999, habiendo intentado regularizar su situación desde entonces en al menos una ocasión.

En la actualidad reside con sus padres, quienes son residentes legales en España, según acredito mediante copia de sus tarjetas de residencia y certificación de nacimiento de D.. [NOMBRE Y APELLIDOS]

II

El Auto que se recurre, que contiene un único hecho y razonamiento jurídico, tan sólo le limita a señalar que D. se encuentra irregularmente en territorio español, como toda motivación del internamiento del mismo con carácter cautelar.

En el mencionado Auto ni siquiera figura la finalidad de la medida cautelar, pareciéndose inferir del mismo que la finalidad es asegurar la ejecución de un expediente administrativo de expulsión.

III

La medida de internamiento conlleva una restricción del derecho fundamental a la libertad proclamado por el artículo 17.1 de la Constitución Española, por lo que debe aplicarse para su adopción el criterio hermeneútico del “favor libertatis”.

En este sentido se pronuncia el Tribunal Constitucional en sentencia n.º 115/1987 según la cual:

“el órgano judicial habrá de adoptar libremente su decisión teniendo en cuenta las circunstancias que concurren en el caso, en el bien entendido no las relativas a la decisión de la expulsión en sí misma (sobre la que el Juez no ha de pronunciarse en este procedimiento), sino las concernientes, entre otros aspectos, a la causa de expulsión invocada, a la situación legal y personal del extranjero, a la mayor o menor probabilidad de su huida o cualquier otra que el Juez estime relevante para adoptar su decisión”.

Es claro, pues, que, como estimó la Audiencia Provincial de Lleida en sentencia n.º 30/2002 de 21 de enero,

“la orden de internamiento no ha de tener carácter automático, sino que en aplicación de la doctrina constitucional citada se ha de atender a las circunstancias legales y personales concurrentes, ponderando el riesgo del que el extranjero huya, se oculte o sustraiga al cumplimiento de la previsible resolución en relación con sus circunstancias familiares, laborales y de domicilio”.

De la misma opinión fue la Audiencia Provincial de Huesca, que en la Sentencia n.º 77/1994 de 28 de Octubre, afirmó que

“de cualquier manera, se ha de justificar la necesidad del internamiento para que el Juez pueda pronunciarse sobre su pertinencia, y apoyarse con datos y hechos que acrediten que es ésa y no otra la que resulta más adecuada para asegurar el fin perseguido, limitando de la menor forma posible los derechos y libertades de los ciudadanos extranjeros”.

En el presente caso, resulta evidente que de la escueta motivación del Tribunal no resulta posible conocer la motivación de la decisión de internar a [...].

Tampoco se ha acreditado el que sólo la medida de internamiento pueda asegurar el fin perseguido, cuando existen otras medidas cautelares que pueden asegurar el fin que el Tribunal parece perseguir (como la comparecencia periódica o la retirada de pasaporte, entre otras).

En resumen, esta parte considera que no se ha motivado suficientemente la necesidad del internamiento de [...], pudiéndose haber adoptado otras medidas que aseguraran el fin perseguido sin restringir el derecho fundamental a la libertad del artículo 17.1 de la Constitución.

Por lo expuesto SUPLICO AL TRIBUNAL que tenga por presentado este escrito con sus copias, lo admita y tenga por formulado Recurso de Reforma contra el Auto de fecha [...] de [...]de 200[...] y tras los trámites legales oportunos dicte resolución estimatoria del presente Recurso, declarando la puesta en liberta de D. [...], sin perjuicio de que se puedan adoptar otras medidas cautelares para asegurar el fin perseguido por el Tribunal.

Por ser Justicia que pido en [...], a [...] de [...] de 200[...].

OTROSI DIGO que en caso de desestimarse el Recurso de Reforma presentado, se interpone Recurso de Apelación contra el Auto referido.

Por lo que SUPLICO AL TRIBUNAL que tenga por interpuesto el Recurso Subsidiario de Apelación contra el Auto referido, se admita y previos los trámites oportunos, se dicte resolución estimatoria del mismo.

Por ser Justicia que reitero en lugar y fecha ut supra.

Fdo: [...]
