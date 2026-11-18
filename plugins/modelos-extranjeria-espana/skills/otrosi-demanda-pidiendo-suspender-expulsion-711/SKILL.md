---
name: otrosi-demanda-pidiendo-suspender-expulsion-711
description: "Redacta el escrito «Otrosí de demanda pidiendo suspender la expulsión» (formulario 711 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí de demanda pidiendo suspender la expulsión

> Formulario 0711 del plugin **Extranjería** · revisado el 17-11-2026.

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

El formulario no tiene campos marcados: revisa el texto por si hay datos implícitos.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 130 de la Ley 29/1998

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

### Formulario 0711 · Otrosí de demanda pidiendo suspender la expulsión

- Año del modelo: 2009
- Revisión 17-11-2026: 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

OTROSI DIGO: De conformidad con lo que se dispone en el artículo 130 de la vigente Ley de la Jurisdicción Contencioso-administrativa, interesa la suspensión de la sanción de expulsión impuesta a mi representado en base a los siguientes hechos y fundamentos:

I.- Solicitamos de este Órgano Jurisdiccional al que tenemos el honor de dirigirnos, la adopción de la medida cautelar de suspensión de la resolución impugnada pues, de no producirse, el recurso perdería su finalidad legítima, produciendo perjuicios irreparables a mi representado.

Los AATS de 2 de noviembre de 2000 y 5 de febrero, 21 de marzo y 25 de junio de 2001 exponen que en el nuevo régimen de medidas cautelares instaurado por la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso-Administrativa, se permite al Órgano jurisdiccional en sus artículos 129 y 130, la adopción de las medidas cautelares teniendo en cuenta una doble referencia: valorando no sólo la posibilidad de que la ejecución del acto pudiera hacer perder su finalidad legítima al recurso, sino también la de que con la medida cautelar pudiera seguirse perturbación grave de los intereses generales o de tercero, que el Juez o Tribunal ponderará de forma circunstanciada.

La exégesis del precepto conduce a las siguientes conclusiones:

a) La adopción de la medida, exige de modo ineludible, que el recurso pueda perder su finalidad legítima, lo que significa que, de ejecutarse el acto, se crearían situaciones jurídicas irreversibles haciendo ineficaz la sentencia que se dicte e imposibilitando el cumplimiento de la misma en sus propios términos, con merma del principio de identidad, en el caso de estimarse el recurso;

b) aun concurriendo el anterior presupuesto, puede denegarse la medida cautelar, siempre que se aprecie perturbación grave de los intereses generales o de tercero, lo que obliga a efectuar siempre un juicio comparativo de todos los intereses en juego, concediendo especial relevancia, a la hora de decidir, a la mayor perturbación que la medida cause al interés general o al de un tercero afectado por la eficacia del acto impugnado; y,

c) en todo caso el juicio de ponderación que al efecto ha de realizar el Órgano jurisdiccional debe atender a las circunstancias particulares de cada situación, y exige una motivación acorde con el proceso lógico efectuado para justificar la adopción o no de la medida cautelar solicitada.

En este sentido, la doctrina jurisprudencial del Tribunal Supremo destaca que el criterio elegido en el artículo 130 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso-Administrativa para decidir la suspensión cautelar es que la ejecución pueda hacer perder su finalidad legítima al recurso. Y esta exigencia viene a representar lo que tradicionalmente se ha denominado el requisito del periculum in mora; resoluciones que señalan que el mismo opera como criterio decisor de la suspensión cautelar (STS 27 de abril de 2004).

II. En el caso de la resolución recurrida que acuerda la expulsión de mi representado, resulta innegable que la ejecución de una medida tan drástica para la esfera personal del sancionado, como es su expulsión del territorio nacional, conlleva que la cabal efectividad de una posible sentencia estimatoria futura quede ciertamente comprometida.

En este sentido, el Tribunal Supremo viene proclamando con reiteración que la suspensión de la ejecución de determinaciones administrativas de expulsión de extranjeros del territorio nacional o mediante las que se impone el deber de abandonar el mismo resulta procedente cuando la persona afectada tiene arraigo en España por razón de sus intereses familiares, sociales o económicos, por lo que la ejecución de la orden de expulsión habría de producirle unos perjuicios de difícil reparación, que en parte afectarían a su esfera personal de sus derechos, por lo que en tales casos el perjuicio grave al interés general, que se aprecia cuando no concurren las circunstancias especiales de arraigo, debe ceder ante los perjuicios concretos que la inmediata expulsión producirían al extranjero" (autos de 6 de Febrero de 1988, 17 de Septiembre de 1992, 28 de Septiembre de 1993, 11 de Julio de 1995 y sentencias de 15 de enero de 1997, 28 de Septiembre y 25 de Noviembre de 1999 y 23 de febrero de 2000).

Pues bien, concurren en mi representado circunstancias de arraigo familiar, social y económico que han sido acreditadas en el expediente sancionador y con la documental aportada con esta demanda como son las siguientes:

Por tanto, existen motivos suficientes para apreciar que la ejecución de la expulsión puede provocar perjuicios de imposible o difícil reparación de la medida cautelar, habida cuenta que existen auténticas circunstancias subjetivas y personales, así como elementos objetivos, demostrativos del arraigo y vinculación del mi representado en nuestro país, por intereses económicos o familiares, por lo cual solicitamos que se decrete la suspensión de la ejecución de la resolución sancionadora.

Por lo expuesto, SUPLICO AL TRIBUNAL que tenga por solicitada la suspensión de la resolución administrativa objeto de impugnación, y en sus méritos, previos los trámites pertinentes, dicte Auto decretando la suspensión de la resolución de expulsión de mi representado en los términos solicitados y lo notifique a la Administración Pública demandada, para que se abstenga de ejecutar la citada resolución.
