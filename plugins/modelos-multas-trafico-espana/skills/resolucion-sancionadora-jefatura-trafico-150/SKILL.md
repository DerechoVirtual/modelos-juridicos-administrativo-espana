---
name: resolucion-sancionadora-jefatura-trafico-150
description: "Redacta el escrito «Resolución sancionadora de una Jefatura de Tráfico» (formulario 150 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución sancionadora de una Jefatura de Tráfico

> Formulario 0150 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] Nº (2 veces)
- [ ] PUNTO KILOMÉTRICO
- [ ] MATRÍCULA
- [ ] MARCA/MODELO (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…el/la denunciado/a circulando por la vía»; «…, con dirección a»; «…, clase»; «…, modelo [MARCA/MODELO], color»; «…, color [COMPLETAR], tara»; «…, tara [COMPLETAR], P. Máx.»; «…siguiente conducta contraria al artículo»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 84 del Real Decreto Legislativo 6/2015
- artículo 96 del Real Decreto Legislativo 6/2015
- Real Decreto 1428/2003
- Ley 39/2015

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

### Formulario 0150 · Resolución sancionadora de una Jefatura de Tráfico

- Año del modelo: 2017
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido a D./Dña. [NOMBRE Y APELLIDOS], DNI número [DNI/NIE], con domicilio en [LOCALIDAD], calle [CALLE] número [NÚMERO], como consecuencia de una infracción a la legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial resulta:

Primero. Datos de la denuncia

Con fecha [FECHA], siendo las [Nº] horas, se hallaba el/la denunciado/a circulando por la vía [COMPLETAR], punto kilométrico [PUNTO KILOMÉTRICO], con dirección a [COMPLETAR], con el vehículo matrícula [MATRÍCULA], clase [COMPLETAR], marca [MARCA/MODELO], modelo [MARCA/MODELO], color [COMPLETAR], tara [COMPLETAR], P. Máx. [COMPLETAR], según consta en la denuncia de fecha [FECHA] formulada por agente de la autoridad.

Segundo. Hecho denunciado

El/la conductor/a del vehículo referenciado en el lugar, fecha y hora consignada en el apartado anterior procedió a realizar la siguiente conducta contraria al artículo [COMPLETAR] del Real Decreto 1428/2003, de 21 de noviembre, por el que se aprueba el Reglamento General de Circulación y artículo Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial:

Tercero. Tramitación del expediente

Con fecha [FECHA], dentro del plazo establecido, por el/la inculpado/a se presentó escrito de descargos y alegaciones en el que se manifiesta lo siguiente para la defensa de su derecho:

Estas alegaciones formuladas por el/la interesado/a no pueden estimarse, por cuanto no desvirtúan el relato de los hechos imputados, ni su calificación jurídica, ni la aplicación de los principios que rigen la potestad sancionadora y el procedimiento sancionador en este expediente, por cuanto que:

Vistos los antecedentes mencionados y en uso de la facultad que me confiere el artículo 84 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial,

RESUELVO:

Primero.- Sancionar a D./Dña. [NOMBRE Y APELLIDOS], con la multa de [IMPORTE] euros y con la privación del permiso de conducir durante el plazo de [Nº] meses como responsable de la infracción administrativa tramitada en este expediente sancionador, en virtud de la denuncia formulada por el hecho que se indica.

Segundo.- Notifíquese la presente resolución al/a la interesado/a con la indicación de los recursos que procedan de conformidad con lo establecido en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, en relación con el artículo 96 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial [NOTA DE REVISIÓN: El art. 17 RD 320/1994 regula el recurso de alzada ante el Ministro del Interior contra sanciones de Delegados/Subdelegados del Gobierno: inaplicable hoy. Contra la resolución sancionadora (que agota la vía administrativa) cabe reposición potestativa en un mes ante el mismo órgano, sin efecto suspensivo y desestimada por silencio al mes (art. 96 TR LSV). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 96; RD 320/1994, BOE-A-1994-8985 art. 17.].

En [LUGAR], a [FECHA].

Firma del órgano competente para sancionar
