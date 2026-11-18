---
name: edicto-ejecucion-subsidiaria-desalojar-personas-enseres-699
description: "Redacta el escrito «Edicto de ejecución subsidiaria para desalojar personas y enseres de un inmueble» (formulario 699 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Edicto de ejecución subsidiaria para desalojar personas y enseres de un inmueble

> Formulario 0699 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] FECHA (4 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA DEL DECRETO
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA DEL ESCRITO
- [ ] 100.1 b) LPACAP
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Nº
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CEDENTES DE HECHO Por resolución de este»; «…de fecha [FECHA] de»; «…de fecha [FECHA] de [COMPLETAR] de 200»; «…nº [NÚMERO] (finca registral»; «…referencia catastral»; «…:»; «…sados un plazo de alegaciones de 10 días»; «…:»; «…:»; «…: [COMPLETAR]) de»; «…: [COMPLETAR]) de [COMPLETAR] de»; «…) de [COMPLETAR] de [COMPLETAR] de 201»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 99 de la Ley 39/2015
- artículo 102.1 LPACAP
- art. 100.3 LPACAP
- artículo 44 de la Ley 39/2015
- art. 112.1 de la Ley 39/2015
- arts. 123 Ley 39/2015

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

### Formulario 0699 · Edicto de ejecución subsidiaria para desalojar personas y enseres de un inmueble

- Año del modelo: 2010
- Revisión 17-11-2026: 23 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 5 huecos del original que se habían perdido sin marca, marcados (FECHA DEL DECRETO, FECHA DEL ESCRITO, NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

por su Decreto de fecha [FECHA] ha dispuesto lo siguiente:

ANTECEDENTES DE HECHO

Por resolución de este [COMPLETAR] de fecha [FECHA] de [COMPLETAR] de 200 [COMPLETAR] se inicia procedimiento de ejecución subsidiaria para el desalojo de personas y enseres de inmueble sito en C/ [CALLE] nº [NÚMERO] (finca registral [COMPLETAR] referencia catastral [COMPLETAR]) que fue declarado en ruina técnica y económica (Decreto de fecha [FECHA DEL DECRETO]: [COMPLETAR]) concediéndose a los interesados un plazo de alegaciones de 10 días [COMPLETAR] Dentro de plazo comparece D./Dña. [NOMBRE Y APELLIDOS]: ocupante de la vivienda, para manifestar que debido a su situación económica no dispone de medios para acceder a otra vivienda, por lo que solicita que sea la Ciudad de Ceuta quien le haga entrega de una vivienda. La propiedad a través de representación legal presenta escrito (de fecha [FECHA DEL ESCRITO]: [COMPLETAR]) en el que solicita que se proceda al desalojo de las personas y enseres que habita el inmueble que nos ocupa, habida cuenta del tiempo transcurrido desde el inicio del citado procedimiento, así como posterior autorización judicial para ejecutar tal acto.

FUNDAMENTOS DE DERECHO

1º.- En cuanto a lo manifestado por el/los alegante/es, escasez de recursos económicos, para acceder a otra vivienda, es necesario indicar que no desvirtúa lo actuado, atendido que lo que se pretende con el desalojo es evitar riegos, tanto para las personas como para los bienes materiales.

2º.- El art. 99 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, establece que las Administraciones Públicas, a través de sus órganos competentes en cada caso, podrán proceder, previo apercibimiento, a la ejecución forzosa de los actos administrativos, salvo en los supuestos en que se suspenda la ejecución de acuerdo con la Ley, o cuando la Constitución o la Ley exijan la intervención de los Tribunales.

- La ejecución subsidiaria es uno de los medios de ejecución forzosa establecidos por dicha norma legal [100.1 b) LPACAP]. El artículo 102.1 LPACAP, dispone que habrá lugar a la ejecución subsidiara cuando se trate de actos que por no ser personalísimos puedan ser realizados por sujeto distinto del obligado.

- El art. 100.3 LPACAP dispone que si fuese necesario entrar en el domicilio del afectado, las Administraciones Públicas deberán obtener el consentimiento del mismo o, en su defecto, la oportuna autorización judicial.

- El art. 8.6 de la Ley 29/98, de 13 de julio, Reguladora de la Jurisdicción contencioso administrativa, atribuye a los Juzgados de dicha jurisdicción autorizar la entrada en domicilio.

3º.- El Consejero de Fomento ostenta competencias en materia de urbanismo por asignación de funciones efectuadas por el Presidente de la Ciudad mediante Decreto de fecha

PARTE DISPOSITIVA

1º.- Se desestima la alegación presentada por D./Dña. [NOMBRE Y APELLIDOS]: contra resolución de esta Consejería de fecha [FECHA]

2º.- Se ordena la ejecución subsidiaria del desalojo de personas y enseres del inmueble sito en C/ [CALLE] nº [NÚMERO] debiéndose fijar día y hora para efectuar el lanzamiento, siendo necesario para ello contar con la preceptiva autorización judicial.

3º.- Dese traslado de la presente resolución a la Consejería de Asuntos Sociales así como a la Empresa Municipal de la Vivienda, S. A. (EMVICESA).

4º.- Solicítese autorización judicial para ejecutar el desalojo de personas y enseres.-

Atendido que no ha podido practicarse la notificación de esta Resolución a D./Dña. [NOMBRE Y APELLIDOS] y a D./Dña. [NOMBRE Y APELLIDOS] según los términos del artículo 44 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, por el presente Anuncio se hace pública la anterior Resolución, significándole que contra esta resolución que agota la vía administrativa, y en cumplimiento de lo previsto en el art. 112.1 de la Ley 39/2015, podrá interponer recurso potestativo de reposición, que cabrá fundar en cualquiera de los motivos de nulidad o anulabilidad previstos en los artículos 47 y 48 de dicha Ley, ante el mismo órgano que dictó el acto, en el plazo de un mes, o ser impugnada directamente ante el Tribunal de Instancia (Sección de lo Contencioso-Administrativo) de esta Ciudad, en el plazo de dos meses contados a partir del día siguiente al de la recepción de esta notificación (arts. 123 Ley 39/2015, de 1 de octubre) y 8.1 y 46 de la 29/98, de 13 de julio.

No obstante lo anterior podrá ejercitar cualquier otro recurso que estime procedente.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

V.ºB.º EL PRESIDENTE, P. D. F. EL CONSEJERO DE FOMENTO (Decreto de la Presidencia de fecha [FECHA]) Fdo.: LA SECRETARIA GENERAL, por Delegación de Firma (Boletín correspondiente: núm. [Nº]: [COMPLETAR]) de [COMPLETAR] de [COMPLETAR] de 201 [COMPLETAR] EL TÉCNICO DE ADMINISTRACIÓN GENERAL.-

Fdo.:
