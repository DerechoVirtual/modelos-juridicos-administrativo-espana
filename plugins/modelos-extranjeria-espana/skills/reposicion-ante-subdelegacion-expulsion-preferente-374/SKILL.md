---
name: reposicion-ante-subdelegacion-expulsion-preferente-374
description: "Redacta el escrito «Reposición ante la Subdelegación en expulsión preferente» (formulario 374 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición ante la Subdelegación en expulsión preferente

> Formulario 0374 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] COLEGIO
- [ ] NÚMERO
- [ ] NACIONALIDAD
- [ ] FECHA (5 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DEL GOBIERNO EN»; «…a la expulsión del territorio español de»; «… la Comisaría de Policía del distrito de»; «…, a [FECHA]. Fdo:»

## Elecciones que hay que hacer

- DELEGACIÓN / SUBDELEGACIÓN

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 53.1.a) de la Ley Orgánica 4/2000
- artículo 124 de la Ley 39/2015
- artículo 123.1 de la Ley 39/2015
- artículo 20.2 de la Ley Orgánica 4/2000
- artículo 55.3 de la Ley Orgánica 4/2000
- artículo 234.4 del Real Decreto 1155/2024
- artículo 66 de la Ley 39/2015
- Ley Orgánica 2/2009

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

### Formulario 0374 · Reposición ante la Subdelegación en expulsión preferente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: DELEGACIÓN / SUBDELEGACIÓN] DEL GOBIERNO EN [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], abogado/a colegiado/a por el Ilustre Colegio de Abogados de [COLEGIO] con el n.º [NÚMERO], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad [NACIONALIDAD], ante este organismo comparezco para formular RECURSO DE REPOSICIÓN contra la resolución de fecha [FECHA], que ha sido notificada el día [FECHA] por la que se decretaba la expulsión del territorio español de [COMPLETAR], con prohibición de entrada en territorio español por un período de tres años, copia de la cual se adjunta con el presente escrito.

HECHOS

Primero.- El día [FECHA], fue incoado Expediente Administrativo de Expulsión por la Comisaría de Policía del distrito de [COMPLETAR], por la presunta infracción del artículo 53.1.a) de la Ley Orgánica 4/2000, reformada por Ley Orgánica 2/2009.

Segundo.- El motivo de la detención de D./Dña. [NOMBRE Y APELLIDOS] fue el carecer de autorización de residencia en España, sin que constara ninguna otra circunstancia en la notificación de acuerdo de inicio del expediente sancionador.

Tercero.- Se formularon alegaciones dentro del plazo de 48 horas previsto por la legislación vigente, alegando la existencia de una situación de arraigo familiar en España del interesado.

Cuarto.- El día [FECHA] fue notificado por fax acuerdo por el que se procedía al cambio de instructor del expediente sancionador.

Quinto.- En contra de lo solicitado en el escrito de alegaciones y a pesar de los argumentos expuestos y la documentación que se adjuntó, se ha dictado la resolución ahora recurrida.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el artículo 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el artículo 123.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta ante el órgano que dictó la resolución.

III

La legislación aplicable al presente procedimiento está contenida en los artículos 63 y ss de la Ley Orgánica 4/2000 y 233 y ss de su Reglamento de Ejecución aprobado por Real Decreto 1155/2024, de 19 de noviembre

En particular es de aplicación el artículo 20.2 de la Ley Orgánica 4/2000, que garantiza el principio de contradicción, audiencia al interesado y motivación de las resoluciones, el Título VI de la Ley 39/2015 del Procedimiento Administrativo Común de las Administraciones Públicas.

IV

Falta de motivación de la resolución recurrida. El artículo 55.1.b) del mencionado cuerpo legal prevé la imposición de una sanción de multa para las infracciones graves, como sería el supuesto del artículo 53.1.a).

Posteriormente, establece en su artículo 57.1 que en este supuesto podrá aplicarse en lugar de la sanción de multa la expulsión del territorio español y añade en su artículo 55.3 que «para la graduación de las sanciones el órgano competente en imponerlas se ajustará a criterios de proporcionalidad, valorando el grado e culpabilidad, y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia».

Se deducen, pues, de la mencionada regulación los siguientes extremos:

— La estancia irregular en España puede ser sancionada con multa o con expulsión del territorio español.
— La sanción principal en los casos de estancia irregular es la de multa, como claramente se deduce del tenor literal de artículo 57.1 cuando establece que «podrá aplicarseen lugar de la sanción de multala expulsión del territorio nacional».
— Si la sanción principal es la de multa, la Administración, en caso de optar por aplicar la sanción de expulsión del territorio español deberá motivar de forma específica e individualizada el porqué se ha optado por esta sanción, mas grave y de aplicación subsidiaria.
— En caso de aplicación de la sanción de expulsión deberán aplicarse los criterios del artículo 55.3 de la Ley Orgánica 4/2000, debiendo la Administración especificar cuáles son las razones de proporcionalidad, de grado de subjetividad, de daño o riesgo derivado de la infracción que concurren para la imposición de la sanción más grave.

Así lo entendió la STS (Sección 5.ª de la Sala de lo Contencioso-Administrativo), de 22 de diciembre de 2005, Rec. 444/2003, doctrina reiterada posteriormente por repetidas sentencias, cuando afirma que:

«Tratándose de supuestos en que la causa de expulsión es pura y simplemente, la permanencia ilegal, sin otros hechos negativos, es claro que la Administración habrá de motivar de forma expresa por qué acude a la sanción de expulsión, ya que la permanencia ilegal, en principio, como veíamos, se sanciona con multa.

Pero en los supuestos en que en el expediente administrativo consten, además de la permanencia ilegal, otros datos negativos sobre la conducta del interesado o sus circunstancias, y esos datos sean de tal entidad que unidos a la estancia ilegal, justifiquen la expulsión, no dejará esta de estar motivada por que no se haga mención de ellos en la propia resolución sancionadora».

En el presente caso no existió más circunstancia para la incoación del expediente sancionador que la mera estancia ilegal en España, habiéndose alegado además la existencia de una situación de arraigo familiar en España, dato sobre el que no consta que la Administración realizara averiguación alguna y que no ha sido tenido en cuenta en el procedimiento, a pesar de haberse propuesto la realización de prueba a tal efecto.

Por ello, lo apropiado hubiera sido imponer, en todo caso, la sanción de multa prevista por la legislación de extranjería vigente.

Al no hacerlo así, y no habiendo motivado cual es la causa que llevó a imponer la sanción de expulsión, se incurre en causa de nulidad de la resolución recurrida.

V

Criterio de proporcionalidad. En caso de que la propuesta de expulsión se resuelva en sentido afirmativo, se pueden causar perjuicios de difícil reparación.

En caso de estimarse que el denunciado es responsable de los hechos que se le imputan e incurso en supuesto de sanción administrativa, ésta ha de ser la más favorable al mismo, conforme al criterio de proporcionalidad alegado.

El artículo 55.3 de la Ley Orgánica 4/2000, establece que «para la graduación de las sanciones, el órgano competente en imponerlas se ajustará a criterios de proporcionalidad, valorando el grado de culpabilidad y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia».

El presente caso no se expone ninguna circunstancia que acredite un exceso de culpabilidad, daño producido o riesgo derivado de la infracción, al no constar que el denunciado hubiera desatendido una anterior orden de expulsión o de salida obligatoria ni ninguna otra infracción a la legislación de extranjería.

VI

En la instrucción del procedimiento se ha incurrido en varias infracciones de la normativa reguladora, en concreto las siguientes:

- No se notificó al interesado la propuesta de resolución tal como establece el artículo 234.4 del Real Decreto 1155/2024, de 19 de noviembre.
- El cambio de instructor decretado por el Comisario Jefe de la Brigada Provincial de Extranjería y Documentación. La competencia para designar un nuevo instructor la hubiera tenido el instructor inicial del procedimiento (el funcionario con carnet profesional n.º (...) adscrito a la Comisaría de Latina), no un nuevo órgano que se inmiscuya en un procedimiento que no ordenó incoar. Ello es causa de nulidad del procedimiento y consecuentemente, de la resolución recurrida, por entenderse que se ha dictado por organismo incompetente para ello.

Así lo ha establecido la Sentencia del Tribunal Supremo (Sala de lo Contencioso, Sección Quinta) de 16 de marzo de 2006, Rec. 7269/2002, considerando dichas circunstancias causas de nulidad de la resolución recurrida.

VII

A efectos de notificaciones, según preceptúa el artículo 66 de la Ley 39/2015, de 1 de octubre, se señala el domicilio del/de la letrado/a D./Dña. [NOMBRE Y APELLIDOS]:

Por lo expuesto,

SOLICITO

Que sea revocada la resolución recurrida, por considerar que los hechos relatados y los fundamentos de derecho expuestos, desvirtúan los fundamentos de derecho de la resolución recurrida, dictándose una nueva mediante la cual se exima al interesado de responsabilidad administrativa alguna.

En [LUGAR], a [FECHA].

Fdo: [COMPLETAR].
