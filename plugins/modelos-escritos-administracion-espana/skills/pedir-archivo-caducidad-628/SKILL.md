---
name: pedir-archivo-caducidad-628
description: "Redacta el escrito «Pedir el archivo por caducidad» (formulario 628 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir el archivo por caducidad

> Formulario 0628 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…ículo 21.3.a) de la Ley 39/2015, el cual»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 21.2 de la Ley 39/2015
- artículos 21, 25 y 95 de la Ley 39/2015
- artículo 21.3.a) de la Ley 39/2015
- artículo 25.1.b) de la Ley 39/2015
- artículo 95 de la Ley 39/2015

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

### Formulario 0628 · Pedir el archivo por caducidad

- Año del modelo: 2010
- Revisión 17-11-2026: 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS] mayor de edad, con DNI número [DNI/NIE], cuyas demás circunstancias ya constan en el procedimiento seguido con el número [Nº DE PROCEDIMIENTO], ante ese órgano comparezco y como mejor proceda en Derecho DIGO:

Que habiendo transcurrido los plazos para resolver el procedimiento de referencia sin que haya sido notificado de resolución alguna, por medio del presente escrito solicito que se dicte resolución de archivo del procedimiento por caducidad, en base a los siguientes HECHOS Y FUNDAMENTOS:

PRIMERO.- El presente procedimiento se inició en fecha [FECHA], sin que hasta este momento se me haya notificado resolución alguna, por lo que han transcurrido más de seis meses desde su iniciación, plazo máximo para resolver, y notificar, con carácter general, según dispone el art. 21.2 de la Ley 39/2015.

Atendido que ha transcurrido el plazo fijado legalmente para resolver, solicito que se acuerde el archivo del procedimiento por caducidad, al amparo de los artículos 21, 25 y 95 de la Ley 39/2015.

En desarrollo de esta solicitud de archivo y a fin de evidenciar su procedencia, debo alegar el artículo 21.3.a) de la Ley 39/2015, el cual [COMPLETAR], establece que el plazo máximo en el que debe notificarse la resolución expresa se contará, en los procedimientos iniciados de oficio, "desde la fecha del acuerdo de iniciación", por lo que el "dies a quo" para el cómputo del plazo es el de la fecha del acuerdo de iniciación, y no el de su notificación, según ha refrendado el Tribunal Supremo en Sentencia de 28 de mayo de 2008, entre otras.

En cuanto al "dies ad quem", con igual claridad establece el artículo 25.1.b) de la Ley 39/2015, que en los procedimientos iniciados de oficio en los que la Administración ejercite potestades de intervención susceptibles de producir efectos desfavorables o de gravamen, como es el caso, el vencimiento de ese plazo máximo sin que se haya dictado y notificado resolución expresa produce, como efecto jurídico, el de la caducidad y consiguiente archivo de las actuaciones, con los efectos previstos en el artículo 95 de la propia LPAC.

En consecuencia, dado que han transcurrido más de seis meses desde la fecha del acuerdo de iniciación del procedimiento el día [FECHA], sin que hasta este momento haya sido notificada a esta parte la resolución que pone fin al procedimiento, debe acordarse el archivo sin más trámites, de conformidad a lo ordenado y con los efectos establecidos en los artículos 21, 25 y 95 de la Ley 39/2015.

Por lo expuesto,

SOLICITO que tenga por formulada esta solicitud y, en su virtud, acuerde el archivo del procedimiento de referencia por caducidad del mismo, acordando su archivo de conformidad con el artículo 95 de la Ley 39/2015.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmado.

ÓRGANO, UNIDAD O CARGO ADMINISTRATIVO AL QUE SE DIRIGE EL ESCRITO
