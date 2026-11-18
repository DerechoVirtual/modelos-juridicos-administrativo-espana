---
name: solicitud-medalla-merito-seguridad-vial-1734
description: "Redacta el escrito «Solicitud de medalla al mérito de la seguridad vial» (formulario 1734 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de medalla al mérito de la seguridad vial

> Formulario 1734 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.

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
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] LUGAR
- [ ] FECHA

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

### Formulario 1734 · Solicitud de medalla al mérito de la seguridad vial

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud para que se otorgue por parte de la Administración la medalla al mérito de la seguridad vial a un particular o a una institución, por haber destacado en su aportación a favor de la seguridad vial, o por haber realizado algún acto heroico o de ejemplar solidaridad humana.

A LA DIRECCIÓN GENERAL DE TRÁFICO

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.], ante la Dirección General de Tráfico, comparece y como mejor proceda en derecho

EXPONE:

Que de la misma forma que resulta necesario sancionar los comportamientos agresivos para la seguridad vial también es preciso que se honren o premien las conductas que entrañan una importante aportación a la seguridad vial, tengan un notorio relieve en la salvaguardia de ésta o constituyan un ejemplo encomiable para los demás.

Que, en cumplimiento de ese objetivo, en virtud de este escrito se solicita el inicio de expediente para la concesión a D./Dña. [NOMBRE Y APELLIDOS] de la medalla al mérito de la seguridad vial, creada mediante Decreto 2464/1974, de 9 de agosto, y la Orden de 6 de noviembre de 1974, por haber contraído méritos suficientes para ello tal y como se acredita con la Memoria adjunta.

Por lo expuesto,

SOLICITA:

Que se tenga por presentado este escrito, junto con los documentos que se acompañan y, de conformidad con lo manifestado en el mismo, se conceda la medalla al mérito en la seguridad vial a D./Dña. [NOMBRE Y APELLIDOS] en función de los merecimientos apuntados que resultan sobradamente acreditados para ello (1).

En [LUGAR], a [FECHA].

Firma

NOTAS DEL FORMULARIO

(1) La Medalla al Mérito de la Seguridad Vial está creada para premiar a las personas naturales o jurídicas que se hayan destacado por su actividad a favor de la seguridad de la circulación bien por la realización de un acto heroico o de ejemplar solidaridad humana, bien por la colaboración en forma relevante con las autoridades o agentes a quienes compete su ordenación y control, prestando servicios eminentes tanto desde el punto de vista técnico o pedagógico como en el orden económico o social. De esta medalla existen tres categorías: oro, plata y bronce y cada una de estas categorías cuenta con tres distintivos: rojo, azul y blanco, que se corresponden con los diferentes méritos contraídos por los beneficiarios de conformidad con lo previsto y regulado en el Decreto 2464/1974, de 9 de agosto, por el que se crea la medalla al mérito de la seguridad vial (BOE 9 septiembre 1974) y la Orden ministerial de 6 de noviembre de 1974, que lo desarrolla (BOE 19 noviembre 1974).
