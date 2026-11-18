---
name: alzada-contra-denegacion-entrada-espana-carta-invitacion-261
description: "Redacta el escrito «Alzada contra denegación de entrada en España con carta de invitación» (formulario 261 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra denegación de entrada en España con carta de invitación

> Formulario 0261 del plugin **Extranjería** · revisado el 17-11-2026.

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

- El art. 4 RD 1155/2024 está reescrito conforme al art. 6 del Reglamento (UE) 2016/399. Si los hechos son anteriores al 20-5-2025, citar el RD 557/2011. La cita al art. 5 del Convenio de Schengen no se ha verificado.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO
- [ ] DNI/NIE
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE (2 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Nº DE COLEGIADO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, nacional de»; «…imero.- La interesada pretendía viajar a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 122 LPACAP
- art. 121.2 LPACAP
- Ley Orgánica 4/2000
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

### Formulario 0261 · Alzada contra denegación de entrada en España con carta de invitación

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 14 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE COLEGIADO)
- Avisos de la revisión: El art. 4 RD 1155/2024 está reescrito conforme al art. 6 del Reglamento (UE) 2016/399. Si los hechos son anteriores al 20-5-2025, citar el RD 557/2011. La cita al art. 5 del Convenio de Schengen no se ha verificado.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA DIRECCION GENERAL DE LA POLICIA

D./Dña. [NOMBRE Y APELLIDOS], abogado/a del ICAM colegiado con el n.º [NÚMERO] y DNI [DNI/NIE], con dirección a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES] en la C/ [CALLE] en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], nacional de [COMPLETAR], ante este organismo comparezco para formular

RECURSO DE ALZADA

Contra la resolución de fecha [FECHA] por la que se denegaba a la entrada en el territorio nacional, así como el retorno al lugar de procedencia de su vuelo, copia de la cual se adjunta con el presente escrito.

Fundamento este recurso en base a los siguientes

HECHOS

Primero.- La interesada pretendía viajar a [COMPLETAR], donde había realizado una reserva hotelera con tal fin.

Segundo.- La interesada contaba con billete de vuelta a su país de origen y con recursos económicos suficientes para el tiempo previsto de estancia.

Tercero.- A pesar de lo expuesto, en el puesto fronterizo del aeropuerto de Madrid, se dictó resolución por la que se acordó denegar la entrada en territorio español del recurrente y su retorno al lugar de procedencia por considerar que el pasajero «no reunía el requisito de presentar los documentos que justifiquen el objeto y las condiciones de la estancia prevista y acreditar medios económicos».

Cuarto.- A efectos de notificaciones, se designa el domicilio del letrado D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD] en la C/ [CALLE] C.P..

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el art. 122 LPACAP, este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el art. 121.2 LPACAP, este recurso se presenta ante el órgano competente para resolver el recurso.

III

Se encuentra expresamente autorizado el/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS] para interponer este recurso en nombre y representación del recurrente, según consta en la declaración prestada por el mismo ante las autoridades policiales del puesto fronterizo de Barajas.

IV

En lo relativo a la entrada en España de extranjeros, es de aplicación la siguiente normativa:

• Artículo 3 y siguientes del convenio de aplicación del acuerdo de Schengen.
• Reglamento (UE) 2016/399 del Parlamento Europeo y del Consejo, de 9 de marzo de 2016, por el que se establece un Código de normas de la Unión para el cruce de personas por las fronteras (Código de fronteras Schengen).
• Artículo 25 de la Ley Orgánica 4/2000, en su redacción en el momento en que los hechos tuvieron lugar:
• Artículos 1 a 18 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: El rango es válido (pasos fronterizos, requisitos y prohibiciones de entrada, transportistas). Pero el formulario dice «en su redacción en el momento en que los hechos tuvieron lugar»: si los hechos son anteriores al 20-5-2025, la norma aplicable es el RD 557/2011. Fuente: RD 1155/2024, arts. 1-18 (BOE-A-2024-24099).], de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000.
• Instrucción consular común dirigida a las misiones diplomáticas y oficinas consulares de carrera de las partes contratantes del convenio de Schengen (2005/c 326/01).

Recordemos que el artículo 6 del Código de Fronteras Schengen (Reglamento (UE) 2016/399) establece que para una estancia que no exceda de tres meses dentro de un período de seis meses, las condiciones de entrada para nacionales de terceros países serán las siguientes:

«c)estar en posesión de documentos que justifiquen el objeto y las condiciones de la estancia prevista y disponer de medios de subsistencia suficientes, tanto para el período de estancia previsto como para el regreso al país de origen o el tránsito hacia un tercer país en el que su admisión esté garantizada, o estar en condiciones de obtener legalmente dichos medios;»

En el presente caso debe concluirse que el recurrente cumplía con los requisitos exigidos por la legislación, pues disponía de billete de vuelta cerrado al lugar de procedencia, tenía reserva hotelera en el lugar de estancia y acreditaba disponer de medios económicos suficientes para el período previsto de estancia.

Dichas circunstancias acreditaban por sí solas el objeto del viaje y la disponibilidad de medios de vida y alojamiento para el tiempo previsto de estancia.

La Sentencia del TSJ de Madrid, Sala de lo Contencioso-administrativo, Secc. 9.ª, núm. 2529/2007, de 23 de enero, Rec. 695/2003, entendió que en un caso similar al presente correspondía anular la resolución recurrida, ya que se consideraba que sí se había justificado el objeto del viaje y las condiciones de la estancia temporal en España.

V

La lesión sufrida por el recurrente ha sido efectiva, por cuanto se le ha impedido la entrada en territorio español, haciéndole perder el importe del billete de avión, además de los días de vacaciones que el incidente le ha hecho perder.

Así lo entendió el TSJ de Madrid, que en la sentencia citada consideró procedente indemnizar a la recurrente por el daño moral sufrido por la indebida denegación de su entrada en España en la cantidad de 600 euros.

Por lo expuesto,

SOLICITO

Que, teniendo por presentado este recurso con los documentos que se adjuntan, se sirva admitirlo y previos los trámites oportunos, se dicte resolución por la que se declare la nulidad de la resolución recurrida, declarándose el derecho del recurrente a entrar en España en calidad de turista e indemnizando al mismo en cantidad equivalente al importe del billete de avión más la cantidad de 600 euros por el daño moral sufrido.

Por ser Justicia que pido en [LUGAR], a [FECHA].

Fdo.:.

Colegiado/a n.º [Nº DE COLEGIADO]
