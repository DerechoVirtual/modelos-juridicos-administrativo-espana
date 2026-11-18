---
name: inadmitir-recurso-alzada-contra-resolucion-expresa-34
description: "Redacta el escrito «Inadmitir el recurso de alzada contra resolución expresa» (formulario 34 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inadmitir el recurso de alzada contra resolución expresa

> Formulario 0034 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] FECHA (3 veces)
- [ ] ÓRGANO
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] ÓRGANO O PERSONA
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…y domicilio en [LOCALIDAD], actuando»; «… fecha [FECHA] y notificada por medio de»; «…, el día [FECHA], en virtud de la cual»; «…esolver el recurso interpuesto, dado que»; «… remitirá directamente las actuaciones a»; «…ará esta circunstancia a los interesados»; «…un acto susceptible de recurso, dado que»; «… la resolución recurrida, concretamente,»; «… manifiestamente de fundamento, dado que»; «…itir el recurso al órgano administrativo»; «…inadmisión del recurso al interesado. En»; «…, a de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 14 de la Ley 40/2015
- art. 116.a) Ley 39/2015

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

### Formulario 0034 · Inadmitir el recurso de alzada contra resolución expresa

- Año del modelo: 2022
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Datos objetivos y subjetivos

Expediente:

Órgano administrativo, centro o unidad administrativa:

Se interpuso recurso administrativo de alzada en fecha [FECHA] ante [ÓRGANO] por parte de D./D.ª [NOMBRE Y APELLIDOS], con DNI [DNI/NIE] y domicilio en [LOCALIDAD], actuando [COMPLETAR], contra la resolución dictada por [ÓRGANO O PERSONA] en fecha [FECHA] y notificada por medio de [COMPLETAR], el día [FECHA], en virtud de la cual [COMPLETAR],

Consideraciones jurídicas

Falta de competencia. Carece de competencia para resolver el recurso interpuesto, dado que [COMPLETAR]. A este respecto, y conforme establece el artículo 14 de la Ley 40/2015, este órgano administrativo remitirá directamente las actuaciones a [COMPLETAR], por considerarlo competente para conocer del recurso de alzada interpuesto, y se notificará esta circunstancia a los interesados [COMPLETAR].

No susceptible de recurso. La resolución recurrida no es un acto susceptible de recurso, dado que [COMPLETAR].

Extemporaneidad. Ha trascurrido el plazo para la interposición del recurso, dado que ha trascurrido más de 1 mes desde la fecha de la notificación de la resolución recurrida, concretamente, [COMPLETAR]. El transcurso del plazo sin haber interpuesto el recurso de alzada, hace que la resolución o acto se convierta en consentido y firme. Contra un acto consentido y firme no puede interponerse recurso de alzada, ni tampoco ningún otro en vía administrativa, salvo el recurso extraordinario de revisión, en los casos en que proceda, y sin perjuicio de la revisión de oficio. El recurso interpuesto fuera de plazo debe inadmitirse por extemporáneo.

Carencia de fundamento. Carece manifiestamente de fundamento, dado que [COMPLETAR].

Conclusión

En atención a las consideraciones anteriores se concluye:

Primero: La inadmisión del recurso administrativo de alzada en virtud del art. 116.a) Ley 39/2015, de 1 de octubre.

Segundo: Remitir el recurso al órgano administrativo [COMPLETAR]

Tercero: Notificar la Resolución de inadmisión del recurso al interesado.

En [COMPLETAR], a de [COMPLETAR].

Firmado:
