---
name: acuerdo-terminacion-convencional-procedimiento-1219
description: "Redacta el escrito «Acuerdo de terminación convencional del procedimiento» (formulario 1219 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo de terminación convencional del procedimiento

> Formulario 1219 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…, a»; «…, Director del órgano administrativo»; «…1. El presente convenio tiene por objeto»; «…ue por daños y perjuicios le es debida a»; «…, por cuanto»; «…cuanto al plazo de vigencia se establece»; «…ación que ostentan, que entrará en vigor»; «… y se publicará en el Boletín Oficial de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 86 de la Ley 39/2015

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

### Formulario 1219 · Acuerdo de terminación convencional del procedimiento

- Año del modelo: 2008
- Revisión 17-11-2026: 1 bloques de alternativas señalados; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR], a [COMPLETAR], y estando presente, de una parte, D./Dña. [NOMBRE Y APELLIDOS], Director del órgano administrativo [COMPLETAR], y de otra, D./Dña. [NOMBRE Y APELLIDOS],

actuando en su propio nombre y derecho

actuando en representación de [NOMBRE DEL REPRESENTADO/A],

en este acto y de común acuerdo deciden dar por concluso el expediente nº [Nº DE EXPEDIENTE], seguido en este órgano desde el [FECHA], fecha en que tuvo lugar su incoación, y a fin de [DESCRIBIR], en virtud del acuerdo alcanzado al amparo de lo dispuesto en el artículo 86 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

Y todo ello de conformidad con las siguientes estipulaciones, que en todo caso recaen sobre materias susceptibles de transacción.

Primera.- Naturaleza jurídica.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Al presente acuerdo se le ha dado el carácter de acto final del procedimiento administrativo, y, como tal, sustituye a la propia resolución.

El presente acuerdo deberá ser homologado por la resolución que haya de recaer en el presente expediente y que, por tanto, se ajustará a las previsiones contenidas en las estipulaciones que siguen.

Al presente acuerdo se le dota de la naturaleza de acto meramente preparatorio de la resolución que deba recaer en el procedimiento, de manera que sus previsiones no tienen carácter vinculante para la Administración, que podrá apartarse de las siguientes estipulaciones en cuanto tenga por conveniente y resulte justificado

Segunda.- Objeto.

1. El presente convenio tiene por objeto [COMPLETAR]

2. Además tiene asimismo como objeto principal fijar la indemnización que por daños y perjuicios le es debida a [COMPLETAR], por cuanto [COMPLETAR]

Tercera.- Ámbito personal, funcional y territorial.

El ámbito personal, funcional y territorial, de este acuerdo son los siguientes.

En cuanto al plazo de vigencia se establece [COMPLETAR]

Y todo ello sin perjuicio de las competencias que corresponden a los correspondientes órganos administrativos, sin que por tanto el presente acuerdo suponga alteración, modificación de las mismas ni de las responsabilidades que se hayan podido derivar en la tramitación del presente procedimiento.

Y, para que así conste, se suscribe el presente convenio por los intervinientes en la representación que ostentan, que entrará en vigor [COMPLETAR], y se publicará en el Boletín Oficial de [COMPLETAR], para su general conocimiento.

En [LUGAR], a [FECHA].

Firmado:
