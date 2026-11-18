---
name: notificar-multa-coercitiva-procedimiento-administrativo-258
description: "Redacta el escrito «Notificar multa coercitiva en procedimiento administrativo» (formulario 258 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificar multa coercitiva en procedimiento administrativo

> Formulario 0258 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NIF (2 veces)
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] PROVINCIA
- [ ] IMPORTE
- [ ] MARCA/MODELO
- [ ] ÓRGANO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…acto literal se transcribe como Anexo, a»; «…or el incumplimiento de la obligación de»; «…irma ANEXO “RESUELVE: PRIMERO. Imponer a»; «…euros con una periodicidad de»; «…hasta el cumplimiento total de»; «…la obligación establecida en el artículo»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 44 de la Ley 39/2015
- artículos 121 y 122 de la Ley 39/2015
- artículo 88.3 de la Ley 39/2015

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

### Formulario 0258 · Notificar multa coercitiva en procedimiento administrativo

- Año del modelo: 2016
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Habiéndose intentado, sin resultado, la notificación de la resolución, cuyo extracto literal se transcribe como Anexo, a [COMPLETAR] con DNI/CIF [NIF], con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], de la provincia de [PROVINCIA], en relación al procedimiento para imponer multa coercitiva por el incumplimiento de la obligación de [COMPLETAR], se procede a su publicación conforme a lo dispuesto en el artículo 44 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, dándose publicidad a los mismos.

Lugar, fecha, sello y firma

ANEXO

“RESUELVE:

PRIMERO. Imponer a [COMPLETAR] con DNI/CIF n.º [NIF] la multa de [IMPORTE] euros con una periodicidad de [COMPLETAR] hasta el cumplimiento total de [COMPLETAR] a fin de que se cumpla íntegramente la obligación establecida en el artículo [COMPLETAR] del

SEGUNDO. Se adjunta el Modelo [MARCA/MODELO] para que proceda a la liquidación de la multa coercitiva impuesta conforme a lo establecido en el art

Para las liquidaciones notificadas entre los días 1 y 15 de cada mes: Desde la fecha de la notificación hasta el día 5 del mes siguiente, o si fuera festivo, el inmediato hábil posterior.

Para las liquidaciones notificadas entre los días 16 y último de cada mes: Desde la fecha de la notificación hasta el día 20 del mes siguiente, o si fuera festivo, el inmediato hábil posterior.

Si transcurrido el plazo indicado sin haber efectuado el ingreso, se procederá al cobro por la vía de apremio, con el recargo y los intereses de demora correspondientes.

TERCERO. Notifíquese al interesado en cumplimiento de los artículos 40 y ss. de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, a los efectos oportunos.

Contra la presente resolución, que no agota la vía administrativa, podrá interponer recurso de alzada en el plazo de un mes a contar desde el día siguiente al de la notificación de la presente resolución, ante [ÓRGANO], en virtud de lo dispuesto en los artículos 121 y 122 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas. Todo ello sin perjuicio de que los interesados puedan interponer cualquier otro recurso que estimen oportuno, según el artículo 88.3 de la Ley 39/2015.
