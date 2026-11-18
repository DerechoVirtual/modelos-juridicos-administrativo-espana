---
name: inadmitir-solicitud-nulidad-disposiciones-actos-128
description: "Redacta el escrito «Inadmitir la solicitud de nulidad de disposiciones y actos» (formulario 128 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inadmitir la solicitud de nulidad de disposiciones y actos

> Formulario 0128 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (4 veces)
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ministración dictó resolución por la que»; «…ión de oficio en los motivos siguientes:»; «…creditan las consideraciones siguientes:»

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

### Formulario 0128 · Inadmitir la solicitud de nulidad de disposiciones y actos

- Año del modelo: 2017
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente número:

Interesados:

Procedimiento:

RESOLUCIÓN:

VISTA la solicitud formulada por D./Dña. [NOMBRE Y APELLIDOS], por la que insta que se declare nulo de pleno Derecho el acto dictado, en fecha [FECHA], sobre [DESCRIBIR] y de conformidad con los siguientes

ANTECEDENTES DE HECHO

PRIMERO.- Con fecha [FECHA], esta Administración dictó resolución por la que [COMPLETAR]. Dicha resolución definitiva en vía administrativa fue notificada en forma a los interesados.

SEGUNDO.- Con fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] presentó escrito ante esta Administración por el que solicitaba la declaración de nulidad de la citada resolución.

TERCERO.- El Servicio Jurídico de esta Administración ha informado favorablemente la inadmisión a trámite de la referida solicitud de nulidad.

FUNDAMENTOS DE DERECHO

PRIMERO.- En síntesis, el interesado funda su petición de nulidad para la revisión de oficio en los motivos siguientes:

[COMPLETAR]

A este respecto, será de subrayar que, conforme dispone el artículo 106.3 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas: "El órgano competente para la revisión de oficio podrá acordar motivadamente la inadmisión a trámite de las solicitudes formuladas por los interesados, sin necesidad de recabar dictamen del Consejo de Estado u órgano consultivo de la Comunidad Autónoma, cuando las mismas no se basen en alguna de las causas de nulidad del artículo 47.1 o carezcan manifiestamente de fundamento, así como en el supuesto de que se hubieran desestimado en cuanto al fondo otras solicitudes sustancialmente iguales".

La solicitud de nulidad formulada contra la precipitada resolución de esta Administración, a tenor de lo dispuesto en el artículo 106 en relación con el 47.1 de la citada Ley del Procedimiento Administrativo, no puede ser admitida, habida cuenta que las actuaciones relatadas no constituye por sí mismas infracción del ordenamiento jurídico insubsanable, ni pueden encuadrarse dentro de las causas de nulidad de pleno Derecho determinadas por la Ley, como lo acreditan las consideraciones siguientes: [COMPLETAR]. Por lo que al no concurrir ninguno de los motivos en que se funda la solicitud procede, sin más trámites, declararla inadmisible y archivar la petición de nulidad.

Además, importa tener en cuenta que, según establece el artículo 110 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, las facultades de revisión de los actos en vía administrativa no pueden ser ejercitadas cuando por prescripción de acciones, por el tiempo transcurrido o por otras circunstancias, su ejercicio resulte contrario a la equidad, a la buena fe, al derecho de los particulares o a las leyes. Por lo que, de acuerdo con reiteradas Sentencias del Tribunal Supremo, como las de 26 de marzo de 1998, de 29 de junio de 2000 y de 26 de abril de 2001, entre otras, la facultad para revisar de oficio los actos y disposiciones de la Administración Pública está limitada en virtud del principio de seguridad jurídica y de respeto a los derechos adquiridos.

SEGUNDO.- Este órgano administrativo es competente para la adopción de la presente resolución conforme a lo establecido en la legislación vigente.

Vistos los preceptos legales citados y demás de pertinente aplicación

RESUELVO

INADMITIR A TRÁMITE, por infundada, la solicitud de revisión de oficio formulada por D./Dña. [NOMBRE Y APELLIDOS], para la declaración de nulidad de pleno Derecho del referido acto o acuerdo adoptado por esta Administración.

Contra la presente resolución, que pone fin a la vía administrativa, se podrá interponer recurso potestativo de reposición ante este mismo órgano, en el plazo de UN MES, a contar desde el día siguiente al de la recepción de su notificación, o interponer recurso contencioso-administrativo, ante [ÓRGANO], en el plazo de DOS MESES, contados desde el día siguiente a la notificación o publicación de la misma, sin perjuicio de que los interesados puedan ejercitar cualquier otro recurso que estimen procedente.

En [LUGAR], a [FECHA].

Firma del titular del órgano administrativo competente
