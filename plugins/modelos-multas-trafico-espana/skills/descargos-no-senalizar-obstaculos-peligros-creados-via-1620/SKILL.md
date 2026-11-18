---
name: descargos-no-senalizar-obstaculos-peligros-creados-via-1620
description: "Redacta el escrito «Descargos por no señalizar obstáculos o peligros creados en la vía» (formulario 1620 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por no señalizar obstáculos o peligros creados en la vía

> Formulario 1620 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] IMPORTE
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…meses»; «…Pago anticipado»; «…consistente en que se tome declaración a»; «…, en su condición de»; «…, en el que se acredita»; «…, en el que se hace referencia a»; «…instructor para apreciar y acreditar que»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Párrafos opcionales (24)

Inclúyelos solo si encajan en los hechos:

- No hacer desaparecer lo antes posible un obstáculo o peligro en la vía por quien lo ha creado.…
- No señalizar de forma eficaz un obstáculo o peligro en la vía por quien lo ha creado.…
- Parar o estacionar en lugares distintos de los fijados por la autoridad responsable.…
- Los objetos o materiales depositados no lo fueron en la vía ni en sus inmediaciones, sino a suficiente distanc…
- Los objetos depositados en la vía pública y que son objeto de esta denuncia no fueron dejados inicialmente en …
- Los objetos o materiales depositados, por el lugar donde se dejaron y por la pequeña cantidad depositada, difí…
- Los objetos o materiales depositados y que en opinión del agente denunciante pueden entorpecer la parada y est…
- Por parte del interesado se adoptaron las medidas necesarias para hacer desaparecer lo antes posible el obstác…
- Prescripción de la infracción, por el transcurso de [Nº] meses [COMPLETAR], contados desde la fecha en que los…
- La caducidad el expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente se…
- La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio…
- La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del …
- La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce i…
- Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no l…
- Concurrencia del siguiente hecho que extingue la responsabilidad en este expediente sancionador:…
- Pago anticipado [COMPLETAR].…
- Haber sido ya sancionado por los mismos hechos.…
- Que la propuesta de sanción inicialmente realizada consistente en el pago de una multa de [IMPORTE] euros tamp…
- Testifical, consistente en que se tome declaración a [COMPLETAR], en cuanto testigos presenciales de los hecho…
- Pericial, consistente en informe de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en su condición de [COMPLET…
- Documental, consistente en escrito de fecha [FECHA], suscrito por [ÓRGANO O PERSONA], en el que se hace refere…
- Reconocimiento sobre el terreno por el órgano instructor para apreciar y acreditar que [COMPLETAR] y los demás…
- Informe de ratificación, por parte del mismo agente denunciante de los hechos contenidos en la denuncia, y en …
- Que, subsidiariamente, en caso de no estimar la petición de archivo del expediente, se disponga la reducción d…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5 del Real Decreto 1428/2003
- artículo 12.3 del Real Decreto Legislativo 6/2015
- artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015
- artículos 25 a 31 de la Ley 40/2015
- art. 5 RGC
- artículo 5.1 del Reglamento General de Circulación
- artículo 5.3 del Reglamento General de Circulación
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

### Formulario 1620 · Descargos por no señalizar obstáculos o peligros creados en la vía

- Año del modelo: 2004
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (3); 1 desplegables convertidos en elección en blanco; 24 párrafos opcionales señalados; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de alegaciones del denunciado dentro del expediente administrativo sancionador en materia de tráfico, oponiéndose al relato de los hechos efectuado por el denunciante (no adoptar las medidas necesarias en relación con obstáculos o peligros creados en la vía), y por tanto a la calificación jurídica de los mismos como constitutivos de infracción administrativa. Con el fin de demostrar lo anterior y de que la autoridad administrativa acuerde el sobreseimiento del expediente sancionador, finaliza el pliego de descargo proponiendo la práctica de pruebas por el órgano instructor.

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], ante [ÓRGANO], órgano competente, como mejor proceda comparece y

DICE

Que, en virtud de este escrito, en el expediente número [Nº DE EXPEDIENTE], incoado mediante denuncia de fecha [FECHA], presenta descargos por no estar de acuerdo con el relato de los hechos en los términos descritos, ni con su calificación jurídica, ni con la propuesta de sanción inicialmente formulada en el acto de la denuncia, y todo ello de conformidad con las siguientes

ALEGACIONES

Que en este procedimiento sancionador se realiza una imputación de hechos que no son del todo exactos, al no ser lo suficientemente descriptivos de la conducta realizada, por lo que para la más completa y correcta determinación de lo sucedido es preciso poner en conocimiento del órgano instructor y del sancionador los hechos tal y como verdaderamente acaecieron:

Que, según el artículo 5 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación y artículo 12.3 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), los hechos imputados han sido calificados en el expediente sancionador como constitutivos de la siguiente infracción: (1)

[OPCIONAL — incluir si procede]

No hacer desaparecer lo antes posible un obstáculo o peligro en la vía por quien lo ha creado.

[OPCIONAL — incluir si procede]

No señalizar de forma eficaz un obstáculo o peligro en la vía por quien lo ha creado.

[OPCIONAL — incluir si procede]

Parar o estacionar en lugares distintos de los fijados por la autoridad responsable.

Que esta imputación no es correcta ya que no se dan los elementos constitutivos y definidores de dicha infracción administrativa, por las siguientes razones:

[OPCIONAL — incluir si procede]

Los objetos o materiales depositados no lo fueron en la vía ni en sus inmediaciones, sino a suficiente distancia como para no ser susceptibles de poder modificar las condiciones apropiadas para circular. Los objetos o materiales que se depositaron en el lugar objeto de la denuncia lo fueron ante la creencia de que tal conducta estaba amparada por bandos o normas de policía y buen gobierno municipal, por la falta de señalización al respecto y por la presencia de materiales similares, no obstante fueron retirados por el denunciado y llevados a lugar adecuado al efecto.

[OPCIONAL — incluir si procede]

Los objetos depositados en la vía pública y que son objeto de esta denuncia no fueron dejados inicialmente en el lugar señalado por el agente de la autoridad autor de la misma sino en lugar apropiado al efecto según hemos dejado señalado anteriormente, ignorando esta parte el procedimiento mediante el cual o las personas responsables del traslado de dichos objetos al emplazamiento referenciado por la denuncia.

[OPCIONAL — incluir si procede]

Los objetos o materiales depositados, por el lugar donde se dejaron y por la pequeña cantidad depositada, difícilmente se puede afirmar con buen criterio que puedan entorpecer la parada y estacionamiento, y así se demuestra por el hecho de que otros usuarios de la vía continuaron aparcando y estacionando en el lugar afectado sin proferir denuncias ni quejas de clase alguna.

[OPCIONAL — incluir si procede]

Los objetos o materiales depositados y que en opinión del agente denunciante pueden entorpecer la parada y estacionamiento fueron colocados en dicho lugar en la creencia de que era el sitio idóneo para ello, ante la ausencia de prohibición alguna y la frecuente existencia en dicho lugar de depósitos de similares características y, no obstante lo anterior, fueron retirados inmediatamente por el denunciado, evitando todo entorpecimiento del espacio vial afectado y enervando por consiguiente toda posible acción sancionadora que por este concepto pudiera emprenderse por la Administración Pública.

[OPCIONAL — incluir si procede]

Por parte del interesado se adoptaron las medidas necesarias para hacer desaparecer lo antes posible el obstáculo o peligro creado en la vía por causas ajenas a su voluntad, siendo su conducta la única exigible teniendo en cuenta las circunstancias del hecho denunciado, por lo que no cabe derivar de estas actuaciones responsabilidad alguna en el orden administrativo sancionador.

No es correcta la imputación realizada en la denuncia ya que por parte del inculpado no se creó el obstáculo o peligro en la vía objeto de este expediente, por lo que no le es exigible que adoptara cuanto antes ninguna determinación para hacer desaparecer una situación creada por terceros ajenos al expediente y contra los que debió dirigirse el mismo en aplicación del principio personalista que rige la culpabilidad y el procedimiento administrativo sancionador.

Como motivos formales de oposición a este expediente sancionador cabe alegar los siguientes (2):

[OPCIONAL — incluir si procede]

Prescripción de la infracción, por el transcurso de [Nº] meses [COMPLETAR], contados desde la fecha en que los hechos supuestamente se hubieron cometido.

[OPCIONAL — incluir si procede]

La caducidad el expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente se haya dictado resolución que le ponga fin;

[OPCIONAL — incluir si procede]

La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]) sino únicamente al propietario del vehículo, incumpliendo el deber de identificar al culpable para notificar la denuncia.

[OPCIONAL — incluir si procede]

La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del órgano competente para resolver a efectos de su eventual recusación.

[OPCIONAL — incluir si procede]

La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce indefensión al interesado.

[OPCIONAL — incluir si procede]

Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no les está atribuido por haberse cometido fuera de su demarcación territorial.

[OPCIONAL — incluir si procede]

Concurrencia del siguiente hecho que extingue la responsabilidad en este expediente sancionador:

[OPCIONAL — incluir si procede]

Pago anticipado [COMPLETAR].

[OPCIONAL — incluir si procede]

Haber sido ya sancionado por los mismos hechos.

[OPCIONAL — incluir si procede]

Que la propuesta de sanción inicialmente realizada consistente en el pago de una multa de [IMPORTE] euros tampoco resulta adecuada de conformidad con el principio de proporcionalidad (poca gravedad y trascendencia de los hechos, ausencia de antecedentes en el inculpado y escaso riesgo potencial creado para la seguridad vial) y demás criterios que gobiernan el ejercicio de la potestad sancionadora en materia de tráfico, atendiendo a las circunstancias expresadas.

Que, para la demostración de las afirmaciones anteriormente manifestadas en este escrito de descargos, y sin perjuicio de las demás actuaciones que de oficio sean practicadas por el órgano instructor competente, se propone la práctica de los siguientes medios de prueba:

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

[OPCIONAL — incluir si procede]

Que, subsidiariamente, en caso de no estimar la petición de archivo del expediente, se disponga la reducción de la sanción inicialmente propuesta para adecuarla a los principios de la potestad sancionadora en materia de tráfico, sin perjuicio de la interposición de los recursos que esta parte tenga por conveniente (3).

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) Uno de los defectos más graves de la actual descripción de las infracciones de tráfico es su «versatilidad» en el sentido de que una misma conducta puede estar descrita en uno o varios preceptos con calificaciones jurídicas muy diferentes. Da la impresión de que las distintas secciones del RGC han sido redactadas por personas diferentes y que cada una de ellas quería tenerlo «todo previsto» en su sección. Un ejemplo muy claro de esta técnica legislativa (tremendamente defectuosa y que nunca se aplica en beneficio del ciudadano) es la redacción del art. 5 RGC donde se contienen infracciones «leves» que, a su vez, a la vista de otros preceptos podrían ser consideradas graves. En realidad, las opciones correspondientes al artículo 5.1 del Reglamento General de Circulación son las siguientes: (01) no adoptar las medidas necesarias para hacer desaparecer lo antes posible un obstáculo o peligro creado en la vía por el denunciado, (02) no adoptar las medidas necesarias para advertir a los demás usuarios de la existencia de un peligro u obstáculo creado en la vía por el denunciado, (03) no adoptar las medidas necesarias para evitar que se dificulte la circulación con un obstáculo o peligro creado en la vía por el denunciado. Por su parte, las opciones correspondientes al artículo 5.3 del Reglamento General de Circulación son: (01) no señalizar de forma eficaz, durante el día, la presencia de un obstáculo o peligro en la vía creado por el denunciado y (02) no señalizar de forma eficaz, durante la noche, la presencia de un obstáculo o peligro en la vía creado por el denunciado. Afortunadamente la nueva redacción de la redacción codificada simplifica estas conductas de modo que a efectos de formular denuncias se tiene en cuenta la redacción simplificada que consta en el modelo para las opciones (1A) y (1B), consideradas infracciones leves.

(2) El art. 112 TR LTCVMSV señala el plazo de prescripción de las infracciones previstas en la ley, que será de tres meses para las infracciones leves y de 6 meses para las demás. Con respecto a la caducidad de las mismas, dicho artículo establece un plazo de un año desde la iniciación del procedimiento.

(3) Del art. 5 RGC se recogen en la relación codificada dos supuestos constitutivos de infracción LEVE, sancionable con multa máxima de 100 euros. En los dos supuestos, el agente denunciante debe hacer constar la descripción del objeto, obstáculo o peligro existente y que da origen al expediente sancionador; o bien la señalización empleada o la falta de la misma, pues en caso de no hacerlo así la imputación sería incorrecta, por ser genérica, y da lugar a indefensión del imputado.
