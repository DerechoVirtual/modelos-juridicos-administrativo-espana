---
name: reposicion-contra-auto-incompetencia-territorial-1224
description: "Redacta el escrito «Reposición contra el auto de incompetencia territorial» (formulario 1224 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra el auto de incompetencia territorial

> Formulario 1224 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, Procurador/a de los Tribunales»; «…, de 7 de enero, de Enjuiciamiento Civil»; «…ritorial, declarando corresponder ésta a»; «…Auto, que fue notificado a esta parte el»; «…administrativo proceden anteriormente de»; «…, el cual, a su vez, lo remitió a ese»; «…risdiccionales sobre dicho particular el»; «…, y las demás partes en fecha/as»; «…rativos. Por lo expuesto, SUPLICO de ese»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ: Adjunto acompaño justificante de la realización de un depósito de 25 € en la "Cuenta de Depósitos y Co…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 60.2 de la Ley 1/2000
- artículo 4 de la Ley 1/2000
- artículo 79 de la Ley 29/1998
- Ley Orgánica 6/1985

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

### Formulario 1224 · Reposición contra el auto de incompetencia territorial

- Año del modelo: 2008
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 1 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Autos de recurso contencioso administrativo nº [Nº DE PROCEDIMIENTO]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales [COMPLETAR], actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], representación que tengo acreditada en autos, por el presente escrito, como mejor proceda en derecho, comparezco y, de acuerdo a lo establecido en el art. 60.2 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil [COMPLETAR], aplicable supletoriamente al Orden Jurisdiccional Contencioso Administrativo conforme al artículo 4 de la Ley 1/2000, de 7 de enero y de acuerdo a la DF 1ª de la Ley 29/1998, Reguladora de la Jurisdicción Contencioso Administrativa (en adelante, LJCA), DIGO

Que por ese Tribunal se ha dictado Auto de fecha [FECHA] por el que se declara su incompetencia territorial, declarando corresponder ésta a [COMPLETAR] y ordenando la remisión de los autos al órgano competente.

Siguiendo por ello instrucciones de mi principal, en tiempo y forma, vengo a interponer recurso de reposición, al amparo del artículo 79 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, contra el referido Auto, que fue notificado a esta parte el [COMPLETAR]; impugnación que sostengo con el siguiente fundamento:

ÚNICO

No se debe olvidar que los presentes autos de recurso contencioso administrativo proceden anteriormente de [COMPLETAR], el cual, a su vez, lo remitió a ese [COMPLETAR] por Auto de [FECHA], tras haberse producido allí la audiencia de las partes sobre dicho particular.

En concreto, como cabe ver de lo actuado, esta representación formuló alegaciones en los primeros autos Jurisdiccionales sobre dicho particular el [COMPLETAR], y las demás partes en fecha/as [COMPLETAR].

El art. 60.2 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, dispone que si la decisión de inhibición de un tribunal por falta de competencia territorial se hubiere adoptado en virtud de declinatoria o con audiencia de todas las partes, el tribunal al que se remitieren las actuaciones estará a lo decidido y no podrá declarar de oficio su falta de competencia territorial.

Pues bien, esa circunstancia de la existencia de previa audiencia a las partes es la concurrente en el presente caso, sin que, a juicio de esta parte, haya obstáculo alguno a la aplicación supletoria de la Ley rituaria civil, ya que no existe precepto paralelo en la Rectora del Presente Orden Jurisdiccional y el precepto que se juzga aplicable supletoriamente no pugna con las instituciones procesales contencioso administrativos.

Por lo expuesto,

SUPLICO de ese [COMPLETAR]

que admita el presente escrito, con las copias que se acompañan, tenga por interpuesto en tiempo y forma recurso de reposición contra el Auto de [FECHA], por el que se acordaba su falta de competencia territorial, dé traslado de este escrito a las demás partes personadas, por término común de tres días, y, transcurrido el citado plazo, dicte Auto por el que anule la resolución impugnada, declare su competencia y acuerde la continuación por sus trámites de los presentes autos.

[OPCIONAL — incluir si procede]

OTROSÍ: Adjunto acompaño justificante de la realización de un depósito de 25 € en la "Cuenta de Depósitos y Consignaciones" de ese Órgano Jurisdiccional, previo al presente recurso, conforme a lo previsto en la Disposición Adicional Decimoquinta, apartado 4, de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial.

Es Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
