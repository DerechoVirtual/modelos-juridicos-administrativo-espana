---
name: reposicion-nacionalidad-espanola-residencia-342
description: "Redacta el escrito «Reposición en nacionalidad española por residencia» (formulario 342 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición en nacionalidad española por residencia

> Formulario 0342 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] NACIONALIDAD
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…LIDAD ESPAÑOLA POR RESIDENCIA Expediente»; «…/20»; «…yor de edad, de nacionalidad Ecuatoriana»; «…itud. Se adjunta documento del Consulado»; «…butaria — Certificado de la Comunidad de»; «…cursos de integración de la Comunidad de»; «…ntación de la solicitud no tuvo lugar en»; «…de»; «…de [COMPLETAR] de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 124 de la Ley 39/2015
- art. 14 del Real Decreto 1004/2015
- artículo 123 de la Ley 39/2015
- artículo 68.1 de la Ley 39/2015
- artículo 68 de la Ley 39/2015
- artículo 48 de la Ley 39/2015

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

### Formulario 0342 · Reposición en nacionalidad española por residencia

- Año del modelo: 2013
- Revisión 17-11-2026: 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

RECURSO DE REPOSICIÓN: NACIONALIDAD ESPAÑOLA POR RESIDENCIA Expediente [COMPLETAR] /20 [COMPLETAR]

AL MINISTERIO DE JUSTICIA

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad Ecuatoriana [COMPLETAR], con N.I.E., y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], en la C/ [CALLE], ante este organismo comparece para

formular

RECURSO DE REPOSICIÓN

Contra la resolución de fecha [FECHA], que ha sido notificada el día [FECHA], por la que se denegaba su solicitud de nacionalidad española por residencia, copia de la cual se adjunta con el presente escrito

HECHOS

Se presentó por el interesado solicitud de nacionalidad española por residencia.

En la fecha mencionada, le fue notificada resolución del Ministerio de Justicia por la que se denegada la nacionalidad española con base en dos motivos:

a) No haber acreditado suficiente grado de integración.

b) No justificarse buena conducta cívica, por estar caducado el certificado de antecedentes penales del país de origen del recurrente.

Que, no obstante lo expuesto, se ha solicitado nuevamente certificado de antecedentes penales de su país de origen, lo cual acredita el cumplimiento del requisito de buena conducta cívica en el momento de la presentación de la solicitud.

Se adjunta documento del Consulado [COMPLETAR] en Madrid acreditando que dicho documento está solicitado y en trámite, el cual se aportará a la tramitación del presente recurso tan pronto como esté disponible.

Se adjunta, asimismo, la siguiente documentación a efectos de acreditar el grado de integración del recurrente en la sociedad española:

— Certificado de matrimonio y tarjeta de identidad de extranjero de D./Dña. [NOMBRE Y APELLIDOS]

— Certificados de nacimiento del hijo mayor del recurrente, el cual tiene nacionalidad española.

— Tarjeta de identidad de extranjero del tercer hijo del recurrente.

— Certificado de vida laboral que acredita que el recurrente ha realizado regularmente una actividad laboral en España.

— Certificado que acredita la titularidad de permiso de conducción del interesado, obtenido en España, y que conserva todos los puntos del mismo.

— Certificado de estar al corriente de pagos con la Agencia Tributaria

— Certificado de la Comunidad de [COMPLETAR] que acredita la asistencia a los cursos de integración de la Comunidad de [COMPLETAR]

Que, a efectos de notificaciones se designa el domicilio del recurrente en la dirección que figura en el encabezamiento.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el artículo 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta dentro del plazo de un mes posterior a su notificación. El art. 14 del Real Decreto 1004/2015, de 6 de noviembre, por el que se aprueba el Reglamento por el que se regula el procedimiento para la adquisición de la nacionalidad española por residencia, establece que, en caso de denegación de la solicitud de nacionalidad, podrá interponerse recurso de reposición en los términos y plazos previstos en las normas generales de procedimiento administrativo común.

II

De acuerdo con lo dispuesto en el artículo 123 de la Ley 39/2015, este recurso se presenta ante el órgano que dictó la resolución.

III

Respecto al primer motivo de denegación, debe señalarse que el recurrente es de nacionalidad [NACIONALIDAD] por lo que el castellano es su lengua materna, lo que por sí solo es un factor importante a efectos de valorar la integración en nuestra sociedad.

Por otra parte, la legislación no establece un procedimiento, así sea de forma orientativa, para que pueda determinarse el grado de integración en la sociedad española del recurrente.

Así, nos encontramos ante una enorme variedad de procedimientos y criterios, siendo que la documentación presentada por el solicitante acredita claramente su integración en la sociedad española.

Pero es que, además de la inseguridad jurídica y de la vulneración del principio de igualdad que supone dicha variedad de criterios para apreciar el grado de integración, se entiende por la Subdelegación del Gobierno de [LOCALIDAD] se está informando desfavorablemente de forma sistemática los expedientes de nacionalidad, sin ningún tipo de motivación, trasladándose a la resolución impugnada tal informe, sin valorarse de forma individualizada el grado de integración del recurrente, quien lo justifica ampliamente con la documental practicada y demás datos obrantes en el expediente, de donde se concluye que tiene un suficiente grado de integración en la sociedad española que determina la procedencia de la adquisición de la nacionalidad.

Por tanto, e de la documentación aportada con la solicitud de nacionalidad y de la aportada con el presente escrito quedaba claramente establecido que, en contra de lo que se considera en la resolución recurrida, el recurrente tiene un grado de integración en nuestra sociedad por encima de la media de lo que pueda ser habitual en las solicitudes de nacionalidad española.

IV

Respecto al segundo motivo de denegación, existe un error de hecho en la resolución, dado que la presentación de la solicitud no tuvo lugar en [COMPLETAR] de [COMPLETAR] de [COMPLETAR] sino en

Se adjunta a efectos de prueba el resguardo sellado de la solicitud de nacionalidad.

Además, debe recordarse que, si la Administración consideraba que dicho documento no acreditaba el cumplimiento del requisito exigido, lo adecuado hubiera sido requerir al interesado para que aportara un documento en vigor, subsanando dicho defecto, en lugar de rechazar de plano la solicitud.

Así lo establece el artículo 68.1 de la Ley 39/2015, que establece que:

1. Si la solicitud de iniciación no reúne los requisitos que señala el artículo 66, y, en su caso, los que señala el artículo 67 u otros exigidos por la legislación específica aplicable, se requerirá al interesado para que, en un plazo de diez días, subsane la falta o acompañe los documentos preceptivos, con indicación de que, si así no lo hiciera, se le tendrá por desistido de su petición, previa resolución que deberá ser dictada en los términos previstos en el artículo 21.

Respecto a dicho precepto, la Sentencia del Tribunal Supremo de de 4 de febrero de 2003, rec. 3437/2001 (Sección 7º de la Sala de lo Contencioso-Administrativo) estableció que:

Es de destacar ya el criterio que la sentencia de 7 de julio de 1997, rec. 6128/1992, de la Sala Tercera, Sección Sexta, fijó en interpretación del artículo 71 (actual artículo 68 de la Ley 39/2015) cuando reconoció que la omisión de datos y errores exige que el órgano administrativo competente se lo haga saber al interesado, señalando dichos errores u omisiones y concediéndole un plazo de diez días para subsanación con la advertencia de que si no lo hiciere, se procederá al archivo del expediente y en todo caso, en dicha sentencia se hace una expresa referencia a la antigua sentencia de la Sala Cuarta de 16 de marzo de 1988, en el sentido de que la Administración no puede arbitrariamente exigir cualquier documentación sino aquélla que sea imprescindible para fijar los datos en base a los cuales ha de dictarse la resolución y esos datos han de ser ignorados por la Administración, ya que si ésta los conoce por haber presentado el interesado los documentos que se le piden, no tiene alcance la indicada consideración, habiéndose de tratar de datos suficientes para resolver y para dictar la correspondiente resolución.

Al no haberse realizado dicho requerimiento, se ha incurrido en causa de anulabilidad prevista por el artículo 48 de la Ley 39/2015, que establece que:

1. Son anulables los actos de la Administración que incurran en cualquier infracción del ordenamiento jurídico, incluso la desviación de poder.

Por lo expuesto SOLICITO que se admita el presente recurso con los documentos que se adjunta, y previos los trámites oportunos, sea revocada la resolución recurrida, por considerar que los hechos relatados y los fundamentos de derecho expuestos, desvirtúan los fundamentos de derecho de la resolución recurrida, dictándose una nueva mediante la cual se reconozca el derecho del recurrente a la concesión de la nacionalidad española por residencia.

En [LUGAR], a [FECHA].

Fdo:
