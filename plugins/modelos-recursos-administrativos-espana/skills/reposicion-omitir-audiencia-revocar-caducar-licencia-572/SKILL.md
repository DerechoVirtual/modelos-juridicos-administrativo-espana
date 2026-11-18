---
name: reposicion-omitir-audiencia-revocar-caducar-licencia-572
description: "Redacta el escrito «Reposición por omitir la audiencia al revocar y caducar una licencia» (formulario 572 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición por omitir la audiencia al revocar y caducar una licencia

> Formulario 0572 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 48 del Real Decreto 763/1979
- artículos 123 y 124 de la Ley 39/2015
- art. 8.4 de la Ley 40/2015
- artículo 84 de la Ley 39/2015
- artículo 8 de la Ley 39/2015
- artículo 13 de la Ley 39/2015
- artículo 47.1.e) de la Ley 39/2015

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

### Formulario 0572 · Reposición por omitir la audiencia al revocar y caducar una licencia

- Año del modelo: 2011
- Revisión 17-11-2026: 6 llamadas a nota sin texto retiradas; 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (DNI/NIE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS], con DNI núm. [DNI/NIE] y

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

actuando en su propio nombre y derecho, interpone, ante el Pleno de dicho Ayuntamiento de dicha localidad, recurso potestativo de reposición contra acuerdo de ese órgano de fecha [FECHA], por el que se declara revocada y se retira la licencia de auto-taxi de este interesado, con base en los siguientes antecedentes de hecho y fundamentos de derecho,

HECHOS

Primero.- Con fecha [FECHA] he recibido notificación del acuerdo de la Junta de Gobierno Local del Ayuntamiento de [LOCALIDAD] por la que se revoca y retira la licencia de auto-taxi de este interesado, al amparo de lo dispuesto en el artículo 48 del Real Decreto 763/1979, de 16 marzo, por el que se aprueba el Reglamento Nacional de los servicios urbanos e interurbanos de transportes en automóviles ligeros.

Segundo.- En dicho precepto se considera motivo suficiente para la revocación descrita el incumplimiento o transgresión de uno de los presupuestos inherentes a la licencia, esto es, la no explotación de la licencia con regularidad y sin interrupciones como se exige en este tipo de licencias. Es trascendente para el buen fin de este recurso manifestar que la notificación que se hace de la resolución impugnada en la fecha descrita, es la primera ocasión en que este interesado tiene conocimiento del procedimiento que ha desembocado en la revocación de la licencia.

FUNDAMENTOS DE DERECHO

Primero.- El recurso potestativo de reposición se interpone conforme a lo que disponen los artículos 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, ya que se trata de un acto que pone fin a la vía administrativa, al haber sido dictado por la Comisión de Gobierno en el ejercicio de una competencia delegada por el Pleno del Ayuntamiento.

Por esta razón se presenta ante el Pleno del Ayuntamiento, ya que de acuerdo con lo que dispone el art. 8.4 de la Ley 40/2015, las resoluciones administrativas que se adopten por delegación se entenderán dictadas por el órgano delegante. Se entiende, por esta razón, que la resolución ahora impugnada que resolvió la caducidad y revocación de la licencia de auto-taxi, fue dictada por el Pleno del Ayuntamiento.

El recurso se interpone en el plazo de un mes desde la notificación de la resolución, tal como exige el artículo 124.1 de la Ley más arriba mencionada.

Segundo.- El procedimiento aludido en el Real Decreto 763/1979, de 16 marzo, para la revocación de las licencias de auto-taxi no tiene naturaleza sancionadora, sino meramente interventora en la actividad del sector del transporte urbano, y ha de formalizarse siguiendo las pautas y disposiciones generales sobre procedimiento administrativo.

De acuerdo con esto, el déficit que el expediente presenta no es accidental ni depurable según criterios de economía procesal.

En primer lugar, no es lo mismo ni tiene las mismas consecuencias invalidantes la omisión de un trámite concreto y preciso como es el de audiencia del interesado del artículo 84 de la Ley 39/2015, en aquellos procedimientos en que interviene el mismo, que el hecho de que el expediente se haya llevado a cabo prescindiendo totalmente de la intervención de este recurrente, persona cuyos derechos e intereses legítimos van a ser directamente afectados por el pronunciamiento dictado en el mismo y sin oportunidad de ser oída, en sentido lato y genérico, al no serle comunicada ni siquiera la existencia de las actuaciones en el modo que hoy impone con carácter general el artículo 8 de la Ley 39/2015.

En el primer caso, se está en presencia de una infracción adjetiva que sólo alcanza eficacia invalidante en tanto produzca efectiva indefensión y que puede tenerse por superada en fases posteriores, incluso en el mismo proceso judicial. En el segundo supuesto, con la privación de toda oportunidad de ser oído el afectado en vía administrativa, quiebran, por el contrario, los principios de publicidad, audiencia y contradicción y se vulnera la garantía esencial de los administrados en sus relaciones con las Administraciones Públicas que comprende el derecho a conocer el estado de tramitación de los procedimientos en que tengan la condición de interesados, así como a formular alegaciones y aportar documentos, entre otros -artículo 13 de la Ley 39/2015-. En otro caso, el procedimiento se vacía de contenido alegatorio, y probatorio por parte de aquél que va a ser privado de derechos o facultades, originándose una completa e insubsanable indefensión.

Todo ello se hace particularmente intenso cuando se está en presencia de una actividad administrativa municipal que pone en agudo contraste los intereses de personas o grupos, asumiendo el expediente un marcado carácter contradictorio, que le aleja de todos aquellos supuestos en que la Administración no tiene en cuenta al resolver otros datos o circunstancias que las declaradas por el mismo interesado.

Tercero.- Se está entonces en presencia de un expediente que por su falta de notificación y audiencia al interesado, la parquedad de sus elementos instructorios, la imposibilidad de práctica de pruebas, y otras insuficiencias formales, incurre en el vicio de radical nulidad a que se refiere el artículo 47.1.e) de la Ley 39/2015, y nada justifica tener por subsanadas sus deficiencias ni permite optar por soluciones convalidatorias so pretexto de antiformalismo, eficacia o economía resolutiva, porque, independientemente de la indefensión efectiva originada y la falta de elementos determinantes del acierto y congruencia de la decisión, nada puede ya depurarse en el proceso.

Aunque exista expediente en un sentido formal estricto, cuestión que no se puede asegurar pues como ya se dejó dicho en los antecedentes de hecho de este recurso, la notificación de la resolución ahora impugnada es la primera noticia que se tiene de este procedimiento, el contenido de la actividad procedimental habrá sido tan simbólica y ritual, y se habrá prescindido de elementos tan esenciales en el procedimiento, que no debería dudarse en aplicar la calificación legal de haberse prescindido completamente del procedimiento legalmente establecido, del artículo 47.1.e) de la Ley 39/2015, de 1 de octubre, al tomar la resolución.

Así lo ha entendido la jurisprudencia en casos similares, de los que cabe citar ahora los de las sentencias del Tribunal Supremo de 19 de diciembre de 1991 o 9 de octubre de 1996, entre otros muchos.

En virtud de lo expuesto, y de conformidad con los artículos 13, 47.1.e), 82, 123 y 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, solicita:

Que se tenga por presentado este escrito, se sirva admitirlo y tenga por interpuesto recurso potestativo de reposición ante la Comisión de Gobierno de ese Ayuntamiento, para que, previa la tramitación que ordena la Ley, se dicte nueva resolución anulando la ahora impugnada al haber sido acordada sin dar trámite de audiencia a este interesado.

En [LUGAR], a [FECHA].

Firmado:
