---
name: pedir-medidas-provisionales-antes-iniciar-procedimiento-569
description: "Redacta el escrito «Pedir medidas provisionales antes de iniciar el procedimiento» (formulario 569 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir medidas provisionales antes de iniciar el procedimiento

> Formulario 0569 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…Al Sr. Delegado del Gobierno en»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 36.16 de la Ley Orgánica 4/2015
- art. 56 de la Ley 39/2015
- art. 36.16 de la Ley Orgánica 4/2015
- art. 49.1 a) de la Ley Orgánica 4/2015

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

### Formulario 0569 · Pedir medidas provisionales antes de iniciar el procedimiento

- Año del modelo: 2011
- Revisión 17-11-2026: 3 llamadas a nota sin texto retiradas; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Sr. Delegado del Gobierno en [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS] con DNI número [DNI/NIE] y

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

actuando en su propio nombre y derecho, ante la Delegación del Gobierno de [LOCALIDAD], órgano competente para conocer de este procedimiento, comparece y como mejor proceda en Derecho

DICE:

Que en virtud de este escrito solicita la adopción de medidas provisionales por parte de esa Delegación del Gobierno, por los hechos que se exponen y con base a los hechos y fundamentos de derecho siguientes:

PRIMERO.- Que en el número 16 de la calle [CALLE], contiguo a la vivienda de esta interesada existe un local destinado a discoteca con nombre "En un lugar de la Marcha", abierto hace apenas dos meses, donde presumiblemente esta parte sospecha que se trafica con drogas tóxicas, estupefacientes y sustancias psicotrópicas, debiendo constar en esa Administración entre los antecedentes de la citada entidad las sucesivas denuncias de otros vecinos de este Barrio sobre los altercados y agresiones inferidas por los clientes y dueños de ese local.

Así mismo, esta interesada quiere hacer constar la existencia de un Centro Público de Educación Primaria en las proximidades, en concreto en los números 3-5 de la misma calle. Teniendo en cuenta la infracción reiterada de los horarios exhibidos a la entrada del citado establecimiento hasta el punto de coincidir en algunas ocasiones con la entrada/salida de alumnos de ese Centro, creemos que es motivo suficiente para formular denuncia ante esa autoridad y solicitar la adopción de medidas cautelares por entendernos interesados en el procedimiento que pueda incoarse.

SEGUNDO.- El artículo 36.16 de la Ley Orgánica 4/2015, de 30 de marzo, sobre Protección de la Seguridad Ciudadana, sanciona como infracción grave "el consumo o la tenencia ilícitos de drogas tóxicas, estupefacientes o sustancias psicotrópicas, aunque no estuvieran destinadas al tráfico, en lugares, vías, establecimientos públicos o transportes colectivos, así como el abandono de los instrumentos u otros efectos empleados para ello en los citados lugares".

Tercero.- El art. 47 y 49 de la misma Ley prevé la adopción de las medidas cautelares imprescindibles para el normal desarrollo del procedimiento, evitar la comisión de nuevas infracciones o asegurar el cumplimiento de la sanción que pudiera imponerse.

Sin prejuzgar ni vincular la competencia de esa Administración en el inicio de actuaciones sancionadoras, esta interesada solicita la investigación de los hechos denunciados y en su caso la adopción de medidas provisionales y cautelares.

Ese mismo precepto autoriza a que los agentes de la autoridad puedan ordenar, con anterioridad a la apertura de un expediente sancionador, el depósito en lugar seguro de los instrumentos o efectos utilizados para la comisión de las infracciones y, en particular, de las drogas tóxicas, estupefacientes o sustancias psicotrópicas.

En virtud de lo expuesto, y de conformidad con el art. 56 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas y lo dispuesto en el art. 36.16 de la Ley Orgánica 4/2015, de 30 de marzo, sobre Protección de la Seguridad Ciudadana, DENUNCIA:

Los hechos más arriba expuestos y en su caso, la adopción de la medida cautelar prevista en el art. 49.1 a) de la Ley Orgánica 4/2015, de 30 de marzo, sobre protección de la seguridad ciudadana.

En [LUGAR], a [FECHA].

Firmado:
