---
name: alegaciones-prueba-iniciacion-denuncia-981
description: "Redacta el escrito «Alegaciones y prueba en la iniciación por denuncia» (formulario 981 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones y prueba en la iniciación por denuncia

> Formulario 0981 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] FECHA (3 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…INTERESADO»; «…, actuando en nombre propio»; «…, con domicilio»; «…po Nacional de Policía copia del boletín»; «… a las siguientes: ALEGACIONES PRIMERA.-»; «…SEGUNDA.-»; «…RGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE»; «…- CONCURRENCIA DE SANCIONES,»; «…CADUCIDAD DEL PROCEDIMIENTO»; «… LA SUPUESTA COMISICIÓN DE LA INFRACCIÓN»; «…-»; «…y su Integración Social, paso a proponer»; …

## Párrafos opcionales (8)

Inclúyelos solo si encajan en los hechos:

- - FALTA DE COMPETENCIA DEL ORGANO PARA LA INSTRUCCIÓN DEL EXPEDIENTE [COMPLETAR]…
- - FALTA DE TIPICIDAD DE LOS HECHOS.…
- - CONCURRENCIA DE SANCIONES, [COMPLETAR].…
- - PRESCRIPCIÓN DE LA INFRACCIÓN.…
- CADUCIDAD DEL PROCEDIMIENTO [COMPLETAR].…
- - ILEGALIDAD DE LA INTERVENCIÓN DE LOS BIENES EMPLEADOS PARA LA SUPUESTA COMISICIÓN DE LA INFRACCIÓN [COMPLETA…
- - INADECUACIÓN DEL PROCEDIMIENTO SIMPLIFICADO.…
- - [COMPLETAR]…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66.1 de la Ley 39/2015
- art. 239.1 del RD 557/2011
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

### Formulario 0981 · Alegaciones y prueba en la iniciación por denuncia

- Año del modelo: 2008
- Revisión 17-11-2026: 8 párrafos opcionales señalados; 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL INSTRUCTOR DEL PROCEDIMIENTO

PROCEDIMIENTO SANCIONADOR SIMPLIFICADO EN MATERIA DE EXTRANJERÍA Nº [Nº]

INTERESADO

[COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], con DNI/NIF/NIE nº [DNI/NIE], actuando en nombre propio [COMPLETAR], con domicilio [COMPLETAR] en [LOCALIDAD], el cual señalo a efectos de notificaciones, conforme al artículo 66.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), a través del presente escrito, comparece, y como mejor proceda en derecho

EXPONE

Que con fecha [FECHA] le ha sido entregada por un funcionario del Cuerpo Nacional de Policía copia del boletín [COMPLETAR] de [FECHA], de denuncia por una supuesta infracción a la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su integración Social.

Que en dicha copia se le indicaba su derecho a formular alegaciones y proponer prueba en el plazo de 10 días.

Por todo ello paso a cumplimentar el indicado trámite con arreglo a las siguientes:

ALEGACIONES

PRIMERA.- [COMPLETAR]

SEGUNDA.- [COMPLETAR]

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

- INADECUACIÓN DEL PROCEDIMIENTO SIMPLIFICADO.

[OPCIONAL — incluir si procede]

- [COMPLETAR]

TERCERA.- Que para la acreditación de cuanto aquí se afirma, y en concreto con respecto a los hechos, y todo ello al amparo de lo dispuesto en el art. 239.1 del RD 557/2011, de 20 de abril, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social, paso a proponer [COMPLETAR] los siguientes medios de prueba:

- Documental:
- Testifical [COMPLETAR]
- Reconocimiento, por parte del instructor, del lugar de los hechos [COMPLETAR].
- Pericial, a cuyos efectos se aporta adjunto un informe emitido por el [ÓRGANO O PERSONA], D./Dña. [NOMBRE Y APELLIDOS], en el que [COMPLETAR].

En atención a todo lo expuesto,

SUPLICO,

que tenga por presentado este escrito en tiempo y forma, lo admita a trámite y, en su virtud, tenga por formuladas las alegaciones en él contenidas y por evacuado el trámite correspondiente, con admisión de la totalidad de los medios de prueba propuestos y, previos los trámites legales, se acuerde el archivo del expediente sancionador por las causas más arriba expresadas.

En [LUGAR], a [FECHA].

Fdo: D./Dña. [NOMBRE Y APELLIDOS]
