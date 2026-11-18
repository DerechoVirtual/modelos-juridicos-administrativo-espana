---
name: nulidad-acto-vulnera-derechos-susceptibles-amparo-156
description: "Redacta el escrito «Nulidad de acto que vulnera derechos susceptibles de amparo constitucional» (formulario 156 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de acto que vulnera derechos susceptibles de amparo constitucional

> Formulario 0156 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO O PERSONA (3 veces)
- [ ] FECHA (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] DESCRIBIR (5 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…continuación literalmente se transcribe:»; «…ncias que concurren en el caso presente:»; «… y perjuicios económicos, por cuanto que»; «… que resultan manifiestas por cuanto que»; «…cos de esa Administración por cuanto que»; «… consistente en incorporar al expediente»; «…da: consistente en aportar al expediente»; «…consistente en que por perito competente»; «…ente en contestar al pliego de preguntas»; «… reconocimiento: consistente en examinar»

## Párrafos opcionales (9)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTROSÍ DIGO:…
- SEGUNDO OTROSÍ DIGO:…
- TERCER OTROSÍ DIGO:…
- A) Documental pública: consistente en incorporar al expediente [COMPLETAR].…
- B) Documental privada: consistente en aportar al expediente [COMPLETAR].…
- C) Prueba pericial: consistente en que por perito competente [COMPLETAR].…
- D) Prueba testifical: consistente en contestar al pliego de preguntas [COMPLETAR].…
- E) Prueba de reconocimiento: consistente en examinar [COMPLETAR].…
- F) Otros medios de prueba: consistentes en [DESCRIBIR].…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 3, 4 y 106.1 de la Ley 39/2015
- artículo 106 LPACAP
- artículo 47.1 LPACAP
- artículo 106.1 LPACAP
- artículo 47 LPACAP
- artículo 24.1 de la Constitución
- artículos 35 y 88.3 LPACAP
- artículos 9 y 103 de la Constitución
- artículo 106.4 LPACAP
- artículo 77.2 LPACAP

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

### Formulario 0156 · Nulidad de acto que vulnera derechos susceptibles de amparo constitucional

- Año del modelo: 2017
- Revisión 17-11-2026: 9 párrafos opcionales señalados; 36 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL [ÓRGANO AL QUE SE DIRIGE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.].

Ante ese órgano administrativo comparezco (Código de identificación núm. [NÚMERO]) y, con el debido respeto, como mejor proceda,

DIGO:

Que, en el ejercicio de los derechos e intereses legítimos que me asisten en calidad de interesado, por medio del presente escrito vengo a ejercitar la ACCIÓN DE NULIDAD contra la resolución adoptada por [ÓRGANO O PERSONA], en fecha [FECHA], en el procedimiento administrativo relativo expediente núm. [Nº DE PROCEDIMIENTO] sobre [DESCRIBIR], por encontrar que la citada resolución no es conforme a Derecho, sobre la base de los hechos y consideraciones jurídicas que fundamentan los siguientes,

MOTIVOS RAZONADOS DE IMPUGNACIÓN

Primero.- Con fecha [FECHA], por esa Administración Pública, en el procedimiento relativo a [DESCRIBIR], se dictó la resolución que agotó la vía administrativa, que a continuación literalmente se transcribe: [COMPLETAR].

Segundo.- La citada resolución administrativa es nula de pleno Derecho, como lo acreditan las siguientes circunstancias que concurren en el caso presente: [COMPLETAR].

Tercero.- Que, según se acredita mediante el informe pericial aportado, la irregular forma de actuar de esa Administración ha producido elevados daños y perjuicios económicos, por cuanto que [COMPLETAR], perfectamente evaluables que ascienden al importe total de [IMPORTE] euros, y que esta parte no tiene el deber jurídico de soportar de acuerdo con la Ley.

Cuarto.- La documentación acreditativa sobre la veracidad de los hechos, adjunto se acompaña debidamente foliada y numerada.

A los anteriores hechos son de aplicación los siguientes,

FUNDAMENTOS JURÍDICOS

I. Sobre la admisibilidad del procedimiento

• De la personalidad y legitimación del solicitante: conforme con lo establecido en los artículos 3, 4 y 106.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP), ostento legitimación suficiente para formular la presente solicitud de nulidad en el referido procedimiento del que soy titular de un derecho subjetivo o interés legítimo conculcado por el acto administrativo cuya nulidad se solicita.

• De la competencia del órgano para conocer el procedimiento: la competencia para resolver el presente procedimiento de revisión fundado en causa de nulidad corresponde al titular de esa Administración en su calidad de administración actuante a la que nos dirigimos, de conformidad con lo previsto en el artículo 106 LPACAP, que reconoce a la Administración la facultad de declarar por ella misma la nulidad de los actos que hayan puesto fin a la vía administrativa o no hayan sido recurridos en el plazo legal establecido, siempre que incurran en alguno de los supuestos de nulidad previstos en el artículo 47.1 LPACAP.

• Del plazo para formular la petición de nulidad: según el referido artículo 106.1 LPACAP, la nulidad de los actos de la Administración podrá declararse "en cualquier momento", aunque hayan transcurrido los plazos para impugnar el acto por la vía de los recursos administrativos, ya que no se da ninguna de las circunstancias previstas en el artículo 106 del indicado texto legal que impidan el ejercicio de la potestad de revisión.

Todos los anteriores requisitos se cumplen en el presente caso, por lo que procede entrar a conocer sobre las cuestiones de fondo planteadas que a continuación se detallan:

II. En cuanto al fondo del asunto

Primero.- La resolución administrativa cuya declaración de nulidad absoluta se solicita ha incurrido en graves y manifiestas infracciones legales, constitutivas de causa de nulidad de pleno Derecho, previstas en el artículo 47 LPACAP, en relación con [DESCRIBIR], por lo que es de interés público su revisión y expulsión del ordenamiento jurídico. En efecto, en la referida resolución adoptada por [ÓRGANO O PERSONA], en fecha [FECHA], concurren los siguientes motivos de nulidad absoluta o de pleno Derecho:

Lesión de derechos y libertades susceptibles de amparo constitucional:

Con carácter previo, cabe señalar, que la resolución impugnada ha provocado una auténtica situación de indefensión legal y material en los derechos e intereses legítimos de esta parte, vulnerando la garantía del derecho a la defensa constitucionalmente reconocida en el artículo 24.1 de la Constitución, susceptible de amparo constitucional, de acuerdo con lo establecido en el artículo 53 de nuestra Carta Magna. En efecto, la falta de motivación de la resolución impugnada ha provocado una auténtica indefensión al no poder llegar a conocer las razones lógicas y jurídicas que determinaron su adopción, conforme exigen los artículos 35 y 88.3 LPACAP. Las consecuencias jurídicas de dicha falta de motivación constituye un vicio de nulidad o, en su caso, de anulabilidad de la resolución adoptada, como ha puesto de manifiesto la jurisprudencia del Tribunal Supremo y el Constitucional en numerosas sentencias.

Además, en la tramitación del procedimiento se han producido las siguientes infracciones de rango constitucional insubsanables, que resultan manifiestas por cuanto que [COMPLETAR].

Dichas exigencias procedimentales de rango constitucional de inexcusable observancia conllevan a que la citada resolución administrativa incurra en causa de nulidad prevista en letra a) del artículo 47 LPACAP. De modo y manera, que es de interés público el restablecimiento del ordenamiento jurídico con la depuración de dicha resolución y, en consecuencia, procede sin más declarar su nulidad de pleno Derecho.

Segundo.- En definitiva, el sometimiento pleno de la Administración Pública al principio de legalidad, impuesto por los artículos 9 y 103 de la Constitución, exige que el contenido de sus actos se ajuste al ordenamiento jurídico y sea adecuado a los fines públicos perseguidos, y constituye un deber reglado de la Administración --y, no una mera facultad-- que requiere una reacción enérgica para depurar el ordenamiento jurídico-administrativo, sobre todo ante la presencia de los actos nulos de pleno derecho. Por ello, las causas de nulidad absoluta están sancionadas como infracción del tipo más grave y notorio que la Administración pueda cometer, y obligan a declarar necesariamente la nulidad del acto viciado, puesto que cuando un acto es nulo, lo es para todo el mundo que pueda verse afectado sin necesidad de previa declaración de nulidad (efectos erga omnes) y desde la fecha en que el acto se dictó (efectos ex tunc). Además, conviene recordar que la nulidad absoluta o radical, aquí denunciada, no puede ser sanada por convalidación posterior de la Administración, ni está sujeta a la prescripción de la acción por límite temporal alguno: es imprescriptible. El acto administrativo que nace nulo queda así durante todo el tiempo que produzca efectos, dado que el acto es siempre nulo. Esta es la respuesta que da nuestro ordenamiento jurídico-administrativo para las infracciones de esta índole cometidas por las Administraciones Públicas.

III. Respecto a la indemnización de daños y perjuicios

El artículo 106.4 LPACAP preceptúa que: "Las Administraciones públicas, al declarar la nulidad de una disposición o acto, podrán establecer, en la misma resolución, las indemnizaciones que proceda reconocer a los interesados, si se dan las circunstancias previstas en los artículos 32.2 y 34.1 de la Ley de Régimen Jurídico del Sector Público sin perjuicio de que, tratándose de una disposición, subsistan los actos firmes dictados en aplicación de la misma".

Ciertamente no toda anulación de un acto o disposición es susceptible de generar responsabilidad patrimonial, pero no es menos cierto que de acuerdo con la expresada Ley se reconoce a los ciudadanos el derecho a ser resarcidos por toda lesión que sufran en cualquiera de sus bienes o derechos, salvo los casos de fuerza mayor, siempre que la lesión sea consecuencia del funcionamiento de los servicios públicos y no tengan el deber jurídico de soportar la lesión producida.

Sin duda, la resolución administrativa cuya nulidad se solicita ha producido un resultado lesivo efectivo, evaluable económicamente e individualizado, en los derechos e intereses legítimos de esta parte, por cuanto que resulta evidente e inequívoca la relación causal de la antijuridicidad del resultado o lesión producido a consecuencia del funcionamiento de los servicios públicos de esa Administración por cuanto que [COMPLETAR], y cuyos perjuicios perfectamente cuantificables no tengo el deber ni la obligación jurídica de soportar (como lo acredita el informe pericial emitido por técnico competente que se aporta), por lo que procede que así se reconozca y acuerde la correspondiente indemnización para el resarcimiento de los daños y perjuicios producidos por esa Administración responsable a la que nos dirigimos.

Por todo ello, y en su atención, es por lo que,

SOLICITO

Que habiendo presentado este escrito junto con la documentación que se acompaña, se sirva admitirlo y, en su virtud, tener por ejercida la ACCIÓN DE NULIDAD contra la resolución adoptada por [ÓRGANO O PERSONA], de fecha [FECHA], en el procedimiento administrativo relativo al expediente núm. [NÚMERO], sobre [DESCRIBIR] y, por las razones expuestas, se declare nula de pleno derecho y, como consecuencia derivada, se revoque y deje sin efecto dicha resolución administrativa.

[OPCIONAL — incluir si procede]

PRIMER OTROSÍ DIGO:

Que, por razones de eficacia y celeridad administrativa, en la misma resolución por la que declare la nulidad absoluta de la resolución impugnada se reconozca a esta parte el DERECHO A LA INDEMNIZACIÓN de [IMPORTE] euros, por los daños y perjuicios producidos en los términos expuestos en el cuerpo este escrito.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSÍ DIGO:

Que, con el fin de evitar perjuicios de difícil o imposible reparación que se pudieran producir para el interés público tutelado y en contra los derechos o intereses legítimos de esta parte afectada, en tanto se sustancie el correspondiente procedimiento revisorio, se acuerde la SUSPENSIÓN DE LA EJECUCIÓN de la resolución impugnada, cuya declaración de nulidad de pleno derecho se solicita, demorando la eficacia inmediata del acto recurrido hasta su resolución definitiva, de acuerdo con lo previsto en el artículo 108 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

[OPCIONAL — incluir si procede]

TERCER OTROSÍ DIGO:

Que, subsidiariamente, para el caso de que no se tengan por ciertos los hechos alegados, al amparo de lo previsto en el artículo 77.2 LPACAP, se solicita la apertura de un PERÍODO DE PRUEBA mediante la práctica de los siguientes medios de prueba que se estiman necesarios para resolución de presente procedimiento revisorio:

[OPCIONAL — incluir si procede]

A) Documental pública: consistente en incorporar al expediente [COMPLETAR].

[OPCIONAL — incluir si procede]

B) Documental privada: consistente en aportar al expediente [COMPLETAR].

[OPCIONAL — incluir si procede]

C) Prueba pericial: consistente en que por perito competente [COMPLETAR].

[OPCIONAL — incluir si procede]

D) Prueba testifical: consistente en contestar al pliego de preguntas [COMPLETAR].

[OPCIONAL — incluir si procede]

E) Prueba de reconocimiento: consistente en examinar [COMPLETAR].

[OPCIONAL — incluir si procede]

F) Otros medios de prueba: consistentes en [DESCRIBIR].

En su virtud,

SOLICITO:

Que, en su caso, tenga a bien declarar la proposición de prueba interesada, y acuerde lo procedente para su efectiva práctica.

En [LUGAR], a [FECHA].

Firmado:
