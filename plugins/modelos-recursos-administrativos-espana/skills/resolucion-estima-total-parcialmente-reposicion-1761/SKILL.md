---
name: resolucion-estima-total-parcialmente-reposicion-1761
description: "Redacta el escrito «Resolución que estima total o parcialmente la reposición» (formulario 1761 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución que estima total o parcialmente la reposición

> Formulario 1761 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] FECHA (6 veces)
- [ ] ÓRGANO O PERSONA
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] ÓRGANO
- [ ] LUGAR

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 123 y 124 Ley 39/2015
- art. 52 LPACAP
- art. 119 LPACAP

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

### Formulario 1761 · Resolución que estima total o parcialmente la reposición

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 18 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Resolución del recurso de reposición interpuesto contra resolución dictada en el procedimiento sancionador, la cual impone una sanción administrativa como consecuencia de la comisión de una infracción en materia de tráfico, por la que se estima en todo o en parte la pretensión del interesado.

Visto el recurso interpuesto por D./Dña. [NOMBRE Y APELLIDOS], DNI [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], contra la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], en la que se impone una sanción administrativa como consecuencia de una infracción de la legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial, resulta:

Primero. Mediante denuncia de fecha [FECHA], formulada por agente de la autoridad encargado de la vigilancia del tráfico, procedió a la incoación de expediente sancionador número [Nº DE PROCEDIMIENTO]/[AÑO], a D./Dña. [NOMBRE Y APELLIDOS], con objeto de depurar las responsabilidades en que hubiera podido incurrir como consecuencia de los siguientes hechos:

Segundo. En el boletín de denuncia entregado al interesado se comunicaron los hechos imputados, las normas que se estimaron infringidas y las sanciones que, en su caso, podían recaer, con objeto de que pudiera presentar descargos y alegaciones, proponer pruebas y tomar audiencia y vista del expediente.

Tercero. Dentro del plazo establecido, por el inculpado no se ha presentado escrito de descargos y alegaciones ni ninguna otra actuación tendente a la defensa de su derecho por lo que se procedió a dictar la Resolución definitiva ahora impugnada.

Mediante Resolución de fecha [FECHA], se ha desestimado, en los términos expresados en su parte dispositiva, el escrito de descargos y alegaciones presentado en el expediente.

Cuarto. Mediante escrito de fecha [FECHA], dentro del plazo establecido, se ha interpuesto Recurso de reposición contra la Resolución mencionada en el que se fundamenta su pretensión de invalidez del acto sancionador en lo siguiente:

Quinto. En el escrito de interposición del recurso se alega y prueba la realización por el órgano actuante de ninguna de las infracciones del ordenamiento jurídico para acceder a lo solicitado, por lo que procede estimar este recurso por cuanto que:

Vistos los antecedentes mencionados, en virtud de lo establecido en los artículos 123 y 124 Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP) y las demás normas de general y pertinente aplicación,

DISPONGO:

Primero.- Se estima el recurso de reposición interpuesto por contra la Resolución de fecha [FECHA], por resultar contraria a derecho en los términos descritos en esta resolución (1).

Segundo.- Notifíquese esta resolución al interesado con la indicación de que, por ser firme en vía administrativa, únicamente podrá interponer contra ella recurso contencioso-administrativo ante [ÓRGANO], en el plazo de dos meses y en la forma indicada en la Ley Reguladora de dicha jurisdicción.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) La resolución del recurso ordinario estimará en todo o en parte o desestimará las pretensiones formuladas en el mismo o declarará su inadmisión. Cuando existiendo vicio de forma no se estime procedente resolver sobre el fondo se ordenará la retroacción del procedimiento al momento en que el vicio fue cometido salvo lo dispuesto en el art. 52 LPACAP. El órgano que resuelva el recurso decidirá cuantas cuestiones, tanto de forma como de fondo plantee el procedimiento, hayan sido o no alegadas por los interesados. En este último caso se les oirá previamente. No obstante, la resolución será congruente con las peticiones formuladas por el recurrente, sin que en ningún caso pueda agravarse su situación inicial (art. 119 LPACAP).
