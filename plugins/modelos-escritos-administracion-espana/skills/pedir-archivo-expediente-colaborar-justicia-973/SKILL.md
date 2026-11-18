---
name: pedir-archivo-expediente-colaborar-justicia-973
description: "Redacta el escrito «Pedir el archivo del expediente por colaborar con la justicia» (formulario 973 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir el archivo del expediente por colaborar con la justicia

> Formulario 0973 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] FECHA (3 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… suscribe por una supuesta infracción de»; «…Extranjeros y su Integración Social. Que»; «…eros en España y su Integración Social y»; «…En concreto este interesado ha realizado»; «… ha sido remitido el aludido informe por»

## Elecciones que hay que hacer

- Delegado / Subdelegado

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66.1 Ley 39/2015
- art. 135 del Real Decreto 557/2011
- Ley Orgánica 4/2000

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

### Formulario 0973 · Pedir el archivo del expediente por colaborar con la justicia

- Año del modelo: 2008
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

AL INSTRUCTOR DEL PROCEDIMIENTO

AL DELEGADO

AL SUBDELEGADO DEL GOBIERNO

PROCEDIMIENTO SANCIONADOR ORDINARIO EN MATERIA DE EXTRANJERÍA Nº [Nº]

INTERESADO

D./Dña. [NOMBRE Y APELLIDOS], con NIE nº [DNI/NIE], actuando en nombre propio, con domicilio en [LOCALIDAD], el cual señalo a efectos de notificaciones conforme al artículo 66.1 Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), a través del presente escrito comparece y como mejor proceda en Derecho dice:

Que con fecha [FECHA] le fue notificado acuerdo de [FECHA], dictado por [ÓRGANO O PERSONA] por el que se resolvía la iniciación de expediente sancionador contra el que suscribe por una supuesta infracción de [COMPLETAR] contra la Ley Orgánica 4/2000, Reguladora de los Derechos y Libertades de los Extranjeros y su Integración Social.

Que [COMPLETAR].

Que sin embargo, procede la declaración de exención de responsabilidad y el archivo de este expediente por darse en el presente caso las circunstancias de colaboración con la justicia del sujeto a expediente previstas en el art. 135 del Real Decreto 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social y [COMPLETAR] de las establecidas en el art. 59 de esta última Ley Orgánica 4/2000 .

En concreto este interesado ha realizado [COMPLETAR].

Que según es sabido por ese instructor, el referido art. 135 del Real Decreto 557/2011, de 20 de abril dispone que la autoridad con la que esté colaborando un extranjero que se encuentre irregularmente en España y sea víctima, perjudicado o testigo de un acto de tráfico ilícito de seres humanos, inmigración ilegal, explotación laboral o de tráfico ilícito de mano de obra o de explotación en la prostitución abusando de su situación de necesidad, remitirá informe sobre dicha colaboración al órgano administrativo competente para la instrucción del expediente sancionador, a los efectos de que pueda proponer al Delegado o Subdelegado competente la exención de responsabilidad de éste.

En el presente caso aún no ha sido remitido el aludido informe por [COMPLETAR] por lo que

Por lo expuesto,

SOLICITA

Del instructor que recabe dicho informe y con él proponga al [ELEGIR: Delegado / Subdelegado] del Gobierno la exención de responsabilidad del firmante del presente escrito y el archivo del expediente.

En [LUGAR], a [FECHA].

Fdo: D./D.ª [NOMBRE Y APELLIDOS]
