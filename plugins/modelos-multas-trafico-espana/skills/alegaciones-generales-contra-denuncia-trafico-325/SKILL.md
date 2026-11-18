---
name: alegaciones-generales-contra-denuncia-trafico-325
description: "Redacta el escrito «Alegaciones generales contra denuncia de tráfico» (formulario 325 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones generales contra denuncia de tráfico

> Formulario 0325 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] DNI/NIE (7 veces)
- [ ] CALLE (7 veces)
- [ ] C.P.
- [ ] NIF
- [ ] ÓRGANO
- [ ] FECHA (2 veces)
- [ ] HORA
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A»; «…DE»; «…ad, con domicilio en la C/ número CP, de»; «…o de la mercantil»; «…de y CIF [NIF]), ante [ÓRGANO] de»; «…horas del día de»; «…horas del día de [COMPLETAR] de»; «…por una presunta infracción del artículo»; «…de»; «…que se adjunta, en el que se acredita»; «… domicilio en la C/ [CALLE] número CP de»; «… domicilio en la C/ [CALLE] número CP de»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Prescripción, competencia, concurrencia y tipicidad / Prescripción / Falta de competencia / Concurrencia de sanciones / Falta de tipicidad — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 95 del Real Decreto Legislativo 6/2015

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

### Formulario 0325 · Alegaciones generales contra denuncia de tráfico

- Año del modelo: 2013
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 42 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (HORA, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A [COMPLETAR] DE [COMPLETAR]

D./Dª [NOMBRE Y APELLIDOS] mayor de edad, con domicilio en la C/ número CP, de [COMPLETAR] y provisto de DNI número [DNI/NIE] (o en representación de D./Dª [NOMBRE Y APELLIDOS] o de la mercantil [COMPLETAR], conforme acredito con la escritura de constitución de dicha sociedad, con domicilio social en la C/ [CALLE] número CP [C.P.] de y CIF [NIF]), ante [ÓRGANO] de [COMPLETAR] comparezco y, como mejor proceda en derecho, DIGO:

Que con fecha [FECHA] se me ha notificado la denuncia formulada a las [HORA] horas del día de [COMPLETAR] de [COMPLETAR] por una presunta infracción del artículo [COMPLETAR] de [COMPLETAR], lo que ha dado lugar a la incoación del Expediente sancionador número [Nº DE EXPEDIENTE] y no estando de acuerdo con la infracción que se imputa ni con la sanción que se pretende imponer, dentro del plazo conferido y en forma legal, por medio del presente escrito formulo las siguientes

ALEGACIONES

[ELEGIR UNA OPCIÓN Y REDACTARLA: Prescripción, competencia, concurrencia y tipicidad / Prescripción / Falta de competencia / Concurrencia de sanciones / Falta de tipicidad — el texto de cada opción no venía en el formulario original]

Que sin perjuicio de lo expuesto anteriormente, hemos de manifestar que el compareciente no cometió los hechos descritos en la denuncia que nos ha sido notificada, y lo que sucedió realmente es lo siguiente:

Que tales hechos no son constitutivos de la infracción administrativa que se imputa, ya que no se dan los elementos ni los requisitos necesarios de la misma y, por ello, la sanción que inicialmente se pretende imponer es, además de excesiva, totalmente inadecuada, toda vez que está prevista para hechos distintos de los presuntamente cometidos por el compareciente.

Que con el fin de acreditar lo narrado en los ordinales anteriores, y al amparo del artículo 95 del Real Decreto Legislativo 6/2015, de 30 de octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, interesa al derecho de esta parte se practiquen los siguientes

MEDIOS DE PRUEBA

A) Consistente en que se tenga por incorporado al expediente el escrito de fecha [FECHA] que se adjunta, en el que se acredita [COMPLETAR]

B) Consistente en que por la Jefatura de Tráfico ante la que comparecemos, se libre atento oficio al superior jerárquico del Agente denunciante a fin de que certifique sobre los siguientes extremos:

Consistente en que se cite a declarar a los testigos que se proponen, por el conocimiento directo que pueden ofrecer de los hechos objeto del expediente, ya que en el día y hora de la denuncia formulada estaban físicamente presentes en el lugar en que se cometió la presunta infracción que se imputa, siendo dichas personas las siguientes:

—D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de [COMPLETAR]

—D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de [COMPLETAR]

—D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de [COMPLETAR]

Consistente en que se tenga por incorporado al expediente el informe emitido el día —D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de

por D. —D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de [COMPLETAR]

en su condición de —D. [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE] y domicilio en la C/ [CALLE] número CP de [COMPLETAR]

en el que se acredita [COMPLETAR] siendo determinante dicha pericia para adoptar una resolución ajustada a derecho en el presente expediente.

En virtud de todo lo expuesto,

SOLICITO A [COMPLETAR] DE [COMPLETAR] tenga por presentado este escrito de descargos en tiempo y forma legales, se digne admitirlo, así como por efectuadas las alegaciones que en él se contienen y por propuestos los medios de prueba de que intenta valerse esta parte, y una vez que sea practicada la prueba propuesta con traslado a esta parte de su resultado, con el fin de efectuar las alegaciones precisas, se dicte resolución en la que se acuerde:

— El archivo del expediente sancionador por no ser ciertos los hechos denunciados y concurrir [COMPLETAR].

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
