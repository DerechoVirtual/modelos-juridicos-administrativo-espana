---
name: personacion-demandado-recurso-lesividad-1140
description: "Redacta el escrito «Personación del demandado en recurso de lesividad» (formulario 1140 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Personación del demandado en recurso de lesividad

> Formulario 1140 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] IDENTIFICACIÓN
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (4 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (6 veces)
- [ ] FECHA (2 veces)
- [ ] ADMINISTRACIÓN RECURRENTE
- [ ] JUZGADO
- [ ] LUGAR

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 49.6 de la Ley 29/1998
- art. 21.1 b) de la LJCA

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

### Formulario 1140 · Personación del demandado en recurso de lesividad

- Año del modelo: 2008
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 1 bloques de alternativas señalados; 13 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL [IDENTIFICACIÓN] de Tribunal o Tribunal

AUTOS DE RECURSO NUMERO D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A] con domicilio social en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], representación que acredito mediante escritura de poder otorgada a mi favor:

[ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:]
— Mediante comparecencia electrónica, a través de la sede judicial electrónica e inscrito en el Registro Electrónico de Apoderamientos Judiciales, y que acredito mediante certificación de dicho Registro aportada como Documento n.º [NÚMERO], y que se puede acreditar mediante consulta automatizada orientada al dato, por parte del órgano judicial al cual tengo el honor de dirigirme.

Mediante comparecencia personal apud acta ante el/la Letrado/a de la Administración de Justicia de cualquier oficina judicial de [LOCALIDAD], posteriormente inscrito en el Registro Electrónico de Apoderamientos Judiciales, y que acredito mediante certificación de dicho Registro mediante certificación de dicho Registro aportada como Documento n.º [NÚMERO], y que se puede acreditar mediante consulta automatizada orientada al dato, por parte del órgano judicial al cual tengo el honor de dirigirme.

Mediante escritura de poder otorgada a mi favor, ante el Notario D./Dña. [NOMBRE Y APELLIDOS], con Notaría sita en [LOCALIDAD]. El poder se inscribió en el Registro Electrónico de Apoderamientos Judiciales, lo cual acredito mediante certificación de dicho Registro mediante certificación de dicho Registro aportada como Documento n.º [NÚMERO], y que se puede acreditar mediante consulta automatizada orientada al dato, por parte del órgano judicial al cual tengo el honor de dirigirme.

Bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], colegiado/a n.º [NÚMERO] del Ilustre Colegio de Abogados de .Ante ese órgano jurisdiccional comparezco y, como mejor proceda en derecho,

DIGO

Que por el órgano jurisdiccional a que tiene el honor de dirigirse, en fecha [FECHA] se ha procedido, conforme al art. 49.6 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso-Administrativa (en adelante, LJCA), al emplazamiento personal de mi principal en el recurso de lesividad interpuesto por [ADMINISTRACIÓN RECURRENTE], para que, en plazo de nueve días, comparezca en concepto de demandado en el citado recurso.

Que mi principal ostenta derechos o intereses legítimos que pueden resultar afectados por la estimación de las pretensiones de la Administración demandante, conforme al art. 21.1 b) de la LJCA.Es por ello por lo que, dentro del plazo de nueve días conferido, vengo a personarme en representación de mi principal en la posición procesal de demandado.

Por lo expuesto,

SUPLICO del [JUZGADO] o Sala que tenga por evacuado en tiempo y forma este escrito junto con el poder que lo acompaña, lo admita, y por ello me tenga por personado y parte en la condición de demandado en el recurso de lesividad más arriba expresado, entendiéndose a partir de este momento conmigo las sucesivas actuaciones.

Por ser de Justicia que pido [LUGAR], a [FECHA].

Firma de Abogado/a

Firma de Procurador/a
