---
name: contencioso-ante-audiencia-nacional-nacionalidad-365
description: "Redacta el escrito «Contencioso ante la Audiencia Nacional en nacionalidad (procedimiento ordinario)» (formulario 365 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso ante la Audiencia Nacional en nacionalidad (procedimiento ordinario)

> Formulario 0365 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Nº
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…eral de los Registros y del Notariado de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 19.1.a) de la LJCA
- art. 14 de la LJCA
- art. 46.1 de la LJCA
- art. 45.2 de la LJCA

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

### Formulario 0365 · Contencioso ante la Audiencia Nacional en nacionalidad (procedimiento ordinario)

- Año del modelo: 2013
- Revisión 17-11-2026: 6 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 2 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO

DE LA AUDIENCIA NACIONAL

D./Dña. [NOMBRE Y APELLIDOS], Procuradora de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], según acredito con la escritura de poder debidamente aceptada y bastanteada que acompaño y cuya devolución solicito una vez compulsada la copia que asimismo se adjunta, ante el Tribunal comparezco y, como mejor en Derecho proceda, DIGO:

Que, en la representación que ostento, dentro del plazo legal y al amparo de lo dispuesto en el art. 45 de la vigente Ley Reguladora de la Jurisdicción Contencioso-Administrativa de 13 de julio de 1998, interpongo recursocontencioso-administrativocontra la Resolución del Director General de los Registros y del Notariado de fecha [FECHA], notificada el día [FECHA], denegatoria de la nacionalidad por residencia de mi representada.

I

Legitimación activa.— Mi representado está legitimado activamente de conformidad con el art. 19.1.a) de la LJCA.

II

Legitimación pasiva.— Está legitimado pasivamente el órgano contra quien me dirijo de acuerdo con los arts. 21.1.a) y cc. de la LJCA.

III

Competencia funcional.— Tal y como señala la resolución objeto del presente recurso, la competencia corresponde a la oportuna Sala de la Audiencia Nacional.

IV

Competencia territorial.— Por su parte, el art. 14 de la LJCA establece la regla de atribuir la competencia al órgano jurisdiccional en cuya circunscripción se hubiese realizado el acto originariamente impugnado.

V

Plazo.— Según dispone el art. 46.1 de la LJCA, el plazo para la interposición del recurso contencioso-administrativo será de dos meses contados desde el día siguiente al de la publicación de la disposición impugnada o al de la notificación o publicación del acto que ponga fin a la vía administrativa. La resolución definitiva se notificó a mi representada el día [FECHA]

VI

Documentos que se aportan.— Que en cumplimiento de lo dispuesto en el art. 45.2 de la LJCA, se acompañan los siguientes documentos.

1. Escritura de poder y su copia.

2. Copia de la resolución que se impugna.

Por lo expuesto,

SUPLICO AL TRIBUNAL, que teniendo por presentado este escrito interponiendo recurso contencioso-administrativocontra la Resolución del Director General de los Registros y del Notariado de [COMPLETAR] denegatoria de la nacionalidad por residencia de mi representada; se sirva admitirlo, tenerme por parte en la representación que ostento, y se dé por interpuesto el recurso jurisdiccional que por el presente escrito se inicia, disponiendo se reclame de la Autoridad cuya resolución se recurre el expediente administrativo tramitado como antecedente de la impugnación presentada por mi representado, y una vez en Secretaría se ponga a disposición del recurrente, al efecto de instruirse de los mismos y deducir la demanda correspondiente.

En [LUGAR], a [FECHA].

Abogado/a núm. [Nº]
