---
name: periodo-reflexion-casos-trata-seres-humanos-381
description: "Redacta el escrito «Periodo de reflexión en casos de trata de seres humanos» (formulario 381 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Periodo de reflexión en casos de trata de seres humanos

> Formulario 0381 del plugin **Extranjería** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] CALLE
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efecto de notificaciones en»; «… el derecho a un período de reflexión de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

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

### Formulario 0381 · Periodo de reflexión en casos de trata de seres humanos

- Año del modelo: 2013
- Revisión 17-11-2026: 9 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA DELEGACIÓN DEL GOBIERNO EN [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], mayor de edad, con pasaporte/NIE nº [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR] en la C/ [CALLE] ante este organismo comparece y

EXPONE

Primero.— Que llegó a España el día [FECHA]

Segundo.— Que las circunstancias de su llegada a España han sido las siguientes:

Tercero.— Que dichas circunstancias referidas le hacen de aplicación lo establecido en el artículo 59.bis de la Ley Orgánica 4/2000 en lo relativo a la concesión de un período de restablecimiento y reflexión de al menos treinta días durante el cual se autorizaría su estancia temporal y se suspendería el expediente sancionador que se hubiera podido incoar o, en su caso, la expulsión o devolución acordadas.

Durante dicho período decidiría si desea cooperar con las autoridades en la investigación del delito del que ha sido víctima.

Este periodo de reflexión ya se recogía en el Plan Integral de Lucha contra la Trata de Seres Humanos del Gobierno, de 12 de diciembre de 2008, cuyo texto reconoce el derecho a un período de reflexión de [COMPLETAR], al menos, 30 días, para que las víctimas “puedan restablecerse y escapar de la influencia de los traficantes y/o decidir su colaboración con las autoridades administrativas, policiales y judiciales”.

La normativa europea señala asimismo la obligación por parte de los Estados del reconocimiento de un período de recuperación y reflexión cuando una persona sea víctima o presunta víctima de la trata de personas.

Así, la Directiva 2004/81/CE del Consejo de Europa, de 29 de abril de 2004, relativa a la expedición de un permiso de residencia a nacionales de terceros países que sean víctimas de la trata de seres humanos o hayan sido objeto de una acción de ayuda a la inmigración ilegal, que cooperen con las autoridades competentes, que entró en vigor en agosto de 2006, señala en su artículo 6 que se garantizará a las personas nacionales de terceros países que sean víctimas de trata un periodo de reflexión que les permita recuperarse y librarse de la influencia de los autores de la trata de personas, de forma que puedan decidir con conocimiento de causa si cooperan con las autoridades competentes.

Por otro lado, el 1 de agosto de 2009 entró en vigor en España el Convenio del Consejo de Europa sobre Lucha contra la Trata de Seres Humanos, cuyo artículo 13 señala que «cuando existan motivos razonables para creer que una persona es una víctima» de la trata, se le deberá reconocer un periodo de restablecimiento y reflexión de al menos 30 días, «para que la persona pueda restablecerse y escapar de la influencia de los traficantes y/o pueda tomar, con conocimiento de causa, una decisión en lo relativo a su cooperación con las autoridades competentes». Durante dicho periodo el Estado deberá autorizar la estancia de la persona en su territorio.

De acuerdo con el Convenio, durante la duración del periodo las víctimas tendrán derecho a acogerse a las siguientes medidas: acceso a una vivienda adecuada y segura y una asistencia psicológica y material, acceso a asistencia médica, ayuda en materia de traducción e interpretación, asesoría e información en relación con los derechos que otorga la ley y los servicios que tiene a su disposición, asistencia para que sus derechos e intereses puedan estar presentes y tenerse en cuenta en los momentos adecuados de las acciones penales entabladas contra los autores de los delitos, atención a sus necesidades en materia de seguridad y protección de las víctimas, medidas para promover la cooperación de las víctimas con las organizaciones no gubernamentales u organizaciones de la sociedad civil y, por último, en el caso de las personas en situación administrativa regular, señala que se adoptarán las normas necesarias para que accedan al mercado de trabajo, a la formación y a la enseñanza.

Es importante señalar que en ningún caso el periodo de reflexión podrá realizarse en un Centro de Internamiento para extranjeros, pues ello sería contrario a lo establecido en el Convenio.

Como señala el Informe explicativo del Convenio del Consejo de Europa, el artículo 13 aplica a aquellas víctimas que se encuentran en situación irregular en el territorio de un Estado parte, tal y como es el caso de la interesada, pues está en una situación de especial vulnerabilidad tras la experiencia sufrida, y por el riesgo que existe de que sean expulsadas del territorio (párrafo 172).

Resulta muy importante destacar que el Informe explicativo señala que la finalidad del periodo de reflexión es que la persona que sufre la trata pueda tomar una decisión informada sobre su colaboración con las autoridades competentes, sin que bajo ningún concepto quede condicionado a que coopere con las autoridades en la investigación o persecución del delito (párrafo 175).

El Informe Explicativo señala también que durante la duración del período de recuperación y reflexión la víctima no podrá ser expulsada del territorio, destacando la importancia de que dicho periodo no dure menos de 30 días, pues uno de los objetivos del mismo es permitir a la víctima decidir sobre su cooperación con las autoridades competentes con el fin de procesar a los autores de la trata, pudiendo así la víctima tomar una decisión con el conocimiento de las medidas de protección y asistencia que le asisten, así como los procedimientos judiciales que existen contra los traficantes (párrafo 174).

Por otro lado, las autoridades del Estado parte tienen la obligación de proveer a las víctimas con los documentos necesarios que les permitan encontrarse en situación regular en territorio durante el tiempo de duración del periodo de recuperación y reflexión (párrafo 178).

Por lo expuesto SOLICITA que le sea de aplicación lo establecido en el artículo 59.bis de la Ley Orgánica 4/2000 y le sea concedido un período de restablecimiento y reflexión de al menos 30 días, y se autorice su estancia temporal en España durante dicho período, suspendiéndose los posibles procedimientos sancionadores incoados o la ejecución de la expulsión o devolución que hubieran podido ser acordados.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo.:
