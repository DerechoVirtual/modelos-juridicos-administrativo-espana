---
name: descargos-libertad-movimientos-atencion-posicion-1607
description: "Redacta el escrito «Descargos por libertad de movimientos, atención, posición, animales y auriculares» (formulario 1607 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por libertad de movimientos, atención, posición, animales y auriculares

> Formulario 1607 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

## Párrafos opcionales (35)

Inclúyelos solo si encajan en los hechos:

- Conducir el vehículo reseñado sin mantener la propia libertad de movimientos, sin mantener el campo de visión,…
- Conducir un vehículo sin mantener la propia libertad de movimientos.…
- Conducir un vehículo sin mantener el campo necesario de visión.…
- Conducir un vehículo sin mantener la atención permanente a la conducción.…
- Conducir un vehículo sin mantener la posición adecuada.…
- Conducir un vehículo sin cuidar de que el resto de los pasajeros mantengan la posición adecuada.…
- Conducir un vehículo sin cuidar de la adecuada colocación de los objetos transportados para que no interfieran…
- Conducir un vehículo sin cuidar de la adecuada colocación de algún animal transportado para que no interfiera …
- Conducir un vehículo prestando atención a dispositivos tales como pantallas con acceso a internet, monitores d…
- Conducir usando auriculares conectados a equipos de sonido, dispositivos de telefonía móvil o cualquier otro m…
- Conducir usando cascos o auriculares conectados a un aparato receptor o reproductor de sonido.…
- Utilizar, sujetándolo con la mano, o manteniéndolo ajustado entre el casco y la cabeza del usuario, dispositiv…
- Conducir utilizando dispositivos de telefonía móvil o cualquier otro medio o sistema de comunicación (1).…
- Instalar o llevar en el vehículo inhibidores de radares o cinemómetros, o llevar en el vehículo mecanismos de …
- Instalar o llevar en los vehículos inhibidores de radares o cinemómetros o cualesquiera otros instrumentos enc…
- Llevar en el vehículo mecanismos de detección de radares o cinemómetros.…
- Negamos los hechos imputados ya que el conductor denunciado permaneció, en todo momento, en condiciones de con…
- A estos efectos por el conductor se cuidó especialmente de mantener la posición adecuada y de que la mantuvier…
- Los auriculares que en el momento de la denuncia portaba el conductor no estaban conectados a aparatos product…
- La conducción usando teléfono móvil se encuentra en estos momentos expresamente tipificada como infracción adm…
- En el presente caso la atención del conductor a los monitores está justificada, por estar estos a la vista y s…
- Prescripción de la infracción, por el transcurso de [Nº] meses [COMPLETAR], contados desde la fecha en que los…
- La caducidad el expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente se…
- La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio…
- La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del …
- La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce i…
- Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no l…
- Concurrencia del siguiente hecho que extingue la responsabilidad en este expediente sancionador:…
- Pago anticipado [COMPLETAR].…
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

- artículo 18 del Real Decreto 1428/2003
- artículos 13 y 76 del Real Decreto Legislativo 6/2015
- artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015
- artículos 25 a 31 de la Ley 40/2015
- artículo 18.1 RGC
- art. 112 TR LTCVMSV
- Ley 19/2001

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

### Formulario 1607 · Descargos por libertad de movimientos, atención, posición, animales y auriculares

- Año del modelo: 2004
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; notas del formulario agrupadas al final (3); 1 desplegables convertidos en elección en blanco; 35 párrafos opcionales señalados; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de alegaciones del denunciado dentro del expediente administrativo sancionador en materia de tráfico, oponiéndose al relato de los hechos efectuado por el denunciante (incumplimiento de las obligaciones del conductor respecto a su libertad de movimientos, visión, atención, posición adecuada, transporte de animales, uso de auriculares o de dispositivos de telefonía móvil, navegadores, inhibidores de radares o cinemómetros o sistemas de detección de estos, etc.), y por tanto a la calificación jurídica de los mismos como constitutivos de infracción administrativa. Con el fin de demostrar lo anterior y de que la autoridad administrativa acuerde el sobreseimiento del expediente sancionador, finaliza el pliego de descargo proponiendo la práctica de pruebas por el órgano instructor.

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], ante [ÓRGANO], órgano competente, como mejor proceda comparece y

DICE

Que, en virtud de este escrito, en el expediente número [Nº DE EXPEDIENTE], incoado mediante denuncia de fecha [FECHA], presenta descargos por no estar de acuerdo con el relato de los hechos en los términos descritos, ni con su calificación jurídica, ni con la propuesta de sanción inicialmente formulada en el acto de la denuncia, y todo ello de conformidad con las siguientes

ALEGACIONES

Que en este procedimiento sancionador se realiza una imputación de hechos que no son del todo exactos, al no ser lo suficientemente descriptivos de la conducta realizada, por lo que para la más completa y correcta determinación de lo sucedido es preciso poner en conocimiento del órgano instructor y del sancionador los hechos tal y como verdaderamente acaecieron:

Que, según el artículo 18 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación, y artículos 13 y 76 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), los hechos imputados han sido calificados en el expediente sancionador como constitutivos de la siguiente infracción

[OPCIONAL — incluir si procede]

Conducir el vehículo reseñado sin mantener la propia libertad de movimientos, sin mantener el campo de visión, sin mantener la atención permanente a la conducción, sin cuidar la adecuada colocación de los objetos transportados para que no interfieran la conducción, sin cuidar la adecuada colocación de algún animal transportado para que no interfiera la conducción

[OPCIONAL — incluir si procede]

Conducir un vehículo sin mantener la propia libertad de movimientos.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin mantener el campo necesario de visión.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin mantener la atención permanente a la conducción.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin mantener la posición adecuada.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin cuidar de que el resto de los pasajeros mantengan la posición adecuada.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin cuidar de la adecuada colocación de los objetos transportados para que no interfieran la conducción.

[OPCIONAL — incluir si procede]

Conducir un vehículo sin cuidar de la adecuada colocación de algún animal transportado para que no interfiera la conducción.

[OPCIONAL — incluir si procede]

Conducir un vehículo prestando atención a dispositivos tales como pantallas con acceso a internet, monitores de televisión y reproductores de vídeo o DVD.

[OPCIONAL — incluir si procede]

Conducir usando auriculares conectados a equipos de sonido, dispositivos de telefonía móvil o cualquier otro medio o sistema de comunicación

[OPCIONAL — incluir si procede]

Conducir usando cascos o auriculares conectados a un aparato receptor o reproductor de sonido.

[OPCIONAL — incluir si procede]

Utilizar, sujetándolo con la mano, o manteniéndolo ajustado entre el casco y la cabeza del usuario, dispositivos de telefonía móvil mientras se conduce.

[OPCIONAL — incluir si procede]

Conducir utilizando dispositivos de telefonía móvil o cualquier otro medio o sistema de comunicación (1).

[OPCIONAL — incluir si procede]

Instalar o llevar en el vehículo inhibidores de radares o cinemómetros, o llevar en el vehículo mecanismos de detección de radares o cinemómetros

[OPCIONAL — incluir si procede]

Instalar o llevar en los vehículos inhibidores de radares o cinemómetros o cualesquiera otros instrumentos encaminados a eludir o a interferir en el correcto funcionamiento de los sistemas de vigilancia del tráfico, así como emitir o hacer señales con dicha finalidad.

[OPCIONAL — incluir si procede]

Llevar en el vehículo mecanismos de detección de radares o cinemómetros.

Que esta imputación no es correcta ya que no se dan los elementos constitutivos y definidores de dicha infracción administrativa, por las siguientes razones:

[OPCIONAL — incluir si procede]

Negamos los hechos imputados ya que el conductor denunciado permaneció, en todo momento, en condiciones de controlar su libertad de movimientos, el campo necesario de visión y la atención permanente a la conducción para garantizar su propia seguridad, la del resto de ocupantes del vehículo y la de los demás usuarios de la vía.

[OPCIONAL — incluir si procede]

A estos efectos por el conductor se cuidó especialmente de mantener la posición adecuada y de que la mantuvieran el resto de los pasajeros, dado las instrucciones oportunas, así como la adecuada colocación de los objetos (o animales) transportados para que hubiera interferencia entre el conductor y cualquiera de ellos.

[OPCIONAL — incluir si procede]

Los auriculares que en el momento de la denuncia portaba el conductor no estaban conectados a aparatos productores o reproductores de sonido, sino que se llevaban desconectados de toda fuente sonora.

[OPCIONAL — incluir si procede]

La conducción usando teléfono móvil se encuentra en estos momentos expresamente tipificada como infracción administrativa, pero únicamente cuando su uso requiera el empleo de las manos o el uso de casos, auriculares u otros instrumentos similares. En este caso se ha usado un dispositivo de manos libres homologado, por lo que no se ha quedado mermada la capacidad de atención del conductor ni sus facultades de percepción, por lo que en esta denuncia se ha realizado una interpretación extensiva en perjuicio del interesado y prohibida por la ley, que impide interpretaciones análogas o extensivas de las normas sancionadoras y penales, por tanto al no quedar acreditada la conducción distraída o desatenta mediante el empleo manual de dispositivos de telefonía, sino el mero uso del teléfono móvil conforme a modalidades de empleo homologadas, no nos hallamos en presencia de una infracción y debe decretarse el sobreseimiento del expediente, ya que el usuario, consciente de la precaución y el dominio del vehículo en todo momento, no ha incurrido en ninguna infracción en los términos tipificados legalmente. (2)

[OPCIONAL — incluir si procede]

En el presente caso la atención del conductor a los monitores está justificada, por estar estos a la vista y ser su utilización necesaria para la visión de acceso o bajada de peatones o para la visión en vehículos con cámara de maniobras trasera, así como el dispositivo GPS.

Como motivos formales de oposición a este expediente sancionador cabe alegar los siguientes (3):

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

Que la propuesta de sanción inicialmente realizada consistente en el pago de una multa de [IMPORTE] euros, tampoco resulta adecuada de conformidad con el principio de proporcionalidad y demás criterios que gobiernan el ejercicio de la potestad sancionadora en materia de tráfico, atendiendo a las circunstancias expresadas.

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

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) La tipificación expresa de la infracción de conducir usando teléfono móvil se realizó con la modificación del artículo 13 de la LTCV tras la reforma introducida por la Ley 19/2001, que excluye el uso de los sistemas de telefonía móvil y de "cualquier otro medio o sistema de comunicación", lo que puede afectar a los taxis. Y sin embargo permite el empleo de estos medios a los agentes de la vigilancia del tráfico, lo que no es solo una curiosidad sino un trato discriminatorio y arbitrario que contradice el principio constitucional de igualdad y deja en los agentes de tráfico el riesgo que pretende castigar en los demás conductores y profesionales de la carretera.

(2) La tarea de conducir requiere la máxima atención para quien la realiza y las nuevas tecnologías son fuente de distracción para los conductores durante la realización de dicha tarea. Según la NHTSA (Agencia Nacional para la Seguridad del Tráfico en la Carretera) en los Estados Unidos, una cuarta parte de los accidentes de tráfico tienen como factor causante principal la distracción del conductor, y es por ello por lo que los nuevos sistemas tecnológicos suponen un problema de seguridad vial. La industria del automóvil, por su parte, considera que los nuevos sistemas a los que se puede acceder desde el vehículo son cada vez más modernos e incluso permiten dicho acceso a través de la voz (sistema de «manos libres»), sin tener que «detenerse a manipularlos». En la actualidad, desde el automóvil se puede navegar vía satélite por Internet, se puede operar sobre el correo electrónico, etc. Sin embargo, estos servicios, aunque se pueden hacer a través de la voz, siguen representando un peligro, porque esta actividad también supone una concentración mental. Por todo ello, su uso por parte de los conductores mientras se circula puede ser considerado infracción administrativa en aplicación de este artículo 18.1 RGC que ordena al conductor mantener la atención permanente en la conducción.

(3) El art. 112 TR LTCVMSV señala el plazo de prescripción de las infracciones previstas en la ley, que será de tres meses para las infracciones leves y de seis meses para las demás. Con respecto a la caducidad de las mismas, dicho artículo establece un plazo de un año desde la iniciación del procedimiento.
