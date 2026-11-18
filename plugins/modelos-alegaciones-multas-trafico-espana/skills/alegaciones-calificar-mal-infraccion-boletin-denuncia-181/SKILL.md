---
name: alegaciones-calificar-mal-infraccion-boletin-denuncia-181
description: "Redacta el escrito «Alegaciones por calificar mal la infracción en el boletín de denuncia» (formulario 181 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones por calificar mal la infracción en el boletín de denuncia

> Formulario 0181 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] HORA
- [ ] MATRÍCULA
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…por el Agente»; «…contraba circulando con un vehículo tipo»; «…, matrícula [MATRÍCULA], por la vía»; «…realizado una infracción calificada como»; «…s como constitutivos de la infracción de»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

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

### Formulario 0181 · Alegaciones por calificar mal la infracción en el boletín de denuncia

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (HORA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]), ante [ÓRGANO] comparece y como mejor proceda en derecho,

DICE:

Que por medio de este escrito y dentro del plazo de veinte días naturales concedido al efecto, manifiesta su oposición a la denuncia formulada con fecha [FECHA] por el Agente [COMPLETAR], expediente número [Nº DE EXPEDIENTE], y presenta los siguientes descargos y alegaciones:

Que el día [FECHA], a las [HORA] horas, se encontraba circulando con un vehículo tipo [COMPLETAR], matrícula [MATRÍCULA], por la vía [COMPLETAR], y por las razones que seguidamente se expresan, realizó la siguiente conducta:

Conducir por calle en dirección prohibida, y con el propósito de estacionar, a la velocidad del paso humano, en ciclomotor, para acudir a cita médica en un domicilio próximo al lugar de la infracción.

Que como consecuencia de los hechos mencionados, fue detenido por un Agente encargado de la vigilancia del tráfico y se le hizo entrega de un Boletín de Denuncia con el que se da principio al expediente en el que se imputa el hecho de haber realizado una infracción calificada como [COMPLETAR] de conformidad con la reglamentación aplicable.

Que la calificación realizada por el Agente Denunciante (o, en su caso, en la Propuesta de Resolución) es incorrecta ya que no se pueden considerar los hechos imputados como constitutivos de la infracción de [COMPLETAR], por cuanto:

Que tal y como queda acreditado, con la simple lectura de los hechos, tal y como acaecieron y de la intención o propósito del infractor, ya en su día manifestada al agente, no se dan los requisitos para tal calificación, pues no hay temeridad alguna, sino que no se trata de una conducta consistente en "circular por dirección prohibida" sin más, sino circular por dirección prohibida a una cierta velocidad (paso humano) y con un propósito bien definido: buscar un estacionamiento próximo al lugar de la cita médica. Esto, ciertamente, se puede considerar infracción leve de no respetar una señal de tráfico, pero no infracción muy grave de conducción temeraria, como esperamos que así se reconozca por el propio agente denunciante en el trance de la ratificación de su denuncia a la vista de este escrito de alegaciones.

Por lo expuesto y de conformidad con el artículo 95 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: Alegaciones (20 días naturales) y traslado al agente (15 días naturales) se rigen hoy por el art. 95.1 y 95.2 TR LSV. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 95.],

SOLICITA:

Que se admita a trámite este escrito de descargos y alegaciones y, previas las comprobaciones oportunas, se proceda al sobreseimiento del expediente o, subsidiariamente, a la correcta calificación de los hechos mediante la oportuna Propuesta de resolución de la que se dé traslado a esta parte para la materialización de su derecho de defensa frente a la calificación que nuevamente se haga para los hechos realizados por el órgano competente.

En [LUGAR], a [FECHA].

Firmado:
