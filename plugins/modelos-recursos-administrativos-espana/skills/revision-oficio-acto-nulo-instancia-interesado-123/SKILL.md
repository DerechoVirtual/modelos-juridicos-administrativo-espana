---
name: revision-oficio-acto-nulo-instancia-interesado-123
description: "Redacta el escrito «Revisión de oficio de un acto nulo a instancia del interesado» (formulario 123 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión de oficio de un acto nulo a instancia del interesado

> Formulario 0123 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] FECHA (4 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…entes que concurren en el caso presente:»; «…l en una Ley especial: En efecto, la Ley»; «…ental Pública: consistente en incorporar»; «…cumental Privada: consistente en aportar»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 106.1 de la Ley 39/2015
- artículos 14 a 29 de la Constitución
- art. 106 CE

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

### Formulario 0123 · Revisión de oficio de un acto nulo a instancia del interesado

- Año del modelo: 2017
- Revisión 17-11-2026: 2 rangos de artículos despegados («25 a31» → «25 a 31»); 23 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al órgano administrativo competente

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.],

comparezco y, como mejor proceda en Derecho,

DIGO:

Que, mediante el presente escrito vengo a ejercitar la ACCIÓN DE NULIDAD contra el acto resolutorio dictado por [ÓRGANO O PERSONA], en fecha [FECHA], en el procedimiento administrativo relativo a [DESCRIBIR], de conformidad con el art. 106.1 de la Ley 39/2015 del Procedimiento Administrativo Común de las Administraciones Públicas, en base a los siguientes

HECHOS

PRIMERO.- Con fecha [FECHA], por esta Administración en el procedimiento sobre [DESCRIBIR], se dictó el acto que puso fin a la vía administrativa que a continuación literalmente se transcribe: "" (se adjunta copia de la notificación practicada como documento núm. 1).

SEGUNDO.- Que la citada resolución administrativa es nula de pleno Derecho, como lo acreditan las circunstancias siguientes que concurren en el caso presente: [COMPLETAR].

TERCERO.- Según se acredita mediante informe pericial (que se acompaña como documento núm. 2) la ilegal forma de actuar de esa Administración ha irrogado a esta parte interesada cuantiosos daños y perjuicios económicos perfectamente evaluables que ascienden a la cantidad total de [IMPORTE] euros, y que esta parte no tiene el deber jurídico de soportar, de acuerdo con la Ley.

FUNDAMENTOS DE DERECHO

I. SOBRE LA ADMISIBILIDAD DEL PROCEDIMIENTO

PRIMERO.-De la personalidad y legitimación del solicitante: conforme con lo establecido en los artículos 3, 4 y 106.1 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, ostento legitimación suficiente para formular la presente la solicitud de nulidad en el referido procedimiento del que soy titular de un derecho subjetivo o interés legítimo conculcado con el acto cuya nulidad se solicita.

SEGUNDO.-De la competencia del órgano para resolver y del procedimiento que ha de seguirse: la competencia para instruir y resolver el presente procedimiento de revisión fundado en causa de nulidad corresponde al titular de esa Administración en su calidad de administración actuante a la que nos dirigimos, de conformidad con lo previsto en el art. 106 de la referida Ley del Procedimiento Administrativo, que reconoce a la Administración la facultad de declarar por ella misma la nulidad de los actos declarativos d derechos o favorables que incurran en alguno de los supuestos de nulidad previstos en el artículo 47.1 de dicho texto legal.

TERCERO.-Del plazo para formular la petición de nulidad: según el referido artículo 106.1 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, la nulidad de los actos de la Administración podrá declararse "en cualquier momento", aunque hayan transcurrido los plazos para impugnar el acto por la vía de los recursos administrativos, ya que no se da ninguna de las circunstancias previstas en el artículo 110 de dicho texto legal que impidan el ejercicio de la potestad de revisión.

II SOBRE EL FONDO DE LOS MOTIVOS DE NULIDAD

CUARTO.- En cuanto al fondo del asunto, el acto administrativo cuya declaración de nulidad absoluta se solicita ha incurrido en graves y manifiestas infracciones legales, por lo que debe ser revisado y expulsado de nuestro ordenamiento jurídico. En efecto, en el presente caso concurren los motivos de nulidad previstos en el artículo 47 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, siguientes:

1. Lesión de derechos y libertades susceptibles de amparo constitucional: previstos en los artículos 14 a 29 de la Constitución y la objeción de conciencia, como es el de
2. Incompetencia manifiesta: el acto ha sido dictado por órgano manifiestamente incompetente por razón de la materia o del territorio. En efecto, sin ningún género de dudas, se evidencia la falta de legitimidad del órgano para dictar el acto
3. Acto de contenido imposible: por lo que dicha imposibilidad material invalida el efecto práctico que con dicho ato se pretende obtener, como lo demuestra el hecho de que
4. Acto constitutivo de infracción penal: al existir una relación directa entre la infracción penal y el dictado del acto administrativo, como lo acredita la sentencia dictada en el procedimiento penal en la que se declara la comisión del delito o delito leve cometido, que se adjunta.
5. Acto dictado sin seguirse el procedimiento legal establecido: por haberse prescindido total y absolutamente del procedimiento legalmente establecido para ello, mediante un procedimiento distinto al expresamente regulado para el presente supuesto, como lo acreditan las consideraciones siguientes
6. Acto expreso o presunto contario al ordenamiento por el que se adquieren facultades o derechos careciendo de los requisitos esenciales para su adquisición: puesto que el acto favorable no es conforme a Derecho por constituir una infracción sustancial a la Ley que le es de aplicación al caso para el otorgamiento de tal facultad o derecho, como es
7. Acto tipificado expresamente de nulidad radical en una Ley especial: En efecto, la Ley [COMPLETAR], como ley específicamente aplicable al caso, tipifica como un supuesto de nulidad de pleno Derecho la infracción cometida por el acto cuya declaración de nulidad se solicita.
8. Acto de aplicación singular de un reglamento ilegal: como lo demuestra el hecho perfectamente constatable de que la norma o disposición de carácter general en la que se fundamenta el acto administrativo cuya declaración de nulidad se insta, contraviene de manera grave y manifiesta lo establecido en la Ley formal que le es de aplicación. Disposición reglamentaria ésta que por el principio de jerarquía normativa reconocido en la Constitución, no puede vulnerar o derogar lo dispuesto en una norma con rango de Ley. Esta sanción de nulidad de pleno Derecho responde a la posibilidad de recurso directo o indirecto frente a las disposiciones de carácter general y la, en su caso, consecuente cuestión de ilegalidad que se regula en los artículos 26, 27 y 123 a 126 de la Ley Reguladora de la Jurisdicción Contencioso-Administrativa.

III. SOBRE LA INDEMNIZACIÓN DE DAÑOS Y PERJUICIOS

QUINTO.- El artículo 106.4 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, preceptúa: "Las Administraciones públicas, al declarar la nulidad de una disposición o acto, podrán establecer, en la misma resolución, las indemnizaciones que proceda reconocer a los interesados, si se dan las circunstancias previstas en los arts. 32.2 y 34.1 de la Ley de Régimen Jurídico del Sector Público; sin perjuicio de que, tratándose de una disposición, subsistan los actos firmes dictados en aplicación de la misma". Ciertamente, no toda anulación de un acto o disposición es susceptible de generar responsabilidad patrimonial, pero no es menos cierto que, de acuerdo con el art. 106 CE, se reconoce a los ciudadanos el derecho a ser indemnizados por toda lesión que sufran en cualquiera de sus bienes o derechos, salvo los casos de fuerza mayor, siempre que la lesión sea consecuencia del funcionamiento de los servicios públicos. Por consiguiente, dado que el acto cuya nulidad se solicita ha producido un resultado lesivo efectivo, evaluable económicamente e individualizado sobre mi patrimonio, cuyos perjuicios perfectamente cuantificables no tengo el deber ni la obligación jurídica de soportar por el daño experimentado (como lo acredita el informe pericial emitido al efecto que se adjunta), es por lo que procede que así se reconozca por esa Administración responsable a la que nos dirigimos.

En virtud de lo expuesto, y de conformidad con lo establecido en la Ley del Procedimiento Administrativo Común de las Administraciones Públicas,

SOLICITO QUE:

Primero.- Admita el presente escrito y, previos los actos de instrucción que sean necesarios, en especial la audiencia a los interesados y el previo dictamen favorable del Consejo de Estado u órgano consultivo equivalente de la Comunidad Autónoma, se dicte resolución por la que se declare la nulidad del acto resolutivo dictado por [ÓRGANO O PERSONA], en fecha [FECHA], sobre el procedimiento de referencia.

Segundo.- En la misma resolución por la que se declare el acto nulo solicitado se reconozca a esta parte del derecho a la indemnización de [IMPORTE] euros (con los importes adicionales correspondientes a las partidas no evaluadas en el presente escrito, aunque sí reseñadas), por los daños y perjuicios producidos en los términos expuestos en los antecedentes de este escrito.

Tercero.- De acuerdo con lo dispuesto en el artículo 108 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, insto la suspensión de la ejecución del acto cuya declaración de nulidad se solicita, dados los perjuicios de imposible o difícil reparación que el mismo puede producir en contra de mis derechos o intereses legítimos.

Cuarto.- Se admitan a trámite y se proceda a la práctica de los siguientes medios de prueba, para acreditar los hechos y fundamentos expuestos en el presente escrito:

A) Documental Pública: consistente en incorporar [COMPLETAR]
B) Documental Privada: consistente en aportar [COMPLETAR]
C) Otros medios de prueba: consistentes en [DESCRIBIR]

En [LUGAR], a [FECHA].

Firmado:
