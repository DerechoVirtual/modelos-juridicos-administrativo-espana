---
name: silencio-positivo-residencia-larga-duracion-certificado-l225
description: "Redacta el escrito «Silencio positivo en la residencia de larga duración: certificado» (formulario 225 (Laboral) de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Silencio positivo en la residencia de larga duración: certificado

> Formulario 0225 de la colección de Laboral del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…SILENCIO POSITIVO Referencia Expediente:»; «…A LA SUBDELEGACIÓN DEL GOBIERNO EN (1)»; «…ón de residencia de larga duración el de»; «…de»; «…, a [DÍA] de [MES] de [AÑO]. Fdo.:»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 24 de la Ley 39/2015
- Ley Orgánica 4/2000

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

### Formulario 0225 · Silencio positivo en la residencia de larga duración: certificado

- Año del modelo: 2019
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 8 campos de relleno marcados en blanco; 1 etiquetas sin dato marcadas en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

RESIDENCIA DE LARGA DURACIÓN: CERTIFICADO SILENCIO POSITIVO

Referencia Expediente: [COMPLETAR]

A LA SUBDELEGACIÓN DEL GOBIERNO EN (1) [COMPLETAR]

D. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], con NIE [DNI/NIE] y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], ante este organismo comparece y como mejor proceda en Derecho

EXPONE:

Primero.— Que fue titular de autorización de residencia y trabajo por cuenta ajena, por lo que solicitó autorización de residencia de larga duración el de [COMPLETAR] de [COMPLETAR] dentro del plazo legal para ello. Se adjunta a efectos de prueba copia del resguardo de solicitud de renovación.

Segundo.— Que hasta la fecha no ha recibido notificación de resolución alguna, por lo que tal y como establece la Disposición Adicional Primera de la Ley Orgánica 4/2000 en su apartado 2, al haber transcurrido más de tres meses desde la solicitud de renovación deberá entenderse ESTIMADA dicha solicitud en aplicación del silencio positivo.

Tercero.— Que el artículo 24 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas establece que los actos administrativos producidos por silencio administrativo podrán ser acreditados por cualquier medio de prueba admitido en Derecho, incluido el certificado acreditativo del silencio producido. Este certificado se expedirá de oficio por el órgano competente para resolver en el plazo de quince días desde que expire el plazo máximo para resolver el procedimiento. Sin perjuicio de lo anterior, el interesado podrá pedirlo en cualquier momento, computándose el plazo indicado anteriormente desde el día siguiente a aquél en que la petición tuviese entrada en el registro electrónico de la Administración u Organismo competente para resolver.

Cuarto.— Que la demora está causando graves perjuicios a quien suscribe, especialmente en el ámbito laboral.

Por todo ello, SOLICITA que se emita CERTIFICADO ACREDITATIVO DEL SILENCIO POSITIVO que ha recaído sobre el expediente de renovación de la autorización de residencia y trabajo de D.. [NOMBRE Y APELLIDOS]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo.: [COMPLETAR].

NOTAS DEL FORMULARIO

(1) En las Comunidades Autónomas uniprovinciales se dirigirá a la Delegación del Gobierno.

════════════════════════════════════════════════════════════════════════
