---
name: pedir-declare-oficio-nulidad-pleno-derecho-1415
description: "Redacta el escrito «Pedir que se declare de oficio la nulidad de pleno derecho» (formulario 1415 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir que se declare de oficio la nulidad de pleno derecho

> Formulario 1415 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (3 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…onstitucional en los siguientes términos»; «…es públicos. 2. El órgano autor del acto»; «…razón de la materia o del territorio por»; «…e un contenido imposible, por cuanto que»; «…nado es constitutivo de infracción penal»; «…enal cometida tiene una relación directa»; «…del procedimiento legalmente establecido»; «…equisitos esenciales para su adquisición»; «…, del apartado»; «… invocadas. Segundo.- Que se indemnice a»

## Elecciones que hay que hacer

- expreso / presunto

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66.1 de la Ley 39/2015
- art. 52.3 LPACAP
- art. 106 de la Ley 39/2015

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

### Formulario 1415 · Pedir que se declare de oficio la nulidad de pleno derecho

- Año del modelo: 2004
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al [ÓRGANO AL QUE SE DIRIGE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]

conforme al artículo 66.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,

actuando

[ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original]

ante comparece, y como mejor proceda

DICE:

Que por medio de este escrito promueve la acción correspondiente para que se declare de oficio la nulidad de pleno derecho de la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], ya que en dicho acto administrativo concurren los presupuestos legales para el fundamento de esta pretensión y así se acredita mediante las siguientes

ALEGACIONES:

1. La resolución mencionada es nula de pleno derecho porque lesiona el contenido esencial de los derechos y libertades susceptibles de amparo constitucional en los siguientes términos [COMPLETAR] Esta nulidad se deriva del carácter de los derechos y libertades fundamentales como principios superiores del ordenamiento, dotados de efectividad inmediata y preferente frente a todos los poderes públicos.
2. El órgano autor del acto [COMPLETAR], es manifiestamente incompetente, por razón de la materia o del territorio por [COMPLETAR] No se trata de una simple incompetencia de grado o incompetencia jerárquica que permita la convalidación del acto por el superior jerárquico del órgano autor del mismo (art. 52.3 LPACAP). Se trata, en definitiva, del ejercicio de facultades atribuidas a otros órganos de la Administración.
3. La resolución dictada tiene un contenido imposible, por cuanto que [COMPLETAR] y así se acredita. Se trata de una imposibilidad de carácter material o físico (no jurídico equivalente a ilegalidad en general); o de carácter lógico: dentro del acto se aprecia que la aplicación de uno de sus efectos anula el efecto requerido por otro, sin que sea posible su aplicación simultánea; o de contenido ambiguo e indeterminable: imposición de una sanción pecuniaria sin concretar su cuantía.
4. El acto impugnado es constitutivo de infracción penal [COMPLETAR]. La infracción penal cometida tiene una relación directa [COMPLETAR], con el acto administrativo posterior.
5. La resolución fue dictada prescindiendo total y absolutamente del procedimiento legalmente establecido [COMPLETAR]. Esta expresión legal hay que referirla a la omisión de los trámites esenciales integrantes del procedimiento y sin los cuales éste resulta inidentificable. No se trata de una infracción procedimental aislada que sólo sirva para apoyar en vía de recurso una pretensión anulatoria. También hay que entender aplicable la sanción de nulidad de pleno derecho cuando se ha observado un procedimiento no previsto por la Ley para ese supuesto.
6. Se trata de un acto [ELEGIR: expreso / presunto] contrario al ordenamiento jurídico por el que se adquieren facultades o derechos cuando se carece de los requisitos esenciales para su adquisición [COMPLETAR]. Solo puede obtenerse por silencio aquello que hubiera podido obtenerse por resolución expresa.

A consecuencia del acto, cuya declaración de nulidad se solicita, esta parte ha sufrido daños y perjuicios, en la cuantía de [IMPORTE] euros, en los términos que se describen y se acreditan a continuación:

Por lo expuesto, y de conformidad con el art. 106 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,

SOLICITA:

Primero.- Que se declare, de oficio, la nulidad de pleno derecho

de la resolución de fecha [FECHA],

del apartado [COMPLETAR] de la resolución, dejando a salvo lo demás dictada por [ÓRGANO O PERSONA], por las causas invocadas.

Segundo.- Que se indemnice a [COMPLETAR], en la suma de [IMPORTE], en concepto de daños y perjuicios causados a consecuencia del acto nulo.

En [LUGAR], a [FECHA].

Firmado:
