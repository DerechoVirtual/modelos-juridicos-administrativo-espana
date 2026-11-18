---
name: reposicion-disciplinario-falta-tipicidad-hechos-probados-553
description: "Redacta el escrito «Reposición en disciplinario por falta de tipicidad de los hechos probados» (formulario 553 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición en disciplinario por falta de tipicidad de los hechos probados

> Formulario 0553 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…curso de alzada contra la resolución del»; «…el»; «…te el período comprendido entre los días»; «…blicas, LPACAP, contra la resolución del»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 25.1 de la Constitución
- art. 24.2 CE
- art. 25.1 CE
- art. 25.1 de la Constitución
- Ley 39/2015

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

### Formulario 0553 · Reposición en disciplinario por falta de tipicidad de los hechos probados

- Año del modelo: 2011
- Revisión 17-11-2026: 2 llamadas a nota sin texto retiradas; 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS] con DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

actuando en su propio nombre y derecho, ante el [ÓRGANO], órgano competente para resolver el recurso de alzada contra la resolución del [COMPLETAR] por la que se impone a este interesado sanción de sesenta días de suspensión de funciones, comparece y como mejor proceda en Derecho

DICE

PRIMERO.- Con fecha [FECHA] el [COMPLETAR] dicta resolución por la que se me impone sanción de sesenta días de suspensión de funciones, por una falta grave del artículo 152.31 del Reglamento de la Ertzaintza.

El artículo 152.31 del citado Reglamento dispone que "... son faltas graves... aquellas infracciones a las leyes y reglamentos de carácter general que puedan afectar a su condición de policía...". En el presente caso dicho precepto se puso en relación con el contenido del artículo 16 del mismo Reglamento, a cuyo tenor "... El policía deberá dar prueba en todo momento de dignidad y evitar todo comportamiento que pueda significar pérdida de confianza y de la consideración que requieren sus funciones o compromete el prestigio y eficacia del servicio de policía...".

Según la resolución impugnada, a través de este último precepto se da entrada al primero como norma típica en la que subsumir la conducta imputada, consistente, en esencia, en que este recurrente "... estando en situación de incapacidad temporal por el padecimiento de un esguince cervical, durante el período comprendido entre los días [COMPLETAR], ambos inclusive, participó en el Campeonato de Euskadi de Culturismo celebrado el día [FECHA] de ese mismo año...".

SEGUNDO.- Es sobradamente conocida la doctrina emanada del Tribunal Constitucional (entre otras en las sentencias 77/1983, de 3 de octubre, 42/1987, de 7 de abril, 3/1988, de 21 de enero, 101/1988, de 8 de junio, 29/1989, de 6 de febrero, 69/1989, de 20 de abril, 219/1989, de 21 de diciembre, etc., según la cual el artículo 25.1 de la Constitución incorpora al repertorio de derechos fundamentales la regla "nullum crimen, nulla poena sine lege", para que opere no solo en el ámbito del Derecho Penal en estricto sentido sino también en el del ordenamiento sancionador administrativo. Los principios inspiradores del orden penal son de aplicación, con ciertos matices, en el ámbito del Derecho administrativo sancionador, dado que ambos son manifestaciones del ordenamiento punitivo del Estado. Ya desde la STC 18/1981, el Tribunal Constitucional ha señalado que las garantías procesales establecidas en el art. 24.2 CE son aplicables, además de en el proceso penal, en los procedimientos administrativos sancionadores, con las matizaciones que resultan de su propia naturaleza, en cuanto que en ambos casos son manifestaciones de la potestad punitiva del Estado (STC 145/1993).

De ella, añade dicha doctrina, se deriva una doble garantía: la primera (única que interesa en este recurso) de orden material y alcance absoluto, tanto por lo que se refiere al ámbito estrictamente penal como al de las sanciones administrativas, refleja la especial trascendencia del principio de seguridad en dichos ámbitos limitativos de la libertad individual y se traduce en la imperiosa exigencia de predeterminación normativa de las conductas ilícitas y de las sanciones correspondientes. Sólo queda cumplida tal exigencia de tipicidad cuando la norma se formula con la suficiente precisión, tanto en la definición de la conducta constitutiva de la infracción, como en la definición de la sanción que pueda imponerse, de manera tal que el ciudadano pueda prever, con suficiente grado de certeza, aquéllas y éstas. La segunda, de carácter formal, se refiere al rango necesario de las normas tipificadoras de aquellas conductas y reguladoras de estas sanciones, por cuanto como este Tribunal ha señalado reiteradamente, el término "legislación vigente" contenido en dicho art. 25.1 es expresivo de una reserva de ley en materia sancionadora.

El mandato de tipificación o principio de tipicidad exige pues una predeterminación normativa de las conductas ilícitas y de las sanciones correspondientes ("lex previa"), y que tal predeterminación permita prever, predecir, con suficiente grado de certeza unas y otras ("lex certa").

TERCERO.- Profundizando aún más en la doctrina jurisprudencial recaída en torno al principio de tipicidad, conviene ahora recordar, de un lado, la afirmación del propio Tribunal Constitucional (Sentencias 69/1989, de 20 de abril, 219/1989, de 21 de diciembre y 116/1993, de 29 de marzo) conforme a la cual el art. 25.1 CE no impide el empleo en la norma típica de conceptos jurídicos indeterminados, pero siempre que con ello quede en pie la posibilidad real y cierta de que la concreción de las conductas infractoras y sus sanciones sea razonablemente factible en virtud de criterios lógicos, técnicos o de experiencia, de tal forma que aquel empleo permita prever, con suficiente seguridad, la naturaleza y las características esenciales de unas y otras. Y de otro lado, la afirmación de que tampoco vulnera la exigencia que nos ocupa la remisión que el precepto que tipifica las infracciones realice a otras normas que impongan deberes u obligaciones concretas de ineludible cumplimiento, de forma que su conculcación se asuma como elemento definidor de la infracción sancionable misma; pero ello, de nuevo, siempre que sea asimismo previsible, con suficiente grado de certeza, la consecuencia punitiva derivada de aquel incumplimiento o transgresión; afirmándose en este sentido como insuficientes para satisfacer las exigencias derivadas del principio de tipicidad las fórmulas omnicomprensivas, entendiendo por tales las que consideran infracción cualquier incumplimiento de la normativa toda de un determinado sector del ordenamiento cuyo objeto sea, sin embargo, más amplio que el de la mera regulación de conductas merecedoras de sanción en estricto sentido.

A la luz de tal doctrina, no se puede afirmar que el transcrito artículo 152.31 del Reglamento de la Ertzaintza satisfaga las exigencias del principio de tipicidad. En él se construye el tipo a través de una fórmula omnicomprensiva que abarcaría en su radio de acción todas las conductas contrarias a cualesquiera mandatos contenidos en leyes y reglamentos de carácter general, con la sola concreción de que se trate de disposiciones que puedan afectar a su condición de policía; no se hace distinción, discriminación o matiz alguno que atienda ni al contenido ni a la importancia de la regulación sustantiva infringida; y se emplean conceptos tales como el del carácter general de la ley o reglamento, o el de la condición de policía, que en nada favorecen el fin de previsibilidad a que ha de atender la norma típica.

En todo caso, aun cuando llegara a entenderse que tal precepto reglamentario no infringe el mandato que se deriva del artículo 25.1 de la Constitución, en el caso enjuiciado el Reglamento de la Ertzaintza, y por tanto su artículo 16, en cuanto norma específica con unos singulares destinatarios, no constituye un reglamento de carácter general en el sentido en que este concepto es empleado en la norma típica aplicada, ni, por ende, la infracción de aquél se subsume en el supuesto previsto en esa norma típica. En definitiva, la subsunción de la conducta imputada en la norma sancionadora aplicada no resulta conforme a derecho, tanto por razón de que dicha norma no satisface las exigencias del principio de tipicidad, como por razón, en último término, de que en el tipo que describe no encaja la concreta conducta realizada.

CUARTO.- El principio de tipicidad supone la necesidad de que, para que un comportamiento determinado pueda ser sancionado, sea exigible que la conducta realizada pueda integrarse o subsumirse, sin analogía "in malam partem" alguna, en un tipo previamente descrito y en que se cumplan, por otra parte, todos los elementos integrantes del mismo. En otras palabras, la exigencia de la salvaguarda del principio de tipicidad supone tanto como desplazar del ámbito sancionador todas aquellas conductas que no sean incardinables en la previsión de la norma y aun a pesar de su aparente antijuridicidad en relación con los propios límites del tipo. Es pues desde esta perspectiva desde la que ha de acometerse el análisis, pues la coincidencia de una conducta con el supuesto de hecho de una norma tipificante es una condición esencial de los hechos determinantes de la sanción, de modo que su inexistencia provoca indefectiblemente la ilegalidad de la resolución en que la misma sea de observar.

Y todo lo dicho, teniendo en cuenta que el alcance de dicha reserva de Ley pierde parte de su fundamentación en el seno de las relaciones de sujeción especial, aunque incluso en dicho ámbito una sanción carente de toda base legal devendría lesiva del derecho fundamental que reconoce el art. 25.1 de la Constitución.

En virtud de lo expuesto,

SOLICITA

Que se tenga por interpuesto el presente Recurso de reposición, de acuerdo con los arts. 121 y ss. de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, LPACAP, contra la resolución del [COMPLETAR] de fecha [FECHA] por la que se impone a este recurrente sanción de sesenta días de suspensión de funciones, y se resuelva la anulación de dicha sanción de acuerdo con los fundamentos expuestos en este escrito.

En [LUGAR], a [FECHA].

Firma:
