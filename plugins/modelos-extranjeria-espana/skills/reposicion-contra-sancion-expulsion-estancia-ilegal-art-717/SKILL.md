---
name: reposicion-contra-sancion-expulsion-estancia-ilegal-art-717
description: "Redacta el escrito «Reposición contra sanción de expulsión por estancia ilegal (art. 53.a Ley de Extranjería)» (formulario 717 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra sanción de expulsión por estancia ilegal (art. 53.a Ley de Extranjería)

> Formulario 0717 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Sancionador de extranjería: la numeración del RD 1155/2024 se desplaza un número respecto del RD 557/2011. La cita al «art. 253» parece un error (es «vigilancia laboral»).
- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS
- [ ] COLEGIO
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (3 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA (3 veces)
- [ ] Nº
- [ ] DESCRIBIR (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en representación de D.»; «…solución del Subdelegado del Gobierno de»; «…ctada por el Subdelegado del Gobierno de»; «…r la cual se sanciona con la expulsión a»; «…CUMENTAL, consistente en que se oficie a»; «…3) TESTIFICAL, a fin de que se cite a D.»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112.1 de la Ley 39/2015
- art. 47 de la Ley 39/2015
- Real Decreto 557/2011
- Ley Orgánica 4/2000
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

### Formulario 0717 · Reposición contra sanción de expulsión por estancia ilegal (art. 53.a Ley de Extranjería)

- Año del modelo: 2009
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Sancionador de extranjería: la numeración del RD 1155/2024 se desplaza un número respecto del RD 557/2011. La cita al «art. 253» parece un error (es «vigilancia laboral»). · Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS] Letrado del Colegio de Abogados de [COLEGIO], colegiado número [Nº DE COLEGIADO/A], con domicilio a efectos de notificaciones sito en [LOCALIDAD] pudiendo ser notificado vía lexnet o en el correo electrónico [CORREO ELECTRÓNICO], y con teléfono [TELÉFONO], en representación de D. [COMPLETAR], la cual me ha sido conferida por turno de oficio, en el procedimiento nº [Nº DE PROCEDIMIENTO]/[AÑO], que se sigue por infracción del art. de la Ley de Extranjería, comparece y como mejor proceda, DICE:

Que en fecha [FECHA] he sido notificado de la resolución del Subdelegado del Gobierno de [COMPLETAR] de fecha [FECHA] por la que se imponía a mi representado la sanción de expulsión con prohibición de entrada en el territorio nacional por plazo de [Nº] años, y de conformidad con lo prevenido en el art. 112.1 de la Ley 39/2015, por medio del presente escrito interpongo RECURSO DE REPOSICIÓN en base a los siguientes MOTIVOS:

PRIMERO.- Al amparo de lo dispuesto en el art. 47 de la Ley 39/2015, en relación con los arts. 253 y concordantes del Real Decreto 557/2011, de 20 de abril [NOTA DE REVISIÓN (sin verificar en el BOE): El art. 253, tanto del RD 557/2011 como del RD 1155/2024, es «Vigilancia laboral» y no guarda relación con la nulidad por omisión del procedimiento. Probablemente quería citarse el procedimiento preferente: hoy arts. 233-236 RD 1155/2024 (antes 234-237 RD 557/2011). No está confirmado cuál era la intención: revisar antes de sustituir. Fuente: RD 557/2011, art. 253 (BOE-A-2011-7703); RD 1155/2024, arts. 233-236 y 253 (BOE-A-2024-24099).], por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, sobre derechos y libertades de los extranjeros en España y su integración social, tras su reforma por Ley Orgánica 2/2009, la resolución es nula por infringir el principio de audiencia, ocasionando indefensión, pues no se ha practicado ninguna de las pruebas propuestas por esta parte en su escrito de alegaciones.

Esta parte entiende que se ha prescindido total y absolutamente del procedimiento establecido en el art. 234.4 del Reglamento de Extranjería aprobado por Real Decreto 1155/2024 [NOTA DE REVISIÓN: Mismo texto («Si el interesado o su representante formulasen alegaciones...»), ahora en el art. 234.4. Fuente: RD 1155/2024, art. 234.4 (BOE-A-2024-24099); RD 557/2011, art. 235.4 (BOE-A-2011-7703).], el cual prescribe que "si el interesado o su representante formulasen alegaciones y realizaran proposición de prueba dentro del plazo establecido, el órgano instructor valorará la pertinencia o no de ésta. Si no se admitiesen las pruebas propuestas por improcedentes o innecesarias, se le notificará al interesado de forma motivada y se le dará trámite de audiencia conforme a lo previsto en el párrafo siguiente. En este supuesto, el acuerdo de iniciación del expediente, sin cambiar la calificación de los hechos, será considerado como propuesta de resolución con remisión a la autoridad competente para resolver. De estimarse por el instructor la pertinencia de la realización de prueba propuesta, ésta se realizará en el plazo máximo de tres días. Practicada en su caso la prueba, el instructor formulará propuesta de resolución que se notificará al interesado y le dará trámite de audiencia en el que se le concederá un plazo de cuarenta y ocho horas para formular alegaciones y presentar los documentos que estime pertinentes. Transcurrido dicho plazo se procederá a elevar la propuesta de resolución, junto con el expediente administrativo, a la autoridad competente para resolver."

Pues bien, esta parte propuso prueba tendente a acreditar el arraigo de mi representado consistente en [DESCRIBIR], la cual no fue admitida por el órgano instructor, no expresando los motivos o razones de la inadmisión y no respetando el trámite preceptivo de audiencia establecido en el citado art. 254.4 del Reglamento.

Ello deja a esta parte en una situación de completa indefensión, sin posibilidad de probar el arraigo de mi representado, lo que supone un motivo de nulidad de pleno derecho, que debe dar lugar a anular y dejar sin efecto la resolución sancionadora.

Con ser claro este motivo de nulidad, paso a exponer de forma subsidiaria los demás motivos, en los cuales se pone de manifiesto la relevancia de la indefensión producida.

SEGUNDO.- Al amparo de lo dispuesto en el art. 55.3 de la Ley de Extranjería en relación con el art. 57 de la misma Ley por infracción del principio de proporcionalidad en el ejercicio de la potestad sancionadora, al ser totalmente desproporcionada la sanción de expulsión, dadas las circunstancias concurrentes en mi representado.

()

Por todo lo expuesto,

SOLICITO: Que tenga por presentado este escrito junto con los documentos que al mismo se acompañan, y por interpuesto recurso de reposición contra [ACTO O RESOLUCIÓN], y previos los trámites legales oportunos, se anule la referida resolución de fecha [FECHA], dictada por el Subdelegado del Gobierno de [COMPLETAR] por la cual se sanciona con la expulsión a [COMPLETAR], y acuerde dictar en su día resolución de archivo del expediente o bien, subsidiariamente, imponer la sanción de multa en su cuantía mínima.

OTROSÍ PRIMERO DIGO: Que esta parte interesa reiterar la proposición de los siguientes medios de prueba en el procedimiento:

1) DOCUMENTAL, consistente en que se admitan los documentos acompañados a este escrito.

2) MÁS DOCUMENTAL, consistente en que se oficie a [COMPLETAR] para que emita certificado sobre [DESCRIBIR]

3) TESTIFICAL, a fin de que se cite a D. [COMPLETAR], con domicilio en [LOCALIDAD], el cual podrá declarar sobre las circunstancias de arraigo de mi representado, concretamente que

Por lo que, SOLICITO que se tengan por propuestos estos medios probatorios, acordándose su admisión y lo conducente a su práctica.

A LA SUBDELEGACIÓN DEL GOBIERNO DE [LOCALIDAD]
