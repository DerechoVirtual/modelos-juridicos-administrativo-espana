---
name: demanda-contra-denegacion-asilo-358
description: "Redacta el escrito «Demanda contra la denegación de asilo» (formulario 358 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra la denegación de asilo

> Formulario 0358 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Asilo: desde el 12-6-2026 se aplica el Reglamento (UE) 2024/1347 (deroga la Directiva 2011/95/UE). La Ley 12/2009 no ha cambiado de texto.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] FECHA (7 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procedimiento Ordinario»; «…A LA SECCION»; «… la persecución que sufría su familia en»; «…Por ser Justicia que pido en Madrid a»; «…de»; «…de»; «… un informe sobre la situación actual en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 11 de la LJCA
- art. 19.1.a) de la LJCA
- art. 139 de la LJCA
- artículo 4 de la Ley 12/2009
- art. 10 de la Ley 12/2009
- art. 37.b) de la Ley 12/2009
- artículo 40.1 de la LJCA
- artículo 60 de la LJCA
- artículo 37.b) de la Ley 12/2009

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

### Formulario 0358 · Demanda contra la denegación de asilo

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); 21 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Asilo: desde el 12-6-2026 se aplica el Reglamento (UE) 2024/1347 (deroga la Directiva 2011/95/UE). La Ley 12/2009 no ha cambiado de texto.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Procedimiento Ordinario [COMPLETAR]

A LA SECCION [COMPLETAR] DE LA SALA DE LO CONTENCIOSOADMINISTRATIVO DE LA AUDIENCIA NACIONAL

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditadoen los autos referenciados, antela Sala comparezco y como mejor proceda en Derecho DIGO:

Que el día [FECHA] me ha sido notificada diligencia de ordenación de fecha [FECHA] por la que se acuerda la entrega de expediente administrativo para formular demanda en el plazo de veinte días y dentro del plazo conferido, formalizo la demanda basándome en los siguientes

HECHOS

Primero.— D./Dña. [NOMBRE Y APELLIDOS] presentó solicitud de protección internacional el día [FECHA]. Dicha solicitud se fundamentaba en la persecución que sufría su familia en [COMPLETAR] por ser miembros de la Iglesia Evangelista.

Segundo.— Lasolicitud de protección internacional fue denegada mediante resolución del Ministerio del Interior de fecha [FECHA].

La denegación de la protección internacional solicitadaestaba motivada en que “no se ha alegado ninguna de las causas que dan lugar a la concesión de la protección internacional”.

Se consideraba, asimismo, que "no se aprecia la existencia de temores fundados de persecución por motivos de raza, religión, nacionalidad, pertenencia a determinado grupo social u opiniones políticas que permitan reconocer la condición de refugiado, tal y como exige e l artículo 1.A.2 párrafo primero de la Convención de Ginebra de 1951, sobre el Estatuto de los Refugiados y conforme a lo dispuesto en el artículo I.2 del Protocolo de Nueva York de 1967, sobre dicho Estatuto'.

Adicionalmente, se afirmaba en la resolución recurrida que “no se desprenden razones humanitarias o de interés público para autorizar la permanencia en España del solicitante”.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

Competencia. La competencia para conocer del recurso corresponde a la Sala de lo Contencioso-Administrativo de la Audiencia Nacional, según lo dispuesto en el art. 11 de la LJCA.

No obstante, para el supuesto de que no se entendiera así, procederá que se remitan as actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en el artículo 7.3 de la ley de esta Jurisdicción.

II

Legitimación. Está legitimado mi representado en virtud de lo establecido en el art. 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

III

Plazo de formulación de la demanda. Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

IV

Costas. En lo relativo a la imposición de costas, es de aplicación el art. 139 de la LJCA. Caso de oponerse al presente recurso, debe estimarse que la Administración actúa con mala fe o temeridad, por lo que deberán imponerse las costas del presente proceso a la Administración demandada.

V

