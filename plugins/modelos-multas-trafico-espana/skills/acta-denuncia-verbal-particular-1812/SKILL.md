---
name: acta-denuncia-verbal-particular-1812
description: "Redacta el escrito «Acta de la denuncia verbal de un particular» (formulario 1812 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de la denuncia verbal de un particular

> Formulario 1812 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] MATRÍCULA
- [ ] MARCA/MODELO (2 veces)
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…r el agente de vigilancia de tráfico. En»; «…, modelo [MARCA/MODELO], color»; «…, color [COMPLETAR], conducido por»; «…ende la presente acta para su remisión a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 7.a), del Real Decreto 320/1994
- art. 7 RD 320/1994

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

### Formulario 1812 · Acta de la denuncia verbal de un particular

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; 2 llamadas a nota sin texto retiradas; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de acta en el que se deja constancia de la denuncia verbal llevada a cabo por particular, de una infracción en materia de tráfico, circulación de vehículos a motor y seguridad vial, prevista para los casos en que no se ha formalizado el reglamentario boletín de denuncia por el agente de vigilancia de tráfico.

En [COMPLETAR], siendo las [Nº] horas del día [FECHA], se persona en las dependencias del Ayuntamiento de [LOCALIDAD], D./Dña. [NOMBRE Y APELLIDOS], DNI número [DNI/NIE], de profesión [PROFESIÓN], con domicilio en [LOCALIDAD], y ante la Unidad de Sanciones, formula la siguiente

DENUNCIA VERBAL:

Que a las [Nº] horas del día [FECHA], con el vehículo matrícula [MATRÍCULA], marca [MARCA/MODELO], modelo [MARCA/MODELO], color [COMPLETAR], conducido por [COMPLETAR], se realizaron los siguientes hechos que pueden ser constitutivos de infracción administrativa:

Y para que así conste a los efectos prevenidos en el artículo 7.a), del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de Procedimiento Sancionador en materia de Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, se extiende la presente acta para su remisión a [COMPLETAR], órgano competente para la tramitación del procedimiento correspondiente.

EL DENUNCIANTE,

EL FUNCIONARIO,

La denuncia voluntaria, realizada por cualquier persona que tenga conocimiento de la infracción, puede realizarse por escrito o verbalmente. La denuncia verbal puede realizarse ante "los agentes de vigilancia del tráfico más próximos al lugar del hecho" (art. 7 RD 320/1994). El agente de vigilancia del tráfico formalizará el reglamentario boletín de denuncia y hará constar si personalmente comprobó o no la infracción denunciada. No obstante, cuando esta actuación no sea posible, la Administración puede hacer constar la denuncia verbal mediante la oportuna acta o diligencia suscrita por el funcionario que la recibe y por el denunciante para acreditar la veracidad de las manifestaciones vertidas verbalmente. Hay que reconocer que no es frecuente que los funcionarios admitan denuncias verbales por la incomodidad que supone redactar actas como la consignada en este formulario, por lo que se suele indicar a los ciudadanos que la forma de denunciar es por escrito, sin embargo está prevista la denuncia verbal y, en consecuencia, se debe facilitar a quien lo desee que se cumplimente, pues de lo contrario se desanima a los ciudadanos a colaborar con la Administración Pública en la vigilancia y control de las actividades a su cargo, lo que es de agradecer, aunque en materia de tráfico la denuncia de particulares es prácticamente inexistente en lo que se refiere a normas de circulación, pero puede ser interesante en incumplimientos referidos a centros de reconocimiento de vehículos, autoescuelas, publicidad del automóvil, obstrucciones en las calzadas, deterioros de señalización, vertederos y otras actividades similares previstas como infracciones en la legislación vial.
