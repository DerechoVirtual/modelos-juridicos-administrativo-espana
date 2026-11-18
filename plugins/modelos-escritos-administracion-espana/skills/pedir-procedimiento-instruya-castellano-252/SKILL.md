---
name: pedir-procedimiento-instruya-castellano-252
description: "Redacta el escrito «Pedir que el procedimiento se instruya en castellano» (formulario 252 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir que el procedimiento se instruya en castellano

> Formulario 0252 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.
- **Criterio de Hacienda y del TEAC** → `buscar_consultas_hacienda` → `leer_consulta_hacienda`; `buscar_doctrina_teac` → `leer_resolucion_teac`.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CORREO ELECTRÓNICO
- [ ] FECHA
- [ ] ACTO O RESOLUCIÓN (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Expdte.-»; «…,»; «…, [COMPLETAR] (interpuse recurso de»; «…contra [ACTO O RESOLUCIÓN]; solicité»; «…a lengua oficial de esta CA, esto es, en»; «…conformidad, tramitando el procedimiento»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 13 de la Ley 39/2015

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

### Formulario 0252 · Pedir que el procedimiento se instruya en castellano

- Año del modelo: 2016
- Revisión 17-11-2026: 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expdte.- [COMPLETAR]

Procedimiento

D/Dª [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE], con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], o vía correo electrónico [CORREO ELECTRÓNICO], por medio del presente escrito, en su propio nombre y representación (o en representación de según poder) EXPONGO:

1.- Que con fecha [FECHA], [COMPLETAR] (interpuse recurso de [COMPLETAR] contra [ACTO O RESOLUCIÓN]; solicité [COMPLETAR]; presenté reclamación de responsabilidad patrimonial contra [ACTO O RESOLUCIÓN]; etc.). Se adjunta copia de la primera página donde consta el registro de entrada.

2.- Que en dicho escrito me expresé en castellano, toda vez que el artículo 13 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, reconoce, entre otros derechos de las personas en sus relaciones con las Administraciones Públicas, el derecho a utilizar las lenguas oficiales en el territorio de su Comunidad Autónoma, de acuerdo con lo previsto en la propia LPAC y en el resto del ordenamiento jurídico.

3.- Que en el presente procedimiento están también interesados D/Dª [NOMBRE Y APELLIDOS]; D./Dª [NOMBRE Y APELLIDOS]; y D/Dª [NOMBRE Y APELLIDOS], siendo que uno de ellos ha solicitado que el procedimiento se instruya en la otra lengua oficial de esta CA, esto es, en [COMPLETAR] (catalán, gallego,).

4.- Que conforme al artículo 15 LPAC, en estos casos, al tratarse de un procedimiento tramitado por la Administración General del Estado, el procedimiento se tramitará en la lengua elegida por el interesado y “si concurrieran varios interesados en el procedimiento, y existiera discrepancia en cuanto a la lengua, el procedimiento se tramitará en castellano, si bien los documentos o testimonios que requieran los interesados se expedirán en la lengua elegida por los mismos”.

Que por lo anterior y de conformidad con lo dispuesto en dicho precepto, solicito el cumplimiento de dicha obligación legal, debiendo tramitarse el procedimiento en castellano.

Por todo lo expuesto,

SOLICITO: Que se tenga por presentado este escrito, y se acuerde de conformidad, tramitando el procedimiento [COMPLETAR] en castellano.

ÓRGANO, UNIDAD O CARGO ADMINISTRATIVO DE LA AGE AL QUE SE DIRIGE EL ESCRITO
