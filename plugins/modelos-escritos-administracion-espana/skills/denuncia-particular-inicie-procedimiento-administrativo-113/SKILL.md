---
name: denuncia-particular-inicie-procedimiento-administrativo-113
description: "Redacta el escrito «Denuncia de un particular para que se inicie un procedimiento administrativo» (formulario 113 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia de un particular para que se inicie un procedimiento administrativo

> Formulario 0113 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] DESCRIBIR (2 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ivo de oficio a los efectos de PRIMERO.-»; «…ado en la narración la fecha de comisión»; «…to administrativo que haya de incoarse a»; «…ión de procedimiento administrativo para»; «…chos objeto de la presente denuncia: 1.-»; «…2.-»; «…2.- [COMPLETAR] 3.-»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (7)

Inclúyelos solo si encajan en los hechos:

- SEGUNDO.- Que tratándose de hechos que pueden ser constitutivos de infracción administrativa se ha señalado en…
- TERCERO.- Que de conformidad al art. 4 de la LPACAP, el denunciante se considera interesado en el procedimient…
- CUARTO.- Que de conformidad al art. 4 de la LPACAP, se consideran interesados en el procedimiento administrati…
- QUINTO.- Que los hechos objeto de la presente denuncia suponen un perjuicio en el patrimonio de las Administra…
- SEXTO.- Previéndose en el procedimiento la notificación de la resolución de inicio del procedimiento procede q…
- PRIMER OTROSÍ DIGO que adjunto al presente escrito se acompañan los siguientes documentos a fin de acreditar l…
- SEGUNDO OTROSÍ DIGO que al amparo del art. 56 de la LPACAP procede y así se insta la adopción de MEDIDAS CAUTE…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66.1 de la Ley 39/2015
- art. 62 de la Ley 39/2015
- art. 4 de la LPACAP
- art. 56 de la LPACAP

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

### Formulario 0113 · Denuncia de un particular para que se inicie un procedimiento administrativo

- Año del modelo: 2018
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 7 párrafos opcionales señalados; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al [ÓRGANO AL QUE SE DIRIGE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.]

conforme al artículo 66.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,

actuando

[ELEGIR UNA OPCIÓN Y REDACTARLA: Comparecer por sí mismo / Comparecer en representación — el texto de cada opción no venía en el formulario original]

ante comparece, y como mejor proceda

EXPONE:

Que mediante el presente escrito y al amparo del art. 62 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (LPACAP) se formula DENUNCIA de los hechos que seguidamente se relacionan por entender que los mismos deben dar lugar al inicio de un procedimiento administrativo de oficio a los efectos de

PRIMERO.- [COMPLETAR]

1.1.-...

1.2.-...

[OPCIONAL — incluir si procede]

SEGUNDO.- Que tratándose de hechos que pueden ser constitutivos de infracción administrativa se ha señalado en la narración la fecha de comisión [COMPLETAR] de los mismos, así como de los datos de que se dispone para la identificación de los presuntos responsables.

[OPCIONAL — incluir si procede]

TERCERO.- Que de conformidad al art. 4 de la LPACAP, el denunciante se considera interesado en el procedimiento administrativo que haya de incoarse por los siguientes motivos [DESCRIBIR]:

En virtud de lo anterior, procede que se tenga por interesado al denunciante, notificándosele las resoluciones que se adopten en el procedimiento con posibilidad de intervenir en el mismo conforme a los trámites previstos en el mismo.

[OPCIONAL — incluir si procede]

CUARTO.- Que de conformidad al art. 4 de la LPACAP, se consideran interesados en el procedimiento administrativo que haya de incoarse a [COMPLETAR]. Debe por tanto notificarse la incoación del expediente a los mismos, con posibilidad de personarse y ser parte en el procedimiento.

[OPCIONAL — incluir si procede]

QUINTO.- Que los hechos objeto de la presente denuncia suponen un perjuicio en el patrimonio de las Administraciones Públicas, consistente en [DESCRIBIR]. El acuerdo de inicio del procedimiento o el que se dicte acordonando no haber lugar a iniciarlo, debidamente motivado, debe ser notificado a quien suscribe la presente denuncia.

[OPCIONAL — incluir si procede]

SEXTO.- Previéndose en el procedimiento la notificación de la resolución de inicio del procedimiento procede que se dé traslado de la misma.

Por cuanto antecede

SOLICITA

Que se tenga por presentado este escrito con los documentos que lo acompañan y se tenga por formulada denuncia de los hechos que en el mismo se relacionan y en su virtud se acuerde la incoación de procedimiento administrativo para [COMPLETAR] teniendo por parte a quien suscribe la presente denuncia.

[OPCIONAL — incluir si procede]

PRIMER OTROSÍ DIGO que adjunto al presente escrito se acompañan los siguientes documentos a fin de acreditar los hechos objeto de la presente denuncia:

1.- [COMPLETAR]
2.- [COMPLETAR]
3.- [COMPLETAR]

SOLICITO que se incorporen al procedimiento acordado que sea su inicio.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSÍ DIGO que al amparo del art. 56 de la LPACAP procede y así se insta la adopción de MEDIDAS CAUTELARES antes de la iniciación del procedimiento administrativo/ en el mismo acto de inicio del procedimiento a fin de asegurar la eficacia de la resolución que ponga fin al procedimiento con fundamento en los siguientes MOTIVOS:

Por cuanto antecede

SOLICITO que se adopten las medidas cautelares que se interesan.

En [LUGAR], a [FECHA].

Firmado:
