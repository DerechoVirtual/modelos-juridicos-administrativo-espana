---
name: solicitud-organo-administrativo-promover-conflicto-1828
description: "Redacta el escrito «Solicitud a un órgano administrativo para promover conflicto de jurisdicción» (formulario 1828 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud a un órgano administrativo para promover conflicto de jurisdicción

> Formulario 1828 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] DESCRIBIR
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con objeto de [DESCRIBIR], en»; «…, tramitado por»

## Elecciones que hay que hacer

- A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]
- la Sala / el Tribunal
- ese Tribunal / esa Sala
- AL TRIBUNAL / A LA SALA

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5.1 de la Ley 29/1998
- art. 103.4 y 103.5, de la LJCA
- Ley Orgánica 2/1987

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

### Formulario 1828 · Solicitud a un órgano administrativo para promover conflicto de jurisdicción

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 3 desplegables convertidos en elección en blanco; 9 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 4 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito por el que un particular solicita del Tribunal (o de la Sala) que promueva conflicto de jurisdicción, con el correspondiente requerimiento de inhibición y suspensión de la tramitación, frente a un órgano administrativo, al entender que el asunto del que está conociendo no es competencia de la Administración pública, sino de la Jurisdicción Contencioso-Administrativa.

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

[ELEGIR: A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE] – PLAZA N.º [Nº] / A LA SALA DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [COMUNIDAD AUTÓNOMA]]

D./Dña. [NOMBRE Y APELLIDOS], actuando en nombre de D./Dña. [NOMBRE Y APELLIDOS], cuya representación acredito mediante escritura de poder, que acompaño, con copia simple de la misma para que me sea devuelto el original, ante [ELEGIR: la Sala / el Tribunal] de lo Contencioso-Administrativo de [LOCALIDAD], comparezco y DIGO:

Que a mi representado se le sigue un procedimiento administrativo, iniciado de oficio, bajo el número [NÚMERO], con objeto de [DESCRIBIR], en [COMPLETAR], en el que se le han notificado los actos administrativos cuyas copias y demás documentación se adjuntan a efectos identificativos.

Que esta parte entiende que el objeto del expediente administrativo referenciado no es de competencia de la Administración Pública actuante ya que se trata de una materia cuyo conocimiento corresponde a [ELEGIR: ese Tribunal / esa Sala] de lo Contencioso-Administrativo y así se acredita con fundamento en los siguientes antecedentes y consideraciones jurídicas (1):

Por lo expuesto y al amparo de lo dispuesto en el artículo 5.1 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa (LJCA), en relación con las previsiones del artículo 9 y concordantes de la Ley Orgánica 2/1987, de 18 de mayo, de Conflictos Jurisdiccionales,

SUPLICO [ELEGIR: AL TRIBUNAL / A LA SALA]

Que tenga por promovido conflicto de jurisdicción en relación con el expediente número [Nº DE EXPEDIENTE], tramitado por [COMPLETAR], y, previos los trámites que correspondan, acuerde cursar al órgano administrativo que está conociendo del asunto referenciado el oportuno requerimiento de inhibición para que suspenda la tramitación emprendida y le remita las actuaciones practicadas.

Es Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) El caso más frecuente será aquel en el que un Tribunal haya dictado Sentencia firme y, pese a ello, o bien la Administración actúa desoyendo lo resuelto o bien directamente pretende desobedecerlo. En cualquiera de estos dos casos podrá emplearse el cauce previsto en este formulario (requerimiento de inhibición) o la vía del art. 103.4 y 103.5, de la LJCA (es decir, pedirle al Tribunal sentenciador que declare directamente la nulidad de los actos administrativos dictados).
