---
name: apelacion-materia-asilo-370
description: "Redacta el escrito «Apelación en materia de asilo» (formulario 370 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación en materia de asilo

> Formulario 0370 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (6 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procedimiento Abreviado»; «…referenciado y que ha sido notificada el»; «….— El motivo de dicha denegación fue que»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 11 de la LJCA
- artículo 85.1 LJCA
- artículo 19.1.a) de la LJCA
- artículo 139.1 de la LJCA
- artículos 16 y 18 de la Ley 12/2009
- artículo 119 de la CE
- artículo 85.7 LJCA
- Ley 1/1996

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

### Formulario 0370 · Apelación en materia de asilo

- Año del modelo: 2013
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 6 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Procedimiento Abreviado [COMPLETAR]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados Centrales de lo Contencioso-administrativo son la Sección de lo Contencioso-Administrativo del Tribunal Central de Instancia (LO 1/2025, DT 2.ª; LOPJ art. 95.e).]

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL CENTRAL DE INSTANCIA – PLAZA N.º [Nº]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a, en nombre y representación de Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados, ante el Tribunal comparezco para interponer

RECURSO DE APELACIÓN

Contra la Sentencia dictada por este Tribunal en fecha [FECHA] en el procedimiento referenciado y que ha sido notificada el [COMPLETAR].

Se fundamenta este recurso en base a los siguientes

HECHOS

Primero.— Dña. presentó solicitud de asilo el día [FECHA].

Dicha solicitud se fundamentaba, en resumen, en la persecución que alegaba haber sufrido en su país como consecuencia de su apoyo a un líder religioso local.

La solicitud fue inadmitida a trámite mediante resolución de fecha [FECHA].

Segundo.— El motivo de dicha denegación fue que [COMPLETAR].

Tercero.— Contra dicha resolución se interpuso recurso contencioso-administrativo, el cual fue desestimado mediante sentencia de fecha [FECHA], contra la cual se interpone el presente recurso de apelación.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

Competencia.— La competencia para conocer del recurso corresponde a la Sala de lo Contencioso-Administrativo de la Audiencia Nacional, según lo dispuesto en el artículo 11 de la LJCA, si bien el recurso se presenta ante el Tribunal que dictó la Sentencia apelada, de acuerdo con lo dispuesto en el artículo 85.1 LJCA.

No obstante, para el supuesto de que no se entendiera así, procederá que se remitan las actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en los artículos 7.3 y 85.5 de la ley de esta Jurisdicción.

II

Legitimación y representación.— Está legitimado el recurrente en virtud de lo establecido en el artículo 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

En cuanto a la representación, la misma fue conferida mediante designación del Ilustre Colegio de Procuradores de Madrid.

III

Plazo de interposición del recurso.— Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

IV

Costas.— En lo relativo a la imposición de costas, es de aplicación el artículo 139.1 de la LJCA. Caso de oponerse al presente recurso, debe estimarse que la Administración actúa con mala fe o temeridad, por lo que deberán imponerse las costas del presente proceso a la Administración demandada.

V

En cuanto a los motivos de desacuerdo con la sentencia recurrida, debe comenzarse recordando que el motivo de la demanda nada tenía que ver con la procedencia o no de la inadmisión a trámite, por lo que no se entrará a discutir lo expuesto por la Sentencia al respecto en los Fundamentos de Derecho Tercero y Cuarto.

Lo que se alegaba en la demanda tenía relación con la indefensión sufrida por la recurrente en el momento de su solicitud de asilo, pues se consideraba que en dicha solicitud no se informaba correctamente del derecho a asistencia letrada y a la Justicia Gratuita, recogidos tanto en la Ley 1/1996, de 10 de enero, de Asistencia Jurídica Gratuita, como en los artículos 16 y 18 de la Ley 12/2009, de 30 de octubre, reguladora del derecho de asilo y de la protección subsidiaria.

No se cuestionaba que la solicitante no fuera informada de sus derechos, ya que, como se afirma en la Sentencia recurrida, efectivamente la solicitante de asilo fue informada de los mismos, sino que lo que se cuestiona es la forma en que se informaba del derecho a asistencia letrada y a su posible prestación por abogado del turno de oficio, lo cual se hizo de forma deficiente mediante la fórmula utilizada en el formulario de solicitud de asilo en el que sólo se informaba del derecho del solicitante a “entrar en contacto con un abogado de su elección a los efectos de ser asistido jurídicamente”, sin mención alguna a la posibilidad de ser asistido por letrado del turno de oficio.

Y respecto a esta objeción se considera que no debe ser suficiente, en contra de lo expuesto en la Sentencia recurrida el hecho de que la recurrente, con posterioridad a la inadmisión a trámite haya presentado los escritos y recursos oportunos, y haya solicitado para ello ser asistida por letrado del turno de oficio, pues ello no subsana la indefensión sufrida en el momento de la solicitud.

Como tampoco lo hace el hecho de que la recurrente hubiera solicitado anteriormente asilo en España, pues no consta que en dicho momento hubiera sido correctamente informada de sus derechos.

Es de aplicación al respecto lo establecido por el Tribunal Supremo, en su Sentencia de 31 de Octubre de 2006 (Sala de lo Contencioso-Administrativo, Sección Quinta, recurso de casación 4979/03), en especial cuando afirmaba que:

“Así las cosas, hemos de concluir que la deficiente información de derechos que se hizo al Interesado, y más concretamente la falta de información sobre la posibilidad de recabar la asistencia letrada de un Abogado de oficio (sobre lo cual el Impreso que la Administración utiliza es claramente defectuoso), derivó en una situación real y efectiva de Indefensión para él, más aún habida cuenta de su condición de extranjero desconocedor del idioma y el Derecho español”.

El mismo criterio se recoge en las Sentencias de la Sección Octava de 28 de noviembre de 2005 y 26 de mayo de 2006 y en la Sentencia de la Audiencia Nacional de siete de Marzo de 2007 (Sala de lo Contencioso-Administrativo, Sección Primera, n.º [Nº] de recurso 290/2006), afirmando esta última en un caso idéntico al actual que:

Del tenor literal de la indicada diligencia de información de derechos, necesariamente se ha de concluir que existe un defecto de información de los derechos al Sr. Sufo, dado que de la repetida diligencia no se desprende una información exacta sobre lo que constituye el contenido de su derecho reconocido en el artículo 119 de la CE que garantiza la gratuidad de la justicia para quienes acrediten insuficiencia de recursos par litigar y que, evidentemente, incluye una actividad prestacional encaminada a proveer los medios necesarios para hacer que este derecho sea real y efectivo cuando quienes deseen ejercerlo carezcan de medios económicos.

Sin que ello quede paliado, contrariamente a lo que mantiene el Juez a quo en la sentencia de instancia, porque el solicitante de asilo fuera informado de sus derechos en forma comprensible para el mismo, “al haber concurrido traductor, de lo que sigue que quedó enterado de que podía beneficiarse de la asistencia de letrado”, pues precisamente dicha información, a pesar de haber sido traducida, redunda en la posible confusión que puede causarse al solicitante de asilo en cuanto que lo que le asiste es el derecho a la asistencia de un abogado elegido por él, más no de un abogado de oficio en caso de insuficiciencia de recursos económicos del mismo.

Al afectar la indefensión sufrida a un derecho susceptible de amparo constitucional, debe considerarse causa de nulidad de pleno derecho de la resolución recurrida, por lo que procedería retrotraer las actuaciones al momento de solicitud de asilo, para posteriormente, y una vez la solicitante sea debidamente informada de sus derechos, estudiar los posibles motivos de inadmisión a trámite.

En su virtud AL TRIBUNAL PARA ANTE LA AUDIENCIA NACIONAL SUPLICO que teniendo por presentado este escrito, tenga por formalizado recurso de apelación contra la Sentencia del Tribunal Central de Instancia (Sección de lo Contencioso-Administrativo) de fecha [FECHA] y eleve los autos y el expediente administrativo, en unión de los escritos presentados, a la Sala de lo Contencioso-administrativo competente para que Se anule la resolución recurrida, retrotrayéndose las actuaciones administrativas a fin de que se reinicie el expediente de solicitud de asilo con la debida observancia del derecho de asistencia letrada.

Por ser Justicia que pido en [LUGAR], a [FECHA].

OTROSÍ DIGO que, según lo establecido por el artículo 85.7 LJCA las partes, en los escritos de interposición y de oposición al recurso, podrán solicitar que se celebre vista, que se presenten conclusiones o que el pleito sea declarado concluso, sin más trámites, para sentencia.

En su virtud, AL TRIBUNAL PARA ANTE EL TRIBUNAL SUPERIOR DE JUSTICIA SUPLICO que el pleito sea declarado concluso, sin más trámites, para sentencia.

Por ser Justicia que reitero en lugar y fecha ut supra.

Procurador de los Tribunales Letrado
