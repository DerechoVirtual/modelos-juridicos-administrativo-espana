---
name: alegaciones-usar-navegador-detector-radares-304
description: "Redacta el escrito «Alegaciones por usar navegador con detector de radares» (formulario 304 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones por usar navegador con detector de radares

> Formulario 0304 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] CALLE (4 veces)
- [ ] NÚMERO (4 veces)
- [ ] C.P. (4 veces)
- [ ] DNI/NIE (4 veces)
- [ ] Nº DE EXPEDIENTE (2 veces)
- [ ] ÓRGANO
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] PUNTO KILOMÉTRICO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A»; «…DE»; «…, número [NÚMERO], CP [C.P.], de»; «…horas, en la Carretera»; «…, con dirección a»; «…, que se adjunta, en el que se acredita»; «…, número [NÚMERO], CP [C.P.], de»; «…, número [NÚMERO], CP [C.P.], de»; «…, número [NÚMERO], CP [C.P.], de»; «…n virtud de todo lo expuesto, SOLICITO A»; «…DE»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 18 del Real Decreto 1428/2003
- art. 13.6 del Real Decreto Legislativo 6/2015
- artículo 5 del Real Decreto 320/1994
- arts. 87 y 88 del Real Decreto Legislativo 6/2015
- artículo 27 de la Ley 40/2015
- art. 95 del Real Decreto Legislativo 6/2015
- Ley 18/2021

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

### Formulario 0304 · Alegaciones por usar navegador con detector de radares

- Año del modelo: 2013
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 35 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A [COMPLETAR] DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en la C/ [CALLE], número [NÚMERO], CP [C.P.], de [COMPLETAR], y provisto de DNI número [DNI/NIE] según consta en el Expediente administrativo sancionador número [Nº DE EXPEDIENTE], ante [ÓRGANO], comparezco y, como mejor proceda en derecho,

DIGO:

Que con fecha [FECHA] se ha formulado en mi contra denuncia a las [Nº] horas, en la Carretera [COMPLETAR], kilómetro [PUNTO KILOMÉTRICO], con dirección a [COMPLETAR], que ha dado lugar a la incoación del Expediente número [Nº DE EXPEDIENTE], por una presunta infracción del artículo 18 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación, y no estando conforme con la misma, dentro del plazo conferido y en forma legal, en aplicación del art. 95 de la Ley de Tráfico, por medio del presente escrito formulo las siguientes

ALEGACIONES

Se nos imputa circular utilizando un navegador con detección de radares para eludir la vigilancia de los agentes de tráfico, lo cual es incierto, y no se concreta en la denuncia ninguna de las circunstancias concurrentes.

El modelo de navegador utilizado está homologado y no vulnera las previsiones efectuadas en el art. 13.6 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial ni el artículo 18 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación.

Que los hechos, tal y como verdaderamente acaecieron, fueron los siguientes:

El artículo 5 del Real Decreto 320/1994, de 25 de febrero, que aprueba el Reglamento del procedimiento sancionador en materia de tráfico, en relación con los arts. 87 y 88 del Real Decreto Legislativo 6/2015, de 30 de octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial), establece que en las denuncias por hechos de circulación deberá constar una relación sucinta del hecho, con expresión del lugar o tramo, fecha y hora, y el nombre, y domicilio del denunciante salvo si fuera un Agente de la Autoridad que deberá facilitar su número de identificación profesional.

En el presente caso no se concreta ni describe ninguna acción u omisión merecedora de sanción, sino que en el boletín de denuncia se copia el texto del precepto que se dice infringido, vulnerando el principio de seguridad jurídica del administrado, pues no se puede sancionar por hechos genéricos o abstractos, sino que éstos han de venir claramente concretados y además ha de probarse debidamente la presunta infracción cometida.

La Administración hace una interpretación extensiva de la norma sancionadora, ya que los hechos presuntamente cometidos no están descritos en el tipo que sirve de fundamento al presente expediente, infringiendo, además, el artículo 27 de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público, el cual establece que sólo constituyen infracciones administrativas las vulneraciones del Ordenamiento Jurídico previstas como tales infracciones por una Ley, y expresamente prohíbe, en su número 4, la aplicación analógica de las normas definidoras de infracciones y sanciones. En el presente caso, el dispositivo no consiste ni en un inhibidor de radar o cinemómetro ni tampoco un detector de los mismos. El modelo en cuestión solo aisa de la posición de los sistemas de vigilancia del tráfico y esto está amparado por el art. 13.6 de la Ley de Tráfico ya citada, en su redacción dada por la Ley 18/2021.

Que con el fin de acreditar lo narrado en los ordinales anteriores, y al amparo del art. 95 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, interesa al derecho de esta parte se practiquen los siguientes

MEDIOS DE PRUEBA

I) DOCUMENTAL.

A) Consistente en que se tenga por incorporado al expediente el escrito de fecha [FECHA], que se adjunta, en el que se acredita [COMPLETAR]

B) Consistente en que por la Jefatura de Tráfico (o Alcaldía) ante la que comparecemos, se libre atento oficio al superior jerárquico del Agente denunciante a fin de que certifique sobre los siguientes extremos:

II) TESTIFICAL.—Consistente en que se cite a declarar a los testigos que se proponen, por el conocimiento directo que pueden ofrecer de los hechos objeto del expediente, ya que en el día y hora de la denuncia formulada estaban físicamente presentes en el lugar en que se cometió la presunta infracción que se imputa, siendo dichas personas las siguientes:

— D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI número [DNI/NIE], y domicilio en la C/ [CALLE], número [NÚMERO], CP [C.P.], de [COMPLETAR]

— D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI número [DNI/NIE], y domicilio en la C/ [CALLE], número [NÚMERO], CP [C.P.], de [COMPLETAR],

— D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI número [DNI/NIE], y domicilio en la C/ [CALLE], número [NÚMERO], CP [C.P.], de [COMPLETAR]

En virtud de todo lo expuesto,

SOLICITO A [COMPLETAR] DE [COMPLETAR] tenga por presentado este escrito de descargos en tiempo y forma legales, se digne admitirlo, así como por efectuadas las alegaciones que en él se contienen y por propuestos los medios de prueba de que intenta valerse esta parte, y una vez que sea practicada la prueba propuesta se nos dé traslado de su resultado, con el fin de efectuar las alegaciones precisas, se dicte resolución en la que se acuerde:

— El archivo del expediente sancionador por no ser ciertos los hechos denunciados.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
