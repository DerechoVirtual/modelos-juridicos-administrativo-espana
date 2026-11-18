---
name: descargos-velocidad-minima-poblado-fuera-poblado-1628
description: "Redacta el escrito «Descargos por velocidad mínima en poblado y fuera de poblado» (formulario 1628 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por velocidad mínima en poblado y fuera de poblado

> Formulario 1628 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (4 veces)
- [ ] IMPORTE
- [ ] Nº
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…dad del conductor estaba determinada por»; «…, ante la necesidad de»; «…dad del conductor estaba determinada por»; «…, ante la necesidad de»; «…la mínima sin riesgo para la circulación»; «…n de la infracción, por el transcurso de»; «…pago anticipado»; «…dad con el principio de proporcionalidad»; «…consistente en que se tome declaración a»; «…, en su condición de»; «…, en el que se acredita»; …

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Párrafos opcionales (19)

Inclúyelos solo si encajan en los hechos:

- Circular a velocidad anormalmente reducida, sin causa justificada, entorpeciendo la marcha de otro vehículo.…
- Circular por una autopista con un vehículo a motor a una velocidad inferior a 60 Km por hora.…
- Circular por una autovía con un vehículo a motor a una velocidad inferior a 60 km por hora.…
- Circular por una carretera con un vehículo a motor a velocidad inferior a la mitad de la genérica estipulada.…
- Negamos la veracidad de las imputaciones realizadas y el hecho de la infracción a las normas sobre "velocidade…
- Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos sup…
- La caducidad del expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente s…
- La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio…
- La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del …
- La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce i…
- Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no l…
- Concurrencia del siguiente hecho que extingue la responsabilidad:…
- pago anticipado [COMPLETAR].…
- haber sido ya sancionado por los mismos hechos en este expediente sancionador.…
- Testifical, consistente en que se tome declaración a [COMPLETAR], en cuanto testigos presenciales de los hecho…
- Pericial, consistente en informe de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en su condición de [COMPLET…
- Documental, consistente en escrito de fecha [FECHA], suscrito por [ÓRGANO O PERSONA], en el que se hace refere…
- Reconocimiento sobre el terreno por el órgano instructor para apreciar y acreditar que [COMPLETAR] y los demás…
- Informe de ratificación de la denuncia, emitido por el mismo agente que la formuló, en el que además se aclare…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 49 del Real Decreto 1428/2003
- artículo 21.2 del Real Decreto Legislativo 6/2015
- artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015
- artículos 25 a 31 de la Ley 40/2015
- art. 112 TR LTCVMSV

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

### Formulario 1628 · Descargos por velocidad mínima en poblado y fuera de poblado

- Año del modelo: 2004
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (3); 1 desplegables convertidos en elección en blanco; 19 párrafos opcionales señalados; 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de alegaciones del denunciado dentro del expediente administrativo sancionador en materia de tráfico, oponiéndose al relato de los hechos efectuado por el denunciante (conducir a velocidad inferior a la permitida), y por tanto a la calificación jurídica de los mismos como constitutivos de infracción administrativa. Con el fin de demostrar lo anterior y de que la autoridad administrativa acuerde el sobreseimiento del expediente sancionador, finaliza el pliego de descargo proponiendo la práctica de pruebas por el órgano instructor.

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante [ÓRGANO], órgano competente, como mejor proceda comparece y

DICE

Que en virtud de este escrito, en el expediente número [Nº DE EXPEDIENTE], incoado mediante denuncia de fecha [FECHA], presenta descargos por no estar de acuerdo con el relato de los hechos en los términos descritos, ni con su calificación jurídica, ni con la propuesta de sanción inicialmente formulada en el acto de la denuncia, y todo ello de conformidad con las siguientes (1) (2)

ALEGACIONES

Que en este procedimiento sancionador, se realiza una imputación de hechos que no son del todo exactos, al no ser lo suficientemente descriptivos de la conducta realizada, por lo que para la más completa y correcta determinación de lo sucedido es preciso poner en conocimiento del órgano instructor y del sancionador los hechos tal y como verdaderamente acaecieron:

Que, según el artículo 49 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación y artículo 21.2 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), los hechos imputados han sido calificados en el expediente sancionador como constitutivos de la siguiente infracción:

[OPCIONAL — incluir si procede]

Circular a velocidad anormalmente reducida, sin causa justificada, entorpeciendo la marcha de otro vehículo.

[OPCIONAL — incluir si procede]

Circular por una autopista con un vehículo a motor a una velocidad inferior a 60 Km por hora.

[OPCIONAL — incluir si procede]

Circular por una autovía con un vehículo a motor a una velocidad inferior a 60 km por hora.

[OPCIONAL — incluir si procede]

Circular por una carretera con un vehículo a motor a velocidad inferior a la mitad de la genérica estipulada.

Que esta imputación no es correcta ya que no se dan los elementos constitutivos y definidores de dicha infracción administrativa, por las siguientes razones:

[OPCIONAL — incluir si procede]

Negamos la veracidad de las imputaciones realizadas y el hecho de la infracción a las normas sobre "velocidades mínimas" por cuanto la velocidad del conductor estaba determinada por [COMPLETAR], ante la necesidad de [COMPLETAR], teniendo en cuenta que no se deberá entorpecer la marcha normal de otro vehículo sin causa justificada circulando a velocidad anormalmente reducida.

No son correctas ni ciertas las imputaciones realizadas y el hecho de la infracción a las normas sobre "velocidades mínimas" por cuanto la velocidad del conductor estaba determinada por [COMPLETAR], ante la necesidad de [COMPLETAR], teniendo en cuenta que la norma establece que se podrá circular por debajo de los límites mínimos de velocidad
en los casos de transportes especiales
cuando las circunstancias del tráfico impidan el mantenimiento de una velocidad superior a la mínima sin riesgo para la circulación
[COMPLETAR]

Como motivos formales de oposición a este expediente sancionador cabe alegar los siguientes:

[OPCIONAL — incluir si procede]

Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos supuestamente se hubieron cometido (3).

[OPCIONAL — incluir si procede]

La caducidad del expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente se haya dictado resolución que le ponga fin;

[OPCIONAL — incluir si procede]

La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]) sino únicamente al propietario del vehículo, incumpliendo el deber de identificar al culpable para notificar la denuncia.

[OPCIONAL — incluir si procede]

La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del órgano competente para resolver a efectos de su eventual recusación.

[OPCIONAL — incluir si procede]

La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce indefensión al interesado.

[OPCIONAL — incluir si procede]

Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no les está atribuido por haberse cometido fuera de su demarcación territorial.

[OPCIONAL — incluir si procede]

Concurrencia del siguiente hecho que extingue la responsabilidad:

[OPCIONAL — incluir si procede]

pago anticipado [COMPLETAR].

[OPCIONAL — incluir si procede]

haber sido ya sancionado por los mismos hechos en este expediente sancionador.

Que la propuesta de sanción inicialmente realizada consistente en el pago de una multa de [IMPORTE] euros y la privación del permiso de conducir durante [Nº] meses, tampoco resulta adecuada de conformidad con el principio de proporcionalidad [COMPLETAR] y demás criterios que gobiernan el ejercicio de la potestad sancionadora en materia de tráfico, atendiendo a las circunstancias expresadas.

Que para la demostración de las afirmaciones anteriormente manifestadas en este escrito de descargos, y sin perjuicio de las demás actuaciones que de oficio sean practicadas por el órgano instructor competente, se propone la práctica de los siguientes medios de prueba:

[OPCIONAL — incluir si procede]

Testifical, consistente en que se tome declaración a [COMPLETAR], en cuanto testigos presenciales de los hechos imputados y que pueden dar razón de los mismos por el conocimiento directo que de ellos tienen en razón de su presencia física el momento y lugar de la infracción supuestamente cometida.

[OPCIONAL — incluir si procede]

Pericial, consistente en informe de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en su condición de [COMPLETAR], en el que se acredita [COMPLETAR], para la mejor determinación de los hechos y las circunstancias relevantes a tener en cuenta en la resolución de este procedimiento sancionador.

[OPCIONAL — incluir si procede]

Documental, consistente en escrito de fecha [FECHA], suscrito por [ÓRGANO O PERSONA], en el que se hace referencia a [COMPLETAR], circunstancia de necesario conocimiento para la más adecuada instrucción del expediente.

[OPCIONAL — incluir si procede]

Reconocimiento sobre el terreno por el órgano instructor para apreciar y acreditar que [COMPLETAR] y los demás elementos constitutivos de la infracción supuestamente cometida.

[OPCIONAL — incluir si procede]

Informe de ratificación de la denuncia, emitido por el mismo agente que la formuló, en el que además se aclare que [COMPLETAR], hecho de necesario conocimiento par la correcta instrucción y resolución de este expediente sancionador.

Por cuanto antecede y de conformidad con las previsiones de los artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: El RD 320/1994 (arts. 10.1 y 12.1) daba 15 días; hoy rige el plazo de 20 días naturales del TR LSV para alegar y proponer prueba o pagar con reducción (arts. 93.1 y 95.1). El RD 320/1994 sigue formalmente vigente pero desplazado por el título V del TR LSV. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 93.1 y 95.1; RD 320/1994, BOE-A-1994-8985 arts. 10 y 12.], en relación con los artículos 25 a 31 de la Ley 40/2015 [NOTA DE REVISIÓN: Errata tipográfica (falta espacio). Fuente: Ley 40/2015 arts. 25-31.], de 1 de octubre, de Régimen Jurídico del Sector Público,

SOLICITA

Que se tenga por presentado este escrito de descargos y, previa la práctica de las pruebas propuestas y la tramitación que proceda, se dicte propuesta de resolución en la que se acuerde el sobreseimiento del expediente sancionador.

Que, subsidiariamente, en caso de no estimar la petición de archivo del expediente, se disponga la reducción de la sanción inicialmente propuesta para adecuarla a los principios de la potestad sancionadora en materia de tráfico, sin perjuicio de la interposición de los recursos que esta parte tenga por conveniente.

Que, finalmente, se disponga dejar sin efecto la sanción, en lo que se refiere a [DESCRIBIR].

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) La velocidad de los vehículos es una magnitud objetiva que puede y debe ser medida con instrumentos de precisión para dar origen a una sanción administrativa. No obstante, como vamos a comprobar, en algunos supuestos todavía la medición de la velocidad no deja de ser una apreciación subjetiva del agente denunciante, tales como el concepto de «velocidad anormalmente reducida». En la actualidad la velocidad se mide mediante cinemómetros homologados y revisados periódicamente, sin que hoy sean eficaces denuncias sobre supuestos «excesos de velocidad» cuya medición se base en métodos tan poco científicos como «chirriar mucho las ruedas en una curva», o bien por el hecho de «desplazar mucho aire al pasar junto a la pareja». Los actuales sistemas de medición, basados en equipos de radar, miden con bastante exactitud la velocidad de los móviles sobre la calzada en función de ciertos ángulos y distancias. No obstante, como ya hemos indicado, estos equipos deben ser revisados periódicamente por el Instituto Nacional de Metrología, organismo dependiente del Ministerio de Fomento, y homologados o autorizados por las autoridades competentes en materia de Industria, que pueden serlo las de las Comunidades Autónomas a raíz del proceso de delegación de competencias. En todo caso hay que tener en cuenta las posibilidades de error, por lo que también hay unos márgenes de tolerancia que se contemplan en beneficio de los usuarios y que son mayores cuando la medición se efectúa desde vehículos en marcha.

(2) En todas las infracciones de exceso de velocidad es necesario proponer pruebas para contradecir la medición efectuada por los agentes de tráfico, ya que es el único medio de discutir los hechos denunciados. La Administración está obligada a pronunciarse sobre las pruebas propuestas, incurriendo en vulneración del derecho de defensa en caso contrario, lo que conlleva la nulidad del expediente, como bien se encarga de recordarlo la STSJ de Castilla La Mancha de 14 enero 2000, recurso número 51/2000: «En el presente supuesto en el que se imputó al actor el haber sobrepasado el límite de velocidad, a través de un dato constatado por un aparato de medición, el cinemómetro, y sin que la imputación de la Administración se apoyase en otro elemento probatorio de cargo, el recurrente, durante la tramitación del expediente sancionador, negó los hechos imputados, y solicitó en su recurso la práctica de una serie de pruebas (folios 4 y 5 del expediente). Dicha solicitud fue rechazada por la Administración (folio 7 del expediente) habida cuenta que la prueba propuesta no resulta necesaria para la averiguación y calificación de los hechos. Dadas las circunstancias del caso concreto, las pruebas solicitadas por el demandante han de calificarse como necesarias o pertinentes, toda vez que constituían el único medio de prueba con virtualidad suficiente desarrollar su derecho a la defensa frente a la comisión de una infracción. Así, el rechazo de la Administración ha supuesto una clara vulneración al referido derecho constitucional que, nos ha de llevar a la estimación del presente recurso, sin necesidad de entrar en consideración sobre las demás alegaciones de las partes».

(3) El art. 112 TR LTCVMSV señala el plazo de prescripción de las infracciones previstas en la ley, que será de tres meses para las infracciones leves y de seis meses para las demás. Con respecto a la caducidad de las mismas, dicho artículo establece un plazo de un año desde la iniciación del procedimiento.
