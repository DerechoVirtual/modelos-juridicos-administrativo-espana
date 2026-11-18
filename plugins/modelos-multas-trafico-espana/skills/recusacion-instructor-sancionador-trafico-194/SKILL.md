---
name: recusacion-instructor-sancionador-trafico-194
description: "Redacta el escrito «Recusación del instructor en un sancionador de tráfico» (formulario 194 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recusación del instructor en un sancionador de tráfico

> Formulario 0194 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] ÓRGANO
- [ ] FECHA (3 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…de»

## Elecciones que hay que hacer

- Jefatura de Tráfico / Alcaldía

## Párrafos opcionales (9)

Inclúyelos solo si encajan en los hechos:

- Tener interés personal en el asunto de que se trate o en otro en cuya resolución pudiera influir la de aquél.…
- Ser administrador de sociedad o entidad interesada.…
- Tener cuestión litigiosa pendiente con algún interesado.…
- Tener un vínculo matrimonial o situación de hecho asimilable y el parentesco de consanguinidad dentro del cuar…
- Compartir despacho profesional o estar asociado con cualquiera de los interesados, con los administradores de …
- Tener amistad íntima o enemistad manifiesta con alguna de las personas mencionadas en el apartado anterior.…
- Haber tenido intervención como perito o como testigo en el procedimiento de que se trate.…
- Tener relación de servicio con persona natural o jurídica interesada directamente con el asunto.…
- Haberle prestado en los dos últimos años servicios profesionales de cualquier tipo y en cualquier circunstanci…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 23 de la Ley 40/2015

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

### Formulario 0194 · Recusación del instructor en un sancionador de tráfico

- Año del modelo: 2016
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 9 párrafos opcionales señalados; 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la [ELEGIR: Jefatura de Tráfico / Alcaldía] de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]), ante [ÓRGANO], órgano administrativo competente, comparece y como mejor proceda en derecho

DICE:

Con fecha [FECHA], se le ha comunicado el escrito de fecha [FECHA] en el que se acuerda la iniciación del expediente sancionador número [Nº DE PROCEDIMIENTO]/[AÑO], por una supuesta infracción de la legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial, en que se contiene la designación de D./Dña. [NOMBRE Y APELLIDOS], como instructor del citado procedimiento.

Que el instructor nombrado debió apartarse voluntariamente de cualquier intervención en el procedimiento sancionador ya que en él concurre, y así se acredita mediante la documentación adjunta, y los demás medios de prueba que seguidamente se proponen, la siguiente causa de abstención, según los motivos previstos en el artículo 23 de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público:

[OPCIONAL — incluir si procede]

Tener interés personal en el asunto de que se trate o en otro en cuya resolución pudiera influir la de aquél.

[OPCIONAL — incluir si procede]

Ser administrador de sociedad o entidad interesada.

[OPCIONAL — incluir si procede]

Tener cuestión litigiosa pendiente con algún interesado.

[OPCIONAL — incluir si procede]

Tener un vínculo matrimonial o situación de hecho asimilable y el parentesco de consanguinidad dentro del cuarto grado o de afinidad dentro del segundo, con cualquiera de los interesados, con los administradores de entidades o sociedades interesadas y también con los asesores, representantes legales o mandatarios que intervengan en el procedimiento.

[OPCIONAL — incluir si procede]

Compartir despacho profesional o estar asociado con cualquiera de los interesados, con los administradores de entidades o sociedades interesadas y también con los asesores, representantes legales o mandatarios que intervengan en el procedimiento, para el asesoramiento, la representación o el mandato.

[OPCIONAL — incluir si procede]

Tener amistad íntima o enemistad manifiesta con alguna de las personas mencionadas en el apartado anterior.

[OPCIONAL — incluir si procede]

Haber tenido intervención como perito o como testigo en el procedimiento de que se trate.

[OPCIONAL — incluir si procede]

Tener relación de servicio con persona natural o jurídica interesada directamente con el asunto.

[OPCIONAL — incluir si procede]

Haberle prestado en los dos últimos años servicios profesionales de cualquier tipo y en cualquier circunstancia o lugar.

Que hasta la fecha presente la abstención voluntaria no se ha producido, ni tampoco se ha notificado a esta parte el cambio de instructor,

Que en el documento acusatorio notificado (denuncia o acuerdo de inicio) no se indica el nombre del instructor del expediente, ni tampoco se identifica a la autoridad sancionadora competente para resolver el procedimiento, lo que, además de ser incorrecto en términos legales, supone la imposibilidad de que por esta parte se haga uso del derecho a la recusación en caso de que se diera alguno de los motivos previstos en la legislación vigente, en consecuencia resulta obligado notificar la identificación de estas personas, con suspensión de la tramitación del expediente a efectos que esta parte pueda ejercitar los derechos que le corresponden.

Por lo expuesto,

SOLICITA:

Que se tenga por presentado este escrito, se admita a trámite, y previas las informaciones que se estimen oportunas se acuerde la sustitución por otro del órgano instructor, en el expediente referenciado, paralizándose la tramitación hasta la finalización del incidente.

Que se tenga por presentado este escrito, se admita a trámite, y de conformidad con lo manifestado en el mismo, se notifique a esta parte la identidad del titular del órgano instructor y de la autoridad sancionadora competente para posibilitar el ejercicio de los derechos que asisten a esta parte en orden a garantizar la imparcialidad de la resolución que pudiera recaer, paralizándose la tramitación del procedimiento hasta la finalización de este incidente.

En [LUGAR], a [FECHA].

Firmado:
