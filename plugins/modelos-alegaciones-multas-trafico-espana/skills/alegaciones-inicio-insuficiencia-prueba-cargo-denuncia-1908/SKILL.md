---
name: alegaciones-inicio-insuficiencia-prueba-cargo-denuncia-1908
description: "Redacta el escrito «Alegaciones al inicio por insuficiencia de prueba de cargo en denuncia de tráfico» (formulario 1908 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones al inicio por insuficiencia de prueba de cargo en denuncia de tráfico

> Formulario 1908 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…da. Al Sr. Jefe Provincial de Tráfico de»; «…perior a la fijada como máxima en la vía»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 12.1 del Real Decreto 320/1994

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

### Formulario 1908 · Alegaciones al inicio por insuficiencia de prueba de cargo en denuncia de tráfico

- Año del modelo: 2012
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de alegaciones al acuerdo de inicio sobre insuficiencia de la prueba de cargo en relación con denuncia de tráfico, por existir defectos formales que implican que la prueba no sea válida.

Al Sr. Jefe Provincial de Tráfico de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], con DNI n.º [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante dicho Órgano comparece y como mejor proceda en Derecho,

EXPONE

PRIMERA.- Que habiendo sido identificada como conductora, he recibido resolución de inicio de procedimiento sancionador dictada en expediente de su referencia n.º [NÚMERO] por una presunta infracción grave cometida el día [FECHA], consistente en circular a velocidad superior a la fijada como máxima en la vía [COMPLETAR].

SEGUNDA.- Que examinado el contenido de dicho acuerdo y no encontrando sus disposiciones ajustadas a Derecho, tengo a bien formular las siguientes ALEGACIONES en virtud del derecho que se reconoce el art. 12.1 del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento del Procedimiento Sancionador en materia de tráfico.

Es imposible determinar si la prueba fotográfica de los hechos denunciados cumple los requisitos a que hace referencia el Apéndice 1 del Anexo XII de la Orden ICT/155/2020, de 7 de febrero, por la que se regula el control metrológico del Estado de determinados instrumentos de medida, al no haberse notificado el acuerdo de inicio del procedimiento junto con la mencionada prueba.

Debe indicarse en el registro fotográfico la fecha y hora de la medida, la velocidad medida del vehículo infractor ni el sentido del desplazamiento, no resultando, por tanto, debidamente probados los hechos acaecidos que dan lugar a la tramitación de este expediente.

Y es que en el procedimiento administrativo sancionador la prueba de cargo válida y suficiente capaz de enervar la presunción de inocencia del presunto responsable ha de cumplir ciertos requisitos formales. La existencia de defectos formales implica que nos encontramos ante una prueba no válida. Las carencias iniciales que se detecten en la prueba fotográfica impiden que el documento público adquiera la fuerza probatoria.

En este sentido las SSTC 129/2003 y 131/2003, de 30 de junio, establecen que "cualquier insuficiencia en el resultado de las pruebas practicadas, libremente valorado por el órgano sancionador, debe traducirse en un pronunciamiento absolutorio".

Por lo anteriormente expuesto, solicito que teniendo por presentado este escrito de alegaciones, se digne admitirlo y, tras los trámites que estime necesarios y la revisión de las pruebas solicitadas, declare el sobreseimiento del expediente.

En [LUGAR], a [FECHA].

Firma:
