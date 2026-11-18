---
name: conflicto-competencia-territorial-entre-organos-negativo-1233
description: "Redacta el escrito «Conflicto de competencia territorial entre órganos (negativo)» (formulario 1233 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conflicto de competencia territorial entre órganos (negativo)

> Formulario 1233 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] Nº
- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ue esta representación se opone a que el»; «…resente recurso procede anteriormente de»; «…, el cual lo remitió a ese»; «…rmuló alegaciones sobre dicho extremo el»; «…, y las demás en fecha/as»; «…conferido, respetuosamente estima que el»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 14 de la LJCA
- art. 60.1 de la Ley 1/2000
- art. 4 de la Ley 1/2000
- art. 60.2 de la Ley 1/2000
- art. 4 Ley 1/2000

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

### Formulario 1233 · Conflicto de competencia territorial entre órganos (negativo)

- Año del modelo: 2008
- Revisión 17-11-2026: 11 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]
AL TRIBUNAL

AUTOS DE RECURSO Nº [Nº DE PROCEDIMIENTO]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], representación que tengo acreditada en autos, por el presente escrito, como mejor proceda en derecho, comparezco y, de acuerdo a lo establecido en el art. 14 de la LJCA y art. 60.1 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, aplicable supletoriamente al Orden Jurisdiccional Contencioso Administrativo conforme al art. 4 de la Ley 1/2000, de 7 de enero y de acuerdo a la DF 1ª de la LJCA, DIGO

Que ese órgano jurisdiccional ha dado traslado a esta parte, en providencia de fecha [FECHA], para que formule alegaciones en relación con su competencia territorial.

Que esta representación se opone a que el [COMPLETAR] acuerde de oficio su propia incompetencia, lo que parece ser su propósito a tenor del trámite alegatorio que acaba de iniciar, pues no se debe olvidar que el presente recurso procede anteriormente de [COMPLETAR], el cual lo remitió a ese [COMPLETAR] por Auto de [FECHA], tras haberse producido la audiencia de las partes sobre dicho particular. En concreto, como cabe ver de lo actuado, esta representación formuló alegaciones sobre dicho extremo el [COMPLETAR], y las demás en fecha/as [COMPLETAR].

El art. 60.2 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, aplicable supletoriamente al Orden Jurisdiccional Contencioso Administrativo como su propio art. 4 Ley 1/2000, de 7 de enero establece, en un mandato que es luego ratificado por la DF 1ª de la LJCA, dispone que si la decisión de inhibición de un tribunal por falta de competencia territorial se hubiere adoptado en virtud de declinatoria o con audiencia de todas las partes, el tribunal al que se remitieren las actuaciones estará a lo decidido y no podrá declarar de oficio su falta de competencia territorial.

Pues bien, esa circunstancia de la existencia de previa audiencia a las partes es la concurrente en el presente caso, sin que, a juicio de esta parte, haya obstáculo alguno a la aplicación supletoria de la Ley rituaria civil, ya que no existe precepto paralelo en la Rectora del Presente Orden Jurisdiccional y el precepto que se juzga aplicable supletoriamente no pugna con las instituciones procesales contencioso administrativos.

Por todo ello, esta parte, evacuando el traslado conferido, respetuosamente estima que el [COMPLETAR] al que tiene el honor de dirigirse no podrá acordar de oficio su propia incompetencia.

Es de justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
