---
name: frente-denegacion-visado-reagrupacion-familiar-280
description: "Redacta el escrito «Frente a la denegación de visado de reagrupación familiar comunitaria» (formulario 280 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Frente a la denegación de visado de reagrupación familiar comunitaria

> Formulario 0280 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Reagrupación: nuevos requisitos del art. 67 RD 1155/2024 y nuevo procedimiento de visado del art. 40. El formulario aún cita el RD 2393/2004.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] CALLE
- [ ] PROVINCIA
- [ ] FECHA
- [ ] AÑO (5 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] DÍA
- [ ] MES
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DO GENERAL DE ESPAÑA EN SANTO DOMINGO Dª»; «…del»; «…del [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de [AÑO], notificada el»; «…de [AÑO], notificada el [COMPLETAR] de»; «…La recurrente nació el»; «…La recurrente nació el [COMPLETAR] de»; «…e [AÑO], inscribiéndose su nacimiento el»; «…de»; «…Extracto de acta de nacimiento tardía de»; «…— Acta inextensa de nacimiento de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 68.1 de la Ley 39/2015
- arts. 38 y 40 del Real Decreto 1155/2024
- art. 48 de la Ley 39/2015

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

### Formulario 0280 · Frente a la denegación de visado de reagrupación familiar comunitaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 22 campos de relleno marcados en blanco
- Avisos de la revisión: Reagrupación: nuevos requisitos del art. 67 RD 1155/2024 y nuevo procedimiento de visado del art. 40. El formulario aún cita el RD 2393/2004.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

N.I.V.:

AL CONSULADO GENERAL DE ESPAÑA EN SANTO DOMINGO

Dª [COMPLETAR], mayor de edad, con cédula No., y domicilio a efectos de notificaciones en Calle [CALLE] del [COMPLETAR] de [COMPLETAR], Provincia [PROVINCIA], ante este Consulado comparece para interponer

RECURSO DE REPOSICIÓN

contra la resolución de fecha [FECHA] de [COMPLETAR] de [AÑO], notificada el [COMPLETAR] de [COMPLETAR] de [AÑO], por la que se denegaba el visado que había solicitado, copia de la cual adjunto al presente escrito

Se fundamenta el recurso en los siguientes

HECHOS

La recurrente solicitó visado de reagrupación familiar en régimen comunitario por ser hija de la ciudadana española D.ª [NOMBRE Y APELLIDOS]

La recurrente nació el [COMPLETAR] de [COMPLETAR] de [AÑO], inscribiéndose su nacimiento el [COMPLETAR] de [COMPLETAR] de [AÑO], la cual fue ratificada por sentencia de fecha 3 de agosto de 1992, según se acreditaba mediante acta de nacimiento tardía aportada con la solicitud.

Se adjuntó, asimismo, acta inextensa de nacimiento y certificado de la Dirección Nacional del Registro del Estado Civil de la República Dominicana en la que se acreditaba la autenticidad de lo expuesto en los documentos anteriores.

A pesar de lo expuesto, la resolución fue denegada por que la recurrente

“no demuestra vínculo con el familiar comunitario. El acta de nacimiento es tardía, no existe ratificación por Sentencia. No se sigue el procedimiento legalmente establecido para la inscripción en el registro de los nacimientos, por lo tanto no se puede comprobar la filiación”.

La hermana de la recurrente, D.ª [NOMBRE Y APELLIDOS], nació el 16 de octubre de 1992 y su nacimiento fue inscrito el 13 de agosto de 1998, el cual fue ratificado por sentencia de fecha 26 de Agosto de 1998.

Dicho documento, exactamente igual al aportado por la recurrente, fue suficiente no sólo para que se le concediera visado por reagrupación familiar sino para obtener la nacionalidad española por residencia.

A efectos de prueba de lo expuesto se adjunta la siguiente documentación:

— Extracto de acta de nacimiento tardía de [COMPLETAR]

— Acta inextensa de nacimiento de [COMPLETAR]

— Certificación de la Directora Nacional de Registro del Estado Civil.

— Extracto de acta de nacimiento tardía de [COMPLETAR], hermana de la recurrente.

— DNI de la hermana de la recurrente, D.ª [NOMBRE Y APELLIDOS]

— DNI de la madre de la recurrente, D.ª [NOMBRE Y APELLIDOS]

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

En primer lugar, se considera que en la resolución denegatoria se ha incurrido en un error de hecho, dado que se dice que no existe ratificación por sentencia, a pesar de que de la documentación aportada se desprende que sí existió sentencia ratificatoria, según se hizo constar en el acta de nacimiento tardía.

La documentación adjunta, además, certificaba suficientemente el vínculo familiar de la recurrente con su madre, D.ª [NOMBRE Y APELLIDOS], pues no sólo se adjunta acta de nacimiento tardía, sino acta inextensa de nacimiento y certificación de la Dirección Nacional de Registro del Estado Civil que acreditaban que en este caso se han cumplido los requisitos legales según la legislación dominicana para acreditar el vínculo familiar de la recurrente con su madre.

Acredita dicho extremo el hecho de que la hermana de la recurrente, con la misma documentación pudo obtener sin problemas su visado de reagrupación familiar y posteriormente la nacionalidad española por residencia, lo que provocó en la recurrente la confianza legítima en la validez de los documentos aportados para la concesión del visado solicitado.

Si lo que ocurrió en realidad fue que el Consulado de España dudaba de la veracidad de los documentos o consideraba que los mismos no eran suficientes para acreditar el vínculo familiar, debió haber requerido a la interesada para que subsanara las carencias detectadas, según lo dispuesto en el art. 68.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas:

Si la solicitud de iniciación no reúne los requisitos que señala el artículo 66, y, en su caso, los que señala el artículo 67 u otros exigidos por la legislación específica aplicable, se requerirá al interesado para que, en un plazo de diez días, subsane la falta o acompañe los documentos preceptivos, con indicación de que, si así no lo hiciera, se le tendrá por desistido de su petición, previa resolución que deberá ser dictada en los términos previstos en el artículo 21.

Al no haber actuado así, la Administración colocó a la recurrente en situación de indefensión, al no conocer los motivos por los que no se consideraba que el documento aportado no había seguido los procedimientos legales, y al no concederle el preceptivo plazo para que hubiera podido subsanar cualquier falta u omisión en su solicitud.

Existe una abundante jurisprudencia del Tribunal Superior de Justicia de Madrid, en casos similares al presente, ente las que podríamos citar la sentencia 225/2008, de 20 de febrero de 2008 y la sentencia 1334/2007, de 28 de septiembre de dos mil siete.

Según establece el TSJM en estas sentencias:

“Conforme a las normas citadas, la inscripción de nacimiento fuera de plazo no constituye causa de denegación de visado y, si la resolución impugnada se ha pretendido fundamentar en la supuesta falsedad de los datos que comprende la declaración de nacimiento o un propósito defraudatorio del Ordenamiento Jurídico español, debería haber explicitado y acreditado las razones que hubieran determinado la decisión administrativa con el objeto de no colocar en situación de indefensión a las personas interesadas y posibilitar a la Sala la revisión del juicio administrativo. En cualquier caso, del mero hecho base de la declaración tardía de nacimiento no puede inferirse racionalmente ningún otro, a lo que debe añadirse que, en el caso que nos ocupa, la declaración de nacimiento de Víctor fue ratificada mediante Sentencia. Así las cosas, concurriendo en la solicitante los requisitos exigidos por el RD 178/03 para la concesión del visado y al no haber quedado constatadas otras razones de fondo que justifiquen su denegación, es procedente, con estimación del presente recurso, anular la resolución administrativa recurrida y declarar el derecho de Rosa a obtener el visado solicitado para reagruparse en España con su madre Dª Emilia.”

Por otra parte, la sentencia del TSJM de 27 de septiembre de 2007 (sentencia 1272/2007) establecía que:

“Es cierto que la declaración de nacimiento de la solicitante del visado tuvo lugar en el año 2003 con referencia a 1991, pero también lo es que el Consulado General de España en Santo Domingo no ha discutido la autenticidad ni la eficacia formal de los documentos aportados al expediente en orden a la acreditación de la relación de filiación invocada y que la declaración de nacimiento tardía ha sido ratificada mediante sentencia 1557 del Juzgado de Primera Instancia del Distrito Judicial de Bahoruco, de 27.10.2003 -según resulta de la certificación de nacimiento en extracto aportada a los autos-. Se está en el caso de que del único hecho base de la tardía declaración de nacimiento de la hija de la recurrente no puede inferirse racionalmente, y en condiciones que excluyan las demás posibilidades razonables, que la solicitante del visado no nació en la fecha que consta en el correspondiente certificado y que no es hija de la demandante y, de otra parte, consta que el padre de la menor ha prestado consentimiento a la reagrupación familiar y encargado a la recurrente la guarda y custodia de la hija común y que la Subdelegación del Gobierno en Lérida ha concedido la correspondiente autorización de residencia, habiéndose solicitado en plazo el visado, por lo que, concurriendo en la solicitante los requisitos exigidos en los arts. 38 y 40 del Real Decreto 1155/2024, de 19 de noviembre, para la concesión del visado de residencia [NOTA DE REVISIÓN: RD 2393/2004 derogado. Revisar el fondo: los requisitos de la reagrupación son hoy los de los arts. 66-68 RD 1155/2024. Fuente: RD 1155/2024, arts. 38 y 40 (BOE-A-2024-24099).] para la reagrupación familiar y al no constar que existan otras razones de fondo para su denegación, es procedente declarar el derecho de la menor María Inmaculada a su obtención, al haberse desvirtuado en este proceso los fundamentos de la decisión administrativa impugnada.”

Son razonamientos plenamente aplicables a este caso, en que no se ha expuesto ni siquiera sucintamente, los motivos por los que el Consulado de España en Santo Domingo considera que los documentos aportados no han seguido el procedimiento legalmente establecido, lo que coloca a la recurrente en situación de indefensión.

En conclusión, la resolución recurrida, habría incurrido en una de las causas de anulabilidad de la resolución recurrida recogida en el art. 48 de la Ley 39/2015, de 1 de octubre.

Por lo expuesto SOLICITA AL CONSULADO DE ESPAÑA EN SANTO DOMINGO que tenga por interpuesto el presente recurso de reposición y previos los trámites oportunos, anule la resolución recurrida y dicte una nueva resolución por la que se otorgue a la recurrente el visado solicitado.

En Santo Domingo, a [DÍA] de [MES] de [AÑO]

Fdo.:
