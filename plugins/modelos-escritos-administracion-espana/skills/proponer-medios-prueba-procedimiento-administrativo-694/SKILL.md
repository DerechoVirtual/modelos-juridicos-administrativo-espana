---
name: proponer-medios-prueba-procedimiento-administrativo-694
description: "Redacta el escrito «Proponer medios de prueba en el procedimiento administrativo» (formulario 694 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Proponer medios de prueba en el procedimiento administrativo

> Formulario 0694 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (3 veces)
- [ ] Nº
- [ ] PROFESIÓN (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a fin de que se reconociese»; «…ca. Consistente en que se certifique por»; «…on domicilio a efectos de su citación en»; «…esponder a las siguientes preguntas: 1.ª»; «…2.ª»; «…2.ª [COMPLETAR] 3.ª»; «…on domicilio a efectos de su citación en»; «…sponder a las siguientes preguntas: 1 .ª»; «…2.ª»; «…2.ª [COMPLETAR] 3.ª»; «…Etc. Es por lo expuesto que a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 77 de la Ley 39/2015

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

### Formulario 0694 · Proponer medios de prueba en el procedimiento administrativo

- Año del modelo: 2010
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS] actuando en su propio nombre y derecho (o en representación de [NOMBRE DEL REPRESENTADO/A]), en el procedimiento número [Nº DE PROCEDIMIENTO] incoado como consecuencia de la solicitud de [FECHA] a fin de que se reconociese [COMPLETAR] como mejor proceda en Derecho, DIGO:

Que con fecha [FECHA] se me ha notificado la Resolución de fecha [FECHA] por la que se acuerda la apertura de un período probatorio en el presente procedimiento por término de [Nº] días (el plazo máximo es de diez días y el máximo de treinta) para acreditar los siguientes hechos: (indicar sucintamente los hechos a que se refiere la prueba)

Que dentro del indicado plazo, manifiesto a continuación los medios de prueba de los que intenta valerse el/la que suscribe para acreditar los mencionados hechos, al amparo de lo dispuesto en el artículo 77 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

MEDIOS DE PRUEBA

PRIMERO. Documental Pública. Consistente en que se certifique por [COMPLETAR] (órgano administrativo que debe emitir la certificación) los siguientes extremos: (relacionarlos enumeradamente).

SEGUNDO. Testifical. Consistente en que a los testigos que se señalan a continuación se les formulen las preguntas que respectivamente se indican para cada uno de ellos.

Primer testigo: D./Dña [NOMBRE Y APELLIDOS] con D.N.I. de profesión [PROFESIÓN] y con domicilio a efectos de su citación en [COMPLETAR], que deberá responder a las siguientes preguntas:

1.ª [COMPLETAR]

2.ª [COMPLETAR]

3.ª [COMPLETAR]

Segundo testigo: D./Dña [NOMBRE Y APELLIDOS] con D.N.I. de profesión [PROFESIÓN] y con domicilio a efectos de su citación en [COMPLETAR], que deberá responder a las siguientes preguntas:

1 .ª [COMPLETAR]

2.ª [COMPLETAR]

3.ª [COMPLETAR]

TERCERO. Pericial. Consistente en [DESCRIBIR]

Etc.

Es por lo expuesto que a [COMPLETAR] (quien corresponda) SOLICITO:

Tenga por presentado este escrito, junto con los documentos que se acompañan, y por propuestos los medios de prueba de los que intenta valerse el que suscribe en el presente procedimiento y con admisión de los mismos acuerde su práctica en el período probatorio concedido.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

 (lugar, fecha y firma)

Sr./Sra. [NOMBRE Y APELLIDOS] (Centro u órgano administrativo que está instruyendo el procedimiento)
