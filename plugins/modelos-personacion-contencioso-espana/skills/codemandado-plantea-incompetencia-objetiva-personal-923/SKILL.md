---
name: codemandado-plantea-incompetencia-objetiva-personal-923
description: "Redacta el escrito «Codemandado plantea incompetencia objetiva en personal (nacimiento de la relación funcionarial)» (formulario 923 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Codemandado plantea incompetencia objetiva en personal (nacimiento de la relación funcionarial)

> Formulario 0923 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…jo contra la resolución del Consejero de»; «…a plaza de Técnico en el Departamento de»; «…cionarial de Técnico del Departamento de»; «…. Es justicia que pido en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 7.3 de la LJCA

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

### Formulario 0923 · Codemandado plantea incompetencia objetiva en personal (nacimiento de la relación funcionarial)

- Año del modelo: 2009
- Revisión 17-11-2026: 6 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 7 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D. [NOMBRE Y APELLIDOS], parte codemandada en este proceso, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que al amparo de lo dispuesto en el artículo 7.3 de la LJCA, mediante el presente escrito solicito del Tribunal el planteamiento de oficio de la falta de competencia objetiva para conocer de este recurso, en base a los siguientes MOTIVOS:

PRIMERO.- El presente recurso se dedujo contra la resolución del Consejero de [COMPLETAR] del concurso-oposición libre para cubrir una plaza de Técnico en el Departamento de [COMPLETAR], hallándose en la actualidad en fase de prueba, sin que por ninguna de las partes se hubiera planteado la falta de competencia objetiva del Tribunal en la contestación a la demanda.

SEGUNDO.- No obstante la falta de planteamiento de la falta de competencia objetiva del Tribunal, lo cierto es que la misma es manifiesta, puesto que el acto impugnado afecta al nacimiento de la relación funcionarial, puesto que se trata de un concurso-oposición libre para cubrir una plaza funcionarial de Técnico del Departamento de [COMPLETAR] tal como se desprende de las bases de la convocatoria que obran en los folios 3 a 12 del expediente administrativo.

De ello se infiere sin dudas que la competencia para el conocimiento de este asunto corresponde a la Sala del TSJ de [LOCALIDAD], puesto que el artículo 8.2.a) excluye del ámbito de conocimiento de los Juzgados las cuestiones de personal que se refieran al nacimiento de la relación funcionarial.

Por este motivo, y pese a no haberse planteado en su momento, ponemos de manifiesto la cuestión al Tribunal para que se aprecie de oficio la carencia de competencia, conforme prescribe el artículo 7.3 de la LJCA, atendido el carácter improrrogable de la competencia objetiva y, por ende, el carácter imperativo para el órgano jurisdiccional y para las partes de las normas que la regulan.

Por lo expuesto, SUPLICO AL TRIBUNAL que tenga por presentado este escrito y, en su virtud, previos los trámites legales, declare de oficio la incompetencia del Tribunal para el conocimiento de la causa, remitiéndose las actuaciones a la Sala del TSJ de [LOCALIDAD].

Es justicia que pido en [COMPLETAR] y