Respecto al motivo de denegación de la solicitud de protección internacional, debe manifestarse el desacuerdo con la resolución recurrida, por cuanto en la solicitud de asilo de mi representado se expusieron hechos que constituyen una persecución personal a él y a sus familiares por uno de los motivos expresamente recogidos en el artículo 1 de la Convención de Ginebra de 1951 sobre el Estatuto del Refugiado, por cuanto el solicitante manifestaba sufrir persecución por motivos religiosos.

Si bien es cierto que el agente de la persecución sufrida era un agente no estatal, el interesado expresa que dicha persecución se desarrolla con el tácito consentimiento de las autoridades que no hacen nada para impedirla.

Debe, pues, considerarse que lo alegado por mi representado es una de las causas previstas en la Convención de Ginebra para la concesión de la protección solicitada y en consecuencia, no estimarse el motivo de denegación de la solicitud de asilo.

VI

Respecto a la alegación de motivos, debe tenerse en cuenta lo que establece la Oficina del Alto Comisionado de las Naciones Unidas para los Refugiados (ACNUR) en su "Manual de procedimientos y criterios para determinar la condición del refugiado".

Este manual, establece que 'la persecución suele ser resultado de la actuación de las autoridades de un país, Puede también emanar de sectores de la población que no respetan las normas establecidas por las leyes de su país. La intolerancia religiosa, equiparable a persecución, en país por lo demás no confesional, en el que importantes sectores de la población no respetan las creencias religiosas de su ciudadanos es un buen ejemplo.

El comportamiento vejatorio o gravemente discriminatorio observado por ciertos sectores de la población local puede equipararse a la persecución si es deliberadamente tolerado por las autoridades o si éstas se niegan a proporcionar una protección eficaz o son incapaces de hacerlo”..

Asimismo, en dicho Manual también se establece que:

71. La Declaración Universal de Derechos Humanos y los Pactos Internacionales de Derechos Humanos proclaman el derecho de toda persona a la libertad de pensamiento, de conciencia y de religión, derecho que incluye la libertad de cambiar de religión y la libertad de manifestar su religión, tanto en público como en privado, por la enseñanza, la práctica, el culto y la observancia.

72. La persecución por “motivos de religión” puede adoptar diversas formas, por ejemplo, la prohibición de pertenecer a una comunidad religiosa, del culto en privado o en público, de la instrucción religiosa, o bien graves medidas de discriminación impuestas a las personas debido a la práctica de su religión o por pertenecer a una determinada comunidad religiosa.

73. Generalmente, el mero hecho de pertenecer a una comunidad religiosa determinada no bastará para justificar la reclamación de la condición de refugiado. Sin embargo, en ciertas circunstancias especiales, la mera pertenencia puede ser una razón suficiente.

De acuerdo, pues, con los criterios del ACNUR, no debería ser motivo suficiente para denegar una solicitud de asilo el hecho de que el solicitante alegue sufrir persecución por parte de grupos ajenos al gobierno o autoridades locales. Si, como ocurre en el caso presente, las autoridades locales no quieren o no son capaces de proporcionar una protección real y efectiva contra este tipo de persecución, debería entenderse que concurre una de las causas de reconocimiento de la condición de refugiado.

VII

Más recientemente, el ACNUR publicó unas Directrices sobre Protección Internacional relativas a las solicitudes de asilo por motivos religiosos bajo el artículo 1.a).2 de la Convención de 1951 y/o el Protocolo de 1967 sobre el Estatuto de los Refugiados.

En dichas directrices se establece lo siguiente:

11. El derecho a la libertad religiosa incluye la libertad de manifestar la religión o las creencias de su elección, ya sea individualmente o colectivamente mediante el culto, la celebración de los ritos, las prácticas y la enseñanza, tanto en público como en privado.

12. La persecución por motivos religiosos puede, por tanto, adoptar diversas formas.

Dependiendo de las circunstancias particulares de cada caso, incluyendo el impacto que tiene sobre la persona afectada, ejemplos de persecución podrían ser la prohibición de pertenecer a una comunidad religiosa, del culto en privado o en público, de la instrucción religiosa o bien, a la imposición de graves medidas de discriminación a las personas debido a la práctica de su religión o por pertenecer o ser identificados con una comunidad religiosa en particular, o porque han cambiado su fe. De igual manera, en determinados casos, en las comunidades donde existe una religión dominante o hay una correlación cercana entre el Estado y las instituciones religiosas, la discriminación contra quienes no profesen la religión dominante o no adhieran a sus prácticas, podría equivaler a persecución9 en un caso particular. La persecución puede ser inter-religiosa (dirigida contra adherentes o comunidades de diferente fe), intra-religiosa (dentro de la misma religión, pero en diferentes sectas o entre miembros de una misma secta) o una combinación de ambas10. El solicitante puede pertenecer a una minoría religiosa o a una mayoría. Las solicitudes por motivos religiosos también pueden ser presentadas por individuos casados donde los cónyuges adhieren a diferentes religiones o pertenecen a distintas comunidades.

13. Aplicando el mismo estándar que para los otros motivos de la Convención, las creencias religiosas, la identidad o la forma de vida pueden ser consideradas características tan fundamentales para la “identidad” humana que uno no debería ser obligado a esconder, cambiar o renunciar a ellas con el objeto de evitar la persecución.

14. Cada solicitud requiere del examen de sus méritos con base en la situación del individuo.

Áreas relevantes de investigación incluyen el perfil individual y las experiencias personales del solicitante; sus creencias religiosas, identidad y/o forma de vida; qué tan importante es esto para el solicitante; qué efectos tienen las restricciones sobre el individuo; la naturaleza de su rol y actividades en el marco de su religión; si estas actividades han llamado o podrían llamar la atención del perseguidor y si podrían resultar en un trato que equivalga a persecución. En este contexto, un temor fundado de persecución “no necesariamente está basado en la experiencia personal del solicitante”. Por ejemplo, lo que le haya sucedido a amigos y parientes del solicitante o a otros miembros del mismo grupo religioso --es decir, a otros individuos en la misma situación--, “puede ser indicio suficiente de que sus temores de convertirse también, más tarde o más temprano, en víctima de persecución son fundados”

VIII

En apoyo del relato del solicitante puede citarse lo expuesto por el Departamento de Estado de Estados Unidos, que en informe de 26 de Octubre de 2009, relativo a la situación de la libertad religiosa en la Federación Rusa afirmaba que:

“Algunas agencias federales, como el Departamento de Organizaciones sin ánimo de lucro del Ministerio de Justicia, y muchas autoridades locales continuaron restringiendo los derechos de algunas minorías religiosas.

Hay indicadores de que servicios de seguridad como el FSB (Servicio Federal de Seguridad), trataba a los líderes de algunos grupos islámicos y no tradiciones, como los Testigos de Jehová, como amenazas a la seguridad.

El Gobierno ha impuesto de forma selectiva restricciones a la libertad religiosa. Las restricciones a la libertad religiosa generalmente se encuentran en cuatro categorías: registro de organizaciones religiosas, acceso a lugares de culto (incluyendo el acceso a terrenos y permisos de construcción), concesión de visados para personal religioso extranjero y acoso gubernamental de personas y organizaciones religiosas.

Existen informe creíbles de que individuos de los servicios federales de seguridad y otros cuerpos de seguridad acosaron a algunos grupos religiosos minoritarios, les investigaron por supuestas actividades criminales e infracciones fiscales y presionaron a propietarios de inmuebles para que rescindieran los contratos con estos grupos.

Se cree que en algunos casos los servicios de seguridad han influidos al Ministro de Justicia para rechazar solicitudes de registro”.

IX

Respecto a la orden de salida que acompaña a la resolución recurrida, se considera que debe ser dejada sinefecto, pues coloca a mirepresentado en situaciónde irregularidad con arreglo a la dispuesto en la legislación general de extranjería.

Esto supone la absoluta imposiblidad de desarrollar de forma legal cualquier tipo de trabajo en España, así como el estar incurso en causa de expulsión del territorio español.

