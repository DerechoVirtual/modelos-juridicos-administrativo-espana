---
name: alegaciones-audiencia-previa-sin-propuesta-resolucion-983
description: "Redacta el escrito «Alegaciones en la audiencia previa, sin propuesta de resolución» (formulario 983 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones en la audiencia previa, sin propuesta de resolución

> Formulario 0983 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, actuando en nombre propio»; «… a las siguientes: ALEGACIONES PRIMERA.-»; «…SEGUNDA.-»; «…do -estimamos que con pleno derecho- son»; «…itaciones reducidas al máximo. TERCERA.-»; «…RGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE»; «…- CONCURRENCIA DE SANCIONES,»; «…CADUCIDAD DEL PROCEDIMIENTO»; «… LA SUPUESTA COMISICIÓN DE LA INFRACCIÓN»; «…-»; «…- [COMPLETAR] -»

## Párrafos opcionales (8)

Inclúyelos solo si encajan en los hechos:

- - FALTA DE COMPETENCIA DEL ORGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE [COMPLETAR]…
- - FALTA DE TIPICIDAD DE LOS HECHOS.…
- - CONCURRENCIA DE SANCIONES, [COMPLETAR].…
- - PRESCRIPCIÓN DE LA INFRACCIÓN.…
- CADUCIDAD DEL PROCEDIMIENTO [COMPLETAR].…
- - ILEGALIDAD DE LA INTERVENCIÓN DE LOS BIENES EMPLEADOS PARA LA SUPUESTA COMISICIÓN DE LA INFRACCIÓN [COMPLETA…
- - IMPROCEDENCIA DE LA SANCIÓN DE EXPULSIÓN POR APLICACIÓN DEL PRINCIPIO DE PROPORCIONALIDAD PREVISTO DE MODO E…
- - [COMPLETAR]…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 235.4 del Real Decreto 557/2011
- art. 53 de la Ley 39/2015
- art. 24.2 de la Constitución
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

### Formulario 0983 · Alegaciones en la audiencia previa, sin propuesta de resolución

- Año del modelo: 2008
- Revisión 17-11-2026: 8 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL INSTRUCTOR DEL PROCEDIMIENTO

PROCEDIMIENTO SANCIONADOR PREFERENTE EN MATERIA DE EXTRANJERÍA Nº [Nº]

INTERESADO

D./Dña. [NOMBRE Y APELLIDOS], con DNI/NIF/NIE nº [DNI/NIE], actuando en nombre propio [COMPLETAR], cuyo domicilio, a efectos de las notificaciones que pudieran serle cursadas en el procedimiento, tiene oportunamente consignado en sus escritos anteriores, a través del presente, comparece y como mejor proceda en derecho

EXPONE

Que con fecha [FECHA] le ha sido dado traslado por ese Instructor de su rechazo de las pruebas que fueron propuestas por este interesado en su anterior escrito de [FECHA], cursándole además el trámite de audiencia, por plazo 48 horas, previsto en el art. 235.4 del Real Decreto 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social.

Por todo ello en el plazo reglamentariamente previsto paso a cumplimentar el indicado trámite con arreglo a las siguientes:

ALEGACIONES

PRIMERA.- [COMPLETAR]

SEGUNDA.- [COMPLETAR]

En concreto, los medios de prueba denegados por ese Instructor, según queda indicado, y que está interesada había solicitado -estimamos que con pleno derecho- son [COMPLETAR].

El art. 53 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), establece el derecho a la práctica de los medios de prueba ‘que resulten procedentes’ como un derecho primario de los administrados en los procedimientos sancionadores. Por otra parte, el art. 24.2 de la Constitución consagra el derecho a la práctica de los medios de prueba como un derecho fundamental, de lo que se deriva que las normas infraconstitucionales deben ser interpretadas de la manera más adecuada a la máxima efectividad del derecho y, contrariamente, sus restricciones o limitaciones reducidas al máximo.

TERCERA.- [COMPLETAR]

[OPCIONAL — incluir si procede]

- FALTA DE COMPETENCIA DEL ORGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE [COMPLETAR]

[OPCIONAL — incluir si procede]

- FALTA DE TIPICIDAD DE LOS HECHOS.

[OPCIONAL — incluir si procede]

- CONCURRENCIA DE SANCIONES, [COMPLETAR].

[OPCIONAL — incluir si procede]

- PRESCRIPCIÓN DE LA INFRACCIÓN.

[OPCIONAL — incluir si procede]

CADUCIDAD DEL PROCEDIMIENTO [COMPLETAR].

[OPCIONAL — incluir si procede]

- ILEGALIDAD DE LA INTERVENCIÓN DE LOS BIENES EMPLEADOS PARA LA SUPUESTA COMISICIÓN DE LA INFRACCIÓN [COMPLETAR].

[OPCIONAL — incluir si procede]

- IMPROCEDENCIA DE LA SANCIÓN DE EXPULSIÓN POR APLICACIÓN DEL PRINCIPIO DE PROPORCIONALIDAD PREVISTO DE MODO EXPLÍCITO EN EL ART. 57.1 DE LA LEY ORGÁNICA 4/2000, TRAS SU REFORMA POR LA LEY ORGÁNICA 2/2009, Y POR IMPERATIVO DE LOS CRITERIOS PARA LA DETERMINACIÓN DE LA SANCIÓN PREVISTOS EN EL ART. 55.3 Y 4 DE LA MISMA LEY ORGÁNICA Y 119.3 DEL REGLAMENTO.

[OPCIONAL — incluir si procede]

- [COMPLETAR]

- [COMPLETAR]

En atención a todo lo expuesto,

SUPLICO

que tenga por presentado este escrito en tiempo y forma, lo admita a trámite y, en su virtud, tenga por formuladas las alegaciones en él contenidas y por evacuado el trámite correspondiente, con admisión de la totalidad de los medios probatorios solicitados por este mismo interesado, y, previos los trámites legales, se acuerde el archivo del expediente sancionador sin declaración de responsabilidad por las causas más arriba expresadas.

En [LUGAR], a [FECHA].

Firma:	Firma:
