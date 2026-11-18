---
name: contencioso-contra-denegacion-certificado-insuficiencia-1
description: "Redacta el escrito «Contencioso contra la denegación del certificado de insuficiencia de demandantes de empleo» (formulario 1 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso contra la denegación del certificado de insuficiencia de demandantes de empleo

> Formulario 0001 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Situación nacional de empleo: el art. 75 RD 1155/2024 se mantiene en lo esencial (catálogo por comunidad autónoma). El inciso sobre «actuaciones formativas» no aparece en el texto vigente: revisarlo.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rocedente del Servicio Público de Empleo»; «… empresa cuyo ramo de actividad es la de»; «…dad era de su interés la contratación de»; «…trabajador/es para la realización de»; «…ecialización resulta imprescindible pues»; «….»; «…posesión de conocimientos o formación en»; «…y su integración social. En consecuencia»; «…pal, en su condición de causahabiente de»; «…entablar acciones las personas jurídicas»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si procede CERTIFICACIÓN SOBRE LA INSUFICIENCIA DE DEMANDANTES DE EMPLEO / Si procede OBLIGACIÓN DE RESPUESTA — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si solicita la celebración de vista / Si NO solicita la celebración de vista — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si NO se solicita práctica de prueba / Si solicita práctica de prueba — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 78 de la Ley 29/1998
- arts. 38.2 de la Ley Orgánica 4/2000
- art. 75 Real Decreto 1155/2024
- art. 19.1 de la Ley 29/1998
- art. 78 de la LJCA
- art. 25.1 de la LJCA
- art. 75.1 y 75.2 Real Decreto 1155/2024
- arts. 45.2 y 78.2 de la LJCA
- art. 78.2 de la LJCA
- arts. 40 y 42 de la LJCA
- Ley Orgánica 2/2009

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

### Formulario 0001 · Contencioso contra la denegación del certificado de insuficiencia de demandantes de empleo

- Año del modelo: 2025
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 16 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Situación nacional de empleo: el art. 75 RD 1155/2024 se mantiene en lo esencial (catálogo por comunidad autónoma). El inciso sobre «actuaciones formativas» no aparece en el texto vigente: revisarlo.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según copia de poder general para pleitos que acompaño adjunta, solicitando que, una vez testimoniada y por necesitarla para otros usos me sea devuelta, por el presente escrito, y, de acuerdo con lo dispuesto en el art. 78 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa (LJCA), COMPAREZCO Y DIGO

Que procedo a interponer recurso contencioso administrativo, directamente por escrito de demanda iniciadora de procedimiento abreviado, contra la resolución de fecha [FECHA], procedente del Servicio Público de Empleo [COMPLETAR], por la que se deniega la expedición de certificación sobre la insuficiencia de demandantes de empleo adecuados y disponibles para aceptar la previa oferta formulada, en respuesta a una específica petición deducida por esta representación y que fue hecha al objeto de proceder a tramitar una posterior solicitud de autorización de residencia y trabajo para trabajadores extranjeros, actuación procesal que hago con sujeción a los siguientes:

HECHOS

PRIMERO.- Esta recurrente es una empresa cuyo ramo de actividad es la de [COMPLETAR].

Para el mejor desarrollo de su actividad era de su interés la contratación de [COMPLETAR] trabajador/es para la realización de [COMPLETAR].

Sin embargo, pese a las gestiones realizadas en el mercado de trabajo español no fue hallado ningún trabajador residente en disposición de aceptar sus ofertas.

Por otra parte, el trabajo indicado no se encuentra comprendido en el Catálogo de Ocupaciones de Difícil Cobertura previsto en los arts. 38.2 de la Ley Orgánica 4/2000, de los Derechos y Libertades de los Extranjeros en España y su Integración Social, modificado por la Ley Orgánica 2/2009, de 11 de diciembre, y art. 75 Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social.

SEGUNDO.- Por ello, en fecha [FECHA] formuló ante el Servicio Público de Empleo oferta de trabajo.

TERCERO.- Una vez promovido el contacto entre los trabajadores y esta empresa por el Servicio Público de empleo se ha visto que ninguno de los presentados era adecuado para el desarrollo del trabajo de que se trata, pues carecían de la oportuna especialización.

Esa especialización resulta imprescindible pues [COMPLETAR]. [COMPLETAR]. Sin embargo, una vez trabado contacto con los trabajadores indicados se ha visto que ninguno de ellos tenía voluntad real de suscribir el contrato pese a que las condiciones del puesto eran, por supuesto, respetuosas con la legislación aplicable y los convenios colectivos del sector, de modo que su disponibilidad era más aparente que real.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si procede CERTIFICACIÓN SOBRE LA INSUFICIENCIA DE DEMANDANTES DE EMPLEO / Si procede OBLIGACIÓN DE RESPUESTA — el texto de cada opción no venía en el formulario original]

