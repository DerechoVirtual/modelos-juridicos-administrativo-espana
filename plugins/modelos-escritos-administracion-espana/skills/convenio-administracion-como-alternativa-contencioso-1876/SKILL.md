---
name: convenio-administracion-como-alternativa-contencioso-1876
description: "Redacta el escrito «Convenio con la Administración como alternativa al contencioso» (formulario 1876 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio con la Administración como alternativa al contencioso

> Formulario 1876 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.
- **Criterio de Hacienda y del TEAC** → `buscar_consultas_hacienda` → `leer_consulta_hacienda`; `buscar_doctrina_teac` → `leer_resolucion_teac`.

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

- [ ] LUGAR
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] ÓRGANO
- [ ] IMPORTE (3 veces)
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, Consejero de»; «…, en la representación que ostenta de»; «…acuerdo MANIFIESTAN Que la Consejería de»; «…ia exclusiva en materia de fomento de la»; «…según el artículo»; «…, tiene competencia en materia de»; «…, es propietario de»; «…y del inmueble correspondiente a»; «…acometer actuaciones de rehabilitación y»; «…dministración está obligada en virtud de»; «…nimiento, conservación y recuperación de»; «… primera, la aportación de la Consejería»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 21.1.b) de la Ley 7/1985
- art. 25.2 de la Ley 7/1985
- art. 29.1 de la Ley 29/1998
- arts. 47 de la Ley 40/2015
- art. 86 de la Ley 39/2015

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

### Formulario 1876 · Convenio con la Administración como alternativa al contencioso

- Año del modelo: 2004
- Revisión 17-11-2026: 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de convenio de colaboración firmado por las partes, que recoge el acuerdo al que llegan la Administración inactiva y la persona afectada por el incumplimiento de la prestación, evitando así el proceso contencioso-administrativo.

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE,

El/La excelentísimo/a señor/a D./Dña. [NOMBRE Y APELLIDOS], Consejero de [COMPLETAR], en la representación de la Comunidad Autónoma y especialmente facultada para este acto en virtud de acuerdo del Consejo de Gobierno de fecha

DE OTRA,

El/La excelentísimo/a señor/a D./Dña. [NOMBRE Y APELLIDOS], Alcalde-Presidente del Ayuntamiento de [LOCALIDAD], en representación de dicha Corporación, en virtud del art. 21.1.b) de la Ley 7/1985, de 2 de abril, Reguladora de las Bases de Régimen Local.

Y DE OTRA,

El/La señor/a D./Dña. [NOMBRE Y APELLIDOS], en la representación que ostenta de [COMPLETAR], según acredita mediante [ÓRGANO], de conformidad con la legislación vigente.

Todas las partes en la representación que ostentan, en ejercicio de las atribuciones que les están conferidas, y reconociéndose capacidad para formalizar el presente acuerdo

MANIFIESTAN

Que la Consejería de [COMPLETAR], tiene competencia exclusiva en materia de fomento de la [COMPLETAR] según el artículo [COMPLETAR] del Estatuto de Autonomía.

Que el Ayuntamiento de [LOCALIDAD], tiene competencia en materia de [COMPLETAR], según previene el art. 25.2 de la Ley 7/1985, de 2 de abril, Reguladora de las Bases de Régimen Local.

Que D./Dña. [NOMBRE Y APELLIDOS], es propietario de [COMPLETAR] y del inmueble correspondiente a [COMPLETAR] sobre el que es necesario acometer actuaciones de rehabilitación y [COMPLETAR], prestación concreta a la que esta Administración está obligada en virtud de [COMPLETAR], sin que resulte necesario ningún acto de aplicación.

Que en aplicación de lo previsto en el art. 29.1 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, en relación con lo dispuesto en el arts. 47 de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público, y el art. 86 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, y en el marco de las competencias respectivas, las partes firmantes concretan sus actuaciones en el presente Convenio de Colaboración, que se regirá por las siguientes

CLAUSULAS

Primera

Es objeto del presente Convenio la intervención para el mantenimiento, conservación y recuperación de [COMPLETAR], que seguidamente se describe:

Segunda

Para la realización de la actuación descrita en la cláusula primera, la aportación de la Consejería [COMPLETAR] será la siguiente:

Entrega a [COMPLETAR], beneficiario directo de esta prestación, de la cantidad de [IMPORTE] euros, con cargo al ejercicio presupuestario de [COMPLETAR], que deberá acreditar su ingreso en contabilidad y proceder a la realización de sus compromisos de colaboración justificándolo ante la Consejería mediante las correspondientes certificaciones de obra.

Por parte del Ayuntamiento de [LOCALIDAD], además de los compromisos que le corresponden en virtud de este convenio, se aportarán [IMPORTE] euros con cargo al ejercicio presupuestario del año en curso.

Por acuerdo de las partes, en función de las necesidades de ejecución de las obras proyectadas, se podrán realizar los ajustes de financiación que sean precisos para la correcta realización de las mismas.

Tercera

Las obras objeto del presente convenio se realizarán según el proyecto elaborado y aprobado al efecto por la Dirección General de [COMPLETAR], de acuerdo con la legislación vigente.

A [COMPLETAR] corresponde la contratación y ejecución de las obras referidas en el aludido proyecto así como la designación de la Dirección Técnica de las mismas y, en su caso, obtener las autorizaciones precisas para las obras en cuestión.

Cuarta

El coste total de las obras a que se refiere el presente convenio asciende a [IMPORTE] euros. El aumento de los gastos que por cualquier motivo pudiera derivarse del cumplimiento del presente convenio será, en todo caso, de cuenta de la parte que contrata las obras. En el supuesto de que se produjera una disminución de los gastos previstos, se reducirán proporcionalmente (en relación con su participación económica en el coste total previsto) las aportaciones de las partes, debiendo reintegrarse el remanente correspondiente a la dotación presupuestaria de la Consejería al Tesoro regional.

Quinta

Para el seguimiento de las actuaciones previstas se establece una Comisión integrada por dos representantes de cada una de las partes firmantes del Convenio. El Ayuntamiento remitirá a la Consejería de [COMPLETAR] las certificaciones de obras que al efecto se expedirán por el Director Facultativo de las mismas, y remitirá información detallada de las actuaciones realizadas a la Consejería de [COMPLETAR] en el plazo de diez días desde que se realicen.

Sexta

El Ayuntamiento acreditará la ejecución de la obra e inversión realizada, por medio de las certificaciones expedidas, según lo establecido en la legislación vigente, sin perjuicio de la posibilidad de que el destino de los fondos podrá ser comprobado en cualquier momento por los procedimientos generales de fiscalización y control de la Comunidad Autónoma, a tenor de la legalidad vigente reguladora de esta materia.

Séptima

En el caso de que el Ayuntamiento dejara de cumplir alguna de las cláusulas del presente Convenio deberá reintegrar el importe de la aportación recibida por la Comunidad Autónoma [COMPLETAR] en su totalidad, por cualquiera de los medios admitidos en Derecho.

Octava

La realización de las obras a que se refiere el presente convenio no eximirá de las autorizaciones administrativas que sean preceptivas en virtud de la legislación urbanística y protectora del patrimonio histórico español, sin perjuicio de lo establecido en la cláusula tercera.

Novena

El adjudicatario queda obligado a colocar en las obras un cartel indicador en el que figure de forma destacada que estas obras están realizadas en colaboración con la Comunidad Autónoma de acuerdo con las indicaciones que reciba desde la Consejería.

Décima

La Consejería se reserva la facultad de inspeccionar las obras o trabajos de restauración o adecuación, en cualquier momento a través del funcionario designado al efecto en la cláusula quinta y adoptar las medidas oportunas a la vista de la inspección.

Undécima

El presente Convenio tendrá vigencia hasta [COMPLETAR] y podrá resolverse por alguna de las siguientes causas: Expiración de su vigencia, incumplimiento de su contenido y mutuo acuerdo.

Duodécima

El presente Convenio tiene naturaleza administrativa, queda excluido de lo previsto en la legislación de contratos públicos, y el conocimiento de todas las cuestiones litigiosas que puedan surgir en torno a su interpretación, modificación, resolución y efectos, corresponderá a la Jurisdicción Contencioso-Administrativa.

Y para que así conste firman el presente Convenio de Colaboración, por triplicado ejemplar en el lugar y fecha indicados al principio.

Firmado: D./Dña. [NOMBRE Y APELLIDOS] 	Firmado: D./Dña. [NOMBRE Y APELLIDOS]

Firmado: D./Dña. [NOMBRE Y APELLIDOS]
