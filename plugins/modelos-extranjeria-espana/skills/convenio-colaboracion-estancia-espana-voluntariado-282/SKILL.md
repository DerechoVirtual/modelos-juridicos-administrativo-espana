---
name: convenio-colaboracion-estancia-espana-voluntariado-282
description: "Redacta el escrito «Convenio de colaboración para estancia en España por voluntariado» (formulario 282 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio de colaboración para estancia en España por voluntariado

> Formulario 0282 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Voluntariado: el contenido del convenio está hoy en el art. 53.1.d).1.º RD 1155/2024.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE (2 veces)
- [ ] Nº
- [ ] NÚMERO
- [ ] LUGAR
- [ ] FECHA
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en nombre y representación de la entidad»; «…micilio social en (País) en la ciudad de»; «…servicio de voluntariado para la entidad»; «…meses»; «…vidades que realizará el voluntario para»; «…, consistirán en»; «…ividades se incluyen dentro del programa»; «…de la entidad, que tiene como objetivo»; «…e realización dichas actividades será de»; «…a»; «…a [COMPLETAR]. La entidad»; «… que este convenio se encuentre en vigor»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 34.1.d), 35 y 36 del Real Decreto 1155/2024

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

### Formulario 0282 · Convenio de colaboración para estancia en España por voluntariado

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 25 campos de relleno marcados en blanco
- Avisos de la revisión: Voluntariado: el contenido del convenio está hoy en el art. 53.1.d).1.º RD 1155/2024.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

DE UNA PARTE

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, en nombre y representación de la entidad [COMPLETAR], con domicilio social en España en la C/ [CALLE],

DE OTRA PARTE

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio social en (País) en la ciudad de [COMPLETAR] en la C/ [CALLE],

Suscriben el presente

CONVENIO DE COLABORACIÓN

El presente convenio se suscribe en cumplimiento de lo establecido en los artículos 34.1.d), 35 y 36 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: Los arts. 34-36 regulan el visado. El convenio con la entidad de voluntariado y su contenido mínimo (descripción del programa, funciones, supervisión, horas, manutención y alojamiento, dinero de bolsillo, formación) se exigen para la autorización en el art. 53.1.d).1.º, con el supuesto definido en el art. 52.1.d) y el procedimiento en el art. 54. Conviene citar los arts. 52.1.d), 53.1.d) y 54, además del 34.1.d). Fuente: RD 1155/2024, arts. 34, 35, 52, 53.1.d) y 54 (BOE-A-2024-24099).], de 19 de noviembre, para la concesión de la autorización de estancia en España de D./Dña. [NOMBRE Y APELLIDOS] para la prestación de un servicio de voluntariado.

El objeto del presente convenio es la prestación de un servicio de voluntariado para la entidad [COMPLETAR] por parte de D./Dña. [NOMBRE Y APELLIDOS]

La duración del presente convenio será de [Nº] meses [COMPLETAR], prorrogables previo acuerdo de las partes antes de su finalización.

Las actividades que realizará el voluntario para [COMPLETAR], consistirán en [COMPLETAR]:

Dichas actividades se incluyen dentro del programa [COMPLETAR] de la entidad, que tiene como objetivo [COMPLETAR]

El horario en que se realización dichas actividades será de [COMPLETAR] a [COMPLETAR].

La entidad [COMPLETAR] se hará cargo de los gastos de viaje, alojamiento y manutención del voluntario el tiempo que este convenio se encuentre en vigor [COMPLETAR].

La entidad [COMPLETAR] tiene suscrito un seguro de responsabilidad civil con la entidad [COMPLETAR], póliza nº [NÚMERO] por el que se cubren riesgos de accidente y enfermedad derivados directamente del ejercicio de la actividad voluntaria.

En [LUGAR], a [FECHA].

En representación de [NOMBRE DEL REPRESENTADO/A]

El/la voluntario/a

Fdo.: D./Dña. [NOMBRE Y APELLIDOS]