FUNDAMENTOS DE DERECHO

PRIMERO.- LEGITIMACIÓN.-

Esta parte posee la oportuna legitimación, según el art. 19.1 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa, por afectar la actividad administrativa que es objeto de impugnación a sus derechos o intereses legítimos y, en concreto, por tener interés empresarial en la contratación de los indicados trabajadores para el mejor desarrollo de su actividad.

SEGUNDO.- COMPETENCIA Y PROCEDIMIENTO.-

La competencia funcional y objetiva para el conocimiento del presente recurso les corresponde a los Tribunales de Instancia (Secciones de lo Contencioso-Administrativo), al amparo de la atribución competencial contenida en el art. 8 de la misma Ley Reguladora de la Jurisdicción Contencioso Administrativa.

La competencia territorial reside en el Tribunal al que esta parte tiene el honor de dirigirse conforme al art. 14 de la citada LJCA.

El procedimiento ajustado a derecho para la tramitación de este recurso será el abreviado, regulado en el art. 78 de la LJCA, por versar la cuestión controvertida sobre extranjería.

TERCERO.- RECURRIBILIDAD AUTÓNOMA DEL ACTO.-

La denegación de certificación positiva solicitada por esta interesada cierra, de modo definitivo, la posibilidad de tramitación de una autorización de trabajo y residencia para trabajadores extranjeros, de modo que el acto es uno de aquellos que impiden la continuación del procedimiento y, en consecuencia, conforme al art. 25.1 de la LJCA, son susceptibles de impugnación separada.

CUARTO.- FONDO DE LA CUESTIÓN CONTROVERTIDA.-

El Servicio Público de Empleo fundamenta su denegación en la existencia en España de trabajadores en disposición de aceptar la indicada oferta, de manera que la Situación Nacional del Empleo impediría la apertura de un procedimiento de autorización de residencia y trabajo para otros trabajadores extranjeros.

Sin embargo, como se ha indicado y justificado por aportación de la oportuna documentación, lo cierto es que los trabajadores con los que se ha facilitado la comunicación por el Servicio Público de empleo carecen de la oportuna formación y sí una mera cualificación genérica en el ramo, mientras que para esta empresa es imprescindible la posesión de conocimientos o formación en [COMPLETAR].

Por la misma razón de máxima especialidad de la actividad, ésta no se encuentra comprendida en un instrumento forzosamente genérico como es el Catálogo de Ocupaciones de Difícil Cobertura previsto en el art. 75 Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social. Y en fin, tampoco se trata de una de aquellas ocupaciones que por su naturaleza podrían ser cubiertas por personas inscritas como demandantes de empleo tras su participación en actuaciones formativas programadas por los Servicios públicos de empleo (art. 75.1 y 75.2 Real Decreto 1155/2024 [NOTA DE REVISIÓN (comprobar): La cita del art. 75 RD 1155/2024 (situación nacional de empleo) es correcta, pero su texto no menciona a «personas inscritas como demandantes de empleo tras su participación en actuaciones formativas»: el 75.1 regula el Catálogo (ahora por comunidad autónoma) y el 75.2 la gestión de la oferta durante ocho días y el certificado de insuficiencia de demandantes en tres días. Revisar ese inciso del formulario. Fuente: RD 1155/2024, art. 75 (BOE-A-2024-24099).], de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social.

En consecuencia [COMPLETAR].

QUINTO.- COSTAS.-

Por lo anteriormente expuesto

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si solicita la celebración de vista / Si NO solicita la celebración de vista — el texto de cada opción no venía en el formulario original]

Conforme a las determinaciones de los arts. 45.2 y 78.2 de la LJCA, adjunto acompaño los siguientes documentos:

1º.- Copia del poder otorgado y acreditativo de la representación del compareciente.
2º.- Documento justificativo de la condición de legitimado de mi principal, en su condición de causahabiente de [COMPLETAR].
3º.- Copia del acto impugnado.
4º.- Documento que acredita el cumplimiento por mi mandante de los requisitos exigidos para entablar acciones las personas jurídicas [COMPLETAR].
5º.- Documentos esenciales en los que esta parte justifica su derecho, conforme a lo dispuesto en el art. 78.2 de la LJCA.

PRIMER OTROSÍ: Conforme a los arts. 40 y 42 de la LJCA cifro la cuantía del presente recurso como indeterminada.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si NO se solicita práctica de prueba / Si solicita práctica de prueba — el texto de cada opción no venía en el formulario original]

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
