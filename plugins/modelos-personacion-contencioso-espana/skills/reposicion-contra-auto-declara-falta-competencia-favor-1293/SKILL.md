---
name: reposicion-contra-auto-declara-falta-competencia-favor-1293
description: "Redacta el escrito «Reposición contra el auto que declara falta de competencia a favor de la Audiencia Nacional» (formulario 1293 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra el auto que declara falta de competencia a favor de la Audiencia Nacional

> Formulario 1293 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en reseñados, notificado a esta parte el»; «…a Nacional por ser el acto o disposición»; «…dictado»; «…dictado [COMPLETAR] y, por consiguiente,»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ: Adjunto acompaño justificante de la realización de un depósito de 25 € en la "Cuenta de Depósitos y Co…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 79 de la Ley 29/1998
- art. 7.3 de la Ley 29/1998
- art. 11 de la Ley 29/1998
- art. 7.2 de la Ley 29/1998
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

### Formulario 1293 · Reposición contra el auto que declara falta de competencia a favor de la Audiencia Nacional

- Año del modelo: 2008
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 1 párrafos opcionales señalados; 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SALA DE LO CONTENCIOSO ADMINISTRATIVO DE LA AUDIENCIA NACIONAL

(SECCIÓN Nº [NÚMERO])

AUTOS DE RECURSO CONTENCIOSO ADMINISTRATIVO NÚMERO [NÚMERO]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], parte actora en el presente recurso contencioso administrativo, representación que tengo debidamente acreditada en los autos, por el presente escrito, como mejor proceda en derecho,

DIGO

Que, siguiendo instrucciones de mi principal, en tiempo y forma, vengo a interponer recurso de reposición, al amparo del artículo 79 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, contra el Auto de [FECHA], dictado por esa Sala en los autos de recurso al margen reseñados, notificado a esta parte el [COMPLETAR], en los que esta representación figura en la posición procesal de actora, resolución aquélla por la que la Sala declara, con fundamento en el art. 7.3 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativo (en adelante, LJCA), su falta de competencia, impugnación que sostengo con el siguiente fundamento:

ÚNICO

La Sala de lo Contencioso Administrativo de la Audiencia Nacional es la competente para la tramitación y conocimiento del recurso interpuesto por esta parte, según cabe deducir del art. 11 de la Ley 29/1998, de 13 de julio, y dado en principio de improrrogabilidad de las normas atributivas de competencia recogido en el art. 7.2 de la Ley 29/1998, de 13 de julio.

Más concretamente, esta parte sostiene la competencia de esa Sala de lo Contencioso Administrativo de la Audiencia Nacional por ser el acto o disposición [COMPLETAR] dictado [COMPLETAR] y, por consiguiente, [COMPLETAR].

Subsidiariamente, esta parte solicita que la Sala proceda en los términos previstos en el art. 7.3 de la Ley 29/1998, de 13 de julio, esto es, acuerde su incompetencia por Auto y remita las actuaciones al órgano de la Jurisdicción que estime competente, para que ante él siga el curso de proceso.

Por lo expuesto,

SUPLICO de esa Excma. Sala

que admita el presente escrito con las copias que se acompañan, tenga por interpuesto en tiempo y forma recurso de reposición contra el Auto de [FECHA], por el que se acordaba la falta de competencia de la Sala de lo Contencioso Administrativo de la Audiencia Nacional para el conocimiento del litigio, dé traslado de este escrito a las demás partes personadas por término común de tres días, y, transcurrido el citado plazo, dicte Auto por el que anule la resolución impugnada, declare su competencia y acuerde la continuación por sus trámites de los presentes autos.

[OPCIONAL — incluir si procede]

OTROSÍ: Adjunto acompaño justificante de la realización de un depósito de 25 € en la "Cuenta de Depósitos y Consignaciones" de ese Órgano Jurisdiccional, previo al presente recurso, conforme a lo previsto en la DA 15ª de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial.

Es Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
