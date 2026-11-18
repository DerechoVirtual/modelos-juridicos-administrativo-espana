---
name: alegaciones-inicio-pidiendo-pruebas-sobre-aparato-1912
description: "Redacta el escrito «Alegaciones al inicio pidiendo pruebas sobre el aparato medidor de velocidad» (formulario 1912 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones al inicio pidiendo pruebas sobre el aparato medidor de velocidad

> Formulario 1912 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…áfico. Sr. Jefe Provincial de Tráfico de»; «…de»; «…de [COMPLETAR] de»; «…perior a la fijada como máxima en la vía»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 320/1994

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

### Formulario 1912 · Alegaciones al inicio pidiendo pruebas sobre el aparato medidor de velocidad

- Año del modelo: 2012
- Revisión 17-11-2026: 15 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de alegaciones al acuerdo de inicio en el que se solicita la práctica de determinadas pruebas en relación con el aparato medidor de la velocidad, en procedimiento sancionador en materia de tráfico.

Sr. Jefe Provincial de Tráfico de [COMPLETAR].

D./Dña. [NOMBRE Y APELLIDOS], con DNI n.º [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

ante dicho Órgano comparece y como mejor proceda en Derecho,

DICE

PRIMERO.- Que habiendo sido identificado/a como conductor/a, he recibido resolución de inicio de procedimiento sancionador dictada en expediente de su referencia n.º [NÚMERO] por una presunta infracción grave cometida el día [FECHA] de [COMPLETAR] de [COMPLETAR] consistente en circular a velocidad superior a la fijada como máxima en la vía [COMPLETAR].

SEGUNDO.- Teniendo en cuenta lo establecido en el art. 12.1 del Reglamento de procedimiento sancionador en materia de Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, aprobado por Real Decreto 320/1994, de 25 de febrero, los órganos competentes de las Jefaturas de la Dirección General de Tráfico y de los Ayuntamientos serán los instructores del expediente.

Examinado el contenido del acuerdo de inicio no figura en el mismo la identidad del titular del órgano instructor, por lo que el conductor denunciado no puede ejercitar su derecho de recusación que garantiza la objetividad de los órganos administrativos que instruyan y resuelvan los procedimientos sancionadores.

TERCERO.- Solicito que con relación al medio mecánico con que se midió la velocidad señalada se me faciliten sus datos y entre ellos, en concreto los siguientes:

1. Marca y modelo del cinemómetro utilizado.
2. Número de la antena del aparato con que se hizo la foto prueba de la denuncia.
3. Número del equipo en el que está implantada la antena.
4. Fecha de la aprobación individualizada, es decir, del aparato en concreto con que se detectó la infracción.
5. Fecha de la revisión anual comprensiva de la fecha de la denuncia.
6. Fecha de la revisión última que haya sido efectuada en el aparato cinemómetro o en cualquiera de las partes que lo componen, realizada con ocasión de alguna reparación que tras su revisión anual haya sido necesaria por avería u otra circunstancia similar.

Asimismo, se solicita certificado de aptitud para manipular el cinemómetro, por los Agentes denunciantes, ya que el funcionamiento de estos aparatos es de alta precisión y cualquiera de las operaciones previas que se realizan manualmente, puede modificar la velocidad detectada, en cuyo caso esta posible medición puede resultar errónea. Y, por supuesto, comprobar las pruebas de inicio del carrete como prueba de buen funcionamiento del radar en su conjunto (equipo de motor).

Debido a la imposibilidad de determinar en el fotograma la existencia de algún otro vehículo circulando en paralelo, teniendo en cuenta la existencia de varios carriles en el mismo sentido en la vía por la que circulaba, solicito sea acreditado que la infracción corresponde a mi vehículo y no a otro u otros. Se hace pues necesario conocer la posición del Radar en ese momento con relación a la línea de calzada y si ésta es recta o curva, pues los dos extremos varían totalmente la velocidad controlada por el radar, y no sería correcta en curva y dependiendo igualmente del carril que ocupara el vehículo infractor en ese momento; todo ello dice mucho sobre la veracidad o no de la velocidad controlada en ese momento.

Por lo anteriormente expuesto, solicito que teniendo por presentado este escrito de alegaciones, se digne admitirlo y, tras los trámites que estime necesarios y la revisión de las pruebas solicitadas, declare el sobreseimiento del expediente.

En [LUGAR], a [FECHA].

Firma:
