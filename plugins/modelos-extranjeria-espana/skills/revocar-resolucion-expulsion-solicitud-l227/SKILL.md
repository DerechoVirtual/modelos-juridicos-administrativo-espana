---
name: revocar-resolucion-expulsion-solicitud-l227
description: "Redacta el escrito «Revocar la resolución de expulsión: solicitud» (formulario 227 (Laboral) de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revocar la resolución de expulsión: solicitud

> Formulario 0227 de la colección de Laboral del plugin **Extranjería** · revisado el 17-11-2026.

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

- Familiar de español: régimen propio en los arts. 93-99 RD 1155/2024; LOFAGE derogada por la Ley 40/2015; art. 109.1 LPAC limita la revocación al plazo de prescripción.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NÚMERO
- [ ] DNI/NIE (4 veces)
- [ ] COLEGIO
- [ ] NACIONALIDAD
- [ ] PROFESIÓN
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ELEGADO (AL SUBDELEGADO) DEL GOBIERNO DE»; «…Nacionalidad:»; «…, con despacho profesional en esa ciudad»; «…, mayor de edad, hijo de»; «…, mayor de edad, hijo de [COMPLETAR] y»; «…, con domicilio familiar actual en»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] se acordó por el»; «…, en la localidad de»; «…, el día [FECHA] de»; «…, Sección»; …

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 53.1.a) de la Ley Orgánica 4/2000
- artículo 109 de la Ley 39/2015
- artículo 55.2 de la vigente Ley Orgánica 4/2000
- artículo 75.f) de la Ley 40/2015
- Real Decreto 1155/2024

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, conciliación o mediación previa, reclamación previa o vía administrativa, según el caso).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0227 · Revocar la resolución de expulsión: solicitud

- Año del modelo: 2019
- Revisión 17-11-2026: 5 citas normativas corregidas tras comprobarlas en el BOE; 30 campos de relleno marcados en blanco; 2 etiquetas sin dato marcadas en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Familiar de español: régimen propio en los arts. 93-99 RD 1155/2024; LOFAGE derogada por la Ley 40/2015; art. 109.1 LPAC limita la revocación al plazo de prescripción.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

SOLICITUD DE REVOCACIÓN DE RESOLUCIÓN DE EXPULSIÓN

AL DELEGADO (AL SUBDELEGADO) DEL GOBIERNO DE [COMPLETAR]

Expte. Expulsión

D. [NOMBRE Y APELLIDOS]

Nacionalidad: [COMPLETAR]

Proc. n.º [NÚMERO]

NIE n.º [DNI/NIE]

D. [NOMBRE Y APELLIDOS], Letrado del Colegio de Abogados de [COLEGIO], con despacho profesional en esa ciudad [COMPLETAR], junto con D. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], de profesión [PROFESIÓN], mayor de edad, hijo de [COMPLETAR] y [COMPLETAR], con pasaporte n.º [DNI/NIE] y con NIE n.º [DNI/NIE], y su esposa Dña. [NOMBRE Y APELLIDOS], de nacionalidad española, con DNI n.º [DNI/NIE], con domicilio familiar actual en [COMPLETAR], calle [CALLE], comparecen y como mejor proceda, DICEN:

HECHOS

1.º Que con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se acordó por el [COMPLETAR] la incoación de procedimiento preferente de expulsión del compareciente D. [NOMBRE Y APELLIDOS], por el motivo de «Encontrarse irregularmente en territorio español» contemplado en el artículo 53.1.a) de la Ley Orgánica 4/2000 [NOTA DE REVISIÓN: Cita de apartado. Fuente: LO 4/2000, BOE-A-2000-544, art. 53.1.a.], de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social. Se adjunta copia del acuerdo de incoación como doc. n.º 1.

2.º Que posteriormente el Sr. ha contraído matrimonio con la nacional española también compareciente Dña. [NOMBRE Y APELLIDOS], en la localidad de [COMPLETAR], el día [FECHA] de [COMPLETAR] matrimonio inscrito en el Registro Civil de [LOCALIDAD], Sección [COMPLETAR]; Tomo [COMPLETAR], Pág. se adjunta Copia compulsada de certificación literal de matrimonio como doc. n.° 2.

