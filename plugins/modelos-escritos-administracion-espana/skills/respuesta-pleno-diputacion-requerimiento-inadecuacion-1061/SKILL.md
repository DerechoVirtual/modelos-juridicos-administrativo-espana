---
name: respuesta-pleno-diputacion-requerimiento-inadecuacion-1061
description: "Redacta el escrito «Respuesta del pleno de la diputación al requerimiento: inadecuación de acciones (Galicia)» (formulario 1061 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Respuesta del pleno de la diputación al requerimiento: inadecuación de acciones (Galicia)

> Formulario 1061 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] FECHA (3 veces)
- [ ] DESCRIBIR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dencias de esta Diputación Provincial el»; «… judiciales ante el orden jurisdiccional»; «…cretario, la Asesoría jurídica o letrado»; «…ularidad local, sino más concretamente a»; «…espondiente. Lo que expido la presente a»

## Elecciones que hay que hacer

- el vecino / los vecinos

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 107 de la Ley 5/1997
- art. 33.2.i) de la Ley 7/1985
- artículos 220 de la Ley 5/1997
- art. 68 de la Ley 7/1985
- art. 220 del Real Decreto 2568/1986
- artículos 221 del Real Decreto 2568/1986
- art. 54.3 del Real Decreto Legislativo 781/1986
- arts. 220.1 de la Ley 5/1997

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

### Formulario 1061 · Respuesta del pleno de la diputación al requerimiento: inadecuación de acciones (Galicia)

- Año del modelo: 2008
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

CERTIFICACIÓN

[NOMBRE Y APELLIDOS], Secretario/a General de la Excma. Diputación Provincial de [LOCALIDAD],

CERTIFICO:

Que de los antecedentes obrantes a mi cargo, en la Secretaría de esta Diputación aparece un Acuerdo dictado en fecha [FECHA] por el Pleno de la Diputación conforme a las atribuciones conferidas por el art. 107 de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, a cuyo tenor «corresponden, en todo caso, al Pleno las siguientes atribuciones: i) El ejercicio de acciones judiciales y administrativas», y el art. 33.2.i) de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, Acuerdo que viene a resolver de conformidad con el dictamen previo al ejercicio de acciones emitido, y que resulta del siguiente tenor:

ANTECEDENTES

PRIMERO.- Visto que en fecha [FECHA], con entrada en las dependencias de esta Diputación Provincial el [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS] formulaba requerimiento a esta entidad local al amparo de los artículos 220 de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, art. 68 de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, y art. 220 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento estatal de Organización, Funcionamiento y Régimen Jurídico de los Entes Locales, para que se procediera al inicio de acciones judiciales ante el orden jurisdiccional [COMPLETAR] para la defensa de los bienes o derechos de titularidad de esta Diputación, consistentes en [DESCRIBIR].

SEGUNDO.- Visto el dictamen previo al ejercicio de acciones emitido en fecha [FECHA] por el Secretario, la Asesoría jurídica o letrado [COMPLETAR] al amparo de los artículos 221 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Entidades Locales y art. 54.3 del Real Decreto Legislativo 781/1986, de 18 de abril, Texto Refundido de las Disposiciones Vigentes de Régimen Local, dictamen expresivo de que las acciones judiciales solicitadas son diferentes de aquellas previstas en los preceptos anteriormente citados, pues no se hallan directamente encaminadas a la defensa de los bienes o derechos de titularidad local, sino más concretamente a [COMPLETAR].

FUNDAMENTOS JURÍDICOS

ÚNICO.-

Atendido que si bien el ejercicio de acciones por las entidades locales no posee carácter potestativo sino imperativo, a tenor de los arts. 220.1 de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, y art. 68 de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, es más cierto es que en este caso aquella imperatividad no juega ya que existe una desviación entre aquellas acciones para las que está prevista en sus normas rectoras y aquellas que [ELEGIR: el vecino / los vecinos] pretenden sean formuladas.

RESOLUCIÓN

El Pleno de la Diputación, conforme a las atribuciones conferidas por el art. 107 de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, a cuyo tenor a éste le corresponde el ejercicio de acciones judiciales y administrativas, y art. 33.2.i) de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, mandato que se extiende, obviamente, a la denegación de su ejercicio, ha resuelto, dentro del plazo legal, denegar el inicio de las acciones solicitadas, quedando, en consecuencia, al interesado expedita la vía judicial correspondiente.

Lo que expido la presente a [COMPLETAR] con el visto bueno del Presidente/a de la Diputación.

Vº Bº

El/La Presidente/a de la Diputación:
