---
name: interposicion-recurso-reposicion-1300
description: "Redacta el escrito «Interposición del recurso de reposición» (formulario 1300 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Interposición del recurso de reposición

> Formulario 1300 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] EN NOMBRE PROPIO
- [ ] DNI/NIE
- [ ] Nº
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] LOS SIGUIENTES HECHOS Y CONSIDERACIONES O
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…o de la mercantil»; «…, en virtud de»; «…(reseñar: escritura de poder»; «…ión de comparecencia ante el funcionario»; «…el»; «…, relativa a [DESCRIBIR] por la que»; «…e para obtención licencia de edificación»; «…, autorización ocupación vía publica»; «…, obtención de subvención»; «…te situación jurídica individualizada En»; «…. ALCALDE-PRESIDENTE DEL AYUNTAMIENTO DE»; «…vincia, se reseñará ILMO. SR. ALCALDE DE»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 117 de la LPACAP
- Ley 39/2015

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

### Formulario 1300 · Interposición del recurso de reposición

- Año del modelo: 2006
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 10 campos de relleno marcados en blanco; 11 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, DNI/NIE, NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D. [NOMBRE Y APELLIDOS], interviniendo [EN NOMBRE PROPIO], con D.N.I. nº [DNI/NIE], o en nombre de D. [NOMBRE Y APELLIDOS] o de la mercantil [COMPLETAR], en virtud de [COMPLETAR] (reseñar: escritura de poder [COMPLETAR], escrito del representado presentado en el Ayuntamiento registrado de entrada nº [Nº], declaración de comparecencia ante el funcionario [COMPLETAR] el [COMPLETAR] (cuya copia se acompaña, etc.), domiciliado a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], c/ [CALLE], respetuosamente comparece y,

EXPONE:

PRIMERO:a) Que en fecha [FECHA] ha recibido la notificación de la Resolución de la Alcaldía (acuerdo de la Junta de Gobierno, del Pleno, del Teniente de Alcalde por delegación del Alcalde, etc.) de fecha [FECHA], relativa a [DESCRIBIR] por la que [COMPLETAR] (p.ejem. se deniega la Solicitud del compareciente para obtención licencia de edificación [COMPLETAR], autorización ocupación vía publica [COMPLETAR], obtención de subvención [COMPLETAR]).b) Que dentro del plazo máximo de un mes establecido al efecto (Art. 52 de la Ley 7/85, de 2 de abril, LBRL y Art. 124 de la Ley 39/2015 LPACAP) interpone RECURSO POTESTATIVO DE REPOSICIÓN contra dicho acto administrativo, por ser contrario a derecho y a los intereses del compareciente.

SEGUNDO:a) Que el recurso se fundamenta por las siguientes ALEGACIONES: b) Se acompañan al presente escrito de recurso los siguientes documentos: (en su caso)

TERCERO:Es procedente la suspensión de la ejecución del acto administrativo recurrido conforme al artículo 117 de la LPACAP, porque, en otro caso se causarían perjuicios de imposible o difícil reparación, como resulta de [LOS SIGUIENTES HECHOS Y CONSIDERACIONES O], en su caso, porque la impugnación se fundamenta en la siguiente (s) causa (s) de nulidad de pleno derecho previstas en el art. 62.1 de la Ley 30/92,Por todo lo anterior:

SOLICITA:1º Se tenga por interpuesto en tiempo y forma el presente recurso potestativo de reposición contra la resolución 2º Se suspenda la ejecución del acto administrativo recurrido.3º Se declare contraria a Derecho y se anule, dejando sin efecto la resolución recurrida4º (En su caso) Se reconozca al recurrente la siguiente situación jurídica individualizada En [COMPLETAR] a Fdo.: SR. ALCALDE-PRESIDENTE DEL AYUNTAMIENTO DE [COMPLETAR] Si se trata de municipio Capital de provincia, se reseñará ILMO. SR. ALCALDE DE [COMPLETAR] Si es municipio incluido en el texto de la LBRL ("Gran población") se reseñara EXCMO. SR. ALCALDE.
