---
name: reposicion-residencia-larga-duracion-antecedentes-360
description: "Redacta el escrito «Reposición en residencia de larga duración por antecedentes penales» (formulario 360 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición en residencia de larga duración por antecedentes penales

> Formulario 0360 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Larga duración: no se exige carecer de antecedentes, pero los arts. 177.4-5 y 184.4-5 RD 1155/2024 permiten denegarla por amenaza al orden público: matizar el argumento.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NACIONALIDAD
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DEL GOBIERNO EN»; «…, a [FECHA]. Fdo.:»

## Elecciones que hay que hacer

- DELEGACIÓN / SUBDELEGACIÓN

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 124 de la Ley 39/2015
- artículo 123.1 de la Ley 39/2015
- artículo 32 de la LO 4/2000
- artículo 32.4 LO 4/2000
- artículo 117 de la Ley 39/2015
- Real Decreto 1155/2024

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

### Formulario 0360 · Reposición en residencia de larga duración por antecedentes penales

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 desplegables convertidos en elección en blanco; 11 campos de relleno marcados en blanco
- Avisos de la revisión: Larga duración: no se exige carecer de antecedentes, pero los arts. 177.4-5 y 184.4-5 RD 1155/2024 permiten denegarla por amenaza al orden público: matizar el argumento.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: DELEGACIÓN / SUBDELEGACIÓN] DEL GOBIERNO EN [COMPLETAR]

Referencia Expediente:

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad [NACIONALIDAD], con N.I.E. y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES] en la C/ [CALLE], ante este organismo comparezco para formular RECURSO DE REPOSICIÓN contra la resolución de fecha [FECHA], por la que denegaba la solicitud de autorización de residencia de larga duración.

Fundamento este recurso en base a los siguientes:

HECHOS

Primero.- El recurrente era titular de autorización de residencia y trabajo, la cual caducaba el día [FECHA]. Habiendo cumplido el plazo de cinco años de residencia legal en España, se presentó solicitud de autorización de residencia de larga duración.

Segundo.- Dicha solicitud fue denegada mediante resolución de fecha [FECHA], copia de la cual se adjunta con el presente escrito.

Tercero.- El motivo de la denegación fue que constaban antecedentes penales del solicitante en España.

Cuarto.- El interesado presenta una situación de arraigo familiar y laboral en España, pues dispone de empleo y convive con su hermana, D./Dña. [NOMBRE Y APELLIDOS], la cual es residente legal en España.

A efectos de prueba, se adjunta copia de la siguiente documentación:

— Certificados de nacimiento del interesado y de su hermana.
— Tarjeta de residencia de la hermana del interesado.
— Contrato de trabajo del que dispone en la actualidad el interesado.

A los anteriores hechos, son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el artículo 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el artículo 123.1 de la Ley 39/2015, de 1 de octubre, este recurso se presenta ante el órgano que dictó la resolución.

III

En el presente caso, la denegación de lo solicitado no tiene amparo legal, pues la LO 4/2000 no exige, como requisito para la concesión de la residencia de larga duración, la carencia de antecedentes penales en España.

El artículo 32 de la LO 4/2000 tan sólo establece que:

«2. Tendrán derecho a residencia de larga duración los que hayan tenido residencia temporal en España durante cinco años de forma continuada, que reúnan las condiciones que se establezcan reglamentariamente. A los efectos de obtener la residencia de larga duración computarán los periodos de residencia previa y continuada en otros Estados miembros, como titular de la tarjeta azul de la UE. Se considerará que la residencia ha sido continuada aunque por períodos de vacaciones u otras razones que se establezcan reglamentariamente el extranjero haya abandonado el territorio nacional temporalmente.
3. Los extranjeros residentes de larga duración en otro Estado miembro de la Unión Europea podrán solicitar por sí mismos y obtener una autorización de residencia de larga duración en España cuando vayan a desarrollar una actividad por cuenta propia o ajena, o por otros fines, en las condiciones que se establezcan reglamentariamente. No obstante, en el supuesto de que los extranjeros residentes de larga duración en otro estado miembro de la Unión Europea deseen conservar el estatuto de residente de larga duración adquirido en el primer estado miembro, podrán solicitar y obtener una autorización de residencia temporal en España.
3 bis. Los extranjeros a quienes España u otro Estado miembro de la Unión Europea hubiese reconocido protección internacional y que se encuentren en España, podrán solicitar por sí mismos y obtener una autorización de residencia de larga duración en España en las condiciones que se establezcan reglamentariamente».

La LO 4/2000, como decíamos, sí establece en su artículo 31 que, para autorizar la residencia temporal, será preciso carecer de antecedentes penales, pero dicha exigencia en ningún caso debe considerarse extensiva a la residencia de larga duración.

Por su parte, el Real Decreto 1155/2024, de 19 de noviembre, cuando desarrolla los requisitos para la obtención de la autorización de residencia de larga duración —tal y como habilita el artículo 32.4 LO 4/2000— en sus artículos 176 (para Unión Europea), 179 (para otro [NOTA DE REVISIÓN: El art. 176 (requisitos de larga duración-UE) es correcto. El 179 regula la larga duración en España del residente de larga duración-UE en otro Estado miembro. La larga duración nacional está en los arts. 182-184. Matizar el fondo: ninguno exige carecer de antecedentes, pero los arts. 177.4-5 y 184.4-5 obligan a recabar de oficio el certificado de antecedentes y el informe policial, y permiten denegar si la persona «representa una amenaza por motivos de orden público o de seguridad pública». Fuente: RD 1155/2024, arts. 176, 177, 179, 183 y 184 (BOE-A-2024-24099); LO 4/2000, art. 32 (BOE-A-2000-544).] Estado de la Unión Europea), 183 (para España), tampoco exige la carencia de antecedentes penales para su obtención. Exige la aportación del certificado de antecedentes penales (en todas las modalidades de autorización de residencia de larga duración), pero no puede entenderse que quepa exigir que dicho certificado sea negativo para que sea concedida la autorización solicitada.

IV

Suspensión de la ejecución de la resolución recurrida

El artículo 117 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas establece:

«Que la impugnación se fundamente en alguna de las causas de nulidad de pleno derecho previstas en el artículo 47.1 de esta Ley.

3. La ejecución del acto impugnado se entenderá suspendida si transcurridos treinta días desde que la solicitud de suspensión haya tenido entrada en el registro del órgano competente para decidir sobre la misma, éste no ha dictado resolución expresa al respecto. En estos casos no será de aplicación lo establecido en el artículo 21.4, segundo párrafo, de esta Ley.»

En este caso, resulta evidente el perjuicio que para el interesado supone quedar en situación de irregularidad mientras se tramita el recurso, sin posibilidad de realizar trabajo remunerado alguno, ni de hacerse cargo de sus cargas familiares, situación que no quedaría subsanada por una posterior estimación del recurso.

Por otra parte, no se aprecia que dicha suspensión pueda causar perjuicio alguno al interés público ni a terceros, por lo que se considera plenamente apropiado en este caso proceder a la suspensión de la ejecución de la resolución recurrida.

Por lo expuesto,

SOLICITO

Que sea anulada la resolución recurrida y se emita una nueva por la que se conceda al recurrente la autorización de residencia de larga duración solicitada, así como que se suspenda la ejecución de la resolución recurrida durante la tramitación del recurso.

En [LUGAR], a [FECHA].

Fdo.: [COMPLETAR].
