---
name: dictamen-consejo-estado-u-organo-autonomico-equivalente-125
description: "Redacta el escrito «Dictamen del Consejo de Estado u órgano autonómico equivalente sobre nulidad de actos» (formulario 125 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Dictamen del Consejo de Estado u órgano autonómico equivalente sobre nulidad de actos

> Formulario 0125 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] FECHA (6 veces)
- [ ] ÓRGANO O PERSONA
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…eral EXCMO. SR.: El pleno del Consejo de»; «…ad, el siguiente dictamen: El Consejo de»; «…mplimiento de la comunicación de V.E. de»; «…ha examinado el expediente instruido por»; «…, por»; «…l expediente remitido está integrado por»; «…rados y foliados, de los cuales del 1 al»; «…, por»; «… perfectamente incardinable en el inciso»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 32.2 y 39.1 de la Ley 40/2015
- Ley 39/2015

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

### Formulario 0125 · Dictamen del Consejo de Estado u órgano autonómico equivalente sobre nulidad de actos

- Año del modelo: 2017
- Revisión 17-11-2026: 26 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Dictamen núm. [Nº]:

D./Dña. [NOMBRE Y APELLIDOS]

Presidente

Ilmo. Sr. [ÓRGANO AL QUE SE DIRIGE]

D./Dña. [NOMBRE Y APELLIDOS]

Vicepresidente

Consejeros

Ilmos. Srs.

D./Dña. [NOMBRE Y APELLIDOS]

D./Dña. [NOMBRE Y APELLIDOS]

D./Dña. [NOMBRE Y APELLIDOS]

Ilmo. Sr. [NOMBRE Y APELLIDOS]:

D./Dña. [NOMBRE Y APELLIDOS]

Secretario General

EXCMO. SR.:

El pleno del Consejo de [COMPLETAR], en sesión celebrada el día [FECHA], con la asistencia de los señores que a arriba se expresan, emitió, por unanimidad, el siguiente dictamen:

El Consejo de [COMPLETAR], en cumplimiento de la comunicación de V.E. de [COMPLETAR], ha examinado el expediente instruido por [COMPLETAR], sobre la revisión de oficio del acto administrativo adoptado por [ÓRGANO O PERSONA], en fecha [FECHA], sobre [DESCRIBIR], del que resultan los siguientes

I. ANTECEDENTES

A la vista del expediente administrativo se desprende que:

Primero.- Por la autoridad competente se ha remitido a este Consejo expediente relativo a la Revisión de Oficio del acto administrativo dictado el día [FECHA], por [COMPLETAR], de acuerdo con lo dispuesto en el artículo 106 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas.

Segundo.- El expediente remitido está integrado por [COMPLETAR] documentos numerados y foliados, de los cuales del 1 al [COMPLETAR] corresponden al expediente al que puso fin la resolución cuya nulidad se formula, y los restantes al expediente de revisión de oficio objeto de consulta.

Tercero.- Con fecha [FECHA], se emitió propuesta de resolución, por el órgano competente para resolver la cuestión de nulidad planteada.

Y, en tal estado de tramitación, V.E. dispuso la remisión del expediente para su dictamen por este Consejo.

II. CONSIDERACIONES

Primera.- Este Alto Órgano Consultivo emite su dictamen, con carácter preceptivo, en cumplimiento de los dispuesto en el art. 106.1 de la Ley del Procedimiento Administrativo Común de las Administraciones Públicas, en relación con la Ley reguladora de este Consejo, puesto que se plantea en el asunto consultado la procedencia de la revisión de oficio por nulidad radical o absoluta de una resolución administrativa.

Segunda.- En lo que respecta a la tramitación procedimental, se han observado las prescripciones legalmente establecidas para la revisión de oficio de actos nulos, según las disposiciones generales de procedimiento administrativo contenías en el Título IV de la LPACAP. Asimismo, se ha concedido audiencia previa a los interesados y se han recabado los diferentes informes preceptivos.

Tercera.- En cuanto al fondo del asunto, el expediente remitido tiene como objeto declarar la nulidad del acto administrativo dictado en fecha [FECHA], por [COMPLETAR], al constatarse que en dicho acto concurre la siguiente causa de nulidad de pleno Derecho de las previstas en el artículo 47.1 de la citada Ley del Procedimiento Administrativo:

En el supuesto que se examina consta acreditada en el expediente la pretendida nulidad, al producirse una clara y grave transgresión del ordenamiento jurídico, resultando perfectamente incardinable en el inciso [COMPLETAR], del artículo 47.1 de la referida Ley 39/2015, de 1 de octubre, por hallarnos ante un acto administrativo contrario al ordenamiento. Además, resulta procedente reconocer a los afectados del derecho a ser indemnizados por responsabilidad de la Administración actuante, dado que concurren las circunstancias previstas en los artículos 32.2 y 39.1 de la Ley 40/2015, de Régimen Jurídico del Sector Público.

En mérito de lo expuesto, es de dictamen formular la siguiente,

III. CONCLUSIÓN

Que procede la revisión de oficio de la Resolución Administrativa sometida a consulta y, en consecuencia, se informa favorablemente la declaración de nulidad de pleno Derecho de dicha resolución adoptada.

Asimismo, procede reconocer a los interesados la indemnización correspondiente por los daños y perjuicios derivados de la declaración de nulidad.

En [LUGAR], a [FECHA].

EL SECRETARIO GENERAL

D./Dña. [NOMBRE Y APELLIDOS]

EL PRESIDENTE

D./Dña. [NOMBRE Y APELLIDOS]
