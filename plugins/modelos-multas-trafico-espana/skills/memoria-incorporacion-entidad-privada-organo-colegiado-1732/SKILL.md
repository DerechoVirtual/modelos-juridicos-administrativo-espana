---
name: memoria-incorporacion-entidad-privada-organo-colegiado-1732
description: "Redacta el escrito «Memoria para la incorporación de una entidad privada a un órgano colegiado de seguridad vial» (formulario 1732 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Memoria para la incorporación de una entidad privada a un órgano colegiado de seguridad vial

> Formulario 1732 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…da. El Pleno de la Asociación denominada»; «…tra parte, el centro de investigación de»; «…tivos la Asociación tiene suscrito desde»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 317/2003

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

### Formulario 1732 · Memoria para la incorporación de una entidad privada a un órgano colegiado de seguridad vial

- Año del modelo: 2004
- Revisión 17-11-2026: 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito, adjunto a la solicitud de incorporación de una organización privada al Consejo Superior de Tráfico y Seguridad de la Circulación Vial, en el que se detallan características de la organización, actividades llevadas a cabo y toda aquella información que pueda ser de interés para los fines del Consejo y haga de máximo interés la admisión de la organización interesada.

El Pleno de la Asociación denominada [COMPLETAR], en sesión celebrada el día [FECHA], por unanimidad de sus miembros, adoptó el acuerdo de solicitar la incorporación de esta entidad al Consejo Superior de Tráfico y Seguridad de la Circulación Vial, de conformidad con lo previsto en el Real Decreto 317/2003, de 14 de marzo, y designar a D./Dña. [NOMBRE Y APELLIDOS], como representante en el citado órgano colegiado, al tiempo que se le faculta para que realice las gestiones ordenadas a solicitar dicha incorporación dando cuenta de todo ello a la Junta Directiva.

La (por ejemplo Asociación de Víctimas de Accidentes de Tráfico) es una entidad sin ánimo de lucro que tiene como objetivo social el estudio de las ciencias y las técnicas relacionadas con la seguridad vial en sus aspectos legales, médicos, psicológicos, industriales y en cualesquiera otros donde este fenómeno se manifieste.

En esta organización, con personalidad jurídica única, podemos diferenciar, a efectos meramente funcionales, de una parte la sección de [LOCALIDAD], en cuanto órgano que ejecuta las políticas relacionadas con la defensa de los agentes relacionados con el ordenamiento jurídico de la circulación; y, por otra parte, el centro de investigación de [COMPLETAR], que asume las funciones de estudio y docentes en colaboración con centros públicos y privados, por lo que sus miembros son profesores universitarios, magistrados y funcionarios que trabajan o investigan en seguridad vial. Para la consecución de estos objetivos la Asociación tiene suscrito desde [COMPLETAR] un convenio de adscripción a la Universidad de [LOCALIDAD], para el desarrollo y ejecución de todas sus acciones formativas.

Desde esta plataforma universitaria se han organizado cursos de especialización en seguridad vial, de uno de los cuales se adjunta programa descriptivo, con objeto de profundizar en el conocimiento de este sector. Igualmente tiene previsto realizar anualmente un congreso sobre seguridad vial en el transporte por carretera, para lo que cuenta con la colaboración de las Administraciones Autonómica y Estatal en materia de transportes. Igualmente, a partir de nuestra incorporación al Consejo sería del máximo interés suscribir un convenio de colaboración con la Dirección General de Tráfico para colaborar en las acciones formativas de los Planes anuales de Seguridad Vial a nivel nacional.

Por todo ello, la incorporación de nuestra entidad en el Consejo Superior de Tráfico y Seguridad de la Circulación Vial es del máximo interés, ya que nuestro objetivo es trabajar en colaboración con las Administraciones Públicas para conseguir los objetivos diseñados en los Planes de Seguridad Vial aprobados por los órganos competentes en materia de tráfico.

En [LUGAR], a [FECHA].

Firma