Como ha establecido el Tribunal Supremo en Auto de 20 de Diciembre de 1990 el derecho a la tutela judicial efectiva implica entre otras cosas el derecho a la tutela cautelar, conclusión que viene impuesta por el principio general del Derecho que se resume en que la necesidad del proceso para tener razón no debe convertirse en un daño para el que tiene razón.

Ello significa el deber que tienen tanto la Administración como los Tribunales de acordar la medida cautelar que sea necesaria paraasegurar la plena efectividad del acto terminal.

En conclusión, para evitar que la ejecución del acto administrativo impugnado haga perder su finalidad al recurso contencioso-administrativo, debería dejarse en suspenso la orden de salida obligatoria, autorizando a mi representado a residir y trabajar en España.

X

En el presente caso, y como se ha expuesto en los fundamentos de derecho anteriores, concurren circunstancias que, en el caso de considerarse por esta Sala que el recurrente no es merecedor de la protección prevista por la Convención de Ginebra de 1951, debería llevar a la aplicación de artículo 4 de la Ley 12/2009 reguladora del derecho de asilo y de la protección subsidiaria y otorgarse la protección subsidiaria contemplada en dicho artículo.

Ello, en virtud de la situación de peligro que correría la integridad física del recurrente en caso de retorno a su país de origen y que es uno de los daños graves recogidos en el art. 10 de la Ley 12/2009 que dan derecho a recibir dicha protección por parte de España.

A ello se añade el hecho de que existe una notoria situación de arraigo familiar en España del interesado y su cónyuge, cuyo único hijo ha nacido en territorio español.

XI

En el interesado concurren circunstancias humanitarias que desaconsejarían su retorno al país de origen, toda vez que, como se acredita con la documentación que se adjunta con el presente escrito, en la actualidad residen en España su cónyuge y el hijo que tienen en común, circunstancias que, en caso de no ser concedida la protección solicitada, harían aconsejable que se autorizase su residencia en España al amparo de lo regulado en el art. 37.b) de la Ley 12/2009.

En su virtud

SUPLICO A LA SALA que teniendo por presentado este escrito, tenga por formalizada la demanda frente a la resolución del Ministerio del Interior de fecha [FECHA] y previos los trámites legales oportunos, dicte sentencia por la que se reconozca la condición de refugiado y se otorgue el derecho de asilo o la protección subsidiaria a D. [NOMBRE Y APELLIDOS]

Por ser Justicia que pido en Madrid a [COMPLETAR] de [COMPLETAR].

OTROSI DIGO que de conformidad con lo dispuesto en el artículo 40.1 de la LJCA se estima que la cuantía del recurso es indeterminada, al constituir el objeto del recurso la impugnación de un acto administrativo que no tiene cuantía.

SEGUNDO OTROSI DIGO que en virtud de lo dispuesto en el artículo 60 de la LJCA se solicita el recibimiento a prueba del presente recurso, consistiendo la prueba en

DOCUMENTAL: Consistente en todos y cada uno de los documentos obrantes en el expediente administrativo de que deriva el presente recurso, salvo los que se opongan a nuestras pretensiones:

MAS DOCUMENTAL: Consistente en Que se libre oficio a las siguientes entidades, para que emitan un informe sobre la situación actual en ____ de los miembros de religiones distintas a la mayoritaria religión Cristiana Ortodoxa, entre ellas de la Iglesia Evangélica, en lo relativo al respeto a su libertad religiosa y de culto y a las persecuciones que puedan sufrir por motivo de su condición de fieles de tal religión:

Amnistía Internacjonal (C/ Fernando VI, 8, 1º Izda., 28004 Madrid)

Comisión Española de Ayuda al Refugiado (CEAR). (C/ General Perón, 32. Madrid).

Ilustre Colegio Nacional de Doctores y Licenciados en Ciencias Políticas y Sociología. (Calle de Quintana, 29, Madrid).

En su virtud, SUPLICO A LA SALA que tenga por propuesta la prueba de que esta parte intenta valerse, declare su pertinencia y acuerde su realización.

TERCER OTROSI DIGO que, en caso de que no se estime que el recurrente reúne los requisitos para que le sea concedido el estatuto de refugiado ni la protección subsidiaria, le debería ser de aplicación lo establecido en el artículo 37.b) de la Ley 12/2009 [NOTA DE REVISIÓN: Cita vigente (Ley 12/2009 sin modificar en el consolidado). La autorización por razones humanitarias del art. 37.b) se desarrolla hoy en el art. 128.1.a) RD 1155/2024. Desde el 12-6-2026 la Directiva 2011/95/UE está derogada y se aplica el Reglamento (UE) 2024/1347: actualizar cualquier referencia a la Directiva. Fuente: Ley 12/2009, arts. 4, 10 y 37 (BOE-A-2009-17242); RD 1155/2024, art. 128.1.a) (BOE-A-2024-24099); Reglamento (UE) 2024/1347, art. 41 (CELEX 32024R1347).] reguladora del derecho de asilo y de la protección subsidiaria por concurrir circunstancias humanitarias que así lo aconsejan.

En su virtud, SUPLICO A LA SALA que, subsidiariamente, para el caso de no acceder a lo solicitado inicialmente, se autorice la residencia en España del recurrente por razones humanitarias.

CUARTO OTROSI DIGO que, según lo dispuesto en el artículo 129 y ss. de la LJCA, se considera que la orden de salida quese adjunta en el acta de notificación de la resolución impugnada podría hacer perder al presente su recurso su finalidad en caso de que fuera ejecutada. Asimismo, existe una situación de arraigo en España, por ser éste el lugar de nacimiento del único hijo del interesado y su cónyuge.

En su virtud SUPLICO A LA SALA que adopte la medida cautelar de suspensión de la orden de salida obligatoria que acompaña a la resolución recurrida, autorizando a mis representados a residir en España en tanto no se resuelve el presente recurso.

Por ser Justicia que reitero en lugar y fecha ut supra.

D./Dña. [NOMBRE Y APELLIDOS] Letrado/a D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales.

FUNDAMENTOS DE DERECHO

I

Competencia. La competencia para conocer del recurso corresponde a la Sala de lo Contencioso-Administrativo de la Audiencia Nacional, según lo dispuesto en el art. 11 de la LJCA.

No obstante, para el supuesto de que no se entendiera así, procederá que se remitan as actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en el artículo 7.3 de la ley de esta Jurisdicción.

II

Legitimación. Está legitimado mi representado en virtud de lo establecido en el art. 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

III

Plazo de formulación de la demanda. Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

IV

Costas. En lo relativo a la imposición de costas, es de aplicación el art. 139 de la LJCA. Caso de oponerse al presente recurso, debe estimarse que la Administración actúa con mala fe o temeridad, por lo que deberán imponerse las costas del presente proceso a la Administración demandada.

V

Respecto al motivo de denegación de la solicitud de protección internacional, debe manifestarse el desacuerdo con la resolución recurrida, por cuanto en la solicitud de asilo de mi representado se expusieron hechos que constituyen una persecución personal a él y a sus familiares por uno de los motivos expresamente recogidos en el artículo 1 de la Convención de Ginebra de 1951 sobre el Estatuto del Refugiado, por cuanto el solicitante manifestaba sufrir persecución por motivos religiosos.

Si bien es cierto que el agente de la persecución sufrida era un agente no estatal, el interesado expresa que dicha persecución se desarrolla con el tácito consentimiento de las autoridades que no hacen nada para impedirla.

Debe, pues, considerarse que lo alegado por mi representado es una de las causas previstas en la Convención de Ginebra para la concesión de la protección solicitada y en consecuencia, no estimarse el motivo de denegación de la solicitud de asilo.

VI

Respecto a la alegación de motivos, debe tenerse en cuenta lo que establece la Oficina del Alto Comisionado de las Naciones Unidas para los Refugiados (ACNUR) en su "Manual de procedimientos y criterios para determinar la condición del refugiado".

Este manual, establece que ''la persecución suele ser resultado de la actuación de las autoridades de un país, Puede también emanar de sectores de la población que no respetan las normas establecidas por las leyes de su país. La intolerancia religiosa, equiparable a persecución, en país por lo demás no confesional, en el que importantes sectores de la población no respetan las creencias religiosas de su ciudadanos es un buen ejemplo.

El comportamiento vejatorio o gravemente discriminatorio observado por ciertos sectores de la población local puede equipararse a la persecución si es deliberadamente tolerado por las autoridades o si éstas se niegan a proporcionar una protección eficaz o son incapaces de hacerlo”..

Asimismo, en dicho Manual también se establece que:

71. La Declaración Universal de Derechos Humanos y los Pactos Internacionales de Derechos Humanos proclaman el derecho de toda persona a la libertad de pensamiento, de conciencia y de religión, derecho que incluye la libertad de cambiar de religión y la libertad de manifestar su religión, tanto en público como en privado, por la enseñanza, la práctica, el culto y la observancia.

72. La persecución por “motivos de religión” puede adoptar diversas formas, por ejemplo, la prohibición de pertenecer a una comunidad religiosa, del culto en privado o en público, de la instrucción religiosa, o bien graves medidas de discriminación impuestas a las personas debido a la práctica de su religión o por pertenecer a una determinada comunidad religiosa.

73. Generalmente, el mero hecho de pertenecer a una comunidad religiosa determinada no bastará para justificar la reclamación de la condición de refugiado. Sin embargo, en ciertas circunstancias especiales, la mera pertenencia puede ser una razón suficiente.

De acuerdo, pues, con los criterios del ACNUR, no debería ser motivo suficiente para denegar una solicitud de asilo el hecho de que el solicitante alegue sufrir persecución por parte de grupos ajenos al gobierno o autoridades locales. Si, como ocurre en el caso presente, las autoridades locales no quieren o no son capaces de proporcionar una protección real y efectiva contra este tipo de persecución, debería entenderse que concurre una de las causas de reconocimiento de la condición de refugiado.

VII

Más recientemente, el ACNUR publicó unas Directrices sobre Protección Internacional relativas a las solicitudes de asilo por motivos religiosos bajo el artículo 1.a).2 de la Convención de 1951 y/o el Protocolo de 1967 sobre el Estatuto de los Refugiados.

En dichas directrices se establece lo siguiente:

11. El derecho a la libertad religiosa incluye la libertad de manifestar la religión o las creencias de su elección, ya sea individualmente o colectivamente mediante el culto, la celebración de los ritos, las prácticas y la enseñanza, tanto en público como en privado.

12. La persecución por motivos religiosos puede, por tanto, adoptar diversas formas.

Dependiendo de las circunstancias particulares de cada caso, incluyendo el impacto que tiene sobre la persona afectada, ejemplos de persecución podrían ser la prohibición de pertenecer a una comunidad religiosa, del culto en privado o en público, de la instrucción religiosa o bien, a la imposición de graves medidas de discriminación a las personas debido a la práctica de su religión o por pertenecer o ser identificados con una comunidad religiosa en particular, o porque han cambiado su fe. De igual manera, en determinados casos, en las comunidades donde existe una religión dominante o hay una correlación cercana entre el Estado y las instituciones religiosas, la discriminación contra quienes no profesen la religión dominante o no adhieran a sus prácticas, podría equivaler a persecución9 en un caso particular. La persecución puede ser inter-religiosa (dirigida contra adherentes o comunidades de diferente fe), intra-religiosa (dentro de la misma religión, pero en diferentes sectas o entre miembros de una misma secta) o una combinación de ambas10. El solicitante puede pertenecer a una minoría religiosa o a una mayoría. Las solicitudes por motivos religiosos también pueden ser presentadas por individuos casados donde los cónyuges adhieren a diferentes religiones o pertenecen a distintas comunidades.

13. Aplicando el mismo estándar que para los otros motivos de la Convención, las creencias religiosas, la identidad o la forma de vida pueden ser consideradas características tan fundamentales para la “identidad” humana que uno no debería ser obligado a esconder, cambiar o renunciar a ellas con el objeto de evitar la persecución.

14. Cada solicitud requiere del examen de sus méritos con base en la situación del individuo.

