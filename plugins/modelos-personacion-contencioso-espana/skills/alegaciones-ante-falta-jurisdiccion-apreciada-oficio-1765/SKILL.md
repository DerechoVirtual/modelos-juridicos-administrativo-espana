---
name: alegaciones-ante-falta-jurisdiccion-apreciada-oficio-1765
description: "Redacta el escrito «Alegaciones ante la falta de jurisdicción apreciada de oficio» (formulario 1765 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones ante la falta de jurisdicción apreciada de oficio

> Formulario 1765 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] LUGAR

## Elecciones que hay que hacer

- el Tribunal / la Sala
- corresponde / no corresponde
- AL TRIBUNAL / A LA SALA
- mantenga su jurisdicción / se declare la falta de jurisdicción

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5 de la Ley 29/1998
- art. 5.3 LJCA

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

### Formulario 1765 · Alegaciones ante la falta de jurisdicción apreciada de oficio

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 4 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 9 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de alegaciones de las partes respecto de la posible falta de jurisdicción apreciada de oficio por el órgano jurisdiccional, estableciendo que el recurso tiene por objeto una pretensión que sí corresponde conocer a la jurisdicción contencioso administrativa, o que corresponde a otro orden su conocimiento, solicitando así que se declare su jurisdicción o falta de jurisdicción para conocer del asunto.

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

A LA SALA
A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], en nombre de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tiene acreditada, en autos de recurso contencioso administrativo número [NÚMERO], que se sigue en ese órgano jurisdiccional, interpuesto por [ÓRGANO O PERSONA], contra la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], sobre, ante [ELEGIR: el Tribunal / la Sala] de lo Contencioso-Administrativo de [LOCALIDAD], como mejor proceda, comparezco y (1) DIGO:

Que evacuando el trámite conferido por providencia de [FECHA], en relación con posible la falta de jurisdicción del orden contencioso administrativo para el conocimiento del proceso iniciado, mediante el presente escrito formulo las siguientes

ALEGACIONES

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

- El recurso contencioso administrativo interpuesto tiene por objeto una pretensión deducida en relación con la actuación de las Administraciones Públicas sujeta al Derecho Administrativo, ya que los fundamentos jurídicos en que se basa son los siguientes:

- La pretensión que se formula en el recurso no le corresponde a la jurisdicción contencioso administrativa por tratarse de una cuestión de índole civil, atribuida a la jurisdicción ordinaria.

- La pretensión formulada no le corresponde a la jurisdicción contencioso administrativa por tratarse de una cuestión que, aunque relacionada con actos de la Administración Pública, es de índole laboral, y que por tanto está atribuida a la jurisdicción social.

- La pretensión formulada no le corresponde a la jurisdicción contencioso administrativa ya que corresponde en forma exclusiva a los tribunales del orden penal la definición de un acto como delito.

De lo dicho se desprende que el objeto del proceso [ELEGIR: corresponde / no corresponde] a la jurisdicción contencioso-administrativa, la cual es improrrogable de conformidad con el artículo 5 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa.

Por lo expuesto,

SUPLICO [ELEGIR: AL TRIBUNAL / A LA SALA]

Que tenga por formuladas las anteriores alegaciones y, en consecuencia, [ELEGIR: mantenga su jurisdicción / se declare la falta de jurisdicción] para conocer de este recurso, con los demás pronunciamientos inherentes a dicha declaración.

Es justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Arts. 9.6 LOPJ; arts. 62.1.a y 82.a LJCA. La declaración por la que se acuerde la falta de jurisdicción, será fundada y se efectuará siempre indicando la concreta jurisdicción que se estime competente. Si la parte demandante se persona ante ella en el plazo de un mes, se entenderá haberlo efectuado en la fecha en que se inició el plazo para interponer el recurso contencioso-administrativo, si se hubiere formulado éste siguiendo las indicaciones de la notificación del acto o si ésta fuese defectuosa (art. 5.3 LJCA).
