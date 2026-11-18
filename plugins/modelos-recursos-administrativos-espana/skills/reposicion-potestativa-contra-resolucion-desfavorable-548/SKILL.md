---
name: reposicion-potestativa-contra-resolucion-desfavorable-548
description: "Redacta el escrito «Reposición potestativa contra resolución desfavorable sin motivación» (formulario 548 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición potestativa contra resolución desfavorable sin motivación

> Formulario 0548 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… la Consejería de Educación y Cultura de»; «… la Consejería de Educación y Cultura de»; «…or esta interesada para el curso escolar»; «…, en el Colegio Público»; «… la Consejería de Educación y Cultura de»; «… la Consejería de Educación y Cultura de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 123 y 124 de la Ley 39/2015
- artículo 35.1.c) de la Ley 39/2015
- art. 48.2 de la Ley 39/2015
- artículos 35.1.c), 48.2, 123 y 124 de la Ley 39/2015

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

### Formulario 0548 · Reposición potestativa contra resolución desfavorable sin motivación

- Año del modelo: 2011
- Revisión 17-11-2026: 4 llamadas a nota sin texto retiradas; 17 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (DNI/NIE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS], con DNI núm. [DNI/NIE] y

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.],

actuando en su propio nombre y derecho, interpone, ante la Dirección General de Recursos Humanos de la Consejería de Educación y Cultura de [COMPLETAR], recurso potestativo de reposición contra su resolución de fecha [FECHA], por la que se desestima la solicitud de comisión de servicios, con base en los siguientes antecedentes de hecho y fundamentos de derecho,

HECHOS

Primero.- Por resolución de la Dirección General de Recursos Humanos de la Consejería de Educación y Cultura de [COMPLETAR], de fecha [FECHA], se desestimó la solicitud de comisión de servicios presentada por esta interesada para el curso escolar [COMPLETAR], en el Colegio Público [COMPLETAR] como consecuencia de la condición de Concejal en dicho Ayuntamiento.

Segundo.- La solicitud se denegaba la solicitud, tal como expresa literalmente la resolución impugnada, "... dada la necesidad de atender con carácter prioritario la ordenación del curso escolar en razones estrictamente docentes, no es posible atender las comisiones de servicio solicitadas por el hecho de reunir el interesado la condición de Concejal. De otro lado es de apreciar que las presentes solicitudes no están basadas en razones estrictamente docentes o de carácter prioritario para el servicio...", sin que se aludiera a motivo algún otro distinto.

FUNDAMENTOS DE DERECHO

Primero.- El recurso potestativo de reposición se interpone conforme a lo que disponen los artículos 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, ya que se trata de un acto que pone fin a la vía administrativa, al haber sido dictado por el Director General de Recursos Humanos de la Consejería de Educación y Cultura de [COMPLETAR] en el ejercicio de una competencia en materia de personal.

Por esta razón se presenta el recurso ante la citada Dirección General, que fue el órgano que resolvió la denegación de la comisión de servicio, y se efectúa en el plazo de un mes desde la notificación de la resolución, tal como exige el artículo 123.1 de la Ley más arriba mencionada.

Segundo.- La motivación de la resolución reproducida literalmente en los antecedentes de hecho resulta del todo genérica, prevista para un número indeterminado de casos, sin efectuar una mínima motivación adecuada específicamente para el caso de la hoy recurrente, sobre todo cuando en cursos anteriores le había sido concedida comisión de servicios de forma reiterada, en iguales circunstancias que la ahora denegada, y cuando el criterio que regía en cursos anteriores por parte de la Administración recurrida y para esta materia era claramente favorecedor de la concesión de la comisión de servicios en supuestos como éste.

Esta denegación, común y general para todas las solicitudes presentadas, no está mínimamente motivada, sin especificar las razones del cambio de criterio en la materia, "ex" artículo 35.1.c) de la Ley 39/2015, antes citada. No es que el precedente administrativo tenga un valor normativo, por cuanto nuestro Ordenamiento Jurídico solo admite los precedentes "extra legem" y no los "contra legem", pero dicho precedente puede tener un cierto valor vinculante para la propia Administración, en el sentido de que para poder apartarse de él será necesario "que razone debidamente los motivos por los que no se sigue el criterio anteriormente adoptado", doctrina ratificada por el Tribunal Supremo en Sentencia de 5 de octubre de 1998, Rec. 8534/1992, cuando hacía ver el riesgo de quiebra del principio de seguridad jurídica si se utilizasen motivaciones genéricas al separarse de criterios anteriores.

Tercero.- Acreditado que las circunstancias de esta interesada, como Concejal del Ayuntamiento de [LOCALIDAD], son las mismas que en los años anteriores, y toda vez que la Administración no ha acreditado ni motivado su cambio de criterio, esta omisión vicia de nulidad la resolución impugnada, que deberá ser anulada por falta de motivación generadora de indefensión, toda vez que se sustraen al administrado las razones o motivos que conducen a ese cambio de criterio dentro de la discrecionalidad de la que dispone la Administración para otorgar la comisión de servicios.

No constando las razones docentes y de organización determinantes de la denegación de la comisión de servicios por razón del cargo de Concejal ostentado por la demandante, sin olvidar la discrecionalidad que la Administración tiene atribuida en esta materia, procede la estimación parcial del recurso interpuesto, lo cual conduce, "ex" art. 48.2 de la Ley 39/2015, a la anulabilidad del acto recurrido, por carecer de los requisitos formales indispensables para alcanzar su fin, y con ello a la reposición de las actuaciones administrativas al momento anterior a la resolución inicial impugnada, a fin de que se determinen las circunstancias que conduzcan al cambio de criterio.

En virtud de lo expuesto, y de conformidad con los artículos 35.1.c), 48.2, 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, solicita:

Que se tenga por presentado este escrito, se sirva admitirlo y tenga por interpuesto recurso potestativo de reposición ante la Dirección General de Recursos Humanos de la Consejería de Educación y Cultura de [COMPLETAR], para que, previa la tramitación que ordena la Ley, se dicte nueva resolución anulando la impugnada, con retroacción de las actuaciones administrativas al momento anterior a la resolución, a fin de que se determinen las circunstancias que conduzcan al cambio de criterio.

En [LUGAR], a [FECHA].

Firmado:
