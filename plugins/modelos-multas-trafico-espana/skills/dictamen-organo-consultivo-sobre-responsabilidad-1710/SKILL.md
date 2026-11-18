---
name: dictamen-organo-consultivo-sobre-responsabilidad-1710
description: "Redacta el escrito «Dictamen del órgano consultivo sobre responsabilidad patrimonial por daños de circulación» (formulario 1710 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Dictamen del órgano consultivo sobre responsabilidad patrimonial por daños de circulación

> Formulario 1710 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…los servicios públicos. ANTECEDENTES Por»; «…pediente en virtud de las previsiones de»; «…ciones Públicas (en lo sucesivo, LPACAP)»; «…pediente: Es cuanto tiene que informar a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 81 de la Ley 39/2015
- artículo 106 de la Constitución
- artículo 32.7 LRJSP
- Real Decreto Legislativo 6/2015
- Ley 40/2015

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

### Formulario 1710 · Dictamen del órgano consultivo sobre responsabilidad patrimonial por daños de circulación

- Año del modelo: 2004
- Revisión 17-11-2026: 5 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de Dictamen del órgano consultivo de la Administración actuante, en el que se pronuncia sobre la existencia o no de la relación de causalidad entre el funcionamiento del servicio público y la lesión producida, así como sobre el daño causado, la cuantía y modo de la indemnización, dentro del procedimiento de responsabilidad de las Administraciones Públicas, derivada de accidente de circulación consecuencia del funcionamiento de los servicios públicos.

ANTECEDENTES

Por [COMPLETAR], se ha solicitado el dictamen a que se refiere el artículo 81 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP), que resulta preceptivo para este expediente en virtud de las previsiones de [COMPLETAR], para la intervención de este órgano consultivo de la Administración actuante.

Examinado el expediente remitido, con todo lo actuado y la propuesta de resolución o la propuesta de acuerdo por la que se podría terminar convencionalmente el procedimiento, resultan acreditados los siguientes antecedentes de hecho:

CONSIDERACIONES JURÍDICAS

A los hechos probados son de aplicación los siguientes fundamentos jurídicos sobre la competencia para instruir y resolver el expediente, el procedimiento seguido, y los contenidos que ha de reunir la resolución (o el acuerdo indemnizatorio) que se adopte:

A la Administración Pública corresponde, de conformidad con lo establecido en el Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, la competencia para la realización de los trabajos de señalización y mantenimiento de la vía objeto de este expediente, teniendo la consideración de mal funcionamiento de los servicios públicos la no realización de las tareas de señalización y mantenimiento necesarias para que las condiciones del tráfico rodado de desarrollen con normalidad.

El procedimiento de exigencia de responsabilidad patrimonial de la Administración del Estado estuvo regulado por el Decreto de 26 de abril de 1957, en su capítulo II del Título IV, "Indemnización por otros daños", que desarrollaba la Ley de 16 de diciembre de 1954, de Expropiación Forzosa, donde se establece en nuestro Derecho el principio de responsabilidad patrimonial, extracontractual, de la Administración del Estado.

La regulación posterior que efectuó la Ley de Régimen Jurídico de la Administración del Estado de 1992 de la responsabilidad patrimonial de la Administración y de sus autoridades y funcionarios no supuso la modificación de las normas procedimentales del Reglamento de desarrollo de la Ley de Expropiación Forzosa de 1954 que se ha venido aplicando hasta esta fecha.

El artículo 106 de la Constitución consagra definitivamente el principio de la responsabilidad patrimonial extracontractual de las Administraciones Públicas por las lesiones que sufran los particulares en cualquiera de sus bienes y derechos, siempre que la lesión sea consecuencia del funcionamiento de los servicios públicos, precepto constitucional que desarrolla la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público (en lo sucesivo, LRJSP) en el Capítulo IV de su Título Preliminar y procedimentalmente la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP) [COMPLETAR].

En nuestro ordenamiento estos expedientes se fundamentan en el principio de exigencia directa de responsabilidad a las Administraciones públicas, que responden en todo caso de los daños causados por ellas mismas o por sus agentes y por la sumisión al procedimiento de la responsabilidad derivada de la actividad de las Administraciones públicas tanto en relaciones de Derecho público como privado.

La declaración de que las resoluciones de los procedimientos ponen fin a la vía administrativa y, por tanto, la improcedencia del recurso administrativo ordinario, quedando expedita la vía jurisdiccional contencioso-administrativa, es, la única procedente en materia de responsabilidad patrimonial de las Administraciones públicas, tanto en relaciones de Derecho público como privado.

Pero sobre todo, la LPACAP prevé el establecimiento de un procedimiento simplificado de reconocimiento de la responsabilidad patrimonial de las Administraciones Públicas, cuando se den los supuestos de inequívoca relación de causalidad ante la lesión y el funcionamiento del servicio público, que la valoración del daño y cálculo de la cuantía de la indemnización sean, asimismo, inequívocos.

Además de estas específicas indeterminaciones legales, la LPACAP tiene otros preceptos en materia de procedimiento administrativo como son la terminación convencional y el carácter no suspensivo de los informes no determinantes de los procedimientos. Obviamente, el acuerdo de terminación convencional no puede incluir, como tal acuerdo con un particular, ningún tipo de transacción sobre la existencia o no de relación de causalidad o de reconocimiento pactado de la responsabilidad de las Administraciones Públicas, sino limitarse a la determinación de la cuantía y el modo.

La LRJSP recoge en la regulación sustantiva de la responsabilidad patrimonial extracontractual de las Administraciones Públicas los elementos tradicionales de nuestro Derecho como son la exclusión de los supuestos de fuerza mayor y la no existencia de responsabilidad cuando exista un deber jurídico de soportar el daño causado y respecto al reconocimiento de esa responsabilidad, la concurrencia inequívoca de los presupuestos de imputación a la Administración, relación de causa a efecto entre el hecho causante y el daño producido, lesión resarcible y efectividad y cuantía del daño, también indiscutible. Por fin, la remisión del artículo 32.7 LRJSP a la Ley Orgánica del Poder Judicial en lo relativo a la responsabilidad patrimonial del Estado por el funcionamiento de la Administración de Justicia, hace conveniente incluir la emisión del informe del Consejo General del Poder Judicial en los procedimientos que se tramiten en los supuestos de funcionamiento anormal de la Administración de Justicia.

Respecto al fondo del asunto la relación de causalidad entre el accidente circulatorio producido y el funcionamiento de los servicios públicos es evidente, por cuanto:

CONCLUSIONES Y PROPUESTAS

En conclusión, salvo mejor criterio, por este órgano consultivo se ha llegado a las siguientes conclusiones sobre la forma y contenido del acto o acuerdo indemnizatorio, y en particular, sobre la existencia o no de la relación de causalidad entre el funcionamiento del servicio público y la lesión producida, la valoración del daño causado y la cuantía y el modo de la indemnización de conformidad con los criterios previstos en la legislación sobre procedimiento administrativo común y aplicable al expediente:

Es cuanto tiene que informar a [COMPLETAR], con carácter preceptivo, este órgano consultivo dentro del plazo conferido al efecto por la legislación aplicable, para que, sin carácter vinculante, sea tenido en cuenta por el órgano competente para la terminación del expediente referenciado.

En [LUGAR], a [FECHA].

Firma:
