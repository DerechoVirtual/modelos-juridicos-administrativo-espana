---
name: demanda-contra-denegar-nacionalidad-falta-integracion-294
description: "Redacta el escrito «Demanda contra denegar la nacionalidad por falta de integración» (formulario 294 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra denegar la nacionalidad por falta de integración

> Formulario 0294 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] FECHA (4 veces)
- [ ] FECHA DE LA DILIGENCIA
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… nacionalidad española por residencia el»; «…presidente de la comunidad de vecinos de»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSI DIGO que se estima que la cuantía del recurso es indeterminada, al constituir el objeto del mismo la im…
- SEGUNDO OTROSÍ DIGO que de conformidad con el artículo 60 LJCA solicito el recibimiento a prueba del presente …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 22.4 del Código Civil
- art. 11 de la LJCA
- art. 7.3 LJCA
- art. 19.1.a) de la LJCA
- art. 139.1 de la LJCA
- artículo 60 LJCA

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

### Formulario 0294 · Demanda contra denegar la nacionalidad por falta de integración

- Año del modelo: 2014
- Revisión 17-11-2026: 2 párrafos opcionales señalados; 11 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA DE LA DILIGENCIA, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA AUDIENCIA NACIONAL

SALA DE LO CONTENCIOSO-ADMINISTRATIVO

SECCIÓN

Procedimiento Ordinario/20

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según consta acreditado en los autos arriba referenciados, mediante el presente escrito., DIGO:

Que el día [FECHA] me ha sido notificada diligencia de ordenación de fecha [FECHA DE LA DILIGENCIA] por la que se otorga el plazo de veinte días para formular demanda, por lo que, dentro del plazo conferido formalizo la DEMANDA basándome en los siguientes

HECHOS

D./Dña. [NOMBRE Y APELLIDOS] solicitó concesión de nacionalidad española por residencia el [COMPLETAR], la cual le fue denegada por resolución de fecha [FECHA].

Que contra dicha resolución se interpuso recurso de reposición, el cual fue desestimado por resolución de fecha [FECHA], contra la que se interpuso recurso contencioso-administrativo.

El motivo de la denegación de la solicitud fue el considerar que el solicitante no había «justificado suficiente grado de integración en la sociedad española conforme a lo previsto en el art. 22.4 del Código Civil, al manifestarlo expresamente así el Juez encargado del Registro Civil en auto dedede 20».

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

La competencia para conocer del recurso corresponde a la sala de lo Contencioso-Administrativo de la Audiencia Nacional según lo dispuesto en el art. 11 de la LJCA.

No obstante, para el supuesto que no se entendiera así, procederá que se remitan las actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en el art. 7.3 LJCA.

Legitimación

Está legitimado mi representado en virtud de lo establecido en el art. 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

Plazo de formulación de la demanda

Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

Costas

En lo relativo a la imposición de costas, es de aplicación el art. 139.1 de la LJCA que establece que «En primera o única instancia, el órgano jurisdiccional, al dictar sentencia o al resolver por auto los recursos o incidentes que ante el mismo se promovieren, impondrá las costas a la parte que haya visto rechazadas todas sus pretensiones, salvo que aprecie y así lo razone, que el caso presentaba serias dudas de hecho o de derecho».

El fondo de la cuestión se refiere a determinar si la Administración interpretó correctamente en el presente caso el concepto de «suficiente grado de integración».

Tradicionalmente, (sirva como ejemplo la Sentencia del TS de 9 de abril de 2007) el criterio que fundamenta con mayor frecuencia los informes negativos sobre la integración en la sociedad española ha sido el conocimiento de la lengua castellana.

En el presente caso, sin embargo, no se ha cuestionado en ningún momento de procedimiento que el solicitante no hable o comprenda de forma suficiente el castellano, sino que la supuesta falta de integración se fundamenta en la entrevista realizada por el Juez encargado del Registro Civil, de la cual no consta acta en el expediente administrativo, por lo que no es posible conocer cuales fueron las preguntas formuladas ni la extensión de la misma.

Pues bien, en el presente caso, además del conocimiento del castellano, que debe presumirse toda vez que no se ha cuestionado dicho conocimiento en ningún momento, concurrían las siguientes circunstancias favorables a la concesión de la nacionalidad española por residencia al solicitante:

