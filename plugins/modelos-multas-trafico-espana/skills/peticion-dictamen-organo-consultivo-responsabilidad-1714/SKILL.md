---
name: peticion-dictamen-organo-consultivo-responsabilidad-1714
description: "Redacta el escrito «Petición de dictamen al órgano consultivo en la responsabilidad patrimonial por daños de circulación» (formulario 1714 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Petición de dictamen al órgano consultivo en la responsabilidad patrimonial por daños de circulación

> Formulario 1714 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO], seguido a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 81 de la Ley 39/2015
- art. 22.13 de la Ley Orgánica 3/1980
- art. 81.2 LPACAP

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

### Formulario 1714 · Petición de dictamen al órgano consultivo en la responsabilidad patrimonial por daños de circulación

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 3 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud de dictamen al órgano consultivo de la Administración, para que se pronuncie sobre la existencia o no de la relación de causalidad entre el funcionamiento del servicio público y la lesión producida, así como sobre el daño causado, la cuantía y modo de la indemnización, dentro del procedimiento de responsabilidad de las Administraciones Públicas.

En este órgano administrativo se ha tramitado el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido a [COMPLETAR], con objeto de que se reconociera, e hiciera efectivo, el derecho a una indemnización, como consecuencia de las lesiones sufridas a causa del funcionamiento de los servicios públicos dependientes de este Departamento.

La instrucción del expediente mencionado ha concluido, habiéndose verificado el trámite de audiencia y elaborado la correspondiente propuesta de resolución o de acuerdo por el que se podría terminar convencionalmente el procedimiento.

En su virtud, y a los efectos prevenidos en el artículo 81 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, solicito que por ese órgano consultivo de esta Administración se elabore dictamen preceptivo, en el que se realice un pronunciamiento sobre los siguientes extremos:

La existencia o no de relación de causalidad entre el funcionamiento del servicio público y la lesión producida.

Sobre la valoración del daño causado y la cuantía y modo de la indemnización, considerando los criterios previstos en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

Cualquier otra cuestión derivada del expediente y que deba tenerse en cuenta para dictar la resolución o el acuerdo indemnizatorio correspondiente (1).

En [LUGAR], a [FECHA].

Firma:

NOTAS DEL FORMULARIO

(1) En el procedimiento administrativo para decidir sobre reclamaciones de responsabilidad patrimonial frente a la Administración del Estado, el art. 22.13 de la Ley Orgánica 3/1980, de 22 de abril, del Consejo de Estado, dispone la previa y preceptiva consulta a la Comisión Permanente del alto Órgano Consultivo en las reclamaciones que, en concepto de indemnización por daños y perjuicios, se formulen a la Administración General del Estado en los supuestos establecidos por las leyes. Por su parte el art. 81.2 LPACAP, establece que en el procedimiento general para la responsabilidad patrimonial será preceptivo el dictamen del Consejo de Estado o, en su caso, del órgano consultivo de la Comunidad Autónoma cuando las indemnizaciones reclamadas sean de cuantía igual o superior a 50.000 € o a la que se establezca en la correspondiente legislación autonómica.
