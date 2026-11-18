---
name: descargos-maniobra-parada-estacionamiento-1644
description: "Redacta el escrito «Descargos por maniobra de parada y estacionamiento» (formulario 1644 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por maniobra de parada y estacionamiento

> Formulario 1644 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (4 veces)
- [ ] DESCRIBIR (2 veces)
- [ ] IMPORTE
- [ ] Nº
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…, realizada ante la necesidad de»; «…or este concepto, teniendo en cuenta que»; «…, que usa el vehículo citado en razón de»; «…la denuncia tuvieron lugar con motivo de»; «…n de la infracción, por el transcurso de»; «…consistente en que se tome declaración a»; «…, en su condición de»; «…, en el que se acredita»; «…, en el que se hace referencia a»; «…instructor para apreciar y acreditar que»; «…to la sanción, en lo que se refiere a la»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Párrafos opcionales (22)

Inclúyelos solo si encajan en los hechos:

- Parar (en vía urbana) el vehículo obstaculizando gravemente la circulación.…
- Estacionar el vehículo obstaculizando gravemente la circulación.…
- Parar el vehículo constituyendo un riesgo para los demás usuarios.…
- Estacionar el vehículo constituyendo un riesgo para los demás usuarios.…
- Según hemos afirmado anteriormente no consideramos ciertos los hechos imputados, en los términos descritos en …
- Que no es el propietario del vehículo quien realizó el estacionamiento o parada que ha dado origen a este expe…
- Que el estacionamiento o parada mencionados en la denuncia tuvieron lugar con motivo de [COMPLETAR], razón de …
- Que la denuncia carece de valor jurídico de cargo, por cuanto ha sido formulada por un controlador pertenecien…
- Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos sup…
- La caducidad del expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente s…
- La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio…
- La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del …
- La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce i…
- Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no l…
- La concurrencia del siguiente hecho que extingue la responsabilidad en este expediente sancionador:…
- Pago anticipado.…
- Haber sido ya sancionado por los mismos hechos.…
- Testifical, consistente en que se tome declaración a [COMPLETAR], en cuanto testigos presenciales de los hecho…
- Pericial, consistente en informe de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en su condición de [COMPLET…
- Documental, consistente en escrito de fecha [FECHA], suscrito por [ÓRGANO O PERSONA], en el que se hace refere…
- Reconocimiento sobre el terreno por el órgano instructor para apreciar y acreditar que [COMPLETAR] y los demás…
- Informe de ratificación, por parte del mismo agente denunciante de los hechos contenidos en la denuncia, y en …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 91.2 del Real Decreto 1428/2003
- artículo 39.3 del Real Decreto Legislativo 6/2015
- artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015
- artículos 25 a 31 de la Ley 40/2015
- art. 105 TR LTCVMSV
- art. 112 TR LTCVMSV
- artículos 80 y 81 TR LTCVMSV

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

### Formulario 1644 · Descargos por maniobra de parada y estacionamiento

- Año del modelo: 2004
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (3); 1 desplegables convertidos en elección en blanco; 22 párrafos opcionales señalados; 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de alegaciones del denunciado dentro del expediente administrativo sancionador en materia de tráfico, oponiéndose al relato de los hechos efectuado por el denunciante (parar o estacionar constituyendo la maniobra un obstáculo para la circulación, o provocando un riesgo para el resto de los usuarios de la vía), y por tanto a la calificación jurídica de los mismos como constitutivos de infracción administrativa. Con el fin de demostrar lo anterior y de que la autoridad administrativa acuerde el sobreseimiento del expediente sancionador, finaliza el pliego de descargo proponiendo la práctica de pruebas por el órgano instructor.

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante [ÓRGANO], órgano competente, como mejor proceda comparece y

DICE

Que en virtud de este escrito, en el expediente número [Nº DE EXPEDIENTE], incoado mediante denuncia de fecha [FECHA], presenta descargos por no estar de acuerdo con el relato de los hechos en los términos descritos, ni con su calificación jurídica, ni con la propuesta de sanción inicialmente formulada en el acto de la denuncia, y todo ello de conformidad con las siguientes (1)

ALEGACIONES

Que en este procedimiento sancionador, se realiza una imputación de hechos que no son del todo exactos, al no ser lo suficientemente descriptivos de la conducta realizada, por lo que para la más completa y correcta determinación de lo sucedido es preciso poner en conocimiento del órgano instructor y del sancionador los hechos tal y como verdaderamente acaecieron:

Que, según el artículo 91.2 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación y artículo 39.3 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), los hechos imputados han sido calificados en el expediente sancionador como constitutivos de la siguiente infracción:

[OPCIONAL — incluir si procede]

Parar (en vía urbana) el vehículo obstaculizando gravemente la circulación.

[OPCIONAL — incluir si procede]

Estacionar el vehículo obstaculizando gravemente la circulación.

[OPCIONAL — incluir si procede]

Parar el vehículo constituyendo un riesgo para los demás usuarios.

[OPCIONAL — incluir si procede]

Estacionar el vehículo constituyendo un riesgo para los demás usuarios.

Que esta imputación no es correcta ya que no se dan los elementos constitutivos y definidores de dicha infracción administrativa, por las siguientes razones:

[OPCIONAL — incluir si procede]

Según hemos afirmado anteriormente no consideramos ciertos los hechos imputados, en los términos descritos en el boletín de denuncia, por resultar excesivamente generales y concretar lo verdaderamente sucedido, por esta razón la conducta del infractor consistente en [DESCRIBIR], realizada ante la necesidad de [COMPLETAR], no puede considerarse contraria a las normas que regulan la parada y el estacionamiento de vehículo, y en particular lo dispuesto en las normas generales sobre "modo y forma de ejecución", ya que no se da el supuesto de hecho habilitante de la potestad sancionadora por este concepto, teniendo en cuenta que [COMPLETAR], no concurriendo, en términos reglamentarios, en el presente caso, no procede el ejercicio de la potestad sancionadora.

[OPCIONAL — incluir si procede]

Que no es el propietario del vehículo quien realizó el estacionamiento o parada que ha dado origen a este expediente sancionador, sino que lo fue D./Dña. [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], que usa el vehículo citado en razón de [COMPLETAR] y que es la única persona contra la que legítimamente puede dirigirse el expediente sancionador.

[OPCIONAL — incluir si procede]

Que el estacionamiento o parada mencionados en la denuncia tuvieron lugar con motivo de [COMPLETAR], razón de urgencia vital que sirve de eximente de la infracción cometida, pues de no haberse efectuado la maniobra de estacionamiento o parada en la forma, lugar y tiempo en que se hicieron, hubiera peligrado la gestión que se estaba realizando, por lo que no existe culpabilidad alguna en esta infracción y debe archivarse el expediente sin más trámite.

[OPCIONAL — incluir si procede]

Que la denuncia carece de valor jurídico de cargo, por cuanto ha sido formulada por un controlador perteneciente a una empresa privada, es decir, no es un funcionario cuyas actuaciones gocen de presunción de veracidad en razón de su objetividad, sino un personal interesado en la recaudación, por tanto, como dijo el Tribunal Supremo (STS 23 noviembre 1993) «los controladores o vigilantes de la ORA no tienen la consideración de agentes de la autoridad, salvo cuando sean miembros de la Policía Local, ni tampoco pueden tener la condición de auxiliares de ésta, al sólo poder existir tales auxiliares en Municipios de menos de 5.000 habitantes donde no exista dicha Policía Local. Es además la doctrina establecida por la STS de 1 octubre 1991, en la que se sienta de forma clara y explícita la negación de la consideración de agentes de la autoridad a los aludidos controladores o vigilantes de la denominada ORA, y por ello, su simple denuncia equivale a la denuncia de un particular, y al no ser adverada por pruebas posteriores, no tiene fuerza suficiente para acreditar los hechos denunciados». Además, como dice la STSJ Madrid de 9 de octubre de 2000, la denuncia de un controlador municipal de la ORA, e incluso su posterior ratificación no basta como prueba para sancionar a un conductor, la sentencia afirma que «no es prueba de cargo para desvirtuar la presunción de inocencia» ya que la ley exige que se aporten todos los medios de prueba posibles, y en consecuencia, está obligada la Administración, por medio del controlador, a aportar por ejemplo una fotografía, es decir, «la Administración debió aportar alguna prueba más para acreditar la comisión de la infracción».