– El solicitante habla y escribe correctamente el castellano
– El solicitante acreditó carecer de antecedente penales en su país de origen y en España.
– El solicitante acreditó haber desempeñado regularmente trabajos remunerados desde que obtuvo autorización de residencia y trabajo en España, como se acredita mediante la copia del certificado de vida laboral que se adjunta con el presente escrito (Doc. 1)..
– El/La solicitante está casado con D./Dña. [NOMBRE Y APELLIDOS], quien ha obtenido la nacionalidad española por residencia, y con la que tiene una hija. A efectos de prueba, se adjunta copia de libro de familia, D.N.I. del D./Dña. [NOMBRE Y APELLIDOS] y certificado del Consulado General de - en España (Doc. 2, 3 y 4).
– El/La recurrente solicitó la cancelación de sus antecedentes policiales, siéndole concedida su petición mediante resolución de 28 de noviembre de 20, copia de la cual se adjunta al presente escrito (Doc. 5).
– El/la recurrente ha colaborado de forma voluntaria con una asociación de ayuda a inmigrantes durante más de tres años, según se acredita mediante certificado de la Asociación XXXX, que se adjunta al presente escrito (Doc. 6)
– Para la obtención de su autorización de residencia por arraigo, el/la recurrente debió acudir a unos cursos obligatorios organizados por la Comunidad de Madrid, tras los cuales se le expidió el correspondiente informe de integración social favorable. Se adjunta copia de los diplomas otorgados por la asistencia a dichos cursos y del informe favorable de integración social (Doc. 7)

La Sentencia de la Audiencia Nacional de dieciocho de septiembre de dos mil catorce, en un caso similar al presente, estableció lo siguiente:

«Dicho lo anterior, en el caso de autos NO se reflejan las preguntas y respuestas, aun por referencia, que sirvieron al Juez encargado de Getafe para la alcanzar la conclusión desfavorable expuesta en su trascripción literal en el fundamento jurídico antecedente, que es en la que, finalmente y por referencia, se basa la resolución impugnada, con lo cual, pese a la relevancia de la conclusión del Encargado derivada de la inmediación, no podemos afirmar que las preguntas formuladas respondan a un nivel básico mínimamente aceptable atendiendo a las circunstancias del caso siendo de destacar que en el informe no se cuestiona el conocimiento institucional básico sino de "la cultura e historia de nuestro país" y con alusión a una no supuesta adaptación a "las costumbres y modo de ser específicamente españoles" ignorándose a qué nivel fue examinado el recurrente (varón, nacido en 1971, casado con nacional marroquí con la que tiene tres hijos, con vivienda en propiedad, en situación de desempleo cuando se produce la solicitud y con residencia legal desde 1999 gozando de una autorización de residencia de permanente desde 1-3-2004) ni sobre que premisas se hizo descansar el modo de ser específicamente español que sirvió de criterio de contraste. No en vano, el Ministerio Fiscal no se opuso.

Frente a ello vemos que se ha acreditado la existencia de una familia con hijos menores establecida en España y con una residencia legal mantenida de forma intachable desde 1999. Por ello no podemos hablar sin más de que por parte del recurrente exista desconocimiento, desinterés o desvinculación con la realidad del Estado cuya nacionalidad pretende obtener, concurriendo circunstancias que vendrían a apoyar la efectividad del arraigo e integración cuestionados frente a un informe que, por su carácter general y apodíctico, aparece como inmotivado en la base de la conclusión desfavorable a la que llega, trasmitiendo este vicio a la resolución que lo acoge como razón única de la denegación de la nacionalidad».

Razonamientos que consideramos plenamente aplicables al caso de mi representado y que deberían llevar, como en el caso de la Sentencia citada, a estimar el recurso y reconocer su integración en la sociedad española en un grado más que suficiente para la concesión de la nacionalidad española solicitad.

En su virtud SUPLICO A LA SALA que tenga por formalizada la demanda en el procedimiento referenciado y previos los trámites procesales oportunos dicte sentencia por la que se revoque la resolución recurrida declarando el derecho del recurrente a que le sea concedida la nacionalidad española por residencia con efectos desde la fecha de solicitud de la misma, condenando en costas a la administración demandada.

Por ser Justicia que pido en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

OTROSI DIGO que se estima que la cuantía del recurso es indeterminada, al constituir el objeto del mismo la impugnación de un acto administrativo que no tiene cuantía.

En su virtud SUPLICO A LA SALA que se fije la cuantía del recurso en indeterminada.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSÍ DIGO que de conformidad con el artículo 60 LJCA solicito el recibimiento a prueba del presente recurso, con la finalidad de acreditar los siguientes hechos:

1. Que el recurrente, en contra de lo expuesto en la resolución recurrida, tiene un elevado grado de integración en España, superior a la media de la población extranjera residente en nuestra sociedad.

Se proponen para ello los siguientes MEDIOS DE PRUEBA:

1.DOCUMENTAL, consistente en que se tengan por reproducidos los documentos aportados con el presente escrito.

2.TESTIFICAL, para la cual deberán citarse los siguientes testigos:

– D. [NOMBRE Y APELLIDOS] presidente de la comunidad de vecinos de [COMPLETAR]
– D. [NOMBRE Y APELLIDOS], presidente de la Asociación de ayuda a inmgirantes XXX

En su virtud, SUPLICO A LA SALA que tenga por solicitado el recibimiento a prueba, y por propuestos los medios de prueba, acordando lo procedente.

Por ser Justicia que reitero en lugar y fecha ut supra.

Fdo.: Procurador/a	Fdo.: Abogado/a
