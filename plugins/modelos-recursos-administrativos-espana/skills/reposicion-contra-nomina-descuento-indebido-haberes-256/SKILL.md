---
name: reposicion-contra-nomina-descuento-indebido-haberes-256
description: "Redacta el escrito «Reposición contra nómina por descuento indebido de haberes» (formulario 256 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra nómina por descuento indebido de haberes

> Formulario 0256 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] CALLE
- [ ] CORREO ELECTRÓNICO
- [ ] FECHA (4 veces)
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con DNI [DNI/NIE], funcionario de»; «…E REPOSICIÓN contra la nómina del mes de»; «…e cese del puesto de trabajo de Jefe del»; «…, dictada en fecha [FECHA], por»; «…e en la nómina correspondiente al mes de»; «…ndientes al puesto de trabajo de Jefe de»; «…e adscribe al nuevo puesto de trabajo de»; «…nciones y responsabilidades como Jefe de»; «…n el presente caso, la nómina del mes de»; «…beres practicada en la nómina del mes de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 39 de la Ley 39/2015
- Ley 30/1992

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

### Formulario 0256 · Reposición contra nómina por descuento indebido de haberes

- Año del modelo: 2016
- Revisión 17-11-2026: 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dª [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], funcionario de [COMPLETAR], y con domicilio a efectos de notificaciones en la calle [CALLE] (correo electrónico [CORREO ELECTRÓNICO]), por medio del presente escrito interpone RECURSO DE REPOSICIÓN contra la nómina del mes de [COMPLETAR] por deducción indebida de haberes, de acuerdo con los siguientes

HECHOS Y FUNDAMENTOS DE DERECHO

PRIMERO Que en fecha [FECHA] se le notificó la resolución y formalización de cese del puesto de trabajo de Jefe del [COMPLETAR], dictada en fecha [FECHA], por [COMPLETAR]

SEGUNDO Que en la nómina correspondiente al mes de [COMPLETAR] se han deducido indebidamente los haberes y emolumentos correspondientes al puesto de trabajo de Jefe de [COMPLETAR] que venía ocupando hasta la fecha de notificación del cese, que tuvo lugar el día [FECHA], y no el

TERCERO Que no es hasta el [FECHA] que se le adscribe al nuevo puesto de trabajo de [COMPLETAR]

CUARTO Es perfectamente sabido que si bien el artículo 39 de la Ley 39/2015, de 1 de octubre, establece que los actos de las Administraciones Públicas producirán efectos desde la fecha en que se dicten, añade asimismo como excepción que “salvo que en ellos se disponga otra cosa” y que “la eficacia quedará demorada cuando así lo exija el contenido del acto o esté supeditada a su notificación, publicación o aprobación superior”.

Asimismo, el artículo 40 de la referida Ley 39/2015 indica que “El órgano que dicte las resoluciones y actos administrativos los notificará a los interesados cuyos derechos e intereses sean afectados por aquéllos, en los términos previstos en los artículos siguientes”.

Por tanto, es meridiano que mientras el acto del cese no me fue notificado yo seguí ejerciendo mis funciones y responsabilidades como Jefe de [COMPLETAR], lo cual debe ser reconocido y establecido así, no solo a los efectos económicos sino también a los de carrera administrativa, etc., por la propia Administración.

QUINTO Lo hasta ahora expuesto es conocido por la Administración, que en otros casos similares ha estimado recursos como el presente, y es doctrina judicial pacífica y generalizada. Así, por vía de ejemplo, entre otras muchas la STSJ Cataluña (Sala de lo Contencioso-Administrativo, Sección 4ª), núm. 453/2007 de 11 junio señala:

El art. 57.1e la Ley 30/1992 establece al que "los actos de las Administraciones Públicas sujetos al Derecho Administrativo se presumirán válidos y producirán efectos desde la fecha en que se dicten, salvo que en ellos se disponga otra cosa". Pero es que este mismo precepto en su apartado 2, contempla una excepción, al prever que la eficacia quedará demorada cuando así lo exija el contenido del acto o esté supeditada a su notificación. Y, en este caso, tanto el acuerdo de nombramiento para el nuevo puesto como el cese del anterior exigen la notificación al funcionario interesado. Y esta notificación es una función que debe llevar a cabo la Administración, por lo que mientras no se notifique el acto, el funcionario continúa desempeñando las funciones del puesto para el que fue nombrado, puesto que únicamente le consta al funcionario la aprobación del nuevo Catalogo pero no cual va a ser su nueva situación o destino en esa reorganización. Es pues evidente que mientras no tenga efectividad el cese y mientras se continúen desempeñando las funciones, debe percibir las retribuciones que correspondan al puesto efectivamente desempeñado, por cuanto a partir de ese momento consta la nueva asignación de un puesto de trabajo con las caracteristicas funcionales del mismo.

En efecto, con carácter general, el desempeño efectivo de un puesto de trabajo por un funcionario se produce, una vez aprobado el nombramiento, desde la toma de posesión hasta el cese

En el presente caso, la nómina del mes de [COMPLETAR] deduce indebidamente haberes percibidos legal y correctamente por esta parte, debiendo procederse a su anulación, reintegrando a quien esto suscribe los haberes indebidamente deducidos.

Por todo lo expuesto y en su virtud,

SOLICITO, Que se tenga por presentado este escrito, por interpuesto RECURSO DE REPOSICIÓN contra la deducción de haberes practicada en la nómina del mes de [COMPLETAR], la anule y deje sin efecto en cuanto a dicha deducción de haberes, ordenando la devolución de las cantidades indebidamente deducidas, reconociendo que la efectividad del cese a todos los efectos lo es con fecha de efectos

Lugar, fecha y firma.

MINISTERIO, CONSEJERÍA, ORGANISMO, DEPARTAMENTO O UNIDAD AL QUE SE DIRIGE EL ESCRITO
