---
name: pedir-terminacion-procedimiento-falta-objeto-comunidad-772
description: "Redacta el escrito «Pedir la terminación del procedimiento por falta de objeto (Comunidad Valenciana)» (formulario 772 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir la terminación del procedimiento por falta de objeto (Comunidad Valenciana)

> Formulario 0772 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…, de»

## Elecciones que hay que hacer

- A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0772 · Pedir la terminación del procedimiento por falta de objeto (Comunidad Valenciana)

- Año del modelo: 2009
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); 6 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

[ELEGIR: A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

DON/DOÑA [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y, en el procedimiento ordinario núm. [Nº], de [COMPLETAR], ante el órgano judicial mencionado comparezco y, como mejor en Derecho proceda, digo:Que, en virtud del presente escrito, insto la terminación del procedimiento por falta o pérdida del objeto del mismo, sobre la base de las siguientes,

ALEGACIONES

Primero.- El presente procedimiento se inició y tiene por objeto el presente acto o disposición:dictado bajo la cobertura del Decreto Legislativo 1/2021, de 18 de junio, del Consell de aprobación del texto refundido de la Ley de ordenación del territorio, urbanismo y paisaje.

Segundo.- Con posterioridad,- se ha dictado resolución judicial, en virtud de la cual el citado acto o disposición ha sido objeto de declaración de nulidad firme.- se ha dictado nueva resolución o disposición derogatoria de la anterior, dejando sin efecto alguna la originaria.

Tercero.- Procede, en consecuencia, de conformidad con la jurisprudencia contenida en las SSTS de 24 de marzo y 28 de mayo de 1997 o 29 de abril de 1998, así como en los arts. 25 y ss. y 74 y ss. de la LJCA, declarar terminado el procedimiento por falta de objeto.

Por lo expuesto,

SUPLICO AL JUZGADO O SALA DEL TSJ DE LO CONTENCIOSO-ADMINISTRATIVO DE [LOCALIDAD] que, habiendo por presentado este escrito con los documentos que se acompañan, se sirva admitirlos y tenga por solicitada la terminación del procedimiento por falta de objeto y, tras los trámites legales pertinentes, dicte resolución declarando terminado el procedimiento, sin imposición de las costas, ya que así procede en Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
