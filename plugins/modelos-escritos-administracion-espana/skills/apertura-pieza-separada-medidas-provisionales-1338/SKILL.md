---
name: apertura-pieza-separada-medidas-provisionales-1338
description: "Redacta el escrito «Apertura de pieza separada de medidas provisionales» (formulario 1338 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apertura de pieza separada de medidas provisionales

> Formulario 1338 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AÑO], seguido en este centro directivo a»; «… las facultades que tengo atribuidas por»; «…recaer en este expediente administrativo»

## Párrafos opcionales (9)

Inclúyelos solo si encajan en los hechos:

- Suspensión temporal de actividades.…
- Prestación de fianzas.…
- Retirada o intervención de bienes productivos o suspensión temporal de servicios por razones de sanidad, higie…
- Embargo preventivo de bienes, rentas y cosas fungibles computables en metálico por aplicación de precios ciert…
- El depósito, retención o inmovilización de cosa mueble.…
- La intervención y depósito de ingresos obtenidos mediante una actividad que se considere ilícita y cuya prohib…
- Consignación o constitución de depósito de las cantidades que se reclamen.…
- La retención de ingresos a cuenta que deban abonar las Administraciones Públicas.…
- Aquellas otras medidas que, para la protección de los derechos de los interesados, prevean expresamente las le…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 56 de la Ley 39/2015

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

### Formulario 1338 · Apertura de pieza separada de medidas provisionales

- Año del modelo: 2004
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 9 párrafos opcionales señalados; 5 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido en este centro directivo a [COMPLETAR], con objeto de [DESCRIBIR], considerando que es necesario, para asegurar la eficacia de la resolución que pudiera recaer en el procedimiento, la adopción de determinadas medidas provisionales, de conformidad con lo dispuesto en el artículo 56 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, y en uso de las facultades que tengo atribuidas por [COMPLETAR], vengo enRESOLVER:Acordar las medidas provisionales que seguidamente se señalan para asegurar la eficacia de la resolución que pudiera recaer en este expediente administrativo [COMPLETAR]:

[OPCIONAL — incluir si procede]

Suspensión temporal de actividades.

[OPCIONAL — incluir si procede]

Prestación de fianzas.

[OPCIONAL — incluir si procede]

Retirada o intervención de bienes productivos o suspensión temporal de servicios por razones de sanidad, higiene o seguridad, el cierre temporal del establecimiento por estas u otras causas previstas en la normativa reguladora aplicable.

[OPCIONAL — incluir si procede]

Embargo preventivo de bienes, rentas y cosas fungibles computables en metálico por aplicación de precios ciertos.

[OPCIONAL — incluir si procede]

El depósito, retención o inmovilización de cosa mueble.

[OPCIONAL — incluir si procede]

La intervención y depósito de ingresos obtenidos mediante una actividad que se considere ilícita y cuya prohibición o cesación se pretenda.

[OPCIONAL — incluir si procede]

Consignación o constitución de depósito de las cantidades que se reclamen.

[OPCIONAL — incluir si procede]

La retención de ingresos a cuenta que deban abonar las Administraciones Públicas.

[OPCIONAL — incluir si procede]

Aquellas otras medidas que, para la protección de los derechos de los interesados, prevean expresamente las leyes, o que se estimen necesarias para asegurar la efectividad de la resolución.

Las medidas provisionales podrán ser alzadas o modificadas durante la tramitación del procedimiento, de oficio o a instancia de parte, en virtud de circunstancias sobrevenidas o que no pudieron ser tenidas en cuenta en el momento de su adopción.

En [LUGAR], a [FECHA].

Firmado:
