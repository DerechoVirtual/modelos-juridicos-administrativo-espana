---
name: reposicion-contra-acto-administracion-local-708
description: "Redacta el escrito «Reposición contra acto de la Administración Local» (formulario 708 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra acto de la Administración Local

> Formulario 0708 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] IMPORTE
- [ ] Nº
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…untamiento por el concepto tributario de»; «… Ejercicio o periodo: Núm. de expediente»; «…Núm. de liquidación»; «…recurrente por el concepto tributario de»; «…, ese Ayuntamiento no tuvo en cuenta»; «…del Ayuntamiento de SEGUNDA.-»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSI DIGO…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 14.2 del Real Decreto Legislativo 2/2004

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

### Formulario 0708 · Reposición contra acto de la Administración Local

- Año del modelo: 2009
- Revisión 17-11-2026: 2 llamadas a nota sin texto retiradas; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 párrafos opcionales señalados; 17 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL [ÓRGANO AL QUE SE DIRIGE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]

actuando

[ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original]

comparece y como mejor proceda en derecho,

EXPONE

Que mediante el presente escrito se interpone RECURSO DE REPOSICIÓN, conforme a lo dispuesto en el artículo 14.2 del Real Decreto Legislativo 2/2004, de 5 de marzo, por el que se aprueba el texto refundido de la Ley Reguladora de las Haciendas Locales, contra el acto administrativo dictado por ese Ayuntamiento por el concepto tributario de [COMPLETAR] con fecha

Que el acto contra el que se recurre es el siguiente:

Ejercicio o periodo:

Núm. de expediente [COMPLETAR]

Núm. de liquidación [COMPLETAR]

Importe [IMPORTE] euros

Que el mismo se estima no ajustado a derecho, así como la subsiguiente liquidación, presentando a estos efectos, como fundamento de la pretensión ejercitada, las siguientes

ALEGACIONES

PRIMERA.- Que en la liquidación que se giró al recurrente por el concepto tributario de [COMPLETAR], ese Ayuntamiento no tuvo en cuenta [COMPLETAR] de acuerdo con lo previsto en la Ordenanza Municipal Nº [Nº] del Ayuntamiento de

SEGUNDA.- [COMPLETAR]

TERCERA.- Que en prueba de las alegaciones expuestas se acompaña la siguiente documentación:

Que al amparo de lo establecido en el artículo 14.2 del Real Decreto Legislativo 2/2004, de 5 de marzo, por el que se aprueba el texto refundido de la Ley Reguladora de las Haciendas Locales, interesa la suspensión del acto administrativo impugnado ofreciéndose a tal efecto como garantía

Por todo lo expuesto, a VS

SOLICITA

Tenga por presentado en tiempo y forma el presente escrito y documentos que lo acompañan y por interpuesto recurso de reposición contra la liquidación tributaria referida y, previos los trámites legales oportunos, se dicte resolución en la que se acuerde anular la liquidación practicada por improcedente y la práctica de una nueva en la que se tenga en cuenta lo expuesto en el presente recurso.

[OPCIONAL — incluir si procede]

OTROSI DIGO

Se solicita expresamente declare suficiente la garantía prestada y dicte resolución por la que se declare en suspenso la ejecución del acto impugnado.

En [LUGAR], a [FECHA].

Firmado:
