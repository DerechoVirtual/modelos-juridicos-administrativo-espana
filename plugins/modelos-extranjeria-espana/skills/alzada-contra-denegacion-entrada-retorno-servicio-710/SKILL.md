---
name: alzada-contra-denegacion-entrada-retorno-servicio-710
description: "Redacta el escrito «Alzada contra la denegación de entrada y retorno del servicio fronterizo» (formulario 710 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra la denegación de entrada y retorno del servicio fronterizo

> Formulario 0710 del plugin **Extranjería** · revisado el 17-11-2026.

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

- El art. 4 RD 1155/2024 está reescrito conforme al art. 6 del Reglamento (UE) 2016/399. Si los hechos son anteriores al 20-5-2025, citar el RD 557/2011.
- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] COLEGIO
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (4 veces)
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…el Servicio Fronterizo del Aeropuerto de»; «… del Puesto Fronterizo del Aeropuerto de»; «…ERO.- Mi mandante, ciudadano nacional de»; «…llegó el día [FECHA] al aeropuerto de»; «…cio del Puesto Fronterizo del Aeropuerto»; «…ambién resultan vulnerados los artículos»; «…vios los trámites legales, se declare la»; «…a AL EXCMO. SR. DELEGADO DEL GOBIERNO DE»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley Orgánica 4/2000
- Ley Orgánica 8/2000
- Ley Orgánica 14/2003
- Real Decreto 557/2011
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

### Formulario 0710 · Alzada contra la denegación de entrada y retorno del servicio fronterizo

- Año del modelo: 2009
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: El art. 4 RD 1155/2024 está reescrito conforme al art. 6 del Reglamento (UE) 2016/399. Si los hechos son anteriores al 20-5-2025, citar el RD 557/2011. · Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./D.ª [NOMBRE Y APELLIDOS], Letrado del Colegio de Abogados de [COLEGIO], colegiado número [Nº DE COLEGIADO/A], con domicilio a efectos de notificaciones sito en [LOCALIDAD] pudiendo ser notificado vía lexnet o en el correo electrónico [CORREO ELECTRÓNICO], y con teléfono [TELÉFONO], en representación de D. [NOMBRE Y APELLIDOS], según consta en el expediente número [Nº DE EXPEDIENTE] del Servicio Fronterizo del Aeropuerto de [COMPLETAR] ante la Delegación del Gobierno de [LOCALIDAD] comparece y como mejor proceda en Derecho, DICE:

Que en virtud de este escrito interpone RECURSO DE ALZADA contra la resolución de fecha [FECHA], dictada por el Jefe de Servicio del Puesto Fronterizo del Aeropuerto de [COMPLETAR] por no encontrarla ajustada a Derecho, con fundamento en los siguientes antecedentes y consideraciones jurídicas.

ANTECEDENTES DE HECHO

PRIMERO.- Mi mandante, ciudadano nacional de [COMPLETAR] llegó el día [FECHA] al aeropuerto de [COMPLETAR] provisto de pasaporte en regla, dictándose Resolución del Jefe de Servicio del Puesto Fronterizo del Aeropuerto [COMPLETAR] de fecha [FECHA], por la que se acuerda denegar la entrada de mi representado en el territorio español, así como el retorno al lugar de procedencia, por no reunir el requisito de presentar un documento válido que la legislación vigente exige para que pueda autorizársele la entrada.

SEGUNDO.- Con fecha [FECHA], se practicó la notificación de la resolución a esta parte quien, considerándola perjudicial para sus intereses, deduce mediante este escrito recurso de alzada que basa en los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- La resolución del Jefe de Servicio del Puesto Fronterizo infringe lo dispuesto en la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social (LOEX), modificada por la Ley Orgánica 8/2000, de 22 de diciembre, y reformada por la Ley Orgánica 14/2003, de 20 de noviembre, que contempla en su artículo 25, en concordancia con lo dispuesto en el artículo 5 del Convenio de Aplicación del Acuerdo de Schengen, de 14 de junio de 1985, que: "1. El extranjero que pretenda entrar en España deberá hacerlo por los puestos habilitados al efecto, hallarse provisto del pasaporte o documento de viaje que acredite su identidad, que se considere válido para tal fin en virtud de convenios internacionales suscritos por España y no estar sujeto a prohibiciones expresas. Asimismo, deberá presentar los documentos que se determinen reglamentariamente que justifiquen el objeto y condiciones de estancia, y acreditar medios de vida suficientes para el tiempo que pretenda permanecer en España, o estar en condiciones de obtener legalmente dichos medios. 2. Salvo en los casos en que se establezca lo contrario en los convenios internacionales suscritos por España o en la normativa de la Unión Europea, será preciso, además, un visado."

El Reglamento de Extranjería, aprobado mediante el Real Decreto 557/2011, de 20 de abril, dispone en el artículo 4.1.c) [NOTA DE REVISIÓN: Equivale al art. 4.1.c) RD 1155/2024 (documentos que justifiquen el objeto y las condiciones de la estancia, art. 8). El encabezamiento del art. 4.1 se ha reescrito: se refiere a estancias de hasta 90 días en 180 y al art. 6 del Reglamento (UE) 2016/399. No basta con cambiar el número: hay que actualizar la cita literal. Si los hechos son anteriores al 20-5-2025, la cita al RD 557/2011 es la correcta para la redacción «del momento de los hechos». Fuente: RD 1155/2024, art. 4.1.c) (BOE-A-2024-24099); RD 557/2011, art. 4.1.c) (BOE-A-2011-7703).] que "La entrada de un extranjero en territorio español estará condicionada al cumplimiento de los siguientes requisitos: a) Titularidad del pasaporte o documentos de viaje a los que se refiere el artículo siguiente ."

Pues bien, mi representado era titular de un pasaporte, reuniendo los demás requisitos establecidos en los citados preceptos, siendo denegada la entrada en el territorio español a mi representado por no reunir el requisito de presentar un documento válido, puesto que según el funcionario actuante el pasaporte estaba falsificado.

Sin embargo, tal afirmación es infundada, y al efecto acreditamos la autenticidad del pasaporte mediante certificado de la autoridad que expidió el pasaporte, que se acompaña como documento número 1, donde se acredita que el documento presentado era auténtico y estaba en vigor, de manera que la decisión de denegar la entrada en España y acordar el retorno infringe lo dispuesto en los preceptos antes mencionados.

SEGUNDO.- También resultan vulnerados los artículos [COMPLETAR], en los siguientes términos:

Por todo lo expuesto, y de conformidad con las previsiones de los artículos 121 y siguientes de la Ley 39/2015, de 1 de octubre del Procedimiento Administrativo Común de las Administraciones Públicas, SOLICITO:

Que se admita el presente recurso de alzada y, previos los trámites legales, se declare la [COMPLETAR] de la resolución de fecha arriba expresa, dejándola sin efecto, y declarando que mi representado reúne los requisitos para la entrada en España

Lugar, fecha, y firma

AL EXCMO. SR. DELEGADO DEL GOBIERNO DE [COMPLETAR]
