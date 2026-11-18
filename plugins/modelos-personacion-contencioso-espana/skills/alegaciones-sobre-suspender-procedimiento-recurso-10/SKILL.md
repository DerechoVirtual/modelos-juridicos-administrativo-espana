---
name: alegaciones-sobre-suspender-procedimiento-recurso-10
description: "Redacta el escrito «Alegaciones sobre suspender el procedimiento por un recurso de casación similar admitido» (formulario 10 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones sobre suspender el procedimiento por un recurso de casación similar admitido

> Formulario 0010 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- El art. 56.5 LJCA exige identidad jurídica sustancial y relevancia de la resolución de casación. Contra el auto que resuelva sobre la suspensión no cabe recurso, así que las alegaciones son la única oportunidad de oponerse.

## Nota explicativa: puntualizaciones de la revisión

La nota explicativa de este formulario se ha revisado en el BOE. Tenlo en cuenta al redactar:

- El art. 56.5 LJCA exige dos requisitos, no uno: identidad jurídica sustancial con el recurso de casación admitido y que la resolución que se dicte en casación «pueda resultar relevante para resolver el procedimiento». Solo cabe una vez presentados la demanda y la contestación y antes de dictar sentencia; el auto que resuelva sobre la suspensión no es recurrible.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión. Empieza con una nota explicativa (para qué sirve el escrito y cuándo se usa), revisada en el BOE: léela antes de redactar, pero no la copies en el escrito.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…onal conforme al art. 23.1 de la LJCA, a»; «…a que pido. Por ser de Justicia que pido»; «…, a»

## Elecciones que hay que hacer

- A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]
- me opongo / me adhiero
- AL TRIBUNAL / A LA SALA
- estime / desestime

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si no procede la acumulación, especificar requisitos por los que no procede [NOTA DE REVISIÓN: Hueco que no se toca, pero mal enfocado: el trámite no es de acumulación sino de suspensión del art. 56.5 LJCA. Las alegaciones deben versar sobre la identidad jurídica sustancial y sobre la relevancia de la resolución de casación para el pleito. Fuente: LJCA, art. 56.5 (R

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 23.1 de la LJCA
- art. 56.5 de la Ley 29/1998

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

### Formulario 0010 · Alegaciones sobre suspender el procedimiento por un recurso de casación similar admitido

- Año del modelo: 2023
- Revisión 17-11-2026: 3 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 7 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 1 cita(s) o dato(s) corregidos tras comprobarlos en el BOE (revisión de Procesal)
- Avisos de la revisión: El art. 56.5 LJCA exige identidad jurídica sustancial y relevancia de la resolución de casación. Contra el auto que resuelva sobre la suspensión no cabe recurso, así que las alegaciones son la única oportunidad de oponerse.
- Nota explicativa incorporada desde la colección Procesal (formulario 87) y revisada en el BOE el 17-11-2026

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

#### Nota explicativa: para qué sirve este escrito

Modelo de escrito de alegaciones de las partes respecto a la posible suspensión del procedimiento, solicitando la estimación o desestimación de la suspensión, basado en si se cumplen o no los requisitos del artículo 56.5 LJCA (existencia o no de identidad jurídica sustancial entre la cuestión debatida con el recurso de casación admitido por la Sala del Tribunal Supremo).

---

[ELEGIR: A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS]

Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], en la representación que tengo acreditada en autos de recurso contencioso-administrativo número

Abogado/a dotado/a de la pertinente representación, en los casos en los que se actúe ante un órgano judicial unipersonal conforme al art. 23.1 de la LJCA,

a [COMPLETAR], como mejor proceda,

DIGO

Que se me ha notificado diligencia de ordenación por la que, de conformidad con lo dispuesto en el art. 56.5 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa (en adelante, LJCA) se me concede plazo de DIEZ días para formular alegaciones sobre la posible suspensión del recurso contencioso número [Nº DE PROCEDIMIENTO].

Que, evacuando el trámite conferido, mediante el presente escrito [ELEGIR: me opongo / me adhiero] a la suspensión pretendida con base en las siguientes

ALEGACIONES

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si no procede la acumulación, especificar requisitos por los que no procede [NOTA DE REVISIÓN: Hueco que no se toca, pero mal enfocado: el trámite no es de acumulación sino de suspensión del art. 56.5 LJCA. Las alegaciones deben versar sobre la identidad jurídica sustancial y sobre la relevancia de la resolución de casación para el pleito. Fuente: LJCA, art. 56.5 (RDL 5/2023).] / Si procede la acumulación, especificar requisitos — el texto de cada opción no venía en el formulario original]

Por lo expuesto,

SUPLICO [ELEGIR: AL TRIBUNAL / A LA SALA]

Que [ELEGIR: estime / desestime] la pretensión de suspensión del procedimiento número [Nº DE PROCEDIMIENTO], pendientes ante este órgano jurisdiccional, pues así procede en Derecho.

Es justicia que pido.

Por ser de Justicia que pido [COMPLETAR], a [COMPLETAR].

Firma de Abogado/a	Firma de Procurador/a

---

#### Notas al pie

[NOTA DE REVISIÓN: El art. 56.5 LJCA exige dos requisitos, no uno: identidad jurídica sustancial con el recurso de casación admitido y que la resolución que se dicte en casación «pueda resultar relevante para resolver el procedimiento». Solo cabe una vez presentados la demanda y la contestación y antes de dictar sentencia; el auto que resuelva sobre la suspensión no es recurrible.]
