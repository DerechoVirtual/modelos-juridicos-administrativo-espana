---
name: certificacion-acto-presunto-silencio-negativo-384
description: "Redacta el escrito «Certificación de acto presunto por silencio negativo» (formulario 384 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificación de acto presunto por silencio negativo

> Formulario 0384 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR], con domicilio actual en»; «…de»; «…de [COMPLETAR] de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 25 de la Ley 39/2015
- Ley Orgánica 4/2000
- Real Decreto 1155/2024

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

### Formulario 0384 · Certificación de acto presunto por silencio negativo

- Año del modelo: 2013
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SUBDELEGACIÓN DEL GOBIERNO EN [LOCALIDAD]

Oficina de Extranjeros

CERTIFICACIÓN DE ACTO PRESUNTO

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad [NACIONALIDAD], con Pasaporte [DNI/NIE], cuyas demás circunstancias constan en expediente de Solicitud de Autorización de Trabajo y Residencia, presentada en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], con domicilio actual en [COMPLETAR], ante esa Subdelegación del Gobierno comparezco y, como mejor proceda, DIGO:

Que mediante escrito de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y cumpliendo todas la exigencias que al respecto se señalan por la legislación vigente, realizó a ese órgano administrativo la siguiente solicitud

«SOLICITUD DE AUTORIZACIÓN DE TRABAJO Y RESIDENCIA»

Que en la legislación reguladora de esa actividad se establece que la resolución del expediente se producirá en el plazo de tres meses, a contar desde la fecha de la presentación de la solicitud en el registro de entrada en el órgano competente para resolver, y que el efecto de no dictar resolución en el plazo establecido es el de poder entender desestimada la resolución de la solicitud, tal y como se recoge en la disposición adicional 1.ª de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, y disposiciones adicionales 7.ª y 8.ª del Real Decreto 1155/2024, de 19 de noviembre, en los términos de la solicitud y con sujeción al régimen jurídico previsto para estas actividades.

Que el plazo establecido en la legislación vigente, para el pronunciamiento de la resolución expresa, ha transcurrido sin que hasta la fecha se haya notificado a esta parte la terminación del citado procedimiento.

Que esta petición tiene por objeto hacer valer la eficacia de la autorización obtenida por acto presunto y, en caso de no ser expedida en el plazo establecido, la autorización correspondiente podrá acreditarse, a todos los efectos legales, mediante la exhibición de esta solicitud.

Por lo expuesto, y de conformidad con el artículo 25 de la Ley 39/2015, del Procedimiento Administrativo Común de las Administraciones Públicas,

SOLICITA

Que se tenga por presentado este escrito y de conformidad con lo que en el mismo se manifiesta, en el plazo de veinte días sea expedida la certificación comprensiva del objeto del expediente, con referencia a los plazos establecidos para resolver, y los efectos generados por la ausencia de la resolución expresa.

[NOMBRE Y APELLIDOS], a [DÍA] de [MES] de [AÑO]

Firmado:
