---
name: audiencia-interesados-resolver-recurso-administrativo-1759
description: "Redacta el escrito «Audiencia a los interesados para resolver el recurso administrativo» (formulario 1759 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Audiencia a los interesados para resolver el recurso administrativo

> Formulario 1759 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] Nº
- [ ] LUGAR

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 118 LPACAP
- artículo 118 de la Ley 39/2015
- art. 118 LPACAP

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

### Formulario 1759 · Audiencia a los interesados para resolver el recurso administrativo

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 5 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de comunicación del trámite de audiencia o alegaciones a los interesados, de conformidad con lo establecido en el artículo 118 LPACAP, en el procedimiento sancionador para la resolución del recurso administrativo interpuesto, que pone fin a la vía administrativa.

Por medio de la presente comunicación pongo en su conocimiento que con esta fecha [FECHA], se ha dado por finalizada la instrucción del procedimiento para la resolución del recurso interpuesto por usted contra la resolución de fecha [FECHA], dictada por la Jefatura de Tráfico de [LOCALIDAD], en cuyo expediente también aparecen otros interesados (1).

En el expediente para la resolución del recurso existen para ser tenidos en cuenta nuevos hechos o documentos no recogidos en el expediente originario y alegaciones e informaciones de otros interesados a los que se les ha dado traslado del recurso interpuesto.

En su virtud, y de conformidad con las previsiones del artículo 118 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP), procede ofrecerle el siguiente

TRÁMITE DE AUDIENCIA

En el plazo de [Nº] días queda de manifiesto el expediente para que pueda tomar vista del mismo y formule alegaciones y presente los documentos y justificaciones que estime procedentes.

Pongo en su conocimiento que no serán tenidos en cuenta en la resolución del recurso los hechos, documentos y alegaciones del recurrente, cuando habiendo podido aportarlos en el trámite de alegaciones no lo haya hecho.

Transcurrido este trámite y vistas las alegaciones que, en su caso, sean aportadas, por este Departamento se dictará resolución que ponga fin al procedimiento en vía de recurso y a la vía administrativa.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) El art. 118 LPACAP, referido a la audiencia a los interesados en vía de recurso, prevé la concesión de un plazo no inferior a diez días ni inferior a quince, para que los interesados (recurrentes o no) puedan presentar las alegaciones, documentos e informaciones que tengan por convenientes. Esta audiencia se limita (en el caso del recurrente) al supuesto de que existan nuevos hechos o documentos distintos a los obrantes en el expediente originario, sin que se consideren documentos nuevos a estos efectos ni el recurso, ni los informes, ni las propuestas. Además puede entenderse, con las debidas cautelas para no eliminar el derecho de defensa, que el recurrente no puede presentar en vía de recurso "los hechos, documentos o alegaciones cuando habiendo podido aportarlos en el trámite de alegaciones no lo haya hecho".
