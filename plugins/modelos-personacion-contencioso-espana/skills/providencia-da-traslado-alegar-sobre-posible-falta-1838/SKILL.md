---
name: providencia-da-traslado-alegar-sobre-posible-falta-1838
description: "Redacta el escrito «Providencia que da traslado para alegar sobre la posible falta de jurisdicción» (formulario 1838 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Providencia que da traslado para alegar sobre la posible falta de jurisdicción

> Formulario 1838 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] LUGAR (2 veces)
- [ ] FECHA (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] NOMBRE Y APELLIDOS

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

### Formulario 1838 · Providencia que da traslado para alegar sobre la posible falta de jurisdicción

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 4 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Providencia del Tribunal concediendo a las partes y al Ministerio Fiscal un plazo de diez días para que aleguen lo que estimen oportuno respecto de la falta de jurisdicción apreciada de oficio por el órgano jurisdiccional, pudiendo interponer recurso de reposición frente a esa resolución.

PROVIDENCIA

En [LUGAR], a [FECHA].

El anterior escrito de interposición de recurso, presentado por [ÓRGANO O PERSONA], regístrese. Se designa como ponente (1) al Ilmo. Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS]. Pudiendo no corresponder a la jurisdicción contencioso administrativa el conocimiento de las pretensiones suscitadas en el litigio, dése traslado a la parte recurrente, a la Administración recurrida y al Ministerio Fiscal, por plazo de DIEZ días, para que aleguen lo que a su derecho convenga. Doy fe.

NOTIFICACIÓN

En [LUGAR], a [FECHA].

Teniendo a mi presencia a la representación de las partes personadas les notifico en legal forma la anterior resolución, a la vez que les pongo de manifiesto que contra la misma cabe interponer recurso de reposición en el plazo de CINCO días ante este mismo órgano.

Y enterados de ello firman conmigo. Doy fe.

Firma del Juez/a:	Firma del Letrado/a de la Administración de Justicia:

NOTAS DEL FORMULARIO

(1) En el caso de que la resolución se dicte en un Tribunal de lo Contencioso no se designa Ponente ya que al ser órgano unipersonal es siempre el titular o su sustituto en su caso el que resuelve. Toda resolución debe ser notificada a las partes personadas y a aquellas que pueda afectar, mediante lectura de la misma y entrega de copia. Las cuestiones de competencia se podrán apreciar de oficio o a instancia de parte; en este último caso será un escrito de la parte demandada el que inicie el incidente, escrito que deberá ser fundado e indicará el órgano judicial que estime competente.
