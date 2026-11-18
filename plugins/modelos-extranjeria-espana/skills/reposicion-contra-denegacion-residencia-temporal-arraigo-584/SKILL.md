---
name: reposicion-contra-denegacion-residencia-temporal-arraigo-584
description: "Redacta el escrito «Reposición contra denegación de residencia temporal por arraigo» (formulario 584 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra denegación de residencia temporal por arraigo

> Formulario 0584 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Fondo desfasado: el arraigo social ya no exige tres años ni contrato. Hoy rigen los arts. 125-127 RD 1155/2024 (dos años; arraigo social sin contrato con vínculos o informe de integración; el contrato pasa al arraigo sociolaboral; desaparece el arraigo laboral). Hay que reformular el recurso.
- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] COLEGIO
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…solución del Subdelegado del Gobierno de»; «…o del art. 31.3 de la Ley de Extranjería»; «…re y hermano, concretamente desde el año»; «…ertificado de empadronamiento (documento»; «…(documento»; «…y por la Embajada de su país (documentos»; «…les, según se acredita en los documentos»; «…a»; «…r tres años como comercial en la empresa»; «… decoraciones y revestimiento (documento»; «…o son alta en entidad aseguradora médica»; «…(documento»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112.1 de la Ley 39/2015
- Real Decreto 557/2011

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

### Formulario 0584 · Reposición contra denegación de residencia temporal por arraigo

- Año del modelo: 2011
- Revisión 17-11-2026: 3 puntualizaciones normativas añadidas en el texto; 31 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Fondo desfasado: el arraigo social ya no exige tres años ni contrato. Hoy rigen los arts. 125-127 RD 1155/2024 (dos años; arraigo social sin contrato con vínculos o informe de integración; el contrato pasa al arraigo sociolaboral; desaparece el arraigo laboral). Hay que reformular el recurso. · Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS], Letrado del Colegio de Abogados de [COLEGIO], colegiado número [Nº DE COLEGIADO/A], con domicilio a efectos de notificaciones sito en [LOCALIDAD] pudiendo ser notificado vía lexnet o en el correo electrónico [CORREO ELECTRÓNICO], y con teléfono [TELÉFONO], en representación de D. [NOMBRE Y APELLIDOS], la cual tengo acreditada en el expediente o conferida por poder notarial que acompaño o que me ha sido conferida por turno de oficio, en el procedimiento nº [Nº DE PROCEDIMIENTO]/[AÑO], que se sigue por infracción del art. de la Ley de Extranjería, comparece y como mejor proceda, DICE:

Que en fecha [FECHA] he sido notificado de la resolución del Subdelegado del Gobierno de [COMPLETAR] de fecha [FECHA] por la que se denegaba a mi representado el permiso de residencia temporal por arraigo solicitado al amparo del art. 31.3 de la Ley de Extranjería [COMPLETAR], y de conformidad con lo prevenido en el art. 112.1 de la Ley 39/2015, por medio del presente escrito interpongo RECURSO DE REPOSICIÓN en base a los siguientes MOTIVOS:

PRIMERO.- Infracción del artículo 31.3 de la Ley de Extranjería, y artículo 124 del Reglamento de Extranjería aprobado por Real Decreto 557/2011, de 20 de abril [NOTA DE REVISIÓN: El arraigo está ahora en los arts. 125-127 RD 1155/2024, con un contenido distinto: cinco tipos (segunda oportunidad, sociolaboral, social, socioformativo y familiar), dos años de permanencia y desaparición del arraigo laboral. Hay que reformular el recurso según el tipo de arraigo denegado. Fuente: RD 1155/2024, arts. 125-127 (BOE-A-2024-24099).].

La resolución recurrida infringe lo dispuesto en el art. 31.3 de la Ley de Extranjería y art. 124.2 del Reglamento, puesto que consta en el expediente que mi representado cumple todos y cada uno de los requisitos establecidos para el otorgamiento del permiso por arraigo social.

El artículo 31.3 de la Ley Orgánica de Extranjería establece la posibilidad de autorizar la residencia temporal por arraigo en los supuestos prevenidos reglamentariamente, precepto éste desarrollado en el artículo 124.2 del Reglamento de Extranjería [NOTA DE REVISIÓN: Arraigo social: hoy arts. 126 y 127.c) RD 1155/2024 (ver nota anterior). Fuente: RD 1155/2024, arts. 126 y 127.c) (BOE-A-2024-24099).] el cual establece que se podrá conceder una autorización de residencia por razones de arraigo en diferentes supuestos allí contemplados, estando mi representado incluido en el apartado 2 en relación a los extranjeros que acrediten la permanencia continuada en España durante un período mínimo de tres años, siempre que carezcan de antecedentes penales en España y en su país de origen, cuenten con un contrato de trabajo firmado por el trabajador y el empresario en el momento de la solicitud cuya duración no sea inferior a un año y bien acrediten vínculos familiares con otros extranjeros residentes, bien presenten un informe que acredite su inserción social emitido por la Comunidad Autónoma en el que tenga su domicilio habitual.

De la documentación obrante en el expediente se desprende claramente el arraigo de mi representado, puesto que se han acreditado las siguientes circunstancias de arraigo:

1) Mi representado lleva residiendo en España más de tres años con su madre

y hermano, concretamente desde el año [COMPLETAR], y carece de antecedentes penales en España y en su país de origen, según se acredita por los siguientes documentos obrantes en el expediente: certificado de empadronamiento (documento [COMPLETAR]); pasaporte donde consta como fecha de entrada en España el día [FECHA] (documento [COMPLETAR]); certificado negativo de antecedentes penales expedido por el Ministerio de Justicia y por la Embajada de su país (documentos [COMPLETAR]).

2) Convive con su madre y su hermano, que son residentes legales, según se acredita en los documentos [COMPLETAR] a [COMPLETAR] del expediente, donde consta las certificaciones de la Embajada acreditativas del parentesco, certificado de empadronamiento y autorización de residencia de la madre y del hermano de mi representado.

3)Mi representado tiene una oferta laboral para la prestación de servicios por tres años como comercial en la empresa [COMPLETAR] dedicada a decoraciones y revestimiento (documento [COMPLETAR]).

4) Finalmente, se aportaron otros documentos que demuestran la vocación de arraigo, como son alta en entidad aseguradora médica [COMPLETAR] (documento [COMPLETAR]), cuenta bancaria aperturada en fecha [FECHA], con saldo de [IMPORTE] euros (documento [COMPLETAR]); y certificado de asistencia y aprovechamiento al curso de formación profesional impartido por la entidad [COMPLETAR] (documento [COMPLETAR]).

De ello se deriva que existe una unidad familiar formada por mi representado y su madre y hermano, acreditándose una situación personal de adaptación a la cultura y costumbres española, conocimiento de los usos de la sociedad española, presencia continuada en España y vocación de permanencia, así como oferta de trabajo, por lo que debe concluirse que mi representado es una persona arraigada, al haber acreditado asimismo tener en nuestro país vínculos familiares de importancia, que encajan en el supuesto definido en el art. 45.2 del Reglamento de Extranjería [NOTA DE REVISIÓN: Es la numeración del RD 2393/2004 (art. 45.2.b, arraigo y definición de vínculos familiares). Hoy la definición está en el art. 127.c) RD 1155/2024. Unificar la cita con el resto del recurso. Fuente: RD 2393/2004, art. 45.2 (BOE-A-2005-323); RD 1155/2024, art. 127.c) (BOE-A-2024-24099).] cuando establece que los vínculos familiares deben entenderse referidos exclusivamente a los cónyuges o parejas de hecho, ascendientes y descendientes de primer grado en línea directa, siendo que mi representado convive con su madre.

En la resolución impugnada no se valoran estas circunstancias, limitándose a denegar la solicitud, siendo que no se han tenido en cuenta las circunstancias plenamente acreditadas de arraigo, por lo que solicitamos la estimación de presente recurso y con ello, la concesión del permiso de residencia solicitado.

SEGUNDO.- [COMPLETAR]

Por todo lo expuesto, SOLICITO tenga por presentado este escrito junto con los documentos que al mismo se acompañan, y por interpuesto recurso de reposición contra la resolución de fecha [FECHA] y, en virtud de las alegaciones contenidas en el mismo y previos los trámites legales, dicte resolución concediendo el permiso de residencia solicitado por mi representado.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma [COMPLETAR]

A LA SUBDELEGACIÓN DEL GOBIERNO DE [LOCALIDAD]
