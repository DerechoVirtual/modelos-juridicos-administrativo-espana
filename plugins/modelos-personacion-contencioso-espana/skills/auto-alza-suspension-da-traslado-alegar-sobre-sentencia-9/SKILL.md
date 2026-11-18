---
name: auto-alza-suspension-da-traslado-alegar-sobre-sentencia-9
description: "Redacta el escrito «Auto que alza la suspensión y da traslado para alegar sobre la sentencia de casación» (formulario 9 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Auto que alza la suspensión y da traslado para alegar sobre la sentencia de casación

> Formulario 0009 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- El alzamiento presupone haber recibido el testimonio que remite la Sección de Enjuiciamiento del TS (art. 56.5 LJCA). La fórmula «Así lo mandan y firman los Ilmos. Señores del margen» solo vale para la Sala; con juez unipersonal hay que adaptarla.

## Nota explicativa: puntualizaciones de la revisión

La nota explicativa de este formulario se ha revisado en el BOE. Tenlo en cuenta al redactar:

- El contenido coincide con el art. 56.5, párrafo cuarto, LJCA (alzar la suspensión y audiencia por plazo común de diez días). Desde el 31-12-2025 el «Juzgado» es la Sección de lo Contencioso-Administrativo del Tribunal de Instancia (LO 1/2025, DT 1.ª y DA 1.ª; arts. 84.2.h y 93 LOPJ).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión. Empieza con una nota explicativa (para qué sirve el escrito y cuándo se usa), revisada en el BOE: léela antes de redactar, pero no la copies en el escrito.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] FECHA (4 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ida en el mismo y el recurso de casación»; «…tencia recaída en el recurso de casación»; «…de»

## Elecciones que hay que hacer

- este Tribunal / esta Sala
- Juez/a o Magistrado/a de la Sección de lo Contencioso-Administrativo del Tribunal de Instancia / Magistrados/as de la Sala de lo Contencioso-Administrativo del Tribunal Superior de Justicia

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 56 de la Ley 29/1998
- Real Decreto-ley 5/2023

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

### Formulario 0009 · Auto que alza la suspensión y da traslado para alegar sobre la sentencia de casación

- Año del modelo: 2023
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 7 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 2 cita(s) o dato(s) corregidos tras comprobarlos en el BOE (revisión de Procesal)
- Avisos de la revisión: El alzamiento presupone haber recibido el testimonio que remite la Sección de Enjuiciamiento del TS (art. 56.5 LJCA). La fórmula «Así lo mandan y firman los Ilmos. Señores del margen» solo vale para la Sala; con juez unipersonal hay que adaptarla.
- Nota explicativa incorporada desde la colección Procesal (formulario 86) y revisada en el BOE el 17-11-2026

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

#### Nota explicativa: para qué sirve este escrito

Modelo de Auto del Juzgado o de la Sala por el que se acuerda, una vez recibido testimonio de la sentencia dictada en el recurso de casación, alzar la suspensión y conceder trámite de audiencia a las partes personadas, por plazo común de diez días, a fin de que aleguen sobre la incidencia que dicho pronunciamiento tiene para resolver el recurso.

---

AUTO

En [LUGAR], a [FECHA].

HECHOS

Que por resolución de fecha [FECHA] se acordó la suspensión del procedimiento por la posible existencia de identidad sustancial entre la cuestión debatida en el mismo y el recurso de casación [COMPLETAR] admitido a trámite por la Sala de lo Contencioso-Administrativo del Tribunal Supremo.

Que con fecha [FECHA] por [ELEGIR: este Tribunal / esta Sala] se ha recibido el testimonio de la sentencia recaída en recurso de casación

RAZONAMIENTOS JURÍDICOS

Establece el apartado 5 del art. 56 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa (LJCA), introducido por el Real Decreto-ley 5/2023, de 28 de junio [NOTA DE REVISIÓN: Errata en el año: el apartado 5 del art. 56 LJCA lo añadió el art. 224.2 del RDL 5/2023 (en vigor desde el 29-7-2023). Fuente: LJCA (BOE-A-1998-16718), art. 56.5; RDL 5/2023 (BOE-A-2023-15135).], que, recibido el testimonio de la sentencia del recurso de casación, el juzgado o tribunal alzará la suspensión y dará un nuevo trámite de audiencia a las partes personadas, por plazo común de diez días, a fin de que aleguen sobre la incidencia que dicho pronunciamiento tiene para resolver el recurso.

LA SALA
EL JUEZ
 ACUERDA:

Alzar la suspensión acordada por Auto de [FECHA] y conceder trámite de audiencia a las partes personadas, por plazo común de diez días, a fin de que aleguen sobre la incidencia que el pronunciamiento de la sentencia recaída en el recurso de casación [COMPLETAR], y cuyo testimonio se acompaña, tiene para resolver el recurso.

Así lo mandan y firman los Ilmos. Señores del margen.

[ELEGIR: Juez/a o Magistrado/a de la Sección de lo Contencioso-Administrativo del Tribunal de Instancia / Magistrados/as de la Sala de lo Contencioso-Administrativo del Tribunal Superior de Justicia] de [COMPLETAR] [NOTA DE REVISIÓN: El Juez de Instrucción (hoy Sección de Instrucción) es un órgano penal. El auto lo dicta el órgano contencioso-administrativo que conoce del recurso. Fuente: LOPJ, arts. 84.2 y 93; LJCA, art. 56.5.]

Firma del Juez/a:

---

#### Notas al pie

[NOTA DE REVISIÓN: El contenido coincide con el art. 56.5, párrafo cuarto, LJCA (alzar la suspensión y audiencia por plazo común de diez días). Desde el 31-12-2025 el «Juzgado» es la Sección de lo Contencioso-Administrativo del Tribunal de Instancia (LO 1/2025, DT 1.ª y DA 1.ª; arts. 84.2.h y 93 LOPJ).]
