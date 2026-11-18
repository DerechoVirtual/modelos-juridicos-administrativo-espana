---
name: notificar-denegacion-prorroga-necesidad-traslado-1906
description: "Redacta el escrito «Notificar la denegación de prórroga por necesidad de traslado» (formulario 1906 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificar la denegación de prórroga por necesidad de traslado

> Formulario 1906 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.
- **Criterio de Hacienda y del TEAC** → `buscar_consultas_hacienda` → `leer_consulta_hacienda`; `buscar_doctrina_teac` → `leer_resolucion_teac`.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…estra condición de propietarios del piso»; «…número [NÚMERO] de»; «…, fueran inevitables". 4. En la cláusula»

## Elecciones que hay que hacer

- Sr. mío / Sra. mía

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 9 LAU
- artículo 9 de la Ley 29/1994

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

### Formulario 1906 · Notificar la denegación de prórroga por necesidad de traslado

- Año del modelo: 2004
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Notificación de denegación de prórroga forzosa del contrato de arrendamiento, por necesidad de traslado inexcusable, al amparo de lo dispuesto en el artículo 9 LAU 1994.

Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS]

Calle

Código Postal-Población

Fecha

Destinatario: Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS]

Calle

Código Postal-Población

Muy [ELEGIR: Sr. mío / Sra. mía]:

Por medio de la presente y por conducto notarial, nos dirigimos a usted en nuestra condición de propietarios del piso [COMPLETAR] de la finca sita en la calle [CALLE] número [NÚMERO] de [COMPLETAR], que le tenemos arrendado mediante contrato de fecha [FECHA], para denegarle, como se lo hacemos saber a través de la presente, la prórroga forzosa de su contrato de arrendamiento con base en las siguientes consideraciones:

1. La denegación de la prórroga se efectúa al amparo de lo dispuesto en el artículo 9 de la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos (LAU) que establece que "1. La duración del arrendamiento será libremente pactada por las partes. Si esta fuera inferior a cinco años, o inferior a siete años si el arrendador fuese persona jurídica, llegado el día del vencimiento del contrato, este se prorrogará obligatoriamente por plazos anuales hasta que el arrendamiento alcance una duración mínima de cinco años, o de siete años si el arrendador fuese persona jurídica, salvo que el arrendatario manifieste al arrendador, con treinta días de antelación como mínimo a la fecha de terminación del contrato o de cualquiera de las prórrogas, su voluntad de no renovarlo.

El plazo comenzará a contarse desde la fecha del contrato o desde la puesta del inmueble a disposición del arrendatario si esta fuere posterior. Corresponderá al arrendatario la prueba de la fecha de la puesta a disposición.

2. Se entenderán celebrados por un año los arrendamientos para los que no se haya estipulado plazo de duración o este sea indeterminado, sin perjuicio del derecho de prórroga anual para el arrendatario, en los términos resultantes del apartado anterior.
3. Una vez transcurrido el primer año de duración del contrato y siempre que el arrendador sea persona física, no procederá la prórroga obligatoria del contrato cuando, al tiempo de su celebración, se hubiese hecho constar en el mismo, de forma expresa, la necesidad para el arrendador de ocupar la vivienda arrendada antes del transcurso de cinco años para destinarla a vivienda permanente para sí o sus familiares en primer grado de consanguinidad o por adopción o para su cónyuge en los supuestos de sentencia firme de separación, divorcio o nulidad matrimonial.

Para ejercer esta potestad de recuperar la vivienda, el arrendador deberá comunicar al arrendatario que tiene necesidad de la vivienda arrendada, especificando la causa o causas entre las previstas en el párrafo anterior, al menos con dos meses de antelación a la fecha en la que la vivienda se vaya a necesitar y el arrendatario estará obligado a entregar la finca arrendada en dicho plazo si las partes no llegan a un acuerdo distinto.

Si transcurridos tres meses a contar de la extinción del contrato o, en su caso, del efectivo desalojo de la vivienda, no hubieran procedido el arrendador o sus familiares en primer grado de consanguinidad o por adopción o su cónyuge en los supuestos de sentencia firme de separación, divorcio o nulidad matrimonial a ocupar esta por sí, según los casos, el arrendatario podrá optar, en el plazo de treinta días, entre ser repuesto en el uso y disfrute de la vivienda arrendada por un nuevo período de hasta cinco años, respetando, en lo demás, las condiciones contractuales existentes al tiempo de la extinción, con indemnización de los gastos que el desalojo de la vivienda le hubiera supuesto hasta el momento de la reocupación, o ser indemnizado por una cantidad equivalente a una mensualidad por cada año que quedara por cumplir hasta completar cinco años, salvo que la ocupación no hubiera tenido lugar por causa de fuerza mayor, entendiéndose por tal, el impedimento provocado por aquellos sucesos expresamente mencionados en norma de rango de Ley a los que se atribuya el carácter de fuerza mayor, u otros que no hubieran podido preverse, o que, previstos, fueran inevitables".

4. En la cláusula [COMPLETAR] del citado contrato se hacía constar la necesidad de ocupar la vivienda arrendada para destinarla a vivienda permanente para nuestra hija, por trasladar su domicilio desde Zaragoza a Madrid con motivo de cursar estudios que no se imparten en la ciudad primeramente citada necesitando así el domicilio que ocupa usted en Fuenlabrada.

El presente requerimiento lo efectuamos con treinta días de antelación, y, de conformidad con lo previsto en el artículo 9 de la ley 29/1994, "ut supra."

Sin otro particular, le saludamos atentamente.

Firma y DNI
