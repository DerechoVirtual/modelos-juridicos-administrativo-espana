---
name: certificacion-descubierto-iniciar-via-apremio-1745
description: "Redacta el escrito «Certificación de descubierto para iniciar la vía de apremio» (formulario 1745 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificación de descubierto para iniciar la vía de apremio

> Formulario 1745 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] FECHA (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…de»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 21.2 del Real Decreto 320/1994
- art. 21 RD 320/1994
- art. 110 TR LTCVMSV

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

### Formulario 1745 · Certificación de descubierto para iniciar la vía de apremio

- Año del modelo: 2004
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 desplegables convertidos en elección en blanco; 12 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de Certificación de Descubierto previsto en artículo 21.2 del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, por el que la Autoridad Administrativa hacen constancia de que el infractor no ha hecho efectivo en el órgano de recaudación la multa impuesta, con el objeto de iniciar la vía de apremio.

Con fecha [FECHA], por la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR], se ha dictado resolución sancionadora en el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], por la que se impone a D./Dña. [NOMBRE Y APELLIDOS], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], una MULTA de [IMPORTE] euros como consecuencia de una infracción administrativa de la legislación de tráfico (1).

Vistos los antecedentes mencionados y el estado de ingresos por dicho concepto al día de la fecha, de conformidad con el artículo 21.2 del Real Decreto 320/1994 [NOTA DE REVISIÓN (sin verificar en el BOE): Formalmente vigente; apoyo legal: art. 110 TR LSV (apremio tras 15 días naturales desde la firmeza; normativa tributaria). Que el título ejecutivo sea hoy la providencia de apremio de la LGT: NO VERIFICADO en esta revisión. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 110; RD 320/1994, BOE-A-1994-8985 art. 21.], de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, se expide la presente CERTIFICACIÓN DE DESCUBIERTO, para hacer constar que el interesado no ha hecho efectiva en el órgano de recaudación la multa impuesta, a los efectos prevenidos para este título ejecutivo en la reglamentación general sobre recaudación en la vía de apremio.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) Las multas deberán hacerse efectivas a los órganos de recaudación de la Administración gestora, directamente o a través de entidades de depósitos, dentro de los QUINCE DÍAS naturales siguientes a la fecha de su firmeza [NOTA DE REVISIÓN: Pago tras la firmeza: 15 días naturales (art. 110.1 TR LSV), no hábiles como decía el art. 21.1 RD 320/1994. La recaudación ejecutiva se rige por la normativa tributaria (110.2). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 110.]. Vencido este plazo de ingreso sin que se hubiese satisfecho la multa, su exacción se llevará a cabo por el procedimiento de apremio. A tal efecto será título ejecutivo la CERTIFICACION DE DESCUBIERTO expedida por el órgano competente de la Administración gestora (art. 21 RD 320/1994 y art. 110 TR LTCVMSV).