3.º Que siendo intención de los comparecientes fijar y documentar su residencia en España, con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] el Sr. solicitó de la delegación del Gobierno en [LOCALIDAD] la autorización de residencia temporal de familiar de persona de nacionalidad española [NOTA DE REVISIÓN (comprobar): Denominación del RD 1155/2024 (aparece dos veces: hecho 3.º y documento n.º 3). Fuente: RD 1155/2024, BOE-A-2024-24099 (vigente desde 20-5-2025), arts. 93-97.]. Se adjunta copia de la solicitud como doc. n.° 3.

4.º Que por medio del presente escrito y de conformidad con lo prevenido en el artículo 109 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, se insta la revocación del expediente de expulsión. Teniendo en cuenta que el posterior matrimonio con ciudadano español permite legalizar la situación del cónyuge de ciudadano español en España al poder acceder a la autorización de residencia temporal de familiar de persona de nacionalidad española regulada en los artículos 93 a 99 del Reglamento aprobado por el Real Decreto 1155/2024, de 19 de noviembre [NOTA DE REVISIÓN (comprobar): El RD 240/2007 se aplica a familiares de ciudadanos de otro Estado de la UE/EEE (art. 2); los familiares de españoles tienen régimen propio en el RD 1155/2024 (arts. 93-99; el TS anuló un inciso del art. 94.1.f el 8-7-2026, BOE-A-2026-19632). Si el español ejerció la libre circulación, valorar el caso concreto. Fuente: RD 1155/2024, BOE-A-2024-24099 (vigente desde 20-5-2025), arts. 93-99; RD 240/2007, BOE-A-2007-4184, art. 2.], por lo que quedarían desvirtuados igualmente los supuestos por el cual se dictó la resolución de expulsión.

FUNDAMENTOS DE DERECHO

I. Las Administraciones públicas pueden revocar, mientras no haya transcurrido el plazo de prescripción, sus actos de gravamen o desfavorables [NOTA DE REVISIÓN: Paráfrasis del antiguo art. 105 Ley 30/1992; el art. 109.1 LPAC limita la revocación al plazo de prescripción. Fuente: Ley 39/2015, BOE-A-2015-10565, art. 109.1.], en particular en aquellos supuestos de ineficacia posterior sobrevenida, siempre que tal revocación no sea contraria al ordenamiento jurídico (artículo 109 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas).

II. El Subdelegado del Gobierno tiene competencia para resolver sobre expulsiones de extranjeros del territorio nacional según lo dispuesto en el artículo 55.2 de la vigente Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social.

Y también el artículo 75.f) de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público. [NOTA DE REVISIÓN (comprobar): La LOFAGE fue derogada por la Ley 40/2015 (DDU c). El art. 75.f atribuye a los Subdelegados la potestad sancionadora que les confieran las normas; la competencia específica sigue siendo el art. 55.2 LOEX. Fuente: Ley 40/2015, BOE-A-2015-10566, DDU c) y art. 75.f; LO 4/2000, BOE-A-2000-544, art. 55.2.]

DOCUMENTOS QUE SE APORTAN: [COMPLETAR]

1.º Copia del acuerdo de incoación. Doc. n.° 1.

2.º Copia compulsada de la certificación literal del matrimonio contraído. Doc. n.° 2.

3.º Copia de la solicitud de autorización de residencia temporal de familiar de persona de nacionalidad española. Doc. n.° 3.

Por lo expuesto,

SOLICITO DE ESA SUBDELEGACIÓN DEL GOBIERNO DE [LOCALIDAD], que tenga por presentado este escrito, con los documentos que se acompañan. se sirva admitir todo ello, y a su vista, y previos los trámites pertinentes, proceda acordar la revocación de la resolución de expulsión dictada contra la nacional

OTROSÍ DECIMOS: Que una vez acordada la revocación se deberá proceder a la devolución del pasaporte original de la expedientada depositado en el Grupo Operativo de extranjeros de la Comisaría Provincial de

En [LUGAR], a [DÍA] de [MES] de [AÑO].

════════════════════════════════════════════════════════════════════════