Áreas relevantes de investigación incluyen el perfil individual y las experiencias personales del solicitante; sus creencias religiosas, identidad y/o forma de vida; qué tan importante es esto para el solicitante; qué efectos tienen las restricciones sobre el individuo; la naturaleza de su rol y actividades en el marco de su religión; si estas actividades han llamado o podrían llamar la atención del perseguidor y si podrían resultar en un trato que equivalga a persecución. En este contexto, un temor fundado de persecución “no necesariamente está basado en la experiencia personal del solicitante”. Por ejemplo, lo que le haya sucedido a amigos y parientes del solicitante o a otros miembros del mismo grupo religioso --es decir, a otros individuos en la misma situación--, “puede ser indicio suficiente de que sus temores de convertirse también, más tarde o más temprano, en víctima de persecución son fundados”

VIII

En apoyo del relato del solicitante puede citarse lo expuesto por el Departamento de Estado de Estados Unidos, que en informe de 26 de Octubre de 2009, relativo a la situación de la libertad religiosa en la Federación Rusa afirmaba que:

“Algunas agencias federales, como el Departamento de Organizaciones sin ánimo de lucro del Ministerio de Justicia, y muchas autoridades locales continuaron restringiendo los derechos de algunas minorías religiosas.

Hay indicadores de que servicios de seguridad como el FSB (Servicio Federal de Seguridad), trataba a los líderes de algunos grupos islámicos y no tradiciones, como los Testigos de Jehová, como amenazas a la seguridad.

El Gobierno ha impuesto de forma selectiva restricciones a la libertad religiosa. Las restricciones a la libertad religiosa generalmente se encuentran en cuatro categorías: registro de organizaciones religiosas, acceso a lugares de culto (incluyendo el acceso a terrenos y permisos de construcción), concesión de visados para personal religioso extranjero y acoso gubernamental de personas y organizaciones religiosas.

Existen informe creíbles de que individuos de los servicios federales de seguridad y otros cuerpos de seguridad acosaron a algunos grupos religiosos minoritarios, les investigaron por supuestas actividades criminales e infracciones fiscales y presionaron a propietarios de inmuebles para que rescindieran los contratos con estos grupos.

Se cree que en algunos casos los servicios de seguridad han influidos al Ministro de Justicia para rechazar solicitudes de registro”.

IX

Respecto a la orden de salida que acompaña a la resolución recurrida, se considera que debe ser dejada sinefecto, pues coloca a mirepresentado en situaciónde irregularidad con arreglo a la dispuesto en la legislación general de extranjería.

Esto supone la absoluta imposiblidad de desarrollar de forma legal cualquier tipo de trabajo en España, así como el estar incurso en causa de expulsión del territorio español.

Como ha establecido el Tribunal Supremo en Auto de 20 de Diciembre de 1990 el derecho a la tutela judicial efectiva implica entre otras cosas el derecho a la tutela cautelar, conclusión que viene impuesta por el principio general del Derecho que se resume en que la necesidad del proceso para tener razón no debe convertirse en un daño para el que tiene razón.

Ello significa el deber que tienen tanto la Administración como los Tribunales de acordar la medida cautelar que sea necesaria paraasegurar la plena efectividad del acto terminal.

En conclusión, para evitar que la ejecución del acto administrativo impugnado haga perder su finalidad al recurso contencioso-administrativo, debería dejarse en suspenso la orden de salida obligatoria, autorizando a mi representado a residir y trabajar en España.

X

En el presente caso, y como se ha expuesto en los fundamentos de derecho anteriores, concurren circunstancias que, en el caso de considerarse por esta Sala que el recurrente no es merecedor de la protección prevista por la Convención de Ginebra de 1951, debería llevar a la aplicación de artículo 4 de la Ley 12/2009 reguladora del derecho de asilo y de la protección subsidiaria y otorgarse la protección subsidiaria contemplada en dicho artículo.

Ello, en virtud de la situación de peligro que correría la integridad física del recurrente en caso de retorno a su país de origen y que es uno de los daños graves recogidos en el art. 10 de la Ley 12/2009 que dan derecho a recibir dicha protección por parte de España.

A ello se añade el hecho de que existe una notoria situación de arraigo familiar en España del interesado y su cónyuge, cuyo único hijo ha nacido en territorio español.

XI

En el interesado concurren circunstancias humanitarias que desaconsejarían su retorno al país de origen, toda vez que, como se acredita con la documentación que se adjunta con el presente escrito, en la actualidad residen en España su cónyuge y el hijo que tienen en común, circunstancias que, en caso de no ser concedida la protección solicitada, harían aconsejable que se autorizase su residencia en España al amparo de lo regulado en el art. 37.b) de la Ley 12/2009.

En su virtud

SUPLICO A LA SALA que teniendo por presentado este escrito, tenga por formalizada la demanda frente a la resolución del Ministerio del Interior de fecha [FECHA] de [COMPLETAR] de 20 y previos los trámites legales oportunos, dicte sentencia por la que se reconozca la condición de refugiado y se otorgue el derecho de asilo o la protección subsidiaria a D. [NOMBRE Y APELLIDOS]

Por ser Justicia que pido en [LUGAR], a [FECHA].

OTROSI DIGO que de conformidad con lo dispuesto en el artículo 40.1 de la LJCA se estima que la cuantía del recurso es indeterminada, al constituir el objeto del recurso la impugnación de un acto administrativo que no tiene cuantía.

SEGUNDO OTROSI DIGO que en virtud de lo dispuesto en el artículo 60 de la LJCA se solicita el recibimiento a prueba del presente recurso, consistiendo la prueba en

DOCUMENTAL: Consistente en todos y cada uno de los documentos obrantes en el expediente administrativo de que deriva el presente recurso, salvo los que se opongan a nuestras pretensiones:

MAS DOCUMENTAL: Consistente en que se libre oficio a las siguientes entidades, para que emitan un informe sobre la situación actual en [COMPLETAR] de los miembros de religiones distintas a la mayoritaria religión Cristiana Ortodoxa, entre ellas de la Iglesia Evangélica, en lo relativo al respeto a su libertad religiosa y de culto y a las persecuciones que puedan sufrir por motivo de su condición de fieles de tal religión:

Amnistía Internacjonal (C/ Fernando VI, 8, 1º Izda., 28004 Madrid)

Comisión Española de Ayuda al Refugiado (CEAR). (C/ General Perón, 32. Madrid).

Ilustre Colegio Nacional de Doctores y Licenciados en Ciencias Políticas y Sociología. (Calle de Quintana, 29, Madrid).

En su virtud, SUPLICO A LA SALA que tenga por propuesta la prueba de que esta parte intenta valerse, declare su pertinencia y acuerde su realización.

TERCER OTROSI DIGO que, en caso de que no se estime que el recurrente reúne los requisitos para que le sea concedido el estatuto de refugiado ni la protección subsidiaria, le debería ser de aplicación lo establecido en el artículo 37.b) de la Ley 12/2009 reguladora del derecho de asilo y de la protección subsidiaria por concurrir circunstancias humanitarias que así lo aconsejan.

En su virtud, SUPLICO A LA SALA que, subsidiariamente, para el caso de no acceder a lo solicitado inicialmente, se autorice la residencia en España del recurrente por razones humanitarias.

CUARTO OTROSI DIGO que, según lo dispuesto en el artículo 129 y ss. de la LJC-A, se considera que la orden de salida quese adjunta en el acta de notificación de la resolución impugnada podría hacer perder al presente su recurso su finalidad en caso de que fuera ejecutada. Asimismo, existe una situación de arraigo en España, por ser éste el lugar de nacimiento del único hijo del interesado y su cónyuge.

En su virtud SUPLICO A LA SALA que adopte la medida cautelar de suspensión de la orden de salida obligatoria que acompaña a la resolución recurrida, autorizando a mis representados a residir en España en tanto no se resuelve el presente recurso.

Por ser Justicia que reitero en lugar y fecha ut supra.

D./Dña. [NOMBRE Y APELLIDOS] Letrado/a D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales.
