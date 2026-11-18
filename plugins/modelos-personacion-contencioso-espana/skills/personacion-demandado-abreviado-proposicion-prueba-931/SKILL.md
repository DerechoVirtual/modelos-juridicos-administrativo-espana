---
name: personacion-demandado-abreviado-proposicion-prueba-931
description: "Redacta el escrito «Personación del demandado en abreviado y proposición de prueba» (formulario 931 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Personación del demandado en abreviado y proposición de prueba

> Formulario 0931 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LOCALIDAD
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e por los edictos publicados en el BO de»; «…a parte. - Que se libre oficio al órgano»; «…para que remita»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0931 · Personación del demandado en abreviado y proposición de prueba

- Año del modelo: 2009
- Revisión 17-11-2026: 8 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de [NOMBRE DEL REPRESENTADO/A], representación que acredito con la adjunta primera copia de escritura de poder, declarado bastante y por mí aceptado, comparezco y DIGO:

Que por los edictos publicados en el BO de [COMPLETAR] me he enterado de que ante este Tribunal penden autos de Procedimiento Abreviado, interpuesto por D. [NOMBRE Y APELLIDOS], contra acuerdo de [FECHA], sobre [DESCRIBIR].

Que aunque habiendo sido emplazado como exige el artículo 49 LJ, siendo mi poderdante titular de derechos derivados del acto objeto del «Recurso Contencioso-Administrativo» expresado, está legitimado pasivamente, según dispone el artículo 21.1.b) de la Ley de la Jurisdicción Contencioso-Administrativa en concepto de demandado.

Por lo que, de conformidad a lo dispuesto en el artículo 50.3 de la citada Ley, comparezco y al Tribunal

SUPLICO

que, mediante el presente escrito, me tenga por personado en concepto de demandado en la representación que ostento en Autos del Procedimiento Abreviado núm. [Nº DE PROCEDIMIENTO]/[AÑO], interpuesto por D. [NOMBRE Y APELLIDOS], contra acuerdo de [FECHA], entendiéndose conmigo las sucesivas diligencias.

OTROSÍ DIGO

que esta parte interesa la práctica de las siguientes citaciones y libramiento de oficios, en relación a los medios de prueba que pretende valerse para el acto de la vista y que no puede aportar:

- Que se cite a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], a fin de que comparezca al acto del juicio para ser declarar como testigo a propuesta de esta parte.

- Que se libre oficio al órgano [COMPLETAR] para que remita [COMPLETAR] a fin de proponerlo como prueba documental.

Por lo que SUPLICO expida la citación y oficio interesados para la proposición y práctica de los medios de prueba a que se refieren en el acto del juicio oral.

Es Justicia que pido.

Lugar, fecha y firma
