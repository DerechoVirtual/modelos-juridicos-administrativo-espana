---
name: revision-oficio-disposiciones-actos-nulos-iniciativa-127
description: "Redacta el escrito «Revisión de oficio de disposiciones y actos nulos por iniciativa de la Administración» (formulario 127 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión de oficio de disposiciones y actos nulos por iniciativa de la Administración

> Formulario 0127 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] DESCRIBIR (2 veces)
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…esta Administración acordó lo siguiente:»; «…o taxativamente preceptuado en la Ley de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 103.1 de la Constitución

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

### Formulario 0127 · Revisión de oficio de disposiciones y actos nulos por iniciativa de la Administración

- Año del modelo: 2017
- Revisión 17-11-2026: 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente número:

Interesados:

Procedimiento:

RESOLUCIÓN:

VISTOS los informes emitidos respecto del acuerdo adoptado por esta Administración sobre [DESCRIBIR], y de conformidad con los siguientes

ANTECEDENTES DE HECHO

PRIMERO.- Con fecha [FECHA], esta Administración acordó lo siguiente: [COMPLETAR]. Dicho acuerdo definitivo en vía administrativa fue notificado a los interesados personados en el expediente administrativo de su razón.

SEGUNDO.- Con fecha [FECHA], se emitió un informe técnico por el que se pone de manifiesto la nulidad radical o de pleno Derecho del citado acuerdo anteriormente descrito al vulnerar lo taxativamente preceptuado en la Ley de [COMPLETAR], por lo que dicho acuerdo incurre en causa de nulidad conforme a lo señalado en el apartado f) del artículo 47.1 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

FUNDAMENTOS DE DERECHO

PRIMERO.- De conformidad con lo dispuesto en el artículo 106.1 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas: "Las Administraciones públicas, en cualquier momento, por iniciativa propia o a solicitud de interesado, y previo dictamen favorable del Consejo de Estado u órgano consultivo equivalente de la Comunidad Autónoma, si lo hubiera, declararán de oficio la nulidad de los actos administrativos que hayan puesto fin a la vía administrativa o que no hayan sido recurridos en plazo, en los supuestos previstos en el artículo 47.1". El sometimiento pleno de la Administración Pública a la Ley y al Derecho, impuesto por el artículo 103.1 de la Constitución, exige ante la presencia de actos nulos una reacción enérgica para depurar el ordenamiento. Se trata de una acción imprescriptible, ejercitable en cualquier momento, que constituye un deber de la Administración (y no una mera facultad) de carácter reglado que obliga, sin alternativa, a declarar necesariamente la nulidad del acto viciado.

SEGUNDO.- De acuerdo con lo establecido en el artículo 108 de la referida Ley del Procedimiento Administrativo Común de las Administraciones Públicas: "Iniciado el procedimiento de revisión de oficio al que se refieren los artículos 106 y 107, el órgano competente para declarar la nulidad o lesividad podrá suspender la ejecución del acto, cuando ésta pudiera causar perjuicios de imposible o difícil reparación". Medida cautelar ésta de carácter transitorio que, en el caso presente, parece necesario adoptar con el fin de evitar que, en la realidad, se produzcan los efectos del acto que se prevé que va a ser eliminado del ordenamiento jurídico a consecuencia del procedimiento en curso, previa audiencia de los particulares afectados.

TERCERO.- Este órgano es el competente para resolver sobre la revisión de oficio, conforme a los determinados en la legislación vigente.

Vistos los preceptos legales citados y demás de pertinente y concordante aplicación

RESUELVO

PRIMERO.- Iniciar el procedimiento de revisión de oficio del acuerdo de esta Administración adoptado, en fecha [FECHA], sobre [DESCRIBIR] Este procedimiento revisorio para la declaración de nulidad del citado acuerdo administrativo deberá concluirse en el plazo máximo de seis meses desde su inicio, transcurrido dicho plazo se producirá la caducidad del mismo, de conformidad con lo previsto en el art. 106.5 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

SEGUNDO.- Conceder audiencia previa a los interesados en el expediente de nulidad iniciado para que en el plazo máximo de quince días aleguen lo que estimen oportuno en defensa de sus derechos e intereses, así como de la posibilidad de suspensión cautelar de la eficacia del citado acuerdo de revisión.

TERCERO.- Recabar el preceptivo dictamen del Consejo de Estado u órgano consultivo equivalente de esta Comunidad Autónoma sobre cuestión de nulidad planteada, a quien se le remitirá copia completa, autenticada, foliada y con índice de documentos del expediente administrativo cuya nulidad se interesa, una vez practicadas las actuaciones necesarias para su resolución final.

Contra esta resolución no cabe recurso administrativo alguno, conforme determina el artículo 112 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

En [LUGAR], a [FECHA].

Firma del titular del órgano administrativo competente
