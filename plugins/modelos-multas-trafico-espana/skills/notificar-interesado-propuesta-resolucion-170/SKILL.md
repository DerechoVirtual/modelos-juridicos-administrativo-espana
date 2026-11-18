---
name: notificar-interesado-propuesta-resolucion-170
description: "Redacta el escrito «Notificar al interesado la propuesta de resolución» (formulario 170 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificar al interesado la propuesta de resolución

> Formulario 0170 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] FECHA (4 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AÑO], seguido en este Centro Directivo a»; «…, calle o plaza»; «…UESTA DE RESOLUCIÓN Primero. Sancionar a»; «…n administrativa prevista en el artículo»; «…otor y Seguridad Vial, con la sanción de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 95.3 del Real Decreto Legislativo 6/2015
- Real Decreto 320/1994

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

### Formulario 0170 · Notificar al interesado la propuesta de resolución

- Año del modelo: 2017
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Por el titular del órgano instructor, con fecha [FECHA], se ha dictado la siguiente propuesta de resolución en expediente sancionador en materia de circulación de vehículos a motor, tráfico y seguridad vial:

"Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido en este Centro Directivo a [COMPLETAR], DNI número [DNI/NIE], con domicilio en [LOCALIDAD], calle o plaza [COMPLETAR], como responsable de una infracción administrativa de la legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial, resulta:

Primero. Mediante denuncia de fecha [FECHA], que se notificó en el acto al infractor, formulada por agente encargado de la seguridad del tráfico, se puso en conocimiento de este órgano administrativo la realización de los siguientes hechos:

Segundo. Frente a la denuncia formulada, dentro del plazo establecido, por el inculpado se presentó escrito de descargos y alegaciones, de fecha [FECHA], en el que se manifestaba lo siguiente:

Tercero. Estas manifestaciones realizadas por el inculpado deben desestimarse por cuanto que ha resultado probado que no desvirtúan la acusación realizada, ni el fundamento de la imputación ni su responsabilidad en los hechos denunciados:

Estas manifestaciones realizadas por el inculpado deben estimarse en su totalidad por cuanto acreditan la falta de adecuación de los hechos imputados a la realidad sucedida, su calificación jurídica y la responsabilidad del interesado los hechos consignados en la denuncia.

Estas manifestaciones realizadas por el interesado en su descargo deben estimarse en parte, por haber resultado probadas, y proceder, en consecuencia, a moderar la sanción inicialmente propuesta en atención a la gravedad y trascendencia del hecho, los antecedentes del infractor o el peligro potencial creado.

Vistos los antecedentes mencionados y de conformidad con las previsiones de los arts. 95.3 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial y 13 del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, procede adoptar la siguiente

PROPUESTA DE RESOLUCIÓN

Primero. Sancionar a [COMPLETAR], como responsable de la infracción administrativa prevista en el artículo [COMPLETAR] del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, con la sanción de [COMPLETAR].

Segundo. Dese traslado de la presente propuesta de resolución al interesado para que en un plazo de [Nº] días (no superior a quince ni inferior a diez) y con vista del expediente, pueda alegar lo que estime pertinente y presentar los documentos que tenga por oportunos.- (Lugar, fecha y firma).- EL INSTRUCTOR,"

Lo que notifico a usted, en cuanto inculpado en el expediente, manifestándole que frente a esta propuesta de resolución puede presentar alegaciones documentos e informaciones, en el plazo de QUINCE DIAS, durante los cuales queda de manifiesto el expediente.

A esta notificación se acompaña una relación de los documentos obrantes en el expediente a fin de que pueda obtener copia de los que estime convenientes.

Una vez presentadas las alegaciones a que se refiere el apartado segundo de la propuesta de resolución cuyo texto íntegro se transcribe, o en caso de no presentar alegaciones en el plazo establecido, se dictará la resolución definitiva que corresponda.

En [LUGAR], a [FECHA].

Firma del secretario:
