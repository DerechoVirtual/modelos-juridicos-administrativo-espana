---
name: alegaciones-expulsion-procedimiento-preferente-388
description: "Redacta el escrito «Alegaciones en expulsión por procedimiento preferente» (formulario 388 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones en expulsión por procedimiento preferente

> Formulario 0388 del plugin **Extranjería** · revisado el 17-11-2026.

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

- La prohibición de entrada se cita por el art. 244.2 RD 1155/2024 y el art. 58 LO 4/2000 (el límite de cinco años está en el 58.1, no en el 57.1). Sigue siendo válida la sustitución por salida obligatoria (245.5).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE
- [ ] NACIONALIDAD
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (2 veces)
- [ ] artículo 53.1.a) de la Ley Orgánica 4/2000, modificada por LO 2/2009
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Extranjería y Documentación (Localidad)»; «…(Nombre)»; «…(Nombre) [COMPLETAR] Procedimiento»; «…, Letrado/a del Colegio Abogados de»; «…. viajó por vía aérea desde la ciudad de»; «…() con destino a Madrid, en el mes de»; «…de»; «…riormente por ferrocarril a la Ciudad de»; «…e en España. 3.º) De esta forma, viajó a»; «…, en el piso de»; «…e voluntariamente del país y dirigirse a»; «…e voluntariamente del país y dirigirse a»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO:…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 53.1.a) de la Ley Orgánica 4/2000
- artículo 244.2 del Real Decreto 1155/2024
- artículo 63.1 de la vigente Ley Orgánica 4/2000
- artículo 233 del Real Decreto 1155/2024
- artículo 76 de la Ley 39/2015
- artículo 28.1 de la vigente Ley Orgánica 4/2000
- artículo 24 del Real Decreto 1155/2024
- art. 245.5 del Real Decreto 1155/2024
- artículo 28.3.c) de la Ley Orgánica 4/2000
- artículo 245.5 del Real Decreto 1155/2024
- artículo 61 de la Ley Orgánica 4/2000
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

### Formulario 0388 · Alegaciones en expulsión por procedimiento preferente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 párrafos opcionales señalados; 23 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: La prohibición de entrada se cita por el art. 244.2 RD 1155/2024 y el art. 58 LO 4/2000 (el límite de cinco años está en el 58.1, no en el 57.1). Sigue siendo válida la sustitución por salida obligatoria (245.5).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

JEFATURA SUPERIOR DE POLICÍA

Brigada Provincial de Extranjería y Documentación

(Localidad) [COMPLETAR]

(Nombre) [COMPLETAR]

Procedimiento [COMPLETAR]

Acuerdo de iniciación

(Tramitación preferente)

D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Colegio Abogados de [COMPLETAR], con despacho profesional abierto en esta ciudad, calle [CALLE] y designado por Turno de Oficio de D./Dña. [NOMBRE Y APELLIDOS] mayor de edad, de nacionalidad [NACIONALIDAD], con domicilio en [LOCALIDAD]; cuyas demás circunstancias constan en esa dependencia, comparezco y como mejor proceda, DIGO:

Que con fecha [FECHA], se ha notificado a mi mandante el Acuerdo de INICIACIÓN DEL PROCEDIMIENTO PREFERENTE DE EXPULSIÓN, en base a los hechos que en el mismo se contienen, y que fundamentalmente se concretan en lo siguiente:

«Encontrarse irregularmente en territorio español» [artículo 53.1.a) de la Ley Orgánica 4/2000, modificada por LO 2/2009].

