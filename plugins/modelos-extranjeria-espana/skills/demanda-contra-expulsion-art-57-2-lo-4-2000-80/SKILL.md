---
name: demanda-contra-expulsion-art-57-2-lo-4-2000-80
description: "Redacta el escrito «Demanda contra la expulsión del art. 57.2 LO 4/2000» (formulario 80 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra la expulsión del art. 57.2 LO 4/2000

> Formulario 0080 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSI DIGO que de conformidad con lo dispuesto en el artículo 40 y ss. de la LJC-A, se considera que la cuant…
- SEGUNDO OTROSI DIGO, que según se ha expuesto en el fundamento X, de esta demanda, concurren los requisitos pa…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 57.2 de la LO 4/2000
- art. 8.4 LJCA
- art. 14 de la LJCA
- art. 7.3 de la LJCA
- art. 19.1.a) de la LJCA
- artículo 57.2 de la Ley Orgánica 4/2000
- art. 240 del Código Penal
- art. 550 del Código Penal
- art. 379 del Código Penal
- art. 48.1 de la Ley 39/2015
- art. 53.1.a) de la LO 4/2000
- arts. 52 a 54 de la Ley Orgánica 4/2000
- art. 135 de la LJCA

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

### Formulario 0080 · Demanda contra la expulsión del art. 57.2 LO 4/2000

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 párrafos opcionales señalados; 5 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 6 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] (QUE POR TURNO CORRESPONDA)

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Abogado/a, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según se acredita mediante designación del Ilustre Colegio de Abogados de Madrid (documento nº 1), ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que de acuerdo con lo establecido en los arts. 78 y siguientes de la LJCA, formalizo la siguiente DEMANDA basándome en los siguientes

HECHOS

Primero. El día [FECHA] fue notificada al demandante resolución dictada por la Subdelegación del Gobierno en Palencia por la que se decretaba su expulsión del territorio español y la prohibición de entrada en el mismo por un período de 10 años. La resolución se dictó en aplicación de lo establecido en el art. 57.2 de la LO 4/2000 (Ley de Extranjería).

Se adjunta la resolución recurrida como doc. Nº 2.

FUNDAMENTOS DE DERECHO

I. Competencia.

La competencia para conocer del recurso corresponde al Tribunal de Instancia (Sección de lo Contencioso-Administrativo), según lo dispuesto en el art. 8.4 LJCA.

Al encontrarse el demandante internado en el Centro de Internamiento de Extranjeros (C.I.E.) de Madrid, es competente el Tribunal de Instancia (Sección de lo Contencioso-Administrativo) de Madrid, en virtud de lo establecido en el art. 14 de la LJCA. Se adjunta certificado del director del C.I.E. acreditando este extremo como doc. Nº 3.

No obstante, para el supuesto de que no se entendiera así, procederá que se remitan las actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en el art. 7.3 de la LJCA.

II. Legitimación.

Está legitimado D. Nasser Hasnaoui en virtud de lo establecido en el art. 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

III. Representación.

Se acredita la representación del recurrente por parte del letrado firmante mediante documento suscrito por ambos partes y por el Director del CIE de Madrid.

Se adjunta con el presente escrito documento de otorgamiento de representación y designación de letrado firmado por el demandante, el letrado firmante y el director del CIE.

IV. Plazo de formulación de la demanda.

Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

V. Costas.

Costas. En lo relativo a la imposición de costas, es de aplicación el art. 139.1 de la LJC-A, por lo que, en caso de oponerse al presente recurso, deberán imponerse las costas del presente proceso a la Administración demandada.

VI. Procedimiento.

La presente demanda debe ser tramitada por el Procedimiento Abreviado, de acuerdo con lo estipulado en los arts. 78 y siguientes de la LJCA, dado que la resolución recurrida pertenece al ámbito de la extranjería.

VII. Requisitos.

Falta de concurrencia de los requisitos del art. 57.2 de la LO 4/2000 según jurisprudencia del TS.

La resolución se ha dictado por considerar que en el recurrente se encontraba en el supuesto del art. 57.2 de la LO 4/2000 [NOTA DE REVISIÓN: El texto entrecomillado («Asimismo, constituirá causa de expulsión...») es el art. 57.2 de la LO 4/2000, no del reglamento. Su desarrollo reglamentario vigente es el art. 241.1 RD 1155/2024 (antes art. 242.1 RD 557/2011). Fuente: LO 4/2000, art. 57.2 (BOE-A-2000-544); RD 1155/2024, art. 241.1 (BOE-A-2024-24099).], que establece que

«Asimismo, constituirá causa de expulsión, previa tramitación del correspondiente expediente, que el extranjero haya sido condenado, dentro o fuera de España, por una conducta dolosa que constituya en nuestro país delito sancionado con pena privativa de libertad superior a un año, salvo que los antecedentes penales hubieran sido cancelados.»

Ante las diferentes interpretaciones judiciales en la aplicación de este precepto, la Sentencia del Tribunal Supremo núm. 893/2018, de 31 de mayo, recurso 1321/2017 (Sala de lo Contencioso-Administrativo Sección Quinta, Sentencia), ha establecido cual debe ser la interpretación correcta del mismo, estableciendo en su Fundamento Jurídico Décimo que

«consideramos como interpretación más acertada del artículo 57.2 de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y libertades de los extranjeros en España y su integración social (LOEX) ---y, en concreto, su inciso "delito sancionado con pena privativa de libertad superior a un año" --- debe ser interpretado en el sentido de que el precepto se refiere a la pena prevista en abstracto en el Código Penal para el delito correspondiente, si bien, sólo en aquellos supuestos en los que la totalidad de la pena establecida en el Código Penal sea "una pena privativa de libertad superior a un año", esto es, excluyendo aquellos delitos en los que, con independencia de máximo previsto para la pena de privación de libertad, el mínimo, igualmente previsto, es de un año o menos.»

Y como vemos en la resolución recurrida, ninguno de los delitos por los que fue condenado el recurrente es sancionado con una pena de prisión cuyo mínimo sea de más de un año de privación de libertad, ya que la práctica totalidad de las condenas lo fueron por robos con fuerza en las cosas, cuya condena es de privación de libertad de uno a tres años (art. 240 del Código Penal), es decir, que según la interpretación del Tribunal Supremo.

Igual ocurriría con las otras condenas citadas en la resolución, las cuales se dictaron como consecuencia de un delito de desobediencia (castigado en el art. 550 del Código Penal con la pena penas de prisión de uno a cuatro años y multa de tres a seis meses si el atentado fuera contra autoridad y de prisión de seis meses a tres años en los demás casos) y otro de conducción bajo la influencia de bebidas alcohólicas (castigado en art. 379 del Código Penal con pena de prisión de tres a seis meses o con la de multa de seis a doce meses o con la de trabajos en beneficio de la comunidad de treinta y uno a noventa días).

Por tanto, ninguna de las condenas mencionadas en la resolución recurrida cumpliría los requisitos que exige el Tribunal Supremo por lo que debe considerarse que concurre una causa de anulabilidad de la resolución recurrida según lo dispuesto en el art. 48.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Pública

VIII. Infracciones y sanciones.

Se hace mención en la resolución recurrida a la concurrencia del supuesto del art. 53.1.a) de la LO 4/2000, artículo que se refiere a la comisión de infracciones en materia de extranjería y que puede llevar a la imposición de una sanción de expulsión.

Sin embargo, en el escrito se expone claramente que «la expulsión se impone en aplicación del art. 57.2 de la L.O. 4/2000» y se menciona reiteradamente que no nos encontramos ante una sanción impuesta por una infracción administrativa.

Por tanto, si se estimaba que lo procedente hubiera sido incoar un procedimiento sancionador por la infracción del precepto mencionado, así se debería haber hecho expresamente, lo que hubiera excluido la aplicación en el procedimiento sancionador del art. 57.2.

Tampoco es relevante en este caso la consideración del recurrente como un «riesgo para el orden público» o la mención al «riesgo de incomparecencia» ya que estos son criterios que sólo deben ser tenidos en cuenta para la aplicación del procedimiento preferente en un procedimiento sancionador, lo que, por otra parte, resulta contradictorio con la insistencia de la resolución recurrida de que no estamos ante una sanción.

Estas, pues, son circunstancias que podrían ser tenidas en cuenta en un procedimiento sancionador incoado por alguna de las infracciones tipificadas en los arts. 52 a 54 de la Ley Orgánica 4/2000 como motivadoras de la imposición de la pena de expulsión en lugar de la de multa, pero para ello debería incoarse el oportuno procedimiento sancionador por alguno de los trámites regulados en los arts. 63 y 63 bis de dicha Ley Orgánica, cosa que hasta el momento no se ha hecho, y que en todo caso no debería tener influencia alguna en el procedimiento que ha dado lugar a la resolución ahora recurrida.

IX. Supuesto.

En el presente caso concurren los supuestos para la suspensión cautelar de la ejecución de la orden de expulsión contra el recurrente, cuales son:

La ejecución de dicha medida supondría perder la finalidad del recurso, pues una eventual sentencia estimatoria sería de imposible ejecución una vez expulsado el recurrente de España.

No se aprecia un daño o perjuicio al interés general en caso de adoptarse dicha medida, pues en caso de que la sentencia no fuera estimatoria siempre podría instarse posteriormente la ejecución de la sanción.

Nos encontramos ante un supuesto de fumus boni iuris, ya que de la resolución recurrida se desprende que en este caso es plenamente aplicable la Sentencia del Tribunal Supremo que hemos citado en el fundamento anterior.

Existe una acreditada situación de arraigo en España del recurrente, donde ha residido hace más de diez años, varios de ellos como titular de autorización de residencia y trabajo en España, siendo éste uno de los criterios determinantes a la hora de otorgar la medida cautelar solicitada.

En este caso, concurren además circunstancias de especial urgencia, ya que el recurrente se encuentra internado en el C.I.E. de Madrid, pendiente de que se ejecute la expulsión decretada en los próximos días, por lo que es de aplicación lo establecido en el art. 135 de la LJCA.

Por lo expuesto SUPLICO AL TRIBUNAL que, en atención a los hechos y fundamentos de derecho expuestos, y previos los trámites procesales oportunos, dicte sentencia por la que se anule la resolución recurrida, condenándose en costas a la Administración demandada.

Por ser Justicia que pido en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

OTROSI DIGO que de conformidad con lo dispuesto en el artículo 40 y ss. de la LJC-A, se considera que la cuantía del presente recurso es indeterminada.

En su virtud, SUPLICO AL TRIBUNAL que se establezca la cuantía del presente recurso como indeterminada.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSI DIGO, que según se ha expuesto en el fundamento X, de esta demanda, concurren los requisitos para que se adopte en la vía contencioso-administrativa la medida cautelar urgente de suspensión de la ejecución de la expulsión del interesado del territorio español por lo que

SUPLICO AL TRIBUNAL que se adopte la MEDIDA CAUTELAR URGENTE del art. 135 de la LJCA de suspensión de la ejecución de la orden de expulsión del interesado del territorio español durante la tramitación del recurso.

Fdo:

Colegiado:
