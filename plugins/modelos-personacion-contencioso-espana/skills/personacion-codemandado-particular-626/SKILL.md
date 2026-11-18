---
name: personacion-codemandado-particular-626
description: "Redacta el escrito «Personación de un codemandado particular» (formulario 626 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Personación de un codemandado particular

> Formulario 0626 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] NÚMERO
- [ ] FIRMAS DE ABOGADO Y PROCURADOR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… O A LA SALA, O A LA OFICINA JUDICIAL DE»; «…con número de colegiación»; «…por la Administración Pública»; «…igencias a que haya lugar en Derecho. En»; «…, a»; «…, a [COMPLETAR], de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 49.1 de la LJCA

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

### Formulario 0626 · Personación de un codemandado particular

- Año del modelo: 2010
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 10 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 4 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso nºJuzgado

AL JUZGADO, O A LA SALA, O A LA OFICINA JUDICIAL DE [COMPLETAR] Don. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A] según acredito con la copia de escritura de poder que se acompaña y cuya devolución solicito previa unión de testimonio a los autos, bajo la dirección letrada de D. [NOMBRE Y APELLIDOS], Abogado del Colegio de [LOCALIDAD] con número de colegiación [COMPLETAR], comparezco ante este Tribunal y DIGO:

PRIMERO.- Que mi representado ha sido notificado el día [FECHA] por la Administración Pública [COMPLETAR] en el recurso contencioso-administrativo número [NÚMERO] de la remisión del expediente administrativo correspondiente a la resolución de fecha [FECHA], en el cual mi representado ostenta la condición de interesado.

SEGUNDO.- Que mediante el presente escrito, y dentro del plazo establecido en el art. 49.1 de la LJCA, vengo a personarme como parte demandada en el presente proceso al ostentar derechos e intereses legítimos que pueden quedar afectados por la resolución de este recurso.

Por todo lo cual,

SUPLICO AL TRIBUNAL, que en atención a lo expuesto anteriormente, me tenga por comparecido en la representación que acredito de D. [NOMBRE Y APELLIDOS] y personado en forma como parte demandada, ordenando lo que sea procedente a efectos de que se entiendan conmigo las sucesivas diligencias a que haya lugar en Derecho.

En [COMPLETAR], a [COMPLETAR], de [COMPLETAR] del año [FIRMAS DE ABOGADO Y PROCURADOR]
