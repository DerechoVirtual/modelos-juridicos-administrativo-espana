---
name: resolucion-pone-fin-procedimiento-administrativo-1327
description: "Redacta el escrito «Resolución que pone fin al procedimiento administrativo» (formulario 1327 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución que pone fin al procedimiento administrativo

> Formulario 1327 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] DESCRIBIR (2 veces)
- [ ] FECHA (8 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AÑO], seguido en este Centro Directivo a»; «…icitó de este órgano que se procediera a»; «…iente con los señalados bajo los números»; «…uncio publicado en el Boletín Oficial de»; «…, por el Servicio de»; «…de funciones y atribuciones realizada en»; «…omún con las especialidades previstas en»; «…rtada, y en los términos establecidos en»; «…, para que se proceda a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 88 de la Ley 39/2015
- artículos 121 y 122 de la Ley 39/2015

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

### Formulario 1327 · Resolución que pone fin al procedimiento administrativo

- Año del modelo: 2004
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 25 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido en este Centro Directivo a [COMPLETAR], con objeto de [DESCRIBIR], resulta:

ANTECEDENTES DE HECHO

Primero.- Mediante escrito de fecha [FECHA], el interesado solicitó de este órgano que se procediera a [COMPLETAR], de conformidad con las previsiones de la reglamentación sustantiva aplicable.

Segundo.- Con fecha [FECHA], por la Sección de [LOCALIDAD], que tramita el expediente, se requirió al solicitante, para que, en un plazo de diez días, procediera a aportar la documentación necesaria con el apercibimiento de que en otro caso se le tendría por desistido de su petición, acordándose el archivo de la misma. La documentación requerida se presentó con fecha [FECHA], por lo que se procedió a continuar el expediente en sus demás trámites.

Tercero.- Mediante acuerdo de [FECHA], al objeto de asegurar la eficacia de la resolución que pudiera recaer, se adoptaron las siguientes medidas provisionales:

Cuarto.- Por acuerdo de [FECHA], se dispuso la acumulación del expediente con los señalados bajo los números [COMPLETAR], ya que con ellos guardaba identidad sustancial o íntima conexión.

Quinto.- Practicadas las pruebas propuestas, y consistentes en [DESCRIBIR], han resultado probados los siguientes hechos:

Sexto.- Se acordó realizar una fase de información pública del expediente, durante treinta días, y así se hizo saber mediante anuncio publicado en el Boletín Oficial de [COMPLETAR], número [NÚMERO] de fecha [FECHA], habiéndose registrado alegaciones a las que se ha dado una respuesta razonada y han sido debidamente consideradas en la resolución de este expediente.

Séptimo.- Con fecha [FECHA], por el Servicio de [COMPLETAR], se elaboró informe técnico en el que se puso de manifiesto lo siguiente:

Octavo.- Una vez ultimada la instrucción del expediente, se dio audiencia y vista del mismo al interesado el cual, haciendo uso de su derecho, ha presentado alegaciones en los siguientes términos:

FUNDAMENTOS JURÍDICOS

Primero.- Este órgano es competente para resolver el expediente de conformidad con la asignación de funciones y atribuciones realizada en [COMPLETAR].

Segundo.- El expediente se ha seguido observando todos los trámites establecidos en el procedimiento administrativo común con las especialidades previstas en [COMPLETAR].

Tercero.- La pretensión suscitada es admisible, en cuanto al fondo, por lo que procede reconocer al interesado el derecho que le asiste para acceder a lo solicitado de conformidad con el proyecto y la documentación complementaria aportada, y en los términos establecidos en [COMPLETAR], disposiciones reguladoras de esta actividad, si bien la autorización concedida queda condicionada por las prescripciones técnicas que se indican en la parte dispositiva de esta resolución.

Vistas las disposiciones citadas, la propuesta de resolución elaborada por [ÓRGANO O PERSONA], el artículo 88 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, y las demás normas de general y pertinente aplicación he tenido a bien dictar la siguiente

RESOLUCIÓN:

Primero.- Se accede a la petición formulada por [ÓRGANO O PERSONA], para que se proceda a [COMPLETAR], en los términos solicitados y con las condiciones que se establecen en al apartado segundo de esta resolución.

Segundo.- Esta autorización (concesión, reconocimiento de situaciones jurídicas individuales o concreta decisión) está sometida, en su actividad, obras e instalaciones, a las condiciones y al plan de vigilancia que se inserta a continuación y cuyo incumplimiento podrá ser causa de revocación de las facultades concedidas:

Tercero.- Notifíquese la presente resolución al interesado con indicación de que, por no poner fin a la vía administrativa, contra la misma se puede interponer recurso de alzada ante [ÓRGANO], en el plazo de un mes, de conformidad con lo establecido en los artículos 121 y 122 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

En [LUGAR], a [FECHA].

Firmado:
