---
name: pedir-rectificar-errores-materiales-hecho-aritmeticos-571
description: "Redacta el escrito «Pedir rectificar errores materiales, de hecho y aritméticos» (formulario 571 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir rectificar errores materiales, de hecho y aritméticos

> Formulario 0571 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] IMPORTE (4 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Al Gerente territorial del Catastro de»; «…D./Dña. [NOMBRE Y APELLIDOS] con D.N.I.»; «… la Gerencia Territorial del Catastro de»; «…esa Gerencia Territorial del Catastro de»; «… cálculo del valor catastral de la finca»; «… se aplica el coeficiente de ponderación»; «…, el Gerente Territorial del Catastro de»; «…euros, resultaría la cifra de»; «…metidas a reglas claramente establecidas»; «…ica. La rectificación del error de hecho»; «… la Gerencia Territorial del Catastro de»; «… cálculo del valor catastral de la finca»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 109.2 de la Ley 39/2015
- art. 109.2 de la Ley 39/2015

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

### Formulario 0571 · Pedir rectificar errores materiales, de hecho y aritméticos

- Año del modelo: 2011
- Revisión 17-11-2026: 2 llamadas a nota sin texto retiradas; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 25 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Gerente territorial del Catastro de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS] con D.N.I. [COMPLETAR],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.],

actuando

[ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original]

ante la Gerencia Territorial del Catastro de [COMPLETAR], competente para conocer de esta solicitud, comparece y como mejor proceda en Derecho dice:

Que en la resolución de esa Gerencia Territorial del Catastro de [COMPLETAR] por la que se determina el cálculo del valor catastral de la finca [COMPLETAR] cuya titularidad me corresponde, se aplica el coeficiente de ponderación [COMPLETAR] de donde resulta una valoración de [IMPORTE] euros, siendo la base sobre la que se aplica tal coeficiente la cantidad de [IMPORTE] euros.

FUNDAMENTOS DE DERECHO

Primero.- Se formula el presente escrito al amparo de lo dispuesto en el artículo 109.2 de la Ley 39/2015, de 1 de octubre; del Procedimiento Administrativo Común de las Administraciones Públicas. El órgano competente para la resolución de esta solicitud es el mismo órgano administrativo que dictó el acto cuya rectificación se pide, el Gerente Territorial del Catastro de [COMPLETAR].

La petición se formula sin sujeción a plazo alguno de ejercicio puesto que el precepto antes citado señala que podrá solicitarse en cualquier momento.

Segundo.- Del análisis de la resolución cuya corrección se pide se deduce la aplicación del coeficiente de ponderación para la valoración de la finca de esta interesada. Del cálculo matemático correspondiente sobre la cantidad de [IMPORTE] euros, resultaría la cifra de [COMPLETAR] y no la fijada por la valoración llevada a cabo por ese órgano, con lo que nos hallaríamos ante un error aritmético.

Tercero.- Los errores aritméticos consisten en simples equivocaciones cometidas al consignar un determinado número o el resultado de operaciones aritméticas sometidas a reglas claramente establecidas [COMPLETAR].

La jurisprudencia exige que el tipo de errores del artículo 109.2 de la Ley 39/2015, de 1 de octubre, consista en simples equivocaciones elementales de nombres, fechas, operaciones aritméticas, transcripciones de documentos. Los errores tienen que apreciarse teniendo en cuenta exclusivamente los datos del expediente administrativo en el que se advierte (SSTS de 19 de enero de 1999, Rec. 11604/1990. Además deben ser patentes y claros, sin necesidad de acudir a interpretación de normas jurídicas aplicables pues este es el dato esencial que separa el error de hecho del de derecho. El error material no debe producir una alteración fundamental en el sentido del acto y debe afectar a los presupuestos fácticos determinantes de la decisión administrativa, pues no existe este error cuando su apreciación implique un juicio valorativo o exija una operación de calificación jurídica.

La rectificación del error de hecho [COMPLETAR] no debe afectar a la subsistencia del acto administrativo, es decir, no puede acarrear la anulación o revocación del mismo en cuanto creador de derechos subjetivos, produciéndose uno nuevo sobre bases diferentes y sin las debidas garantías para el afectado, pues el acto administrativo rectificador ha de mostrar idéntico contenido dispositivo, sustantivo y resolutorio que el acto rectificado, sin que pueda la Administración, so pretexto de su potestad rectificadora de oficio, encubrir una auténtica revisión, pues ello entrañaría un fraude de ley, constitutivo de desviación de poder.

Esto no es óbice, como han acertado a destacar algunos autores, para que en algunos supuestos se deduzcan determinados efectos de la actuación rectificadora que en parte afectan a su contenido. Si el acto reconocía el derecho a recibir determinada cantidad por diversos conceptos y ha existido un error en su suma, la rectificación producirá el efecto del derecho a percibir el exceso o devolver la diferencia.

Cuarto.- No estamos en presencia del error de hecho siempre que su apreciación implique un juicio valorativo o exija una operación de calificación jurídica, entendiendo que se caracteriza por poseer una realidad independiente de lo opinable y del razonamiento humano, que se produzcan en la transcripción o de simple cuenta. No existe error de hecho cuando la comprobación del mismo exige tener que acudir a datos de los que no hay constancia en el expediente administrativo.

En virtud de lo expuesto, y de conformidad con el art. 109.2 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, el que subscribe solicita:

Que se tenga por presentado este escrito, se sirva admitirlo y tenga por solicitada la rectificación del error aritmético cometido en la resolución de la Gerencia Territorial del Catastro de [COMPLETAR] por la que se determina el cálculo del valor catastral de la finca [COMPLETAR], sustituyendo la cantidad de [IMPORTE] euros por la de [COMPLETAR].

En [LUGAR], a [FECHA].

Firmado:

Gerente territorial del catastro de [COMPLETAR]
