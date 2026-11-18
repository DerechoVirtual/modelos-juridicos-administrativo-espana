---
name: reposicion-peticion-suspension-prueba-tramite-audiencia-122
description: "Redacta el escrito «Reposición con petición de suspensión, prueba y trámite de audiencia» (formulario 122 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición con petición de suspensión, prueba y trámite de audiencia

> Formulario 0122 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…esolución de fecha [FECHA] por la que se»; «…ento en los siguientes MOTIVOS Primero.-»; «…Segundo.-»; «…Segundo.- [COMPLETAR] Tercero.-»; «…por la que»; «… tramitación oportuna se deje sin efecto»; «…os siguientes documentos: Documento nº 1»; «…ón contenida en el acto impugnado de que»; «…estado a disposición de esta parte hasta»; «…Documento nº 2»; «…por causa no imputable al interesado. C)»; «…o, procede cuando menos la suspensión de»

## Elecciones que hay que hacer

- me ha notificado / ha publicado

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Supuestos en que la ejecución pue causar perjuicios de imposible o difícil reparación. / Supuesto en que la impugnación se fundamente en alguna de las causas de nulidad de pleno derecho previstas en el artículo 47.1 de esta Ley. — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTRO SÍ DIGO que conforme se desprende del art. 77 y ss. y art. 118.1 de la LPACAP se solicita la práct…
- SEGUNDO OTROSÍ DIGO que con fundamento en el art. 117 de la Ley 39/2015, de 1 de octubre, del Procedimiento Ad…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 123 y 124 de la Ley 39/2015
- art. 118.1 de la LPACAP
- art. 117 de la Ley 39/2015

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

### Formulario 0122 · Reposición con petición de suspensión, prueba y trámite de audiencia

- Año del modelo: 2017
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 2 párrafos opcionales señalados; 25 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.],

DICE:

Que con fecha [FECHA] se [ELEGIR: me ha notificado / ha publicado] Resolución de fecha [FECHA] por la que se [COMPLETAR]. Entendiendo que dicha resolución es contraria de derecho, con fundamento en los arts. 123 y 124 de la Ley 39/2015 del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante LPACAP), mediante el presente escrito interpongo en tiempo y forma contra la misma RECURSO DE REPOSICIÓN con fundamento en los siguientes

MOTIVOS

Primero.- [COMPLETAR]

Segundo.- [COMPLETAR]

Tercero.- [COMPLETAR]

Por cuanto antecede

SOLICITA

Que se tenga por presentado este escrito y por formulado en tiempo y forma recurso de reposición contra la Resolución de [FECHA] por la que [COMPLETAR] y tras la tramitación oportuna se deje sin efecto [COMPLETAR].

[OPCIONAL — incluir si procede]

PRIMER OTRO SÍ DIGO que conforme se desprende del art. 77 y ss. y art. 118.1 de la LPACAP se solicita la práctica de la siguiente PRUEBA:
A) Adjunto al presente escrito se acompañan los siguientes documentos:

Documento nº 1 [COMPLETAR] La pertinencia del documento viene suscitada

por la afirmación contenida en el acto impugnado de que [COMPLETAR]

porque dicho documento no ha estado a disposición de esta parte hasta [COMPLETAR]

Documento nº 2 [COMPLETAR]

B) Se interesa la práctica de la testifical de D./Dña. [NOMBRE Y APELLIDOS] que no pudo practicarse en el curso del procedimiento administrativo por causa no imputable al interesado.
C) [COMPLETAR]

Por cuanto antecede

SOLICITO que se acuerde la práctica de la prueba que se interesa.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSÍ DIGO que con fundamento en el art. 117 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, se solicita la SUSPENSIÓN DE LA EJECUTIVIDAD DEL ACTO ADMINISTRATIVO IMPUGNADO con fundamento en los siguientes MOTIVOS:

Primero.-

[ELEGIR UNA OPCIÓN Y REDACTARLA: Supuestos en que la ejecución pue causar perjuicios de imposible o difícil reparación. / Supuesto en que la impugnación se fundamente en alguna de las causas de nulidad de pleno derecho previstas en el artículo 47.1 de esta Ley. — el texto de cada opción no venía en el formulario original]

Segundo.- Como quiera que la suspensión del acto no causará perjuicio alguno al interés público no se hace necesaria caución o garantía alguna para enjugar el eventual perjuicio que pueda causarse al interés público. No obstante, se está en disposición de prestar la caución o constituir la garantía que se establezca.

Tercero.- Subsidiariamente y para el caso de que no se acuerde la suspensión de la integridad del acto impugnado, procede cuando menos la suspensión de [COMPLETAR]

Por cuanto antecede

SOLICITA que se acuerde la suspensión del acto administrativo en los términos solicitados.

En [LUGAR], a [FECHA].

Firmado:
