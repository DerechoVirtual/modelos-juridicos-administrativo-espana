---
name: alegaciones-ante-declinatoria-jurisdiccion-contratos-649
description: "Redacta el escrito «Alegaciones ante declinatoria de jurisdicción en contratos públicos» (formulario 649 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones ante declinatoria de jurisdicción en contratos públicos

> Formulario 0649 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] FECHA
- [ ] DESCRIBIR

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5.1 de la Ley 29/1998
- artículos 5 y 10 de la LJCA
- Ley 9/2017

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

### Formulario 0649 · Alegaciones ante declinatoria de jurisdicción en contratos públicos

- Año del modelo: 2010
- Revisión 17-11-2026: 3 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

Que el pasado [FECHA] me ha sido notificada la providencia dictada por la Sala el día anterior, por la que se hace saber a las partes la posibilidad de que se aprecie de oficio la falta de jurisdicción, concediéndosenos un plazo común de 10 días para alegar lo procedente y, dentro de dicho plazo evacuo el trámite conferido en base a las siguientes.

ALEGACIONES

PRIMERA. De conformidad con lo previsto en el artículo 5.1 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, esta jurisdicción es improrrogable, y en su artículo 2 establece que en ella se conocerá de las cuestiones que se susciten en relación con «b) Los contratos administrativos y los actos de preparación y adjudicación de los demás contratos sujetos a la legislación de contratación de las Administraciones Públicas».

SEGUNDA. Como quiera que el contrato público que se ha suscrito es relativo a [DESCRIBIR], cuyo contenido obligacional comporta, entre otros, hemos de entender, en base a lo establecido en los artículos 18 y siguientes de la Ley 9/2017, de Contratos del Sector Público, que se trata de un contrato mixto, con carácter administrativo, y con un régimen jurídico eminentemente administrativo, por lo que, de conformidad con lo previsto en el artículo 27 de la citada Ley 9/2017, será competencia del órgano jurisdiccional contencioso-administrativo la resolución de controversias que surjan entre las partes en relación a este tipo de contratos.

Por ello, y en atención a lo dispuesto precisamente en los artículos 5 y 10 de la LJCA, corresponde a la Jurisdicción Contencioso-administrativa y a las Salas de lo Contencioso Administrativo de los Tribunales Superiores de Justicia el conocimiento de los recursos que se deduzcan en relación con estos asuntos, y es por ello por lo que

A LA SALA SUPLICO: Que, teniendo por presentado este escrito, tenga por evacuado el trámite conferido y, en consecuencia, se sirva declarar la competencia de la Sala para conocer del recurso interpuesto, ordenándose la continuación del procedimiento por los trámites preceptivos.

Lugar, Fecha (día/mes/año) y Firma.
