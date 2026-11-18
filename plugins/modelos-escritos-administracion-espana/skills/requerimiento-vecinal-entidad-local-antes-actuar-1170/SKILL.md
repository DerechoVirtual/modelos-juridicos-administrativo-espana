---
name: requerimiento-vecinal-entidad-local-antes-actuar-1170
description: "Redacta el escrito «Requerimiento vecinal a la entidad local antes de actuar por sustitución (Navarra)» (formulario 1170 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Requerimiento vecinal a la entidad local antes de actuar por sustitución (Navarra)

> Formulario 1170 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…, vecino de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 68 de la Ley 7/1985
- art. 220 del Real Decreto 2568/1986

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

### Formulario 1170 · Requerimiento vecinal a la entidad local antes de actuar por sustitución (Navarra)

- Año del modelo: 2008
- Revisión 17-11-2026: 4 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

REQUERIMIENTO

D./Dña. [NOMBRE Y APELLIDOS], vecino de [COMPLETAR], actuando en propio nombre y en su cualidad de tal, hallándose en la plenitud de ejercicio de sus derechos civiles y políticos,

EXPONE

El art. 110 de la Ley Foral 6/1990, de 2 de julio, de la Administración Local de Navarra, dispone:

"1. Las entidades locales de Navarra deben velar por la conservación, defensa, recuperación y mejora de los bienes y derechos de su patrimonio, y tienen la obligación de ejercer las acciones necesarias para la defensa de los mismos.
2. Cualquier vecino que se halle en pleno goce de sus derechos civiles y políticos podrá requerir a las entidades locales el ejercicio de las acciones necesarias para la defensa de sus bienes y derechos. Este requerimiento, del que se dará conocimiento a quienes pudiesen resultar afectados por las correspondientes acciones, suspenderá el plazo para el ejercicio de las mismas por un término de treinta días hábiles.

Transcurrido el plazo mencionado sin que la entidad local acuerde el ejercicio de las acciones solicitadas, los vecinos pueden ejercitar dicha acción en nombre e interés de la misma, a cuyo efecto se les facilitará por ésta los antecedentes, documentación y elementos de prueba necesarios y que al efecto soliciten por escrito dirigido al Presidente de la corporación".

Asimismo, su art. 111 de la Ley Foral 6/1990, de 2 de julio, establece que las entidades locales de Navarra podrán recuperar por sí mismas y en cualquier momento la posesión indebidamente perdida de los bienes y derechos de dominio público o comunal que les pertenezcan, previo dictamen del secretario, de la Asesoría jurídica, o en su caso, de un letrado, y con audiencia del interesado. Y dice: "Promoverán asimismo el ejercicio de las acciones civiles que sean necesarias para la recuperación y defensa de dichos bienes".

Por lo expuesto, y por estimar que a esa entidad local le corresponde la obligación del ejercicio de acciones de defensa de sus bienes o derechos consistentes en [DESCRIBIR], viene a formular, al amparo de los artículos relatados de la Ley Foral 6/1990, de Administración Local de Navarra, y conforme también a los apartados 2, 3 y 4 del art. 68 de la Ley 7/1985, de 2 de abril, de Bases de Régimen Local, y el art. 220 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de los Entes Locales,

EXPRESO REQUERIMIENTO

previo al ejercicio de acciones judiciales por sustitución en caso de su desatención, para que por los órganos locales competentes se adopten, en término improrrogable de treinta días y previo traslado a los potenciales afectados, las resoluciones oportunas en orden a iniciar y proseguir en legal forma las acciones necesarias para la defensa de aquellos bienes o derechos de titularidad local que más arriba se expresan.

Asimismo anuncia que, en efecto, en caso de no iniciarse las referidas acciones por los servicios administrativos locales, procederá a ejercerlas por sí, a nombre de la entidad, y que si dichas acciones se vieran favorecidas por el éxito solicitará judicialmente en reembolso de cuantos gastos, costas, daños y perjuicios le hubiera causado la omisión municipal.

En [LUGAR], a [FECHA].

Firmado:
