---
name: reposicion-contra-visado-reagrupacion-familiar-denegado-300
description: "Redacta el escrito «Reposición contra visado de reagrupación familiar denegado» (formulario 300 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra visado de reagrupación familiar denegado

> Formulario 0300 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Reagrupación: nuevos requisitos del art. 67 RD 1155/2024 (medios, vivienda) y visado por los arts. 38 y 40.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (5 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AL CONSULADO GENERAL DE ESPAÑA EN»; «…, asistido/a por su padre, D. S»; «…. El Consulado de España en»; «…r en España a los siguientes familiares:»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 124 de la Ley 39/2015
- art. 123 de la LPACAP
- art. 17.1.c) de la LO 4/2000
- art. 66.1.d) del Real Decreto 1155/2024
- artículos 38 y 40 del Real Decreto 1155/2024
- art. 48 de la LPACAP
- Ley Orgánica 4/2000

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

### Formulario 0300 · Reposición contra visado de reagrupación familiar denegado

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 12 campos de relleno marcados en blanco
- Avisos de la revisión: Reagrupación: nuevos requisitos del art. 67 RD 1155/2024 (medios, vivienda) y visado por los arts. 38 y 40.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL CONSULADO GENERAL DE ESPAÑA EN [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], asistido/a por su padre, D. S [COMPLETAR], ambos de nacionalidad Marroquí, ante este organismo comparece para interponer RECURSO DE REPOSICIÓN contra la resolución de fecha [FECHA], que le ha sido notificada en fecha [FECHA], por la que se denegaba la solicitud de visado,

Se adjunta copia de la resolución denegatoria.

Fundamento este recurso en base a los siguientes

HECHOS

Primero.- Se presentó solicitud de autorización de residencia temporal por reagrupación familiar de D./Dña. [NOMBRE Y APELLIDOS] por parte de su hermana Dña. [NOMBRE Y APELLIDOS], quien acreditó ser representante legal de la misma mediante acta de tutela que se adjuntó con la solicitud.

Segundo.- Dicha solicitud fue resuelta favorablemente por la Delegación del Gobierno en Madrid, mediante resolución de [FECHA] por la que se concedía la autorización de residencia temporal por reagrupación familiar solicitada.

Se adjunta a efectos de prueba copia de la resolución mencionada.

Tercero.- Posteriormente, se procedió a solicitar el correspondiente visado el día [FECHA].

El Consulado de España en [COMPLETAR], sin embargo, requirió para que se aportase sentencia del Juez marroquí de concesión de la tutela dativa con representación legal a favor de la reagrupante.

Alegó la interesada que no le era posible adjuntar dicha documentación de acuerdo al derecho de familia marroquí, pero que la representación legal de la familiar reagrupada constaba acreditada mediante la documentación adjunta con la solicitud.

Documentación que la Delegación del Gobierno en Madrid, como hemos expuesto anteriormente, también consideró suficiente para acreditar el requisito legal de la representación legal de la reagrupada.

Quinto.- A pesar de lo expuesto, el Consulado de España ha dado a la solicitante por desistida de su solicitud, por lo que ha tenido por concluido el procedimiento y contra la que se interpone el presente recurso.

Sexto.- A efectos de notificaciones, se designa el siguiente domicilio:

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el art. 124 de la Ley 39/2015, de 1 de octubre (en adelante, LPACAP), este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el art. 123 de la LPACAP, este recurso se presenta ante el órgano que dictó la resolución.

III

En la solicitud de autorización de residencia por reagrupación familiar y en la tramitación del visado, se ha seguido lo dispuesto por el la Ley Orgánica 4/2000 y el Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba su Reglamento de desarrollo.

En concreto, el art. 17.1.c) de la LO 4/2000 establece que

«El extranjero residente tiene derecho a reagrupar con él en España a los siguientes familiares

c) Los menores de dieciocho años y los mayores de esa edad que no sean objetivamente capaces de proveer a sus propias necesidades, debido a su estado de salud, cuando el residente extranjero sea su representante legal y el acto jurídico del que surgen las facultades representativas no sea contrario a los principios del ordenamiento español».

Por su parte, el art. 66.1.d) del Real Decreto 1155/2024, de 19 de noviembre, establece que:

«La persona extranjera podrá reagrupar en España a los siguientes familiares:

[COMPLETAR]

d) Las personas representadas legalmente por la persona reagrupante, cuando sean menores de dieciocho años en el momento de la solicitud de la autorización de residencia a su favor o los mayores de esa edad que tengan una discapacidad que requiera de apoyo, o los mayores de edad que no sean objetivamente capaces de proveer a sus propias necesidades debido a su estado de salud, siempre que el acto jurídico del que surgen las facultades representativas no sea contrario a los principios del ordenamiento español».

A continuación, los arts. 68 y ss del Real Decreto 1155/2024, regulan el procedimiento para la solicitud de autorización de residencia temporal por reagrupación familiar y, en caso de concesión, del correspondiente visado.

IV

Recordemos que en este caso se había producida ya la concesión de la autorización de residencia, por lo que el Consulado sólo hubiera debido centrarse en la concurrencia los requisitos para la concesión del visado contemplados en los artículos 38 y 40 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: El art. 67 contiene los requisitos del reagrupante para la autorización (medios, vivienda, seguro...). Los requisitos del visado son los del art. 38, y el art. 40.2 delimita lo que valora el consulado. Esto refuerza el argumento del formulario. Fuente: RD 1155/2024, arts. 38, 40.2 y 67 (BOE-A-2024-24099).].

Es de aplicación al caso, por tanto, la Sentencia del Tribunal Supremo de 5 de octubre de 2011 (Rec. 5245/2008) que estableció que:

«Al resolver sobre la solicitud de visado de esa manera, el Cónsul vino a considerar, aunque fuera de forma implícita pero en todo caso evidente, que la Subdelegación del Gobierno en Castellón (que ya había tenido que valorar la concurrencia del requisito controvertido) se había equivocado al conceder el permiso de residencia temporal por reagrupación familiar en favor de la ahora recurrente. Empero, si un órgano de la Administración llega a la conclusión de que otro órgano de la misma Administración ha interpretado o aplicado mal el Derecho y ha concedido lo que no debía, no puede obviar lo acordado y reconducir las cosas según su criterio sobre lo que es o no conforme a derecho, sino que ha de estar y pasar por lo reconocido, sin perjuicio de promover (si procede) la revisión de oficio de lo que reputa incorrectamente concedido.

Por tal razón, si el Cónsul apreciaba, como apreció, que esa dependencia no existía, pero tal consideración fue únicamente fruto de su subjetiva valoración de las circunstancias concurrentes y no de otros factores (como, v.gr., la verificación de que los documentos aportados a la Subdelegación del Gobierno mediante copia incurrían en algún tipo de falsedad), debió haberse abstenido de valorar aquello que ya había sido tomado en consideración por la Subdelegación del Gobierno, y conceder el visado; siendo cuestión distinta la eventual posibilidad y viabilidad legal de promover la revisión de oficio de lo acordado por la Subdelegación.

Las razones antedichas conducen a la estimación del recurso de casación y del contencioso administrativo previo. En efecto, la resolución de la Delegación del Gobierno de Cantabria de 39 de junio de 2.009 fue motivada y asegura el cumplimiento por la reagrupante del derecho ejercido a la reagrupación familiar, sin que por parte del Consulado de Casablanca se mencionen circunstancias o hechos que no hubieran sido ya examinados por el primero de ambos órganos.»

En el mismo sentido se han pronunciado muchas otras sentencias del Tribunal Supremo, como la del veintisiete de diciembre de dos mil doce (Rec. 3287/2012).

Otorgada la autorización temporal de residencia por reagrupación familiar por el órgano competente -en el caso de autos, la Delegación del Gobierno de Cantabria-, no puede denegarse el visado por el Consulado correspondiente si no es por causas no examinadas por aquél órgano o, dicho en otros términos, no puede proceder a reexaminar lo ya visto y resuelto por el citado órgano competente.

En el presente caso la Delegación del Gobierno en Madrid ya había examinado la concurrencia de los requisitos relativos a la condición de familiar reagrupable de Mariam El Omari, por lo que el Consulado no hubiera debido entrar en valorar dicha circunstancia y no hubiera debido solicitar documentación alguna.

Al hacerlo, y de acuerdo con la doctrina del Tribunal Supremo que hemos expuesto, ha actuado de forma indebida, excediéndose de sus competencias en el procedimiento, por lo que se ha incurrido en causa de anulabilidad de la resolución recurrida según establece el art. 48 de la LPACAP.

Por todo lo expuesto

SOLICITO

Que se tenga por presentado el presente recurso con la documentación que se adjunta y previos los trámites oportunos sea concedido el visado solicitado, al considerar que los hechos y la documentación adjunta, desvirtúan los fundamentos de derecho de la resolución recurrida.

En [LUGAR], a [FECHA].

Fdo.: 	Fdo.:
