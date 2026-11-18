---
name: demanda-abreviada-extranjeria-autorizacion-residencia-713
description: "Redacta el escrito «Demanda abreviada en extranjería: autorización de residencia y trabajo» (formulario 713 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda abreviada en extranjería: autorización de residencia y trabajo

> Formulario 0713 del plugin **Extranjería** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] COLEGIO
- [ ] CALLE
- [ ] CORREO ELECTRÓNICO
- [ ] FECHA (9 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] Nº
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con número de colegiado»; «…, con despacho profesional en»; «… el plazo para la interposición vence el»; «…, Departamento de»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSI DIGO I: Que la cuantía del procedimiento es indeterminada.…
- OTROSI DIGO II, se solicita el recibimiento a prueba con el fin de poder acreditar la realidad de las alegacio…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 78 de la LJCA
- art. 8 y 14 de la LJCA
- art. 25 de la LJCA
- artículo 45 y 46 de la LJCA
- art. 31.7 de la LO 4/2000
- art. 24 de la CE
- art. 80 del RD 1155/2024
- art. 139.1 de la LJCA
- Ley Orgánica 2/2009
- Real Decreto 1155/2024

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

### Formulario 0713 · Demanda abreviada en extranjería: autorización de residencia y trabajo

- Año del modelo: 2009
- Revisión 17-11-2026: 2 párrafos opcionales señalados; 23 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 3 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS] Letrado/a en ejercicio del Iltre. Colegio de Abogados de [COLEGIO], con número de colegiado [COMPLETAR], con despacho profesional en [COMPLETAR], calle [CALLE], número de fax/correo electrónico [CORREO ELECTRÓNICO], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], tal como se acredita por la designación de turno de oficio que se acompaña, ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, al amparo de lo dispuesto en el art. 78 de la LJCA, interpongo demanda por el Procedimiento Contencioso Administrativo Abreviado, frente a la Resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], por la que se desestima el recurso de Reposición interpuesto contra la resolución de fecha [FECHA] por la que se imponía a mi representado la sanción de expulsión con prohibición de entrada por un plazo de [Nº] años, de la que se acompaña copia como documento número 1, de conformidad a los siguientes

HECHOS

PRIMERO.- Mi mandante presentó con fecha [FECHA] solicitud de autorización de residencia permanente ante la Subdelegación/Delegación del Gobierno en [LOCALIDAD]

La Resolución de la Subdelegación/Delegación de Gobierno de fecha [FECHA], aquí impugnada, deniega la solicitud de residencia, por existir informe gubernativo desfavorable.

Esta parte interpuso recurso de alzada contra dicha resolución en fecha [FECHA], no habiendo sido contestado por lo que debe entenderse desestimado por silencio negativo.

SEGUNDO.- La denegación de la autorización de residencia en que se funda la resolución impugnada se basa exclusivamente en la existencia de un informe gubernativo desfavorable, el cual no cumple los requisitos establecidos jurisprudencialmente para tener relevancia denegatoria.

Así, la Sala Tercera del Tribunal Supremo, en su sentencia de fecha 5 de marzo de 2003, y, en igual sentid la de 28 de septiembre de 2004 del mismo Tribunal, establece que «Entiende la Sala insuficiente como para denegar el permiso solicitado la existencia de sendas diligencias penales, unas archivadas y sobreseídas, pendientes de juicio las otras, que no acreditan la puesta en peligro del orden público, tal y como hoy se debe éste interpretar».

Por tanto, la simple existencia de diligencias penales, archivadas y sobreseídas las primeras y pendientes de juicio las segundas, no son motivos suficientes para apreciar que el demandante se encuentra incurso en una conducta contraria al orden público que justifica, por sí misma, la denegación del permiso solicitado.

En este caso, si bien consta que mi representado fue detenido en dos ocasiones, lo cierto es que no se acredita que exista sentencia condenatoria en ninguno de los dos supuestos, debiendo añadirse que esta parte puede acreditar, en la medida de sus posibilidades, que le fue notificada sentencia absolutoria en el primero de los hechos reflejados en el informe acaecido el día [FECHA], la cual se acompaña por testimonio como documento número 1. En cuanto al segundo de los hechos, esta parte desconoce que haya seguido tramitándose el procedimiento al no recibir ninguna notificación.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

FUNDAMENTOS JURÍDICO PROCESALES

PRIMERO.- Corresponde la competencia objetiva y territorial al Tribunal al que me dirijo, de conformidad a lo dispuesto en el art. 8 y 14 de la LJCA, debiendo tramitarse el procedimiento por los trámites del procedimiento abreviado, al tratarse de una resolución dictada por la Administración periférica en materia de extranjería.

SEGUNDO.- La LJCA, art. 19.1 a), sobre legitimación activa del demandante por tener indudable interés directo en la anulación del acto objeto de impugnación.

TERCERO.- El art. 25 de la LJCA sobre la impugnabilidad del acto objeto de impugnación, por ser una resolución que pone fin a la vía administrativa.

CUARTO.- El artículo 45 y 46 de la LJCA, sobre requisitos y plazo para la interposición del recurso contencioso administrativo. Al haberse desestimado presuntamente el recurso administrativo, el plazo se inicia el día [FECHA], el plazo para la interposición vence el [COMPLETAR] Presentado el escrito de interposición del recurso contencioso administrativo, antes de dicha fecha, lo es dentro del plazo.

FUNDAMENTOS JURÍDICO MATERIALES

QUINTO.- La resolución impugnada es nula de pleno derecho por cuanto se funda en un informe desfavorable como causa de denegación de la renovación, cuando la reforma operada por Ley Orgánica 2/2009 ha flexibilizado dicho requisito, puesto que ni tan siquiera se contempla la condena como causa de denegación de la autorización; así, el art. 31.7 de la LO 4/2000, reformado por la LO 2/2009, el cual establece que «para la renovación de las autorizaciones de residencia temporal, se valorará en su caso: 1º Los antecedentes penales, considerando la existencia de indultos o las situaciones de remisión condicional de la pena o la suspensión de la pena privativa de libertad. 2º El incumplimiento de las obligaciones del extranjero en materia tributaria y de seguridad social. A los efectos de dicha renovación, se valorará especialmente el esfuerzo de integración del extranjero que aconseje su renovación, acreditado mediante un informe positivo de la Comunidad Autónoma que certifique la asistencia a las acciones formativas contempladas en el artículo 2 ter de esta Ley», y el art. 80.5 del Reglamento de Extranjería. En este punto, la resolución se funda erróneamente en el art. 78 y 80 del Reglamento de Extranjería, aprobado por el Real Decreto 1155/2024, de 19 de noviembre, al haberse informado desfavorablemente por la Comisaría de Extranjería y Documentación la renovación, al constarle a mi representado dos detenciones policiales; sin embargo, es indudable que si la condena no es causa suficiente para denegar la solicitud, con menor razón podrá serlo un informe fundado exclusivamente en la existencia de antecedentes policiales.

Por tanto, el informe gubernativo no es suficiente para denegar la solicitud, cumplidos que han sido los demás requisitos del art. 80 del citado RD 1155/2024, como pone de manifiesto reiterada jurisprudencia que interpreta que la mera existencia de antecedentes policiales no es suficiente para justificar un informe desfavorable, sobre todo cuando el carácter desfavorable del mismo se apoya de forma exclusiva en el hecho de existir proceso judicial en trámite, en el que no consta, al tiempo de dictarse la resolución administrativa denegatoria del permiso en cuestión, que haya recaído sentencia firme, en un sentido u otro. La jurisprudencia interpreta que el informe desfavorable, sin mediar antecedentes penales y una sentencia firme, quebranta la presunción de inocencia establecida por el art. 24 de la CE, por cuanto que se está concediendo a tales antecedentes policiales un valor que no respeta tal presunción de inocencia.

Este criterio se recoge, entre otras, en las SSTSJ de Cataluña de 27 de julio de 2010 y Murcia de 14 de octubre de 2011, que indican que hay que tener en cuenta la modificación realizada de la Ley Orgánica 2/2009, de 11 de diciembre, donde la carencia de antecedentes penales ya no es un requisito sine qua non para conceder la autorización, sino una circunstancia a valorar, con lo que con menor motivo se puede fundar la denegación en meros antecedentes policiales.

SEXTO.- La falta de justificación de la denegación y el cumplimiento de los requisitos establecidos para la renovación deben determinar la concesión de la autorización. En este sentido, mi representado cumple los requisitos establecidos para la renovación, recogidos en el art. 80 del RD 1155/2024 cuando dispone que «la renovación de las autorizaciones de residencia temporal y trabajo por cuenta ajena deberá solicitarse, en modelo oficial, durante los dos meses previos a la fecha de expiración de la vigencia de su autorización. La presentación de la solicitud en este plazo prorrogará la validez de la autorización anterior hasta la resolución del procedimiento. También se prorrogará hasta la resolución del procedimiento en el supuesto en que la solicitud se presentase dentro de los noventa días naturales posteriores a la fecha en que hubiera finalizado la vigencia de la anterior autorización, sin perjuicio de la incoación del correspondiente procedimiento sancionador por la infracción en la que se hubiese incurrido», debiendo renovarse la autorización de residencia y trabajo por cuenta ajena cuando se acredite la continuidad en la relación laboral que dio lugar a la concesión de la autorización cuya renovación se pretende, todo lo cual resulta justificado en el expediente, de lo que se deriva que debe concederse la renovación solicitada.

SÉPTIMO.- En relación a las costas, el art. 139.1 de la LJCA, introduce el principio del vencimiento objetivo, disponiendo que las costas se impondrán a la parte que haya visto rechazadas todas sus pretensiones, salvo en los casos excepcionales de serias dudas de hecho o de derecho, que en este caso no existen puesto que de la argumentación realizada en este escrito de demanda ha quedado patente la disconformidad a derecho de la actividad administrativa impugnada.

En virtud de lo expuesto, al Tribunal

SUPLICO que se tenga por interpuesta demanda en procedimiento Contencioso Administrativo Abreviado, frente a la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA] y previos los trámites legales y celebración de la preceptiva vista, se dicte sentencia por la que declare nulo y deje sin efecto el acto objeto de recurso, declarando el derecho de mi representado a que le sea concedida la autorización de residencia, con expresa imposición de las costas a la Administración demandada en caso de oponerse al recurso.

[OPCIONAL — incluir si procede]

OTROSI DIGO I: Que la cuantía del procedimiento es indeterminada.

SUPLICO, que se tenga por hecha dicha manifestación a los efectos oportunos.

[OPCIONAL — incluir si procede]

OTROSI DIGO II, se solicita el recibimiento a prueba con el fin de poder acreditar la realidad de las alegaciones de la demanda, expresadas en el hecho segundo, y que versará sobre el cumplimiento de los requisitos para la renovación y el esfuerzo de integración realizado por mi representado.

Para acreditar tales hechos, y sin perjuicio de lo que resulte del traslado del expediente administrativo y de la proposición que se pueda realizar en el acto de la vista, esta parte PROPONE de los siguientes medios de prueba:

I. DOCUMENTAL, que se admitan los documentos acompañados a este escrito de demanda.
II. MÁS DOCUMENTAL, expidiendo oficio a la Comunidad Autónoma de [LOCALIDAD], Departamento de [COMPLETAR] para que emita el informe prevenido en el artículo 80.6 del Reglamento de Extranjería sobre el esfuerzo de integración realizado por mi representado.
III.

Por lo que SUPLICO A LA SALA acuerde de conformidad en el momento procesal correspondiente, admitiendo los medios de prueba propuestos y citando a los testigos para el acto de la vista.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
