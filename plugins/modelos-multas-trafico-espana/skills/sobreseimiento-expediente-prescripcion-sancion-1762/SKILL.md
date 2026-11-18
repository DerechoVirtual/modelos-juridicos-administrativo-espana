---
name: sobreseimiento-expediente-prescripcion-sancion-1762
description: "Redacta el escrito «Sobreseimiento del expediente por prescripción de la sanción» (formulario 1762 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Sobreseimiento del expediente por prescripción de la sanción

> Formulario 1762 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] AÑO (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…resado, de un procedimiento de ejecución»; «…el archivo de las actuaciones seguidas a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 30 de la Ley 40/2015
- artículo 30 LRJSP
- art. 30 LRJSP
- Ley 39/2015
- Real Decreto Legislativo 6/2015

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

### Formulario 1762 · Sobreseimiento del expediente por prescripción de la sanción

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 7 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Acuerdo por el que se declara la prescripción de la sanción y se procede al archivo de las actuaciones seguidas en el expediente sancionador como consecuencia de la misma.

Mediante resolución firme de fecha [FECHA], recaída en el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], por este Centro Directivo, se impuso a D./Dña. [NOMBRE Y APELLIDOS], la siguiente sanción:

Resultando que, desde la fecha en que ganó firmeza la resolución mencionada, han transcurrido los plazos establecidos para la prescripción de la sanción impuesta, sin que se haya procedido a su ejecución en la forma reglamentaria (1).

Considerando que de conformidad con las previsiones del artículo 30 de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público (en adelante, LRJSP), el plazo de prescripción de las sanciones comenzará a contarse desde el día siguiente a aquel en que sea ejecutable la resolución por la que se impone la sanción o haya transcurrido el plazo para recurrirla y que interrumpirá la prescripción el inicio, con conocimiento del interesado, de un procedimiento de ejecución [COMPLETAR], volviendo a transcurrir el plazo si aquél está paralizado durante más de un mes por causa no imputable al infractor.

Vistos los antecedentes mencionados, el artículo 30 LRJSP, y las demás normas de general y pertinente aplicación, he tenido a bien

RESOLVER

Primero.- Se declara la prescripción de la sanción y el archivo de las actuaciones seguidas a [COMPLETAR], en el expediente sancionador número [Nº DE PROCEDIMIENTO]/[AÑO], que se ha tramitado en este Centro Directivo.

Segundo.- Notifíquese la presente resolución al interesado con indicación de los recursos que procedan de conformidad con lo previsto en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) El art. 30 LRJSP se remite a los plazos de prescripción establecidos en leyes especiales. Si éstas no fijan plazos de prescripción, las sanciones impuestas por faltas muy graves prescribirán a los tres años, las impuestas por faltas graves a los dos años y las impuestas por faltas leves a los seis meses. En nuestro caso, el art. 112. 4 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, establece el plazo de prescripción de cuatro años para las sanciones consistentes en multa y de un año para la sanción de suspensión prevista en el artículo 80. Conviene hacer notar que la prescripción puede ser apreciada de oficio por los tribunales: "La Sala puede revisar de oficio aquellos defectos y circunstancias que incidan en la legalidad de la resolución, pues no se compadecería con el derecho a la tutela judicial efectiva una declaración que obviase tal circunstancia ya que el principio iura novit curia legitima una decisión como la efectuada. A este respecto y teniendo en cuenta el criterio jurisprudencial que considera aplicables a dicha parte del Derecho Administrativo los principios clásicos que inspiran el Derecho Penal, no está de más recordar que la jurisprudencia de la Sala Segunda del TS ha afirmado resueltamente la naturaleza material de la prescripción en la esfera de lo punitivo, rechazando el carácter procesal que se le venía concediendo por influjo del Derecho Privado, y ha reconocido la posibilidad de ser declarada de oficio en cualquier estado del procedimiento" (STS 27 julio 1989).
