---
name: resolucion-sancionadora-trafico-alcaldia-152
description: "Redacta el escrito «Resolución sancionadora de tráfico de una Alcaldía» (formulario 152 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución sancionadora de tráfico de una Alcaldía

> Formulario 0152 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] Nº
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO], seguido en esta Alcaldía de»; «…, calle o plaza»; «…tiva según lo establecido en el artículo»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 84 TR LTCVMSV
- Real Decreto Legislativo 6/2015
- Ley 39/2015

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

### Formulario 0152 · Resolución sancionadora de tráfico de una Alcaldía

- Año del modelo: 2017
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el expediente sancionador número [Nº DE PROCEDIMIENTO]/[AÑO], seguido en esta Alcaldía de [COMPLETAR], a D./Dña. [NOMBRE Y APELLIDOS], DNI número [DNI/NIE], con domicilio en [LOCALIDAD], calle o plaza [COMPLETAR], número [NÚMERO], como consecuencia de una infracción a la legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial, resulta:

ANTECEDENTES DE HECHO

Primero.- Con fecha [FECHA], siendo las [Nº] horas, por el/la denunciado/a se realizaron los siguientes hechos, según consta en la denuncia de fecha [FECHA], formulada por agente encargado de la vigilancia del tráfico:

Segundo.- Con fecha [FECHA] se presentó escrito de descargos y alegaciones por parte del/de la inculpado/a en el que se manifestó cuanto tuvo por conveniente en orden a la mejor defensa de su derecho en el que realiza las siguientes manifestaciones:

FUNDAMENTOS JURIDICOS

Primero.- La conducta realizada por el/la infractor/a y que ha resultado probada en el expediente, es infracción administrativa según lo establecido en el artículo [COMPLETAR] del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), por cuanto:

Segundo.- Las alegaciones presentadas por el/la inculpado/a no pueden estimarse, por cuanto no desvirtúan el relato de los hechos, ni su calificación jurídica, ni la aplicación correcta de los principios que gobiernan la potestad sancionadora y el procedimiento sancionador seguido en este expediente y así se acredita en los siguientes términos:

Vistos los antecedentes mencionados, la propuesta de resolución del órgano instructor, habiéndose observado todos los trámites legales y reglamentarios establecidos, de conformidad con las previsiones del artículo 84 TR LTCVMSV, he tenido a bien dictar el siguiente

DECRETO:

Primero. Imponer una sanción de [IMPORTE] euros a D./Dña. [NOMBRE Y APELLIDOS], como responsable de la infracción administrativa a que se hace referencia en el apartado primero de los fundamentos jurídicos de esta resolución.

Segundo. Notifíquese la presente resolución al interesado con indicación de los recursos que procedan de conformidad con lo establecido en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, en relación con las disposiciones de régimen local aplicables.

En [LUGAR], a [FECHA].

Firma del/la Alcalde/Alcaldesa
