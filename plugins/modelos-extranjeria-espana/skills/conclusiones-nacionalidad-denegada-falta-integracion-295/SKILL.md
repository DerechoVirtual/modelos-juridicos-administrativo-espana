---
name: conclusiones-nacionalidad-denegada-falta-integracion-295
description: "Redacta el escrito «Conclusiones: nacionalidad denegada por falta de integración» (formulario 295 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conclusiones: nacionalidad denegada por falta de integración

> Formulario 0295 del plugin **Extranjería** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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
- [ ] FECHA
- [ ] LOCALIDAD

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

### Formulario 0295 · Conclusiones: nacionalidad denegada por falta de integración

- Año del modelo: 2014
- Revisión 17-11-2026: 4 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Procedimiento Ordinario/20

A LA SALA DE LO CONTENCIOSO ADMINISTRATIVO DE LA AUDIENCIA NACIONAL

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según consta acreditado en los autos arriba referenciados, mediante el presente escrito ante la Sala comparezco y DIGO

Que habiéndoseme notificado en fecha [FECHA] providencia por la que se emplaza a esta parte a fin de presentar escrito de conclusiones, mediante el presente escrito y dentro del plazo establecido presento las siguientes:

CONCLUSIONES

PRIMERA.- Del resultado de las pruebas realizadas ha quedado claramente acreditado que el recurrente tiene un elevado grado de integración social, según la documentación aportada y el testimonio de los testigos, que han demostrado que mi representado no sólo lleva una conducta irreprochable en España, sino que está involucrado de forma altruista en actividades sociales y comunitarias que avalan su interés en el buen funcionamiento de nuestra sociedad.

Debe resaltarse, además, el hecho de que la propia Administración emitiera en su momento un informe de integración social favorable gracias al cual le fue concedida la autorización de residencia por arraigo social en España.

SEGUNDA.- Frente a la contundencia de las pruebas aportadas, no puede considerarse suficiente para considerar que mi representado no acreditaba un suficiente grado de integración en nuestra sociedad el mero informe del Juez encargado del Registro Civil estimándolo así, máxime cuando no ha sido posible conocer el contenido de la entrevista ni de las preguntas que allí se formularon y que habría que valorar en su conjunto para ver si dicha estimación del Juez encargado del Registro Civil estaba suficientemente motivada.

En todo lo demás, nos remitimos a los hechos de la demanda, reiterando la solicitud de revocación de la resolución recurrida y la solicitud de condena en costas a la Administración demandada.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

Se reiteran los fundamentos recogidos en la demanda, especialmente la Sentencia de la Audiencia Nacional de [LOCALIDAD]

En su virtud, SUPLICO A LA SALA que, teniendo por presentado este escrito, con sus copias, se sirva admitirlo; y por presentado el escrito de conclusiones, se acuerde declarar el pleito concluso para sentencia, y dictar sentencia revocando la resolución recurrida y declarando el derecho de mi representado a la concesión de la nacionalidad española por residencia, con expresa imposición de costas a la Administración.

Por ser Justicia que reitero en lugar y fecha ut supra.

Fdo:

Procurador/a

Fdo:

Abogado/a