Asimismo se le comunica que la sanción que puede llegar a imponerse es la de expulsión del territorio nacional, con prohibición de entrada en España por un período máximo de cinco años, de conformidad con el artículo 57.1 de la expresada Ley Orgánica 4/2000, así como según lo dispuesto en el artículo 244.2 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: La prohibición de entrada (máximo cinco años, diez si hay amenaza grave) está en el art. 244.2; el 244.4 regula el decomiso. El límite de cinco años es el del art. 58.1 LO 4/2000, no el del 57.1, que solo permite sustituir la multa por la expulsión. El 244.2 también obliga a no imponer o a revocar la prohibición si la persona sale durante el expediente o en el plazo voluntario (casos del art. 53.1.a y b). Fuente: RD 1155/2024, art. 244.2 (BOE-A-2024-24099); LO 4/2000, arts. 57.1 y 58 (BOE-A-2000-544).], de 19 de noviembre.

Que, asimismo, de conformidad con lo dispuesto en el artículo 63.1 de la vigente Ley Orgánica 4/2000, y el artículo 233 del Real Decreto 1155/2024, de 19 de noviembre se le notifica que el procedimiento tendrá carácter preferente.

Que cautelarmente se ha acordado la medida provisional de retirada de pasaporte, motivándose dicha medida por carecer de domicilio fijo y arraigo en España y no haber realizado ningún trámite tendente a su legalización en territorio español.

Que a tenor de lo prevenido en el artículo 63 de la citada Ley Orgánica y, así como lo dispuesto en el artículo 76 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, por medio del presente escrito paso a efectuar las siguientes

ALEGACIONES

I. ANTECEDENTES DE HECHO

1.º) El expedientado, Sr. viajó por vía aérea desde la ciudad de [COMPLETAR] () con destino a Madrid, en el mes de [COMPLETAR] de [COMPLETAR], dirigiéndose posteriormente por ferrocarril a la Ciudad de [COMPLETAR].

El control de entrada en territorio Schengen se realizó por ello en la frontera del aeropuerto de Barajas. El Sr. portaba visado Schengen tipo "C" expedido por la Embajada española en

Todo ello, se comprueba por el examen del pasaporte del interesado en el que consta el sello de entrada y cuyo original se encuentra depositado en esas dependencias policiales.

2.º) El motivo del viaje era visitar a su familia, madre, hermanos, tíos y primos residentes en España, con la intención de examinar las posibilidades de establecimiento en nuestro país. Desde hacía bastante tiempo venía sopesando la oportunidad de reagruparse familiarmente y establecerse en España.

3.º) De esta forma, viajó a [COMPLETAR] donde se encuentran su madre Dña. [NOMBRE Y APELLIDOS], hermanos D. y Dña. [NOMBRE Y APELLIDOS] y demás tíos y primos, todos ellos residentes legales en España y con permisos renovados.

4.º) El expedientado cuenta con domicilio fijo, pues vive junto con su hermana Dña. [NOMBRE Y APELLIDOS], en el piso de [COMPLETAR], n.º [NÚMERO], y en el que se encuentra empadronado.

Se acompañan copia de los documentos que prueban las anteriores manifestaciones.

5.º) El expedientado tiene arraigo familiar en España y se encuentra dentro del supuesto preferencial para la tramitación del permiso de residencia laboral al ser hijo de residente legal con permiso renovado y tiene intención de regresar a su país al objeto de efectuar la solicitud del visado consular.

II. PROCEDENCIA DE LA ADVERTENCIA DE SALIDA OBLIGATORIA PREVIA A LA INCOACIÓN DE EXPEDIENTE.

El artículo 28.1 de la vigente Ley Orgánica 4/2000 señala que «las salidas del territorio español podrán realizarse libremente, excepto en los casos previstos en el Código Penal y en la presente Ley»,

indicando en el apartado 3 del citado artículo que «la salida será obligatoria en los siguientes supuestos: (...) c) Denegación administrativa de las solicitudes formuladas por el extranjero para continuar permaneciendo en territorio español, o falta de autorización para encontrarse en España».

En estos casos, el artículo 24 del Real Decreto 1155/2024, de 19 de noviembre, prevé el mecanismo para la realización de la salida obligatoria:

a) Deberá efectuarse en el plazo máximo de 15 días, salvo que concurriendo circunstancias excepcionales y acreditando medios de vida se prorrogue hasta 90 días.
b) Si se realizase la salida del territorio español no serán objeto de prohibición de entrada en el país, pudiendo volver a España con arreglo a las normas que regulan el acceso al territorio español.

En este sentido una reciente Sentencia del Tribunal Supremo de 19 de junio de 2001, Rec. 6895/1996, en el supuesto de expulsión de una ciudadana colombiana, estima el recurso interpuesto la recurrente señalando que en estos supuestos: «(...) se advertirá a los interesados y, si saliesen del territorio sin haber incurrido en causa de expulsión no serán objeto de prohibición de entrada en el país, pudiendo volver a España con arreglo a las normas que regulan el acceso al territorio nacional».

Por ello, la actuación procedente por parte de la autoridad actuante debió ser la de limitarse, a tenor de los artículos legales y reglamentarios citados, a comunicar a la compareciente su situación de falta de autorización para encontrarse en España y señalar el plazo en el que deberá efectuar la salida del territorio español, absteniéndose, en este caso, de iniciar un procedimiento de expulsión que, la previsión legal, razones de oportunidad y prudencia administrativa aconsejan restringir para aquellos supuestos más graves y de pertinaz y continuada situación de irregularidad residencial.

En cualquier caso el art. 245.5 del Real Decreto 1155/2024, de 19 de noviembre previene que:

«Salvo en supuestos en que se hubiera impuesto un periodo de cumplimiento voluntario de la sanción y éste hubiera sido inatendido por el extranjero, en caso de que éste dispusiera de medios económicos y asumiera el coste de la repatriación de manera voluntaria, el Delegado o Subdelegado del Gobierno que hubiera dictado dicha resolución podrá acordar, de oficio o a instancia de parte, su sustitución por la salida obligatoria si se cumplen las siguientes condiciones:

a) Que la infracción que haya motivado la resolución de expulsión sea la contenida en el artículo 53.1.a) y b) de la Ley Orgánica 4/2000, de 11 de enero;
b) Que existan garantías suficientes o pueda comprobarse la realización de la oportuna salida obligatoria prevista en el artículo 28.3.c) de la Ley Orgánica 4/2000; y
c) Que la persona extranjera esté por su nacionalidad sometida a la obligación de visado para cruzar las fronteras exteriores en aplicación de un acuerdo de régimen común de visados, de carácter internacional, en el que España sea parte.»

En el presente caso, el expedientado, cumpliendo los requisitos expuestos, manifiesta su intención de ausentarse voluntariamente del país y dirigirse a [COMPLETAR]. Por lo que en todo caso solicita acogerse a la previsión reglamentaria del citado artículo 245.5 del Real Decreto 1155/2024, de 19 de noviembre.

Para ello, solicita expresamente que en el caso de que se acuerde su expulsión se le conceda un plazo para poder realizar el abandono del territorio nacional y en ese caso se proceda al archivo del expediente de expulsión, una vez acreditada su salida.

III. OTRAS CONSIDERACIONES JURÍDICAS

Primera.- El artículo 53.1.a) de la Ley Orgánica 4/2000, reformada por Ley Orgánica 2/2009, contempla como infracción grave el hecho de:

«Encontrarse irregularmente en territorio español, por no haber obtenido o tener caducada más de tres meses la prórroga de estancia, la autorización de residencia o documentos análogos, cuando fueren exigibles, y siempre que el interesado no hubiere solicitado la renovación de los mismos en el plazo previsto reglamentariamente».

Señalando el artículo 55, que la sanción a imponer en este supuesto será de 501 hasta 10.000 euros, aunque el artículo 57.1 señale que cuando los infractores sean extranjeros y realicen conductas de las tipificadas como muy graves, o conductas graves de las previstas en los apartados a), b), c) d) y f) del artículo 53 de esta Ley Orgánica, podrá aplicarseen lugar de la sanción de multa la expulsión del territorio español, previa la tramitación del correspondiente expediente administrativo.

Segunda.- Es cierto que en el presente caso se han incumplido los trámites reglamentarios previstos en el reglamento aprobado mediante Real Decreto 1155/2024, de 19 de noviembre, pero también lo es que el artículo 55.3 de la citada Ley Orgánica 4/2000 dice que para la graduación de las sanciones, el órgano competente en imponerlas se ajustará a criterios de proporcionalidad, valorando el grado de culpabilidad y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia y el artículo 55.4, que para la determinación de la cuantía de la sanción se tendrá especialmente en cuenta la capacidad económica del infractor.

Debe considerarse también que un principio fundamental que incorpora la Ley Orgánica 4/2000, original y reformada, es el «principio pro integración» del inmigrante. En el presente caso, todo ello deberá ser tomado en cuenta, dada la escasa gravedad y trascendencia de la infracción parecería más prudente resolver el expediente con la imposición de una sanción económica, que tenga en cuenta la escasa capacidad económica de la expedientada y que permita a la misma tratar de normalizar su residencia en nuestro país.

A ello responde el tenor del artículo 55.3 LOEx que impone criterios de proporcionalidad para la graduación de las sanciones, así: «Para la graduación de las sanciones, el órgano competente en imponerlas se ajustará a criterios de proporcionalidad, valorando el grado de culpabilidad y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia».

El artículo 55.4 LOEx, por su parte, atiende especialmente a la capacidad económica del infractor para la fijación de la determinación del importe de la multa.

En el presente caso entendemos concurren todas las notas que aconsejarían el archivo del expediente o en su caso la imposición alternativa de una sanción pecuniaria. Téngase en cuenta que el expedientado tiene toda su familia residiendo en España y su expulsión supondría el alejamiento de su familia y la ruptura del núcleo familiar.

Medidas cautelares.

El artículo 61 de la Ley Orgánica 4/2000 permite la adopción de alguna medida cautelar con la finalidad de asegurar la eficacia de la resolución final y si bien está medida parece más acorde a la legalidad vigente fijarla en la propuesta de resolución es indudable que deberá ser motivada.

En el presente caso la motivación es únicamente la hipotética circunstancia de carecer de domicilio fijo. Sin embargo, es evidente que carece de cualquier fundamento tal afirmación, dado que el expedientado está empadronado en el padrón Municipal del Ayuntamiento de [LOCALIDAD], junto con sus familiares próximos.

Por consiguiente, carece de fundamento la adopción de la medida cautelar de retirada del pasaporte que deberá ser devuelto al expedientado.

IV. PROPOSICIÓN DE PRUEBA

En cualquier caso y en orden a la desacreditación de los hechos imputados se solicita la apertura del período probatorio en el que sean admitidos y practicados los siguientes medios de prueba:

1.º) Documental: Por aportación al expediente administrativo de los siguientes documentos:
a) Certificado del Padrón Municipal. Doc. núm 1.
b) Dado lo precipitado del plazo de 48 horas no puede aportar en este momento la tarjeta de su madre y hermanos, que adjuntará en momento posterior.
2.º) Testifical: Al objeto de justificar las circunstancias de arraigo alegadas se propone la testifical de su madre y hermanos, que comparecerán voluntariamente a requerimiento de ese órgano instructor, pudendo ser citada a través de esta representación.

Por lo expuesto,

SOLICITA

Se tenga por presentado este escrito, junto con los documentos que se acompañan, lo admita y por efectuadas las alegaciones que en el mismo se contienen. Y, a su vista, se acuerde el archivo del expediente de expulsión incoado o alternativamente se proponga imponer al expedientado la sanción económica que se estime más adecuada de acuerdo con la escasa importancia de la infracción y su capacidad económica.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO:

Que, en cualquier caso, el expedientado manifiesta su intención de ausentarse voluntariamente del país y dirigirse a [COMPLETAR] Por lo que en todo caso solicita acogerse a la previsión reglamentaria de artículo 245.5 del Real Decreto 1155/2024, de 19 de noviembre.

En [LUGAR], a [FECHA].

Fdo.:
