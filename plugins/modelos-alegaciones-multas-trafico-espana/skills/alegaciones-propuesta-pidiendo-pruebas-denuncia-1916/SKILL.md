---
name: alegaciones-propuesta-pidiendo-pruebas-denuncia-1916
description: "Redacta el escrito «Alegaciones a la propuesta pidiendo pruebas en denuncia de controlador de estacionamiento» (formulario 1916 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones a la propuesta pidiendo pruebas en denuncia de controlador de estacionamiento

> Formulario 1916 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (2 veces)
- [ ] MATRÍCULA
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…r el Pleno del Ayuntamiento con fecha de»; «…(BOP»; «…rio respecto de los hechos denunciados (»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5 del Real Decreto 320/1994
- artículo 14 del Real Decreto 320/1994
- Ley 40/2015

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

### Formulario 1916 · Alegaciones a la propuesta pidiendo pruebas en denuncia de controlador de estacionamiento

- Año del modelo: 2012
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de alegaciones a la propuesta de resolución en el que se solicita la práctica de determinadas pruebas en relación con denuncia formulada por controlador del servicio de estacionamiento, ya que dicha denuncia carece de uno de los datos del denunciante que deben constar en toda denuncia, tal y como es el nombre del denunciante.

D./Dña. [NOMBRE Y APELLIDOS], con DNI n.º [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante dicho Órgano comparece y como mejor proceda en Derecho,

EXPONE

PRIMERA.- Que he recibido notificación de propuesta de resolución de procedimiento sancionador dictada en expediente de su referencia n.º [NÚMERO] por una presunta infracción cometida el día [FECHA] consistente estacionar por tiempo igual o superior a 5 minutos en zona de carga y descarga durante las horas fijadas para su uso el vehículo con matrícula [MATRÍCULA] en la calle [CALLE].

SEGUNDO.- La denuncia de los hechos descritos ha sido formulada por un controlador del Servicio de Estacionamiento Regulador y carece de uno de los datos del denunciante que deben constar en toda denuncia, tal y como es el nombre del denunciante, por así establecerlo el artículo 5 del Real Decreto 320/1994 [NOTA DE REVISIÓN: Contenido de la denuncia: hoy art. 87.2 TR LSV (identificación del vehículo, del denunciado si se conoce, hecho con lugar o tramo, fecha y hora, y datos del denunciante o número profesional del agente o del controlador de estacionamiento regulado, este último añadido por Ley 18/2021). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 87.2.], de 25 de febrero por el que se aprueba el Reglamento del Procedimiento Sancionador en materia de tráfico. En el mismo sentido se pronuncia el artículo 98.4 de la Ordenanza de Tráfico aprobada por el Pleno del Ayuntamiento con fecha de [COMPLETAR] (BOP [COMPLETAR]).

TERCERO.- Según el artículo 14 del Real Decreto 320/1994 únicamente "las denuncias efectuadas por los agentes de la autoridad encargados de la vigilancia del tráfico tendrán valor probatorio respecto de los hechos denunciados ( [COMPLETAR])".

Por todo lo cual, solicita copia de la denuncia original, así como la apertura del periodo de prueba, contemplado en el art. 13 del citado Real Decreto, aportándose las pertinentes pruebas por parte de la Administración denunciante, consistentes en la ratificación de los hechos por agentes de la Policía Municipal para así romper la presunción de inocencia recogida en la Constitución y en la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público.

En [LUGAR], a [FECHA].

Firma:
