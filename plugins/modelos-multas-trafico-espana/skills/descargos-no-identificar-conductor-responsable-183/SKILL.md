---
name: descargos-no-identificar-conductor-responsable-183
description: "Redacta el escrito «Descargos por no identificar al conductor responsable» (formulario 183 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por no identificar al conductor responsable

> Formulario 0183 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] FECHA (6 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] ÓRGANO O PERSONA
- [ ] MATRÍCULA
- [ ] HORA
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…por la unidad de sanciones de tráfico de»; «…, en el que se me comunica»; «…e la infracción cometida con el vehículo»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 24 de la Constitución
- Real Decreto Legislativo 6/2015

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

### Formulario 0183 · Descargos por no identificar al conductor responsable

- Año del modelo: 2016
- Revisión 17-11-2026: 2 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (HORA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], ante [ÓRGANO], órgano administrativo competente, como mejor proceda comparece y

EXPONE:

Que con fecha [FECHA], ha recibido la notificación de la propuesta de resolución de fecha [FECHA], cursada por la unidad de sanciones de tráfico de [COMPLETAR], en el que se me comunica [COMPLETAR], en el expediente número [Nº DE EXPEDIENTE], que se tramita en ese órgano administrativo, y cuya copia se adjunta a efectos identificativos.

Que en el escrito mencionado se hace referencia a la responsabilidad que me incumbe como consecuencia de dejar desatendido el requerimiento de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en el que se conminaba a la identificación del conductor responsable de la infracción cometida con el vehículo [COMPLETAR], matrícula [MATRÍCULA], el día [FECHA] a las [HORA] horas en la vía pública que se menciona.

Que no se ha podido cumplimentar el requerimiento de identificación antes referenciado como consecuencia de las circunstancias que se enumeran a continuación y que esta parte considera que constituyen justificación suficiente para que no se considere cometida la infracción muy grave que se le imputa:

Que no es cierto que se hubiera incumplido el deber de colaboración con la Administración de Tráfico actuante, toda vez que mediante escrito de fecha [FECHA], por este interesado se manifestó ante el órgano sancionador que el titular del vehículo no era el conductor, sino que lo podía ser D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], cuyos datos de identificación se expresaron debidamente, por lo que debió darse por contestado el requerimiento de identificación y no pasar a imponer una sanción contraviniendo el artículo 24 de la Constitución Española.

Por lo expuesto, de conformidad con las previsiones del artículo 77.j del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV)

SOLICITA:

Que se tenga por presentado este escrito y en virtud de sus manifestaciones y elementos probatorios se proceda al sobreseimiento del expediente sancionador abierto contra el interesado, dando por realizada la justificación suficiente para no considerar cometida la infracción que se le imputa, o teniendo por formulado el recurso correspondiente en caso de no estimarse estas manifestaciones a efectos de retrotraer el expediente al momento procesal en que deba tenerse por cumplimentado el deber de identificar a los responsables de la infracción denunciada.

En [LUGAR], a [FECHA].

Firmado:
