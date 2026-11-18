---
name: pedir-caducidad-expediente-expulsion-386
description: "Redacta el escrito «Pedir la caducidad del expediente de expulsión» (formulario 386 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir la caducidad del expediente de expulsión

> Formulario 0386 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Remite a la vía del art. 31.3 LO 4/2000: hoy rigen los arts. 125-128 RD 1155/2024 y el tiempo como solicitante de protección internacional no computa (art. 126.b).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] COLEGIO
- [ ] NACIONALIDAD
- [ ] PROFESIÓN
- [ ] DNI/NIE
- [ ] CALLE
- [ ] FECHA (4 veces)
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… para su vida que supondría su regreso a»; «…vida del expedientado. 2) Certificado de»; «…3) Declaración de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 224.1 del Real Decreto 1155/2024
- artículo 31.3 de la LO 4/2000
- Ley 4/2000

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

### Formulario 0386 · Pedir la caducidad del expediente de expulsión

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)
- Avisos de la revisión: Remite a la vía del art. 31.3 LO 4/2000: hoy rigen los arts. 125-128 RD 1155/2024 y el tiempo como solicitante de protección internacional no computa (art. 126.b).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SUBDELEGACIÓN DEL GOBIERNO

Expte. Expulsión

Proc. N.º [Nº]

Asunto: Expulsión

D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Colegio de Abogados de [COLEGIO] y de D./Dña. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], de profesión [PROFESIÓN], con Pasaporte [DNI/NIE], con despacho profesional abierto en esta ciudad, calle [CALLE], Tfs., Fax., e-mail., comparezco y como mejor proceda, DIGO:

HECHOS

1) Que con fecha [FECHA], se le notificó a mi mandante el Acuerdo de INICIACIÓN DE PROCEDIMIENTO PREFERENTE DE EXPULSIÓN, en base a los hechos que en el mismo se contienen, y que fundamentalmente se concretan en lo siguiente:

«Se le imputa la comisión de una infracción a la Ley 4/2000, artículo 53.1.a): Encontrarse irregularmente en territorio español, por no haber obtenido o tener caducada más de tres meses la prórroga de estancia, la autorización de residencia o documentos análogos, cuando fueren exigibles y siempre que el interesado no hubiere solicitado la renovación de los mismos en el plazo previsto reglamentariamente».

2) Que en plazo legal el expedientado realizó el oportuno pliego de alegaciones.

3) Caducidad. Que el artículo 224.1 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la LO 4/2000, sobre Derechos y Libertades de los extranjeros en España señala que:

«1. El plazo máximo en que debe dictarse y notificarse la resolución que resuelva el procedimiento será de seis meses desde que se acordó su iniciación, sin perjuicio de lo dispuesto para el procedimiento simplificado en el artículo 237.

Transcurrido dicho plazo sin haberse resuelto y notificado la expresada resolución se producirá la caducidad del procedimiento y se procederá al archivo de las actuaciones a solicitud de cualquier interesado o de oficio por el órgano competente para dictar la resolución, excepto en los casos en que el procedimiento se hubiera paralizado por causa imputable a los interesados o en aquellos supuestos en que se hubiese acordado su suspensión.»

4) Que en el presente caso ha transcurrido el plazo máximo de los seis meses sin que se haya dictado y notificado la resolución que resuelva el procedimiento iniciado el día [FECHA], sin que se hubiera paralizado por causa imputable a los interesados o se hubiese acordado la suspensión del mismo, por lo que procede declarar la caducidad del procedimiento y el archivo de las actuaciones.

5) Que habiéndose acordado como medida cautelar la retirada del pasaporte del expedientado se deberá dejar igualmente sin efecto la medida, acordando su devolución al interesado.

6) Que en cualesquiera de los casos se quiere hacer constar en el expediente los documentos recientemente recibidos por el expedientado que demuestran la grave situación de peligro para su vida que supondría su regreso a [COMPLETAR] como consecuencia de las amenazas vertidas contra su persona por grupos paramilitares al margen de la ley y que están siendo estudiados con objeto de promover la solicitud de residencia temporal por motivos humanitarios acogida al tenor del artículo 31.3 de la LO 4/2000 [NOTA DE REVISIÓN: Las razones humanitarias del art. 31.3 LO se desarrollan hoy en el art. 128 RD 1155/2024. El art. 224.1 citado en el mismo formulario (caducidad a los seis meses) es correcto. Fuente: RD 1155/2024, arts. 128 y 224.1 (BOE-A-2024-24099).].

Docs. núms. 1 a 4, consistentes en:

1) Certificado de constancia del personero municipal sobre amenazas y peligro para la vida del expedientado.
2) Certificado de [COMPLETAR]
3) Declaración de [COMPLETAR]
4) Fotocopia de la denuncia.

Por lo expuesto,

SOLICITO DE ESA SUBDELEGACIÓN DEL GOBIERNO DE [LOCALIDAD], que tenga por presentado este escrito. Se sirva admitirlo, y a su vista, y previos los trámites pertinentes, proceda acordar la declaración de caducidad del procedimiento sancionador iniciado contra D./Dña. [NOMBRE Y APELLIDOS] el día [FECHA] y el archivo de las actuaciones, dejando asimismo sin efecto la medida cautelar de retirada de pasaporte, con devolución del mismo al interesado y dejando nota de los documentos acompañados.

En [LUGAR], a [FECHA].

Fdo.:
