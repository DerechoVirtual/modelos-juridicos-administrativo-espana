---
name: alegaciones-denegarse-prueba-propuesta-320
description: "Redacta el escrito «Alegaciones por denegarse la prueba propuesta» (formulario 320 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones por denegarse la prueba propuesta

> Formulario 0320 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] DNI/NIE
- [ ] CALLE
- [ ] NIF
- [ ] Nº DE EXPEDIENTE
- [ ] ÓRGANO
- [ ] FECHA (2 veces)
- [ ] artículo 47.1.a) de la propia Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A»; «…DE»; «…n representación de D. o de la mercantil»; «…número CP de»; «…ante [ÓRGANO] de»; «…n virtud de todo lo expuesto, SOLICITO A»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 24.2 de la Constitución
- artículo 53.2 b) de la Ley 39/2015
- artículo 87.1 del Real Decreto Legislativo 6/2015
- artículo 95 del Real Decreto Legislativo 6/2015

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

### Formulario 0320 · Alegaciones por denegarse la prueba propuesta

- Año del modelo: 2013
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A [COMPLETAR] DE [COMPLETAR]

D.mayor de edad, con domicilio en la C/ número CP de y provisto de DNI número [DNI/NIE] (o en representación de D. o de la mercantil [COMPLETAR] conforme acredito con la escritura de constitución de dicha sociedad, con domicilio social en la C/ [CALLE] número CP de [COMPLETAR] y CIF [NIF]), según consta en el Expediente administrativo sancionador número [Nº DE EXPEDIENTE] ante [ÓRGANO] de [COMPLETAR] comparezco y, como mejor proceda en derecho, DIGO:

Que con fecha [FECHA] se me ha notificado la denegación de la prueba propuesta por esta parte en nuestro escrito de alegaciones de fecha [FECHA] sin que se motive ni fundamente tal resolución en precepto alguno, lo que causa auténtica indefensión y, por medio del presente escrito, formulo las siguientes

ALEGACIONES

Al impedir que el administrado pueda valerse de prueba de descargo sin razonamiento jurídico alguno, se crea auténtica indefensión al compareciente y se vulnera la presunción de inocencia garantizada en el artículo 24.2 de la Constitución y en el artículo 53.2 b) de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, lo que vicia de nulidad el presente expediente [artículo 47.1.a) de la propia Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas].

El instructor vulnera el más elemental principio de contradicción en el expediente, pues hace una valoración que sólo compete al órgano sancionador y, por ello, se excede de modo evidente en sus funciones, amén de no fundamentar su decisión, incurriendo por lo tanto en arbitrariedad.

El artículo 87.1 del Real Decreto Legislativo 6/2015, de 30 de Octubre, que aprueba el nuevo Texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, textualmente dice: “Los Agentes de la autoridad encargados de la vigilancia del tráfico deberán denunciar las infracciones que observen”, y sólo dichas denuncias tienen presunción de “veracidad”, “sin perjuicio del deber de aquéllos de aportar todos los elementos probatorios que sean posibles sobre el hecho denunciado”, conforme dispone el artículo 88 del citado Real Decreto Legislativo 6/2015.

Ante semejante enunciado legal resulta, cuando menos, sorprendente, que se rechace sin motivación alguna la prueba propuesta por el compareciente cuando los denunciantes no han efectuado prueba de cargo.

El artículo 95 del Real Decreto Legislativo 6/2015, de 30 de Octubre, exige del instructor una resolución motivada, para poder rechazar las pruebas propuestas por los interesados.

En virtud de todo lo expuesto,

SOLICITO A [COMPLETAR] DE Que tenga por presentado este escrito en tiempo y forma legales, se digne admitirlo, tenga por hechas las alegaciones en él contenidas, y a su tenor ordene la práctica de cuantas pruebas se propusieron en nuestro anterior escrito de alegaciones, so pena de viciar de nulidad el presente expediente.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
