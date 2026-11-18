---
name: impugnar-defecto-jurisdiccion-495
description: "Redacta el escrito «Impugnar por defecto de jurisdicción» (formulario 495 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnar por defecto de jurisdicción

> Formulario 0495 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (5 veces)
- [ ] SEDE (4 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AL TRIBUNAL»; «… en los presentes autos registrados como»; «…, asistido por el/la Letrado/a»; «…o (cuya copia se acompaña como documento»; «…ocasionados en el local de su asegurada,»; «…al contencioso-administrativo (Documento»; «…o (cuya copia se acompaña como documento»; «…nial dirigida contra el mismo demandado,»; «…Sección de lo Contencioso-Administrativo»; «…lo registró como procedimiento abreviado»; «…ia igualmente se acompaña como documento»; «…e de tal previsión legal es el que sigue»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 50 LOPJ
- art. 42 LOPJ
- arts. 1902 y 1903 CCiv
- art. 9 LOPJ
- art. 50.3 LOPJ
- art. 50.1 LOPJ
- arts. 9.4 LOPJ
- arts. 2 LPACAP
- art. 9.2 LOPJ

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

### Formulario 0495 · Impugnar por defecto de jurisdicción

- Año del modelo: 2012
- Revisión 17-11-2026: 25 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL TRIBUNAL [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], según tengo ya acreditado en los presentes autos registrados como [COMPLETAR], asistido por el/la Letrado/a [COMPLETAR], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, y al amparo de lo dispuesto en el art. 50 LOPJ, interpongo RECURSO POR DEFECTO DE JURISDICCIÓN ante este Tribunal y para la SALA DE CONFLICTOS DE COMPETENCIA regulada en el art. 42 LOPJ, conforme a los siguientes:

HECHOS

PRIMERO

En fecha [FECHA], mi mandante interpuso demanda de juicio ordinario (cuya copia se acompaña como documento [COMPLETAR]) ante la Sección Civil del Tribunal de Instancia de [SEDE], contra [ACTO O RESOLUCIÓN] UTE, concesionaria de aguas del Ayuntamiento de [LOCALIDAD], en la que se reclamaba el pago de una cantidad en ejercicio de la acción de subrogación o reembolso ex art. 43 LCS, enmarcada en el ámbito de exigencia de responsabilidad civil extracontractual de los arts. 1902 y 1903 CCiv, por los daños ocasionados en el local de su asegurada, [COMPLETAR] S.L., como consecuencia de una inundación producida el día [FECHA] por una subida de presión en las conducciones de agua por unas obras de reparación de la red subterránea de distribución del agua potable, ejecutadas por la demandada.

Por la Sección Civil del Tribunal de Instancia [SEDE], se dictó Auto de fecha [FECHA] en el que se acordó la falta de jurisdicción de dicho Tribunal para conocer el procedimiento por corresponder el asunto al orden jurisdiccional contencioso-administrativo (Documento [COMPLETAR]).

SEGUNDO

A la vista de la anterior resolución esta parte interpuso recurso contencioso-administrativo (cuya copia se acompaña como documento [COMPLETAR]) frente a la desestimación presunta de su reclamación patrimonial dirigida contra el mismo demandado, [COMPLETAR] UTE, ante la Sección de lo Contencioso-Administrativo [COMPLETAR], siendo repartido al Tribunal al que me dirijo, que lo registró como procedimiento abreviado [COMPLETAR], en el que de nuevo reclamaba el pago de la indemnización que había satisfecho a su asegurada, en ejercicio de acción de repetición por daños derivados de culpa por responsabilidad extracontractual de una entidad que, en régimen de concesión administrativa, explota la gestión del servicio municipal de aguas, actuando como un supuesto de los contenidos en los arts. 1902 y 1903 CCiv, al tratarse de los daños producidos por una inundación debida a un incremento de la presión en las conducciones de agua.

Dicho Tribunal al que había correspondido el conocimiento del recurso ha efectuado declaración de incompetencia de jurisdicción por medio de auto, de fecha [FECHA] (cuya copia igualmente se acompaña como documento [COMPLETAR]), con la siguiente parte dispositiva: "Se declara la falta de jurisdicción en el presente recurso contencioso administrativo por considerar corresponde al orden jurisdiccional civil. Contra esta resolución cabe en el plazo de diez días recurso por defecto de jurisdicción conforme al art. 50 LOPJ. El recurso se interpondrá ante este Tribunal, quien, tras oír a las partes personadas remitirá las actuaciones a la Sala de Conflictos".

A los anteriores hechos les son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I

El remedio previsto en el art. 50 LOPJ, llamado "recurso por defecto de jurisdicción" requiere como presupuestos indispensables para su interposición dos requisitos, que se cumplen en este caso.

El primero consiste en que el órgano del orden jurisdiccional indicado en la resolución a la que se refiere el apartado 6 del art. 9 LOPJ declare su falta de jurisdicción. El iter procedimental que se infiere de tal previsión legal es el que sigue [COMPLETAR]: a) En primer lugar debe producirse una declaración de incompetencia por parte de un órgano judicial que indique en su resolución cual es el orden jurisdiccional competente; b) Una vez producida tal declaración, y no antes, el demandante debe acudir al orden al que es remitido; la razón estriba en que solo puede existir conflicto o enfrentamiento de criterios judiciales cuando la resolución del segundo orden se dicta respondiendo a la previa declaración de incompetencia del primero, y conociendo sus argumentos; de ahí que el art. 50.3 LOPJ se refiera al órgano que declaró "en primer lugar" su falta de jurisdicción. Dicho en otros términos, el litigante no puede crear artificialmente el conflicto planteando simultáneamente la misma pretensión ante órganos de dos órdenes jurisdiccionales distintos; para acudir al segundo, debe necesariamente esperar la resolución del primero; c) Finalmente es necesario que el órgano del orden Jurisdiccional al que remitió el que entendió primero, dicte una resolución firme declarando su falta de jurisdicción, que integra el conflicto negativo de competencia.

El segundo requisito que exige el art. 50.1 LOPJ es que la resolución firme que dicte el órgano que entendió en segundo lugar se produzca en un proceso cuyos sujetos y pretensiones fuesen los mismos que los del proceso suscitado ante el orden Jurisdiccional que primero declinó conocer del asunto.

II

El recurso se interpondrá ante el órgano que dictó la última resolución, declinando su jurisdicción, el cual, tras oír a las partes personadas, si las hubiere, remitirá las actuaciones a la Sala de Conflictos prevista en el art. 42 LOPJ.

La Sala reclamará del Tribunal que declaró en primer lugar su falta de jurisdicción que le remita las actuaciones y, oído el Ministerio Fiscal por plazo no superior a diez días, dictará auto dentro de los diez siguientes por medio del cual se encauzará definitivamente la concreta pretensión de la recurrente en el orden jurisdiccional al que corresponda resolverla.

III

Mi mandante sostiene que la competencia corresponde en este caso a la jurisdicción civil y, en particular, al Tribunal de Instancia [SEDE]

En efecto, la vis atractiva del orden contencioso-administrativo para conocer de las reclamaciones que, por responsabilidad patrimonial, se dirijan contra las Administraciones Públicas opera si aquella responsabilidad se atribuye a personas jurídico-públicas, aun cuando cuenten con un seguro de responsabilidad o en la producción del daño hayan concurrido particulares (arts. 9.4 LOPJ y 2.e) LJCA). Sin embargo, cuando la acción se plantea exclusivamente frente a sociedades mercantiles que, pese a gestionar un servicio municipal y estar participadas por capital público, se rigen por el derecho privado y no ejercen potestades públicas, sin que les convenga la calificación de Administraciones Públicas a la luz de lo dispuesto en los arts. 2 LPACAP, y 1.2 LJCA, la competencia corresponde a los tribunales del orden civil que, con arreglo al art. 9.2 LOPJ, conocen, además de las materias que les son propias, todas aquellas que no estén atribuidas a otro orden jurisdiccional.

