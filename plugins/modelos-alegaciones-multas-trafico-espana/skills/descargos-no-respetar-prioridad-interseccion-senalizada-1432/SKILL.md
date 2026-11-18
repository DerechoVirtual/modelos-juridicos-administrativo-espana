---
name: descargos-no-respetar-prioridad-interseccion-senalizada-1432
description: "Redacta el escrito «Descargos por no respetar la prioridad en intersección señalizada» (formulario 1432 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Descargos por no respetar la prioridad en intersección señalizada

> Formulario 1432 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] DESCRIBIR (5 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…, se realizó por»; «…, se realizó por»; «…, se realizó por»; «…, se realizó por»; «…n de la infracción, por el transcurso de»; «…pago anticipado»; «…nción inicialmente realizada consistente»; «…dad con el principio de proporcionalidad»; «…consistente en que se tome declaración a»; «…, en su condición de»; «…, en el que se acredita»; …

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:

## Párrafos opcionales (19)

Inclúyelos solo si encajan en los hechos:

- Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la r…
- Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la r…
- Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la r…
- Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la r…
- Es procedente afirmar que la denuncia está incorrectamente formulada, por cuanto se limita a realizar una afir…
- Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos sup…
- La caducidad del expediente, por el paso de un año desde el inicio del mismo sin que hasta la fecha presente s…
- La falta de notificación del expediente al autor de la infracción (D./Dña. [NOMBRE Y APELLIDOS], con domicilio…
- La ausencia en el boletín de denuncia de los datos esenciales para identificar al instructor y al titular del …
- La ausencia del empleo de la lengua oficial en esta Comunidad Autónoma, lo que resulta obligatorio y produce i…
- Falta de competencia del órgano instructor y sancionador por tratarse de una infracción cuyo conocimiento no l…
- Concurrencia del siguiente hecho que extingue la responsabilidad:…
- pago anticipado [COMPLETAR]…
- haber sido ya sancionado por los mismos hechos en este expediente sancionador.…
- Testifical, consistente en que se tome declaración a [COMPLETAR], en cuanto testigos presenciales de los hecho…
- Pericial, consistente en informe de fecha [FECHA], emitido por [ÓRGANO O PERSONA], en su condición de [COMPLET…
- Documental, consistente en escrito de fecha [FECHA], suscrito por [ÓRGANO O PERSONA], en el que se hace refere…
- Reconocimiento sobre el terreno por el órgano instructor para apreciar y acreditar que [COMPLETAR] y los demás…
- Informe de ratificación, elaborado por el mismo agente que formuló la denuncia, en el que además se aclare que…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 56 del Real Decreto 1428/2003
- artículo 23.1 del Real Decreto Legislativo 6/2015
- artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015
- artículos 25 a 31 de la Ley 40/2015

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

### Formulario 1432 · Descargos por no respetar la prioridad en intersección señalizada

- Año del modelo: 2004
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 2 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 19 párrafos opcionales señalados; 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante [ÓRGANO], órgano competente, como mejor proceda comparece y

DICE

Que en virtud de este escrito, en el expediente número [Nº DE EXPEDIENTE], incoado mediante denuncia de fecha [FECHA], presenta descargos por no estar de acuerdo con el relato de los hechos en los términos descritos, ni con su calificación jurídica, ni con la propuesta de sanción inicialmente formulada en el acto de la denuncia, y todo ello de conformidad con las siguientes

ALEGACIONES

Que en este procedimiento sancionador, se realiza una imputación de hechos que no son del todo exactos, al no ser lo suficientemente descriptivos de la conducta realizada, por lo que para la más completa y correcta determinación de lo sucedido es preciso poner en conocimiento del órgano instructor y del sancionador los hechos tal y como verdaderamente acaecieron:

Que, según el artículo 56 del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación y artículo 23.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en adelante, TR LTCVMSV), los hechos imputados han sido calificados en el expediente sancionador como constitutivos de la siguiente infracción:

[ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:]
— Opción correspondiente al artículo 56.2 del Reglamento General de la Circulación: No ceder el paso en intersección señalizada, obligando al conductor de otro vehículo a maniobrar bruscamente.
— Opción correspondiente al artículo 56.3 del Reglamento General de la Circulación:
— Opciones correspondientes al artículo 56.5 del Reglamento General de la Circulación:

Que esta imputación no es correcta ya que no se dan los elementos constitutivos y definidores de dicha infracción administrativa, por las siguientes razones:

[OPCIONAL — incluir si procede]

Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la realización de una infracción administrativa de las normas sobre prioridad de paso en "intersecciones señalizadas" ya que la conducta del denunciado consistente en [DESCRIBIR], se realizó por [COMPLETAR], por lo que no cabe formular imputación alguna, debiendo tenerse por cumplida la norma que establece que los conductores de vehículos que se aproximen a una intersección regulada por agente de la circulación deberán detener sus vehículos, cuando así lo ordene de forma reglamentaria.

[OPCIONAL — incluir si procede]

Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la realización de una infracción administrativa de las normas sobre prioridad de paso en "intersecciones señalizadas" ya que la conducta del denunciado consistente en [DESCRIBIR], se realizó por [COMPLETAR], por lo que no cabe formular imputación alguna, debiendo tenerse por cumplida la norma que establece que todo conductor de un vehículo que se aproxime a una intersección regulada por semáforos debe detener su vehículo para ceder el paso cuando así lo indiquen las luces correspondientes.

[OPCIONAL — incluir si procede]

Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la realización de una infracción administrativa de las normas sobre prioridad de paso en "intersecciones señalizadas" ya que la conducta del denunciado consistente en [DESCRIBIR], se realizó por [COMPLETAR], por lo que no cabe formular imputación alguna, debiendo tenerse por cumplida la norma que establece que los conductores de los vehículos que se aproximen a una intersección señalizada con señal de intersección con prioridad, o que circulen por una vía señalizada con señal de calzada con prioridad, tendrán prioridad de paso sobre los vehículos que circulen por otra vía o procedan de ella.

[OPCIONAL — incluir si procede]

Negamos la veracidad de los hechos imputados, en la versión dada por el agente denunciante, y, por tanto, la realización de una infracción administrativa de las normas sobre prioridad de paso en "intersecciones señalizadas" ya que la conducta del denunciado consistente en [DESCRIBIR], se realizó por [COMPLETAR], por lo que no cabe formular imputación alguna, debiendo tenerse por cumplida la norma que establece que en las intersecciones de vías señalizadas con señal de "ceda el paso", "detención obligatoria" o de "stop", los conductores cederán el paso a los vehículos que transiten por la vía preferente, sea cualquiera el lado por el que se aproximen, llegando por completo a detener su marcha cuando sea preciso y, en todo caso, cuando así lo indique la señal correspondiente.

[OPCIONAL — incluir si procede]

Es procedente afirmar que la denuncia está incorrectamente formulada, por cuanto se limita a realizar una afirmación general de incumplimiento del precepto, en los términos definidos reglamentariamente, pero sin hacer suficiente referencia a los hechos concretos que individualizan la denuncia formulada, por lo se ha causado una grave indefensión al interesado, ya que no puede articular un pliego de descargos de forma adecuada y se deja también al órgano competente para sancionar sin elementos de juicio adecuados en lo que se refiere a la determinación de la infracción y las circunstancias modificativas de la responsabilidad que deben tenerse en cuenta para el correcto ejercicio de la potestad sancionadora en materia de tráfico.

Como motivos formales de oposición a este expediente sancionador cabe alegar los siguientes:

[OPCIONAL — incluir si procede]

Prescripción de la infracción, por el transcurso de [COMPLETAR], contados desde la fecha en que los hechos supuestamente se hubieron cometido.

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

pago anticipado [COMPLETAR]

[OPCIONAL — incluir si procede]

haber sido ya sancionado por los mismos hechos en este expediente sancionador.

Que la propuesta de sanción inicialmente realizada consistente [COMPLETAR], tampoco resulta adecuada de conformidad con el principio de proporcionalidad [COMPLETAR] y demás criterios que gobiernan el ejercicio de la potestad sancionadora en materia de tráfico, atendiendo a las circunstancias expresadas.

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

Informe de ratificación, elaborado por el mismo agente que formuló la denuncia, en el que además se aclare que [COMPLETAR] lo que resulta necesario para justificar la conducta del conductor en este expediente por incumplimiento de normas de prioridad en intersecciones señalizadas.

Por cuanto antecede y de conformidad con las previsiones de los artículos 93.1 y 95.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: El RD 320/1994 (arts. 10.1 y 12.1) daba 15 días; hoy rige el plazo de 20 días naturales del TR LSV para alegar y proponer prueba o pagar con reducción (arts. 93.1 y 95.1). El RD 320/1994 sigue formalmente vigente pero desplazado por el título V del TR LSV. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 93.1 y 95.1; RD 320/1994, BOE-A-1994-8985 arts. 10 y 12.], en relación con los artículos 25 a 31 de la Ley 40/2015 [NOTA DE REVISIÓN: Errata tipográfica (falta espacio). Fuente: Ley 40/2015 arts. 25-31.], de 1 de octubre, de Régimen Jurídico del Sector Público,

SOLICITA

Que se tenga por presentado este escrito de descargos y, previa la práctica de las pruebas propuestas y la tramitación que proceda, se dicte propuesta de resolución en la que se acuerde el sobreseimiento del expediente sancionador.

Que, subsidiariamente, en caso de no estimar la petición de archivo del expediente, se disponga la reducción de la sanción inicialmente propuesta para adecuarla a los principios de la potestad sancionadora en materia de tráfico, sin perjuicio de la interposición de los recursos que esta parte tenga por conveniente.

Que, finalmente, se disponga dejar sin efecto la sanción, en lo que se refiere a [DESCRIBIR].

En [LUGAR], a [FECHA].

Firmado:
