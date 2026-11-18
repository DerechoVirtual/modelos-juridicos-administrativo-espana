---
name: pedir-certificado-escolar-obtener-residencia-legal-69
description: "Redacta el escrito «Pedir certificado escolar para obtener la residencia legal» (formulario 69 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir certificado escolar para obtener la residencia legal

> Formulario 0069 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR (2 veces)
- [ ] FECHA (2 veces)
- [ ] DNI/NIE (3 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD
- [ ] NACIONALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] C.P.
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, a [FECHA]. D.»; «…, a [FECHA]. D. [COMPLETAR], ciudadano»; «…y Dña. [NOMBRE Y APELLIDOS], ciudadana»; «…, N.º [NÚMERO],»; «…, [COMPLETAR] CP [C.P.]. Tercero.-»; «…cadémico 20/20 Cuarto.- Que con fecha de»; «…centro de enseñanza oficial autorizado.»»; «…, N.º [NÚMERO],»; «…artículo 160.3, se acredita que el menor»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 1155/2024
- Ley Orgánica 4/2000
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

### Formulario 0069 · Pedir certificado escolar para obtener la residencia legal

- Año del modelo: 2019
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (DNI/NIE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

SECRETARÍA DEL COLEGIO PÚBLICO

En [LUGAR], a [FECHA].

D. [COMPLETAR], ciudadano [COMPLETAR] con residencia legal y NIE [DNI/NIE] y Dña. [NOMBRE Y APELLIDOS], ciudadana [COMPLETAR] con pasaporte nº [DNI/NIE], manifiestan:

HECHOS

Primero.- Que los arriba referenciados son los progenitores del menor, nacido en [LOCALIDAD] y de nacionalidad [NACIONALIDAD], que es poseedor del pasaporte nº [DNI/NIE]:

Segundo.- Que tanto los progenitores como su menor, tienen su domicilio familiar en la C/ [CALLE], N.º [NÚMERO], [COMPLETAR] CP [C.P.].

Tercero.- [COMPLETAR], cursa educación obligatoria en este Centro, desde el curso académico 20/20

Cuarto.- Que con fecha de [COMPLETAR], D. [NOMBRE Y APELLIDOS], ha obtenido su residencia legal en España, siendo desde entonces, titular de una autorización de residencia y trabajo.

FUNDAMENTOS DE DERECHO

Primero.- Que el Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, sobre derechos y libertades de los extranjeros en España y su integración social, en su artículo 160 establece que:

«1. Los hijos, biológicos o adoptivos, no nacidos en España que sean solteros y menores de dieciocho años en el momento de la solicitud, y que se encuentren acompañados del progenitor extranjero con residencia en nuestro país o los hijos que tengan una discapacidad y no sean objetivamente capaces de proveer sus propias necesidades debido a su estado de salud y siempre que, en ambos casos, no hayan constituido su propia unidad familiar, podrán obtener una autorización de residencia temporal cuando se acredite su permanencia continuada e ininterrumpida en España durante un mínimo de dos años previos a la fecha de la solicitud y sus padres o tutores cumplan los requisitos de medios económicos y alojamiento exigidos en este reglamento para ejercer el derecho a la reagrupación familiar.

Cuando se trate de hijos de uno solo de los cónyuges o miembros de la pareja se requerirá, además, que éste ejerza en solitario la patria potestad, que se le haya otorgado la custodia con carácter exclusivo y se haya autorizado el traslado de residencia del menor a España por la autoridad judicial o bajo consentimiento del otro progenitor, o que se haya otorgado con carácter compartido, siempre que el otro titular del derecho de custodia haya dado su consentimiento para que resida en territorio nacional.

No obstante lo anterior, también se admitirá la presentación de la solicitud mientras se encuentre en trámite la autorización de residencia del progenitor.

2. Cuando se cumplan los requisitos establecidos en el apartado anterior, también podrán acceder al mismo tipo de autorización, los que sean menores de dieciocho años en el momento de la solicitud acompañados por la persona extranjera residente en España que ejerza legalmente su tutela, siempre y cuando esta relación haya sido constituida conforme al ordenamiento jurídico español.
3. Cuando los menores se encuentren en edad de escolarización obligatoria, se deberá acreditar en el procedimiento que se encuentra matriculado en un centro de enseñanza oficial autorizado.» [COMPLETAR].

Segundo.- El procedimiento seguido respetará en todo caso lo formulado en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

Tercero.- Se señala como domicilio a efectos de notificaciones, el sito en la C/ [CALLE], N.º [NÚMERO], [COMPLETAR] CP.

Por todo ello, y con el fin de solicitar la residencia legal de su hijo, D. y Dña. [NOMBRE Y APELLIDOS]:

Solicitan ante este Colegio ACREDITACIÓN FORMAL de:

Que, tal y como exige el artículo 160.3, se acredita que el menor [COMPLETAR], está matriculado en este Centro desde la fecha referida, y que ha venido asistiendo de manera regular a clase, con máximo aprovechamiento de los mismas.

En [LUGAR], a [FECHA].

Fdo: D. [NOMBRE Y APELLIDOS]

Fdo: Dña. [NOMBRE Y APELLIDOS]
