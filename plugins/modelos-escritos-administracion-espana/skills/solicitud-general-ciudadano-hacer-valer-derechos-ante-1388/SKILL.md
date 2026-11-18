---
name: solicitud-general-ciudadano-hacer-valer-derechos-ante-1388
description: "Redacta el escrito «Solicitud general del ciudadano para hacer valer sus derechos ante la Administración» (formulario 1388 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud general del ciudadano para hacer valer sus derechos ante la Administración

> Formulario 1388 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…d de este escrito y ante la necesidad de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (9)

Inclúyelos solo si encajan en los hechos:

- A conocer, en cualquier momento, el estado de la tramitación de los procedimientos en los que tengan la condic…
- A identificar a las autoridades y al personal al servicio de las Administraciones Públicas bajo cuya responsab…
- A no presentar documentos originales salvo que, de manera excepcional, la normativa reguladora aplicable estab…
- A no presentar datos y documentos no exigidos por las normas aplicables al procedimiento de que se trate, que …
- A formular alegaciones, utilizar los medios de defensa admitidos por el Ordenamiento Jurídico, y a aportar doc…
- A obtener información y orientación acerca de los requisitos jurídicos o técnicos que las disposiciones vigent…
- A actuar asistidos de asesor cuando lo consideren conveniente en defensa de sus intereses.…
- A cumplir las obligaciones de pago a través de los medios electrónicos previstos en el artículo 98.2 LPACAP.…
- A cualesquiera otros que les reconozcan la Constitución y las leyes.…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66.1 de la Ley 39/2015
- artículo 53 de la Ley 39/2015
- artículo 98.2 LPACAP

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

### Formulario 1388 · Solicitud general del ciudadano para hacer valer sus derechos ante la Administración

- Año del modelo: 2004
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 9 párrafos opcionales señalados; 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]

conforme al artículo 66.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,

actuando

[ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original]

ante comparece, y como mejor proceda en derecho,

EXPONE:

Que, en virtud de este escrito y ante la necesidad de [COMPLETAR], al amparo de lo establecido en el artículo 53 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, en cuanto ciudadano en sus relaciones con las Administraciones Públicas, ejercita el siguiente derecho:

[OPCIONAL — incluir si procede]

A conocer, en cualquier momento, el estado de la tramitación de los procedimientos en los que tengan la condición de interesados; el sentido del silencio administrativo que corresponda, en caso de que la Administración no dicte ni notifique resolución expresa en plazo; el órgano competente para su instrucción, en su caso, y resolución; y los actos de trámite dictados. Asimismo, también tendrán derecho a acceder y a obtener copia de los documentos contenidos en los citados procedimientos.

Quienes se relacionen con las Administraciones Públicas a través de medios electrónicos, tendrán derecho a consultar la información a la que se refiere el párrafo anterior, en el Punto de Acceso General electrónico de la Administración que funcionará como un portal de acceso. Se entenderá cumplida la obligación de la Administración de facilitar copias de los documentos contenidos en los procedimientos mediante la puesta a disposición de las mismas en el Punto de Acceso General electrónico de la Administración competente o en las sedes electrónicas que correspondan.

[OPCIONAL — incluir si procede]

A identificar a las autoridades y al personal al servicio de las Administraciones Públicas bajo cuya responsabilidad se tramiten los procedimientos.

[OPCIONAL — incluir si procede]

A no presentar documentos originales salvo que, de manera excepcional, la normativa reguladora aplicable establezca lo contrario. En caso de que, excepcionalmente, deban presentar un documento original, tendrán derecho a obtener una copia autenticada de éste.

[OPCIONAL — incluir si procede]

A no presentar datos y documentos no exigidos por las normas aplicables al procedimiento de que se trate, que ya se encuentren en poder de las Administraciones Públicas o que hayan sido elaborados por éstas.

[OPCIONAL — incluir si procede]

A formular alegaciones, utilizar los medios de defensa admitidos por el Ordenamiento Jurídico, y a aportar documentos en cualquier fase del procedimiento anterior al trámite de audiencia, que deberán ser tenidos en cuenta por el órgano competente al redactar la propuesta de resolución.

[OPCIONAL — incluir si procede]

A obtener información y orientación acerca de los requisitos jurídicos o técnicos que las disposiciones vigentes impongan a los proyectos, actuaciones o solicitudes que se propongan realizar.

[OPCIONAL — incluir si procede]

A actuar asistidos de asesor cuando lo consideren conveniente en defensa de sus intereses.

[OPCIONAL — incluir si procede]

A cumplir las obligaciones de pago a través de los medios electrónicos previstos en el artículo 98.2 LPACAP.

[OPCIONAL — incluir si procede]

A cualesquiera otros que les reconozcan la Constitución y las leyes.

El derecho que el interesado pretende hacer efectivo en virtud de este escrito resulta necesario para la correcta defensa de sus intereses legítimos por las razones que seguidamente se indican y así se acreditan mediante la siguiente documentación:

Por lo expuesto,

SOLICITA:

Que se tenga por presentado este escrito, con los documentos que se acompañan y, de conformidad con lo manifestado en el mismo se acceda a hacer efectivo el derecho de este ciudadano en sus relaciones con las Administraciones Públicas, en los términos solicitados.

En [LUGAR], a [FECHA].

Firmado:
