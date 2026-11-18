---
name: denuncia-particular-infracciones-trafico-seguridad-vial-1742
description: "Redacta el escrito «Denuncia de un particular por infracciones de tráfico y seguridad vial» (formulario 1742 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia de un particular por infracciones de tráfico y seguridad vial

> Formulario 1742 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CORREO ELECTRÓNICO
- [ ] CALLE
- [ ] NÚMERO
- [ ] TELÉFONO
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] MATRÍCULA
- [ ] MARCA/MODELO (2 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…y domicilio para notificaciones en»; «…, calle [CALLE], número [NÚMERO] piso»; «…de»; «…horas del día [FECHA] de»; «…, color»; «…, marca [MARCA/MODELO], conducido por»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía
- Alcaldía / Jefatura de Tráfico

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 4.2 del Real Decreto 320/1994
- artículo 4.2 Real Decreto 320/1994
- art. 5 RD 320/1994

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

### Formulario 1742 · Denuncia de un particular por infracciones de tráfico y seguridad vial

- Año del modelo: 2004
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 2 desplegables convertidos en elección en blanco; 20 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de denuncia de particular sobre hechos constitutivos de infracciones de tráfico y seguridad vial, con relato de los mismos e identificación del vehículo infractor.

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], de profesión [PROFESIÓN], con correo electrónico [CORREO ELECTRÓNICO] y domicilio para notificaciones en [COMPLETAR], calle [CALLE], número [NÚMERO] piso [COMPLETAR], teléfono [TELÉFONO], ante la [ELEGIR: Alcaldía / Jefatura de Tráfico] de [COMPLETAR] formula la siguiente DENUNCIA (1)

EXPONE:

Que siendo las [Nº] horas del día [FECHA] de [COMPLETAR] del año en curso, el vehículo con matrícula [MATRÍCULA], color [COMPLETAR], modelo [MARCA/MODELO], marca [MARCA/MODELO], conducido por [COMPLETAR], realizó los siguientes

Hechos:

Que los citados hechos pueden ser constitutivos de infracción administrativa, por los que los denuncia, de conformidad con las previsiones del artículo 4.2 del Real Decreto 320/1994 [NOTA DE REVISIÓN: Compatible y formalmente vigente; el apoyo legal es el art. 86.1 TR LSV (incoación por denuncia de cualquier persona). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 86.1; RD 320/1994, BOE-A-1994-8985 art. 4.], de 25 de febrero, por el que se aprueba el Reglamento de Procedimiento Sancionador en materia de Tráfico, Circulación de Vehículos a Motor y Seguridad Vial.

En virtud de lo expuesto,

SOLICITA:

Que se tenga por presentado este escrito de denuncia y previas las comprobaciones que sean necesarias se proceda a la iniciación del correspondiente expediente sancionador contra las personas que resulten responsables de las infracciones cometidas.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) El artículo 4.2 Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de Procedimiento Sancionador en materia de Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, recoge como denuncia de carácter voluntario la realizada por cualquier persona.

El contenido que reglamentariamente debe constar en estas denuncias es el siguiente:

• identificación del vehículo con el que se hubiese cometido la supuesta infracción,
• la identidad del denunciado si fuere conocida,
• una relación circunstanciada del hecho, con expresión del lugar,
• fecha y hora y el nombre, profesión y domicilio del denunciante (art. 5 RD 320/1994).

A diferencia de las denuncias formuladas por agentes de la autoridad (cuya formulación constituye el acto de incoación del expediente), las denuncias formuladas por particulares no pueden ser consideradas como medios de iniciación del procedimiento, "la denuncia carece de virtualidad para poner en marcha el procedimiento sancionador" (STS 23 junio 1987).