Como motivos formales de oposición a este expediente sancionador cabe alegar los siguientes (2):

[OPCIONAL — incluir si procede]

Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos supuestamente se hubieron cometido.

[OPCIONAL — incluir si procede]

La caducidad del expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente se haya dictado resolución que le ponga fin.

[OPCIONAL — incluir si procede]

La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]) sino únicamente al propietario del vehículo, incumpliendo el deber de identificar al culpable para notificar la denuncia.

[OPCIONAL — incluir si procede]

La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del órgano competente para resolver a efectos de su eventual recusación.

[OPCIONAL — incluir si procede]

La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce indefensión al interesado.

[OPCIONAL — incluir si procede]

Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no les está atribuido por haberse cometido fuera de su demarcación territorial.

[OPCIONAL — incluir si procede]

La concurrencia del siguiente hecho que extingue la responsabilidad en este expediente sancionador:

[OPCIONAL — incluir si procede]

Pago anticipado.

[OPCIONAL — incluir si procede]

Haber sido ya sancionado por los mismos hechos.

Que la propuesta de sanción inicialmente realizada consistente en el pago de una multa de [IMPORTE] euros y la privación del permiso de conducir durante [Nº] meses, tampoco resulta adecuada de conformidad con el principio de proporcionalidad y demás criterios que gobiernan el ejercicio de la potestad sancionadora en materia de tráfico, atendiendo a las circunstancias expresadas.

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

Informe de ratificación, por parte del mismo agente denunciante de los hechos contenidos en la denuncia, y en particular sobre [DESCRIBIR], extremos cuya determinación es necesaria en esta imputación y no han sido debidamente acreditados.

Por cuanto antecede y de conformidad con las previsiones de los artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: El RD 320/1994 (arts. 10.1 y 12.1) daba 15 días; hoy rige el plazo de 20 días naturales del TR LSV para alegar y proponer prueba o pagar con reducción (arts. 93.1 y 95.1). El RD 320/1994 sigue formalmente vigente pero desplazado por el título V del TR LSV. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 93.1 y 95.1; RD 320/1994, BOE-A-1994-8985 arts. 10 y 12.], en relación con los artículos 25 a 31 de la Ley 40/2015 [NOTA DE REVISIÓN: Errata tipográfica (falta espacio). Fuente: Ley 40/2015 arts. 25-31.], de 1 de octubre, de Régimen Jurídico del Sector Público,

SOLICITA

Que se tenga por presentado este escrito de descargos y, previa la práctica de las pruebas propuestas y la tramitación que proceda, se dicte propuesta de resolución en la que se acuerde el sobreseimiento del expediente sancionador.

Que, subsidiariamente, en caso de no estimar la petición de archivo del expediente, se disponga la reducción de la sanción inicialmente propuesta para adecuarla a los principios de la potestad sancionadora en materia de tráfico, sin perjuicio de la interposición de los recursos que esta parte tenga por conveniente.

Que, finalmente, se disponga dejar sin efecto la sanción, en lo que se refiere a la [COMPLETAR] (3).

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) Los argumentos que más se suelen utilizar en estas situaciones son la alegación de alguna circunstancia extraordinaria que obliga al usuario a estacionar el vehículo, a sabiendas de la prohibición o limitación, ante la necesidad de atender alguna urgencia. Por otra parte, la mayor dificultad del Ayuntamiento es que el boleto de denuncia se deja en el cristal del parabrisas del vehículo ya que el conductor no permanece en el interior del vehículo estacionado y ello ocasiona dos riesgos: que el boleto de denuncia desaparezca del cristal por estar al alcance de cualquiera y que no sea el propietario del vehículo el conductor que aparcó de forma incorrecta, lo que lleva a la Administración a tramitar muchas de estas infracciones por el art. 105 TR LTCVMSV.

(2) El art. 112 TR LTCVMSV señala el plazo de prescripción de las infracciones previstas en la ley, que será de tres meses para las infracciones leves y de 6 meses para las demás. Con respecto a la caducidad de las mismas, dicho artículo establece un plazo de un año desde la iniciación del procedimiento.

(3) En relación con las sanciones, téngase en cuenta los artículos 80 y 81 TR LTCVMSV.
