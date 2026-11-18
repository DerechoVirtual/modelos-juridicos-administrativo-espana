---
name: pedir-revocar-acto-resolucion-administrativa-629
description: "Redacta el escrito «Pedir revocar un acto o resolución administrativa» (formulario 629 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir revocar un acto o resolución administrativa

> Formulario 0629 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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
- [ ] CALLE
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (5 veces)
- [ ] SE DESCRIBIRÁ
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, de»; «… impone a mi representado una sanción de»; «…comisión de una infracción tipificada en»; «…diante copia que acompaño como documento»; «… tal como acredito mediante el documento»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 109.1 de la Ley 39/2015
- art. 109.1 de la Ley 39/2015
- artículo 48.2 de la Ley 39/2015

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

### Formulario 0629 · Pedir revocar un acto o resolución administrativa

- Año del modelo: 2010
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA ADMINISTRACIÓN DE D./D.ª [NOMBRE Y APELLIDOS] mayor de edad, con DNI nº [DNI/NIE] y con domicilio a efecto de notificaciones en calle [CALLE], de [COMPLETAR] (además, en su caso, teléfono, fax y/o correo electrónico), en nombre propio (o en representación de [NOMBRE DEL REPRESENTADO/A] según poder que se acompaña) EXPONE:1) Que en fecha [FECHA] se dictó acto administrativo consistente en [SE DESCRIBIRÁ], el cual tiene carácter desfavorable o de gravamen para este interesado.2) Que concurren razones de justicia para la revocación del citado acto, como se expondrá, sin que concurran otros motivos que lo impidan.3) Atendido lo anterior, y de acuerdo con lo prevenido en el artículo 109.1 de la Ley 39/2015, por medio del presente escrito solicito la REVOCACIÓN del citado acto en base a los siguientes HECHOS Y FUNDAMENTOS:

HECHOS Y FUNDAMENTOS PRIMERO.- La resolución cuya revocación se solicita, de fecha [FECHA], impone a mi representado una sanción de [COMPLETAR] por comisión de una infracción tipificada en [COMPLETAR], la cual acompaño a este escrito como documento número [Nº DE DOCUMENTO] SEGUNDO.- Dicha sanción se impuso en procedimiento seguido sin audiencia de mi representado y sin notificación efectiva al mismo, puesto que las comunicaciones practicadas lo fueron por edictos, al hallarse circunstancialmente ausente del domicilio.

Sin discutir la regularidad de las comunicaciones practicadas, lo cierto es que mi representado había facilitado otro domicilio a la Administración a la que me dirijo, concretamente en el escrito presentado en fecha [FECHA], con motivo de su intervención en otro procedimiento, según acredito mediante copia que acompaño como documento [COMPLETAR], no habiéndose agotado por la Administración los medios para dar comunicación efectiva del procedimiento al interesado. Por otra parte, la infracción que fue objeto de sanción ha quedado totalmente desvirtuada al haberle sido otorgada con posterioridad a mi representado la autorización cuya carencia motivó la imposición de la misma, tal como acredito mediante el documento [COMPLETAR] que acompaño a este escrito.

TERCERO.- A la vista de los hechos expuestos, solicito de esa Administración que, en uso de las facultades establecidas en el art. 109.1 de la Ley 39/2015, acuerde la revocación de la resolución impuesta, puesto que se dan todos los requisitos para ello.

En primer lugar, se trata de un acto de gravamen o desfavorable, que no concede derechos a terceros.

En segundo lugar, la resolución dictada podría incurrir en vicio de anulabilidad, conforme al artículo 48.2 de la Ley 39/2015, al no haberse dado audiencia a mi representado, por cuanto que no se agotaron los medios para dar conocimiento efectivo del procedimiento sancionador, constándole a la Administración un domicilio distinto, habiendo acudido a la vía ficticia de la notificación edictal, con lo que se produjo una situación de indefensión a mi representado.

Por otra parte, existen razones de justicia y equidad concurrentes, por cuanto mi representado, tan pronto como conoció la imposición de la sanción, procedió a solicitar y obtener la autorización administrativa por cuya carencia había sido sancionado, de manera que ha quedado sin objeto la sanción impuesta.

Por último, el acto de revocación en modo alguno constituiría una dispensa o exención no permitida por las leyes, ni incurriría en vulneración alguna del principio de igualdad, interés público o del ordenamiento jurídico, puesto que se dan circunstancias que justifican el ejercicio de la potestad de revocación en el caso contemplado, tal como se ha expuesto.

Por estos motivos, solicito de la Administración que dicte resolución por la que se revoque el acto administrativo de fecha [FECHA], dejándolo sin efecto.

Por todo lo expuesto, SOLICITO que tenga por presentado este escrito y los documentos acompañados, y, en su virtud y tras los trámites legales, acuerde la revocación de la resolución dictada por esa Administración de fecha [FECHA] dejándola sin efecto.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].Firmado ÓRGANO, UNIDAD O CARGO ADMINISTRATIVO AL QUE SE DIRIGE EL ESCRITO