En definitiva, en la decisión de conflictos similares ha puesto de manifiesto esa Sala —entre otros, en el Auto del Tribunal Supremo, 19 de noviembre de 2.007, rec. 17/2007; el Auto del Tribunal Supremo, 18 de diciembre de 2.009, rec. 5/2009 y el Auto del Tribunal Supremo, 18 de diciembre de 2.009, rec. 14/2009— que la mera condición de concesionaria de un servicio público, en este caso municipal, no atribuye a quien lo sea la condición de administración pública ni la de ejerciente de potestades administrativas.

De ahí que, como en la demanda no se imputa daño alguno a un ente que sea merecedor de aquella calificación, el conocimiento de la pretensión deducida por mi mandante —una aseguradora que, pagada la indemnización a su asegurada, ejercita contra quien señala como causante del daño a la concesionaria demandada— corresponde a los órganos judiciales del orden civil.

En virtud de lo expuesto,

SOLICITO AL TRIBUNAL

que teniendo por presentado este escrito en tiempo y forma, junto con los documentos que al mismo acompañan, se sirva admitirlo, dé traslado a la contraparte y, acuerde tener por interpuesto recurso por defecto de jurisdicción, así como elevar las actuaciones a la Sala Especial de Conflictos de Competencia del Tribunal Supremo, para que reclame las actuaciones AL TRIBUNAL DE INSTANCIA DE [SEDE] y cumplidos los demás trámites legalmente establecidos resuelva cuál de los órganos jurisdiccionales en conflicto es competente, determinando a qué órgano corresponde el conocimiento del asunto.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a
