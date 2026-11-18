---
name: pedir-certificado-acto-presunto-doble-silencio-330
description: "Redacta el escrito «Pedir certificado de acto presunto por doble silencio» (formulario 330 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir certificado de acto presunto por doble silencio

> Formulario 0330 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (6 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] ÓRGANO (2 veces)
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…o Territorial de al número de expediente»; «…solicité al»; «…autorización administrativa de»; «… (6 meses de conformidad con el artículo»; «…ncio, que de conformidad con el artículo»; «…miento de autorización administrativa de»; «…ialmente ante el Servicio Territorial de»; «…al número de expediente»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 122.2 de la Ley 39/2015
- artículo 24.4 de la LPACAP

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

### Formulario 0330 · Pedir certificado de acto presunto por doble silencio

- Año del modelo: 2013
- Revisión 17-11-2026: 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la Delegación Territorial de la Junta de Castilla y León en Zamora

D./Dña. [NOMBRE Y APELLIDOS] mayor de edad, provisto de DNI [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

como interesado/a en el procedimiento de solicitud de autorización administrativa en el procedimiento seguido en el Servicio Territorial de al número de expediente [COMPLETAR], y como interesado/a en el procedimiento de recurso de alzada interpuesto frente a la desestimación por silencio del primero de los procedimientos citados, seguido en la Delegación Territorial a que va dirigido este escrito al número de expediente

DIGO

PRIMERO.- Con fecha [FECHA] solicité al [COMPLETAR] autorización administrativa de [COMPLETAR], teniendo entrada la solicitud en el registro de dicho Servicio Territorial en la fecha indicada (se adjunta copia del escrito de solicitud de autorización como documento nº [Nº DE DOCUMENTO]).

SEGUNDO.- Transcurrido el plazo máximo de resolución del procedimiento iniciado a instancia de quien suscribe (6 meses de conformidad con el artículo [COMPLETAR]), con fecha [FECHA], considerando producidos los efectos del silencio, que de conformidad con el artículo [COMPLETAR] de la norma reguladora son de sentido negativo, interpuse recurso de alzada frente a dicha desestimación presunta ante [ÓRGANO]. Se adjunta copia del escrito de interposición de recurso como documento nº [Nº DE DOCUMENTO].

TERCERO

Transcurridos tres meses desde la interposición del recurso en fecha [FECHA], éste no ha sido resuelto.

CONSIDERANDO

Que de acuerdo con lo establecido en el art. 122.2 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP), el plazo máximo para dictar y notificar la resolución del recurso de alzada será de tres meses. Por lo tanto, interpuesto el recurso de alzada en fecha [FECHA], se entiende producido el silencio administrativo en fecha [FECHA].

Y VISTOS

El art. 24.1 párrafo segundo in fine de la LPACAP que establece que: «cuando el recurso de alzada se haya interpuesto contra la desestimación por silencio administrativo de una solicitud por el transcurso del plazo, se entenderá estimado el mismo si, llegado el plazo de resolución, el órgano administrativo competente no dictase resolución expresa, siempre que no se refiera a las materias enumeradas en el párrafo anterior de este apartado».

Y el artículo 24.4 de la LPACAP que establece que: «Los actos administrativos producidos por silencio administrativo se podrán hacer valer tanto ante la Administración como ante cualquier persona física o jurídica, pública o privada. Los mismos producen efectos desde el vencimiento del plazo máximo en el que debe dictarse y notificarse la resolución expresa sin que la misma se haya expedido, y su existencia puede ser acreditada por cualquier medio de prueba admitido en Derecho, incluido el certificado acreditativo del silencio producido. Este certificado se expedirá de oficio por el órgano competente para resolver en el plazo de quince días desde que expire el plazo máximo para resolver el procedimiento. Sin perjuicio de lo anterior, el interesado podrá pedirlo en cualquier momento, computándose el plazo indicado anteriormente desde el día siguiente a aquél en que la petición tuviese entrada en el registro electrónico de la Administración u Organismo competente para resolver.».

SOLICITO

Que sea emitida certificación de acto presunto en sentido estimatorio en el procedimiento de autorización administrativa de [COMPLETAR], seguido inicialmente ante el Servicio Territorial de [COMPLETAR] al número de expediente [COMPLETAR] y que fue recurrido en alzada frente a su desestimación presunta ante [ÓRGANO] seguido al número de expediente

En [LUGAR], a [FECHA].

Firmado:
