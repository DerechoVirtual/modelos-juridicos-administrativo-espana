---
name: alegaciones-propuesta-resolucion-980
description: "Redacta el escrito «Alegaciones a la propuesta de resolución» (formulario 980 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones a la propuesta de resolución

> Formulario 0980 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, actuando en nombre propio»; «… a las siguientes: ALEGACIONES PRIMERA.-»; «…SEGUNDA.-»; «…RGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE»; «…- CONCURRENCIA DE SANCIONES,»; «…CADUCIDAD DEL PROCEDIMIENTO»; «…de expulsión al amparo de una motivación»; «…ntes medios de prueba documentales: 1º.-»; «…2º.-»; «…2º.- [COMPLETAR] 3º.-»

## Párrafos opcionales (7)

Inclúyelos solo si encajan en los hechos:

- - FALTA DE COMPETENCIA DEL ORGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE [COMPLETAR]…
- - FALTA DE TIPICIDAD DE LOS HECHOS.…
- - CONCURRENCIA DE SANCIONES, [COMPLETAR].…
- - PRESCRIPCIÓN DE LA INFRACCIÓN.…
- CADUCIDAD DEL PROCEDIMIENTO [COMPLETAR].…
- - IMPROCEDENCIA DE LA SANCIÓN DE EXPULSIÓN POR APLICACIÓN DEL PRINCIPIO DE PROPORCIONALIDAD PREVISTO DE MODO E…
- TERCERA.- Que para la acreditación de cuanto aquí se afirma, y en concreto con respecto a los hechos, y todo e…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 55.3 y 57.1 de la Ley Orgánica 4/2000
- art. 29 Ley 40/2015
- art. 55.3 y 4 de la Ley Orgánica 4/2000
- art. 57.1 de la Ley Orgánica 4/2000
- artículo 53.1 de la Ley Orgánica 4/2000
- art. 242.1 del Real Decreto 557/2011
- art. 55.3 de la Ley Orgánica 4/2000
- art. 222.3 del RD 557/2011
- art. 55 de la Ley Orgánica 4/2000
- art. 235.4 del Real Decreto 557/2011

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

### Formulario 0980 · Alegaciones a la propuesta de resolución

- Año del modelo: 2008
- Revisión 17-11-2026: 7 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL INSTRUCTOR DEL PROCEDIMIENTO

PROCEDIMIENTO SANCIONADOR PREFERENTE EN MATERIA DE EXTRANJERÍA Nº [Nº]

INTERESADO

D./Dña. [NOMBRE Y APELLIDOS], con DNI/NIF/NIE nº [DNI/NIE], actuando en nombre propio [COMPLETAR], cuyo domicilio, a efectos de las notificaciones que pudieran serle cursadas en el procedimiento, tiene oportunamente consignado en sus escritos anteriores, a través del presente comparece y como mejor proceda en derecho

EXPONE

Que con fecha [FECHA] le ha sido dado traslado por ese Instructor de la propuesta de resolución elaborada en el procedimiento sancionador preferente en materia de extranjería seguido contra [ACTO O RESOLUCIÓN], cuyo número de referencia queda reseñado al margen, tramitado por una supuesta infracción a la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social, y en la que se propone la expulsión del sujeto a procedimiento.

Que en dicha propuesta de resolución se le indicaba su derecho a formular alegaciones y presentar prueba documental en el plazo de 48 horas, según establece el art. 235.4, en su párrafo cuarto, del RD 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero.

Por todo ello en el plazo reglamentariamente previsto paso a cumplimentar el indicado trámite con arreglo a las siguientes:

ALEGACIONES

PRIMERA.- [COMPLETAR]

SEGUNDA.- [COMPLETAR]

[OPCIONAL — incluir si procede]

- FALTA DE COMPETENCIA DEL ORGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE [COMPLETAR]

[OPCIONAL — incluir si procede]

- FALTA DE TIPICIDAD DE LOS HECHOS.

[OPCIONAL — incluir si procede]

- CONCURRENCIA DE SANCIONES, [COMPLETAR].

[OPCIONAL — incluir si procede]

- PRESCRIPCIÓN DE LA INFRACCIÓN.

[OPCIONAL — incluir si procede]

CADUCIDAD DEL PROCEDIMIENTO [COMPLETAR].

[OPCIONAL — incluir si procede]

- IMPROCEDENCIA DE LA SANCIÓN DE EXPULSIÓN POR APLICACIÓN DEL PRINCIPIO DE PROPORCIONALIDAD PREVISTO DE MODO EXPLÍCITO EN EL ART. 57.1 DE LA LEY ORGÁNICA 4/2000 TRAS SU REFORMA POR LA LEY ORGÁNICA 2/2009, Y POR IMPERATIVO DE LOS CRITERIOS PARA LA DETERMINACIÓN DE LA SANCIÓN PREVISTOS EN EL ART. 55.3 Y 4 DE LA MISMA LEY ORGÁNICA Y ARTS. 233.3 Y 233.4 DE SU REGLAMENTO APROBADO POR RD 557/2011, DE 20 DE ABRIL.

La propuesta de resolución estima que procede imponer a este interesado la sanción de expulsión al amparo de una motivación [COMPLETAR] y con infracción de la Ley Orgánica 4/2000 y su Reglamento Ejecutivo.

Por el contrario debiera llevar a otra solución distinta de la expulsión la aplicación del principio de proporcionalidad contenido en los arts. 55.3 y 57.1 de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, y su Reglamento de desarrollo, como el art. 29 Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Publico (en adelante, LRJSP) y, muy especialmente, tal principio de proporcionalidad, de alcance constitucional, como derivado del otro de legalidad sancionadora.

Lo mismo se impone por aplicación de las reglas para la individualización de las sanciones previstas en el art. 55.3 y 4 de la Ley Orgánica 4/2000, de 11 de enero, y 222.3 del Reglamento aprobado por RD 557/2011, de 20 de abril.

A todo ello debe añadirse la condición de principal que tiene en la Ley la sanción de multa, frente a la cual la expulsión es un sustitutivo cuya aplicación, por tanto, debe estar fundada en una racionalidad estrictamente sancionadora y asentada en una suficiente motivación. Esta relación de principal-sustitutivo entre la multa y la expulsión se obtiene del art. 57.1 de la Ley Orgánica 4/2000, de 11 de enero, en el que se indica que cuando los infractores sean extranjeros y realicen conductas tipificadas como muy graves, o conductas graves de las previstas en los apartados a), b), c), d) y f) del artículo 53.1 de la Ley Orgánica 4/2000, de 11 de enero, podrá aplicarse, en atención al principio de proporcionalidad, "en lugar de la sanción de multa" la expulsión del territorio español’ previa la tramitación del correspondiente expediente administrativo. Lo propio se establece ("en lugar de") en el art. 242.1 del Real Decreto 557/2011, de 20 de abril.

Por otra parte, como queda indicado, el art. 55.3 de la Ley Orgánica 4/2000 dispone que para la graduación de las sanciones el órgano competente para imponerlas se ajustará a criterios de proporcionalidad, valorando el grado de culpabilidad y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia. El art. 222.3 del RD 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica, dispone que para la determinación de la sanción que se imponga, además de los criterios de graduación a que se refieren los apartados 3 y 4 del art. 55 de la Ley Orgánica 4/2000, de 11 de enero, se valorarán también, a tenor de su art. 57, las circunstancias de la situación personal y familiar del infractor.

Pues bien, ninguna de estas razones fundamenta por sí misma la expulsión. Ninguna de ellas ampara fines de orden político, atendibles si son defendidos a través de técnicas jurídicas diferentes a la sanción, como puede ser la política migratoria, la limitación de flujos de entrada, el orden público, la estabilidad económica o cualesquiera otros. Tampoco la probabilidad de la insolvencia y posible dificultad en el cobro de la sanción encuentran hueco en la proporcionalidad ni la individualización.

[OPCIONAL — incluir si procede]

TERCERA.- Que para la acreditación de cuanto aquí se afirma, y en concreto con respecto a los hechos, y todo ello al amparo de lo dispuesto en el art. 235.4 del Real Decreto 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social, aporto adjuntos al presente escrito los siguientes medios de prueba documentales:

1º.- [COMPLETAR]
2º.- [COMPLETAR]
3º.- [COMPLETAR]

En atención a todo lo expuesto,

SUPLICO

que tenga por presentado este escrito en tiempo y forma, lo admita y, en su virtud, tenga por formuladas las alegaciones en él contenidas y por evacuado el trámite correspondiente, con admisión de la totalidad de los medios documentales aportados, y, previos los trámites legales, se acuerde el archivo del expediente sancionador por las causas más arriba expresadas:

En [LUGAR], a [FECHA].

Fdo: D./Dña. [NOMBRE Y APELLIDOS]
