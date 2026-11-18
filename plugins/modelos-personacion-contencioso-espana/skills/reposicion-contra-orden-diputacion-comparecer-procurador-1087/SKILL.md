---
name: reposicion-contra-orden-diputacion-comparecer-procurador-1087
description: "Redacta el escrito «Reposición contra la orden a la Diputación de comparecer con procurador (órganos colegiados)» (formulario 1087 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra la orden a la Diputación de comparecer con procurador (órganos colegiados)

> Formulario 1087 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en reseñados, notificado a esta parte el»; «…de»

## Elecciones que hay que hacer

- el Auto / la providencia

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ: Esta entidad local se encuentra exenta de la constitución del depósito para recurrir regulado en la DA…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 551.3 de la Ley 6/1985
- art. 54.4 del Real Decreto Legislativo 781/1986
- art. 221.2 del Real Decreto 2568/1986
- artículo 79 de la Ley 29/1998
- art. 45.3 de la LJCA
- art. 23.2 de la LJCA
- art. 551.3 de la Ley Orgánica 6/1985

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

### Formulario 1087 · Reposición contra la orden a la Diputación de comparecer con procurador (órganos colegiados)

- Año del modelo: 2008
- Revisión 17-11-2026: 2 desplegables convertidos en elección en blanco; 1 párrafos opcionales señalados; 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AUTOS DE RECURSO NÚMERO [Nº DE PROCEDIMIENTO]

D./Dña. [NOMBRE Y APELLIDOS], Letrado/a Asesor/a de la Excma. Diputación Provincial de [LOCALIDAD], cuya representación ostento al amparo de los arts. 551.3 de la Ley 6/1985, de 1 de julio, del Poder Judicial, art. 54.4 del Real Decreto Legislativo 781/1986, de 18 de abril, Texto Refundido de Disposiciones Vigentes en materia de Régimen Local y art. 221.2 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Entidades Locales, actuando en nombre y representación de la misma, por el presente escrito, comparezco ante la Sala y DIGO

Que, siguiendo instrucciones de mi principal, en tiempo y forma, vengo a interponer recurso de reposición al amparo del artículo 79 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, contra [ELEGIR: el Auto / la providencia] de fecha [FECHA], dictado/a por esa Sala en los autos de recurso al margen reseñados, notificado a esta parte el [COMPLETAR], resolución aquélla por la que, con fundamento en el art. 45.3 de la LJCA/98, se requiere a esta parte para subsanar supuestos defectos ocurridos en su comparecencia, y más concretamente que ésta no se produjera a través de Procurador, conforme parece ordenar el art. 23.2 de la LJCA/98, ya que la expresada comparecencia se efectúa ante un órgano jurisdiccional colegiado, impugnación que sostengo con el siguiente fundamento:

PRIMERO.- El art. 551.3 de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial, dispone que la representación y defensa en juicio de los entes locales corresponderá a los letrados que sirvan en los Servicios Jurídicos de los mismos, salvo que designen abogado colegiado que les represente y defienda.

Asimismo, el art. 221.2 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Entidades Locales, dispone que, de acuerdo con lo establecido en el art. 54.4 del Real Decreto Legislativo 781/1986, de 18 de abril y en la LOPJ, la representación y defensa en juicio de los entes locales corresponderá a los letrados que sirvan en los Servicios Jurídicos de los mismos, salvo que designen Abogado colegiado que les represente y defienda.

Por último, el art. 54.4 del Real Decreto Legislativo 781/1986, de 18 de abril, Texto Refundido de las Disposiciones Vigentes en Materia de Régimen Local, dice que, en cuanto a la representación y defensa en juicio de las entidades locales, se estará a lo dispuesto por la Ley Orgánica del Poder Judicial.

SEGUNDO.- Es de notar que en los preceptos relatados se atribuye a los referidos letrados de los servicios jurídicos de la Diputación Provincial no sólo su defensa en juicio, sino también su «representación» procesal; de suerte que no cabe sino concluir que las citadas normas articulan un régimen especial, oponible al general del 23.2 de la LJCA/98, que permite a las Diputaciones Provinciales la comparecencia en juicio sin la necesidad de la mediación de aquel profesional. De la aplicación de tales preceptos especiales deriva, pues, la conclusión de que las Corporaciones Locales, entre las que se cuenta esta Diputación Provincial, pueden comparecer por medio de sus servicios jurídicos propios, en cuyo caso, aunque lo hagan ante órganos colegiados, no será preceptiva la intervención de Procurador. Y no obsta, por último, a la aplicación de las normas especiales ya dichas, el hecho de que la regla general establecida en el art. 23.2 de la Ley Reguladora de la Jurisdicción Contencioso Administrativa sea posterior en el tiempo a los preceptos de cobertura antes citados (lo que pudiera hacer pensar en una unificación del régimen de representación y en una abrogación de aquellas especialidades), pues, además de que no existe derogación alguna de carácter expreso en la Ley, en el propio 24 de la LJCA/98 se establece, en lo que ahora interesa, que la representación y defensa de las Administraciones Públicas se rige por lo dispuesto en la Ley Orgánica del Poder Judicial. En suma, queda clara en este último precepto la voluntad del legislador de mantener aquel régimen especial de representación, frente a cualquier otra interpretación contraria.

Por ello, esta parte estima que no se ajusta a derecho la resolución jurisdiccional impugnada en reposición por lo que solicita su anulación.

Por lo expuesto,

SUPLICO la Sala

que admita el presente escrito con las copias que se acompañan, tenga por interpuesto en tiempo y forma recurso de reposición contra [ELEGIR: el Auto / la providencia] de [COMPLETAR], por el que se acordaba la comparecencia de esta Diputación Provincial a través de Procurador, dé traslado de las copias de este escrito a las demás partes personadas por término común de tres días, y, transcurrido el citado plazo, dicte Auto por el que anule la resolución impugnada y tenga al letrado de los servicios jurídicos de la Diputación como comparecido en su defensa y representación.

[OPCIONAL — incluir si procede]

OTROSÍ: Esta entidad local se encuentra exenta de la constitución del depósito para recurrir regulado en la DA 15ª de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial.

Es Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
