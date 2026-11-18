---
name: alzada-contra-resolucion-administrativa-1010
description: "Redacta el escrito «Alzada contra resolución administrativa» (formulario 1010 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra resolución administrativa

> Formulario 1010 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO (2 veces)
- [ ] FECHA (9 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…s Administraciones Públicas (LPACAP), en»; «…, presentó instancia»; «…ante [ÓRGANO], a fin de que»; «…GUNDO.- Concluida la fase de instrucción»; «…con fecha [FECHA],»; «…de las partes la propuesta de resolución»; «…parte. RAZONAMIENTOS JURÍDICOS PRIMERO.-»; «…SEGUNDO.-»; «…SEGUNDO.- [COMPLETAR] TERCERO.-»; «…s 121 y 122 LPACAP, SUPLICA Que se anule»; «…, por la que»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 66.1.b) de la Ley 39/2015
- art. 21.4 LPACAP
- artículos 121 y 122 LPACAP

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

### Formulario 1010 · Alzada contra resolución administrativa

- Año del modelo: 2008
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.],

conforme al art. 66.1.b) de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (LPACAP), en [COMPLETAR], comparece ante [ÓRGANO], y como mejor proceda en derecho

EXPONE

Que en virtud de este escrito interpone recurso de ALZADA contra la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], por cuanto, y dicho en términos de defensa, considera que no es ajustada a derecho, lo que realiza con base en los siguientes hechos y fundamentos de derecho.

ANTECEDENTES DE HECHO

PRIMERO.- Mediante escrito de fecha [FECHA], presentó instancia [COMPLETAR] ante [ÓRGANO], a fin de que [COMPLETAR], de conformidad con la legislación sustantiva y de procedimiento aplicable.

Con fecha [FECHA], se dictó acuerdo de iniciación de expediente que fue notificado con fecha [FECHA]. En dicha notificación se indicaba, conforme al art. 21.4 LPACAP, el plazo máximo establecido para la resolución y notificación, así como de los efectos del silencio administrativo. Asimismo se indicaba el objeto del procedimiento y la tramitación a seguir, así como los órganos responsables de la misma.

SEGUNDO.- Concluida la fase de instrucción [COMPLETAR] con fecha [FECHA], [COMPLETAR], se puso de manifiesto el expediente a fin de que los interesados pudieran tomar audiencia y vista del mismo y alegaran cuanto tuvieran por conveniente, con el resultado que obra en el mismo.

TERCERO.- Mediante escrito de fecha [FECHA], se puso en conocimiento de las partes la propuesta de resolución [COMPLETAR] a fin de [DESCRIBIR]

CUARTO.- Con fecha [FECHA], se me ha notificado la resolución que pone fin al expediente, por la que se deniega lo solicitado por esta parte.

RAZONAMIENTOS JURÍDICOS

PRIMERO.- [COMPLETAR]

SEGUNDO.- [COMPLETAR]

TERCERO.- [COMPLETAR]

En atención a los preceptos citados y de conformidad con las previsiones de los artículos 121 y 122 LPACAP,

SUPLICA

Que se anule [COMPLETAR] de la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], por la que [COMPLETAR], y en su lugar, se resuelva conforme a lo solicitado por este parte en su escrito de iniciación del presente expediente.

En [LUGAR], a [FECHA].

Firmado:
