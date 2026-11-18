---
name: resolucion-anula-actos-trafico-gravemente-contrarios-1818
description: "Redacta el escrito «Resolución que anula actos de tráfico gravemente contrarios al ordenamiento» (formulario 1818 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución que anula actos de tráfico gravemente contrarios al ordenamiento

> Formulario 1818 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…nistración actuante, en el que se afirma»; «…, por la que se»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 106 LPACAP
- artículo 106 de la Ley 39/2015

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

### Formulario 1818 · Resolución que anula actos de tráfico gravemente contrarios al ordenamiento

- Año del modelo: 2004
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de acuerdo mediante el cual el órgano administrativo, facultado por el artículo 106 LPACAP, estima la nulidad del acto administrativo sancionador en materia de tráfico, por infringir este acto el ordenamiento jurídico.

Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], que se sigue a D./Dña. [NOMBRE Y APELLIDOS], en esta [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR], con objeto de que se proceda a la revisión de un acto anulable dictado en ejercicio de las potestades administrativas en materia de circulación de vehículos a motor, tráfico y seguridad vial, resulta:

Que mediante escrito de fecha [FECHA], por el interesado D./Dña. [NOMBRE Y APELLIDOS], se solicitó la revisión de la resolución de fecha [FECHA], dictada por D./Dña. [NOMBRE Y APELLIDOS], al considerar que el citado acto administrativo infringía gravemente normas de rango legal o reglamentario, y así ha resultado acreditado en este expediente, en los siguientes términos:

Que el acto administrativo objeto de este procedimiento revisorio incurre, por tanto, en la infracción grave señalada, lo que ha resultado, además, evidente y sin que haya sido necesario el uso de reglas interpretativas para la obtención de la conclusión citada.

Que instruido el procedimiento, se ha evacuado dictamen del órgano consultivo de la Administración actuante, en el que se afirma [COMPLETAR], aunque no es necesario que este acto revisorio sea conforme con la calificación realizada ya que el dictamen citado no es vinculante para la Administración que ejerce la potestad anulatoria.

Que el procedimiento anulatorio ha seguido todos los trámites legales establecidos: iniciación, trámite de audiencia, dictamen del órgano consultivo, cumpliendo, igualmente, el requisito formal de haberse iniciado el procedimiento antes de transcurridos cuatro años desde que fue dictado al acto cuya revisión se pretende.

Vistos los antecedentes mencionados y el artículo 106 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, he tenido a bien dictar el siguiente

ACUERDO

Primero.- Se procede a la anulación de la resolución de fecha [FECHA], por la que se [COMPLETAR] en ejercicio de las potestades administrativas en materia de circulación de vehículos a motor, tráfico y seguridad vial, ya que dicho acto infringe gravemente normas de rango legal o reglamentario en los términos expuestos.

Segundo.- Notifíquese esta resolución al interesado con indicación de los recursos que procedan de conformidad con lo establecido en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

En [LUGAR], a [FECHA].

Firmado:
