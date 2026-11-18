---
name: mandato-poder-representacion-tramitar-nacionalidad-262
description: "Redacta el escrito «Mandato con poder de representación para tramitar la nacionalidad española» (formulario 262 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Mandato con poder de representación para tramitar la nacionalidad española

> Formulario 0262 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] LUGAR
- [ ] FECHA

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 1709 a 1739 del Código Civil
- artículo 5 de la Ley 39/2015
- Ley Orgánica 3/2018

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

### Formulario 0262 · Mandato con poder de representación para tramitar la nacionalidad española

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS] con NIE nº [DNI/NIE] y domicilio en [LOCALIDAD] en la C/ [CALLE] C.P. en concepto de MANDANTE, manifiesta:

Que por el presente documento confiere MANDATO CON PODER DE REPRESENTACIÓN a favor de D./Dña. [NOMBRE Y APELLIDOS], Abogado en ejercicio, colegiado número [Nº DE COLEGIADO/A], perteneciente al Ilustre Colegio de Abogados de [COLEGIO], con domicilio en [LOCALIDAD] en la C/ [CALLE] C.P. en concepto de MANDATARIO

Que el presente MANDATO, que se regirá por los artículos 1709 a 1739 del Código Civil, se confiere al amparo del artículo 5 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, [NOTA DE REVISIÓN: Se ha suprimido la cita del art. 23 de la Ley 11/2007, derogada por la Ley 39/2015 (disposición derogatoria única); el apoderamiento se rige por el art. 5 de la Ley 39/2015. Fuente: Ley 39/2015, art. 5 y disposición derogatoria única (BOE-A-2015-10565).] para que promueva, solicite y realice todos los trámites necesarios en relación con el siguiente ASUNTO: SOLICITUD DE NACIONALIDAD ESPAÑOLA POR RESIDENCIA DE D./Dña. [NOMBRE Y APELLIDOS]

Que el presente MANDATO se confiere para su actuación ante todos los órganos y entidades de la Administración del Estado, Autonómica, Provincial y Local que resulten competentes, en relación con los trámites del asunto objeto de este MANDATO, y específicamente ante el Ministerio de Justicia del Gobierno de España.

Que conoce y acepta que los datos que se suministran pueden incorporarse a ficheros automatizados de los que será responsable el abogado al que se le otorga el MANDATO, con el único objeto de posibilitar la prestación de los servicios profesionales objeto del presente MANDATO y el cumplimiento de las obligaciones derivadas del trámite encomendado, pudiendo ejercitar ante los mismos, en su caso, los derechos de acceso, rectificación, cancelación y oposición, de conformidad con la Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales.

Que el MANDATARIO acepta el MANDATO conferido y se obliga a cumplirlo de conformidad con las instrucciones del mandante, y declara bajo su responsabilidad que los documentos recibidos del mandante han sido verificados en cuanto a la corrección formal de los datos contenidos en los mismos.

En [LUGAR], a [FECHA].

Fdo.:	EL MANDANTE
Fdo.	EL MANDATARIO
