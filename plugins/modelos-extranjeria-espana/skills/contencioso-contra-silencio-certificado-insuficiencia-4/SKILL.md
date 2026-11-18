---
name: contencioso-contra-silencio-certificado-insuficiencia-4
description: "Redacta el escrito «Contencioso contra el silencio en el certificado de insuficiencia de demandantes de empleo» (formulario 4 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso contra el silencio en el certificado de insuficiencia de demandantes de empleo

> Formulario 0004 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Situación nacional de empleo: el art. 75 RD 1155/2024 se mantiene en lo esencial (catálogo por comunidad autónoma).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] PARTE RECURRENTE
- [ ] IDENTIFICACIÓN (2 veces)
- [ ] FECHA (3 veces)
- [ ] DESCRIPCIÓN
- [ ] NÚMERO TRABAJADOR/ES PARA LA REALIZACIÓN DE
- [ ] CONCRETA ACTIVIDAD
- [ ] RAZONES
- [ ] (EN
- [ ] MATERIA PRECISA
- [ ] ARGUMENTOS COMPLEMENTARIOS REFERIDOS AL CASO CONCRETO
- [ ] LO
- [ ] SOLO APLICABLE A LAS PERSONAS JURÍDICAS
- [ ] PUNTOS DE HECHO
- [ ] los que procedan, debiendo tener en cuenta que los medios probatorios son los previstos en los arts. 299 y ss de la LEC
- [ ] LUGAR

## Elecciones que hay que hacer

- Si procede CERTIFICACIÓN SOBRE LA INSUFICIENCIA DE DEMANDANTES DE EMPLEO
- (Si se solicita la celebración de la vista)Por lo anteriormente expuesto,
- Si se solicita apertura del procedimiento de prueba

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 78 de la Ley 29/1998
- art. 38.2 de la Ley Orgánica 4/2000
- art. 75 del Real Decreto 1155/2024
- art. 75.2 del Real Decreto 1155/2024
- art. 19.1 de la LJCA
- art. 14 de la LJCA
- art. 78 de la LJCA
- art. 25.1 de la LJCA
- arts. 45.2 y 78.2 de la LJCA
- art. 78.2 de la LJCA
- arts. 40 y 42 de la LJCA
- art. 60 de la LJCA
- art. 60 LJCA
- art. 78.1 de la LJCA
- Ley Orgánica 2/2009
- Ley 37/2011

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

### Formulario 0004 · Contencioso contra el silencio en el certificado de insuficiencia de demandantes de empleo

- Año del modelo: 2025
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 4 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Situación nacional de empleo: el art. 75 RD 1155/2024 se mantiene en lo esencial (catálogo por comunidad autónoma).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la Sección de lo Contencioso-Administrativo del Tribunal de Instancia de [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [PARTE RECURRENTE], según copia de poder general para pleitos que acompaño adjunta, solicitando que, una vez testimoniada y por necesitarla para otros usos me sea devuelta, por el presente escrito, y, de acuerdo con lo dispuesto en el art. 78 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa (LJCA), COMPAREZCO Y DIGO

Que procedo a interponer recurso contencioso administrativo, directamente por escrito de demanda iniciadora de procedimiento abreviado, contra la denegación, por silencio administrativo negativo, por el Servicio Público de Empleo [IDENTIFICACIÓN], de la petición deducida por esta parte en fecha [FECHA] para la expedición de certificación sobre la insuficiencia de demandantes de empleo adecuados y disponibles para aceptar la previa oferta formulada, al objeto de proceder a tramitar una posterior solicitud de autorización de residencia y trabajo para trabajadores extranjeros, actuación procesal que hago con sujeción a los siguientes:HECHOSPRIMERO.- Esta recurrente es una empresa cuyo ramo de actividad es la de [DESCRIPCIÓN]

Para el mejor desarrollo de su actividad era de su interés la contratación de [NÚMERO TRABAJADOR/ES PARA LA REALIZACIÓN DE] [CONCRETA ACTIVIDAD].

Sin embargo, pese a las gestiones realizadas en el mercado de trabajo español no fue hallado ningún trabajador residente en disposición de aceptar sus ofertas.

Por otra parte, el trabajo indicado no se encuentra comprendido en el Catálogo de Ocupaciones de Difícil Cobertura previsto en el art. 38.2 de la Ley Orgánica 4/2000, de los Derechos y Libertades de los Extranjeros en España y su Integración Social, modificado por la Ley Orgánica 2/2009, de 11 de diciembre, y en el art. 75 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social

SEGUNDO.- Por ello, en fecha [FECHA] formuló ante el Servicio Público de Empleo oferta de trabajo.

TERCERO.- Una vez promovido el contacto entre los trabajadores y esta empresa por el Servicio Público de empleo se ha visto que ninguno de los presentados era adecuado para el desarrollo del trabajo de que se trata, pues carecían de la oportuna especialización.

Esa especialización resulta imprescindible, pues [RAZONES] específicas que hacen que un trabajador del ramo no sea suficiente. [(EN] su caso apórtese justificación documental o, al menos, los oportunos argumentos que justifiquen no ser en efecto bastante con un grado general de especialización)Sin embargo, una vez trabado contacto con los trabajadores indicados se ha visto que ninguno de ellos tenía voluntad real de suscribir el contrato, pese a que las condiciones del puesto eran, por supuesto, respetuosas con la legislación aplicable y los convenios colectivos del sector, de modo que su disponibilidad era más aparente que real.

[ELEGIR: Si procede CERTIFICACIÓN SOBRE LA INSUFICIENCIA DE DEMANDANTES DE EMPLEO]

CUARTO.- Por todo ello esta representación vino a solicitar del Servicio Público de Empleo la expedición de certificación sobre la insuficiencia de demandantes de empleo, conforme al art. 75 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social adecuados y disponibles para aceptar dicha oferta en territorio español, siempre con objeto de proceder a tramitar una posterior solicitud de autorización de residencia y trabajo para trabajadores extranjeros.(Si procede OBLIGACIÓN DE RESPUESTA)

CUARTO.- Transcurrido el plazo de tres días previsto en el art. 75.2 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: El plazo de tres días para el certificado de insuficiencia de demandantes está en el art. 75.2. Fuente: RD 1155/2024, art. 75.2 (BOE-A-2024-24099).], de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración socialcontados a partir de la notificación por el empleador del resultado negativo de la selección, el Servicio Público de empleo guarda silencio sobre la solicitud formulada.FUNDAMENTOS DE DERECHOPRIMERO.- LEGITIMACIÓN.-Esta parte posee la oportuna legitimación, según el art. 19.1 de la LJCA, por afectar la actividad administrativa que es objeto de impugnación a sus derechos o intereses legítimos y, en concreto, por tener interés empresarial en la contratación de los indicados trabajadores para el mejor desarrollo de su actividad.

SEGUNDO.- COMPETENCIA Y PROCEDIMIENTO.-La competencia funcional y objetiva para el conocimiento del presente recurso les corresponde a los Tribunales de Instancia (Secciones de lo Contencioso-Administrativo), al amparo de la atribución competencial contenida en el art. 8 de la misma Ley Reguladora de la Jurisdicción Contencioso Administrativa.

La competencia territorial reside en el Tribunal al que esta parte tiene el honor de dirigirse, conforme al art. 14 de la LJCA.El procedimiento ajustado a derecho para la tramitación de este recurso será el abreviado, regulado en el art. 78 de la LJCA, por versar la cuestión controvertida sobre extranjería.

TERCERO.- RECURRIBILIDAD AUTÓNOMA DEL ACTO Y TEMPORANEIDAD DE LA IMPUGNACIÓN.-La denegación, por silencio, de la solicitud de certificación solicitada por esta interesada cierra, de modo definitivo, la posibilidad de tramitación de una autorización de trabajo y residencia para trabajadores extranjeros, de modo que el acto es uno de aquellos que impiden la continuación del procedimiento y, en consecuencia, conforme al art. 25.1 de la LJCA, son susceptibles de impugnación separada.

El art. 38.2 de la Ley Orgánica 4/2000 dispone que se entenderá que la situación nacional de empleo permite la contratación en ocupaciones no catalogadas cuando de la gestión de la oferta se concluya la insuficiencia de demandantes de empleo adecuados y disponibles. Y añade que reglamentariamente se determinarán los requisitos mínimos para considerar que la gestión de la oferta de empleo es considerada suficiente a estos efectos.

El art. 75.2 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, indica que se considerará que la situación nacional de empleo permite la contratación en las ocupaciones no calificadas como de difícil cobertura cuando el empleador acredite ante la Oficina de Extranjería la dificultad de cubrir los puestos de trabajo vacantes con trabajadores ya incorporados en el mercado laboral interno.A tal efecto —como aquí ha ocurrido— deberá presentar dicho empleador una oferta en el portal Empléate y en los Servicios Públicos de Empleo, formulada de forma precisa y ajustada a los requerimientos del puesto de trabajo y sin contener requisitos que no tengan relación directa con su desempeño. A partir de ello el Servicio Público de Empleo ha de gestionar la oferta promoviendo (como también ha acontecido en este caso) el contacto entre el empleador y los demandantes de empleo que se adecuen a los requerimientos de la misma.

Transcurridos ocho días desde la presentación de la oferta por el empleador, éste deberá comunicar al Servicio Público de Empleo el resultado de la selección de candidatos que se han presentado para cubrir los puestos de trabajo vacantes, indicando los candidatos que han sido admitidos y los que han sido rechazados, así como la causa del rechazo. También ello ha sido realizado.Y en fin, el precepto reglamentario dispone que el Servicio Público de Empleo emitirá la certificación de insuficiencia de demandantes en un plazo máximo de tres días contados a partir de la comunicación por parte del empleador del resultado de la selección.

CUARTO.- FONDO DE LA CUESTIÓN CONTROVERTIDA.-Como se ha indicado y justificado por aportación de la oportuna documentación, lo cierto es que los trabajadores con los que se ha facilitado la comunicación por el Servicio Público de empleo carecen de la oportuna formación y sí una mera preparación genérica en el ramo, mientras que para esta empresa es imprescindible la posesión de conocimientos o formación en [MATERIA PRECISA].

Por la misma razón de máxima especialidad de la actividad, ésta no se encuentra comprendida en un instrumento forzosamente genérico como es el Catálogo de Ocupaciones de Difícil Cobertura previsto en el Reglamento de desarrollo de la Ley Orgánica 4/2000, con sus sucesivas modificaciones.

En consecuencia [ARGUMENTOS COMPLEMENTARIOS REFERIDOS AL CASO CONCRETO]

QUINTO.- COSTAS.- [LO] que proceda en el caso concreto

[ELEGIR: (Si se solicita la celebración de la vista)Por lo anteriormente expuesto,]

SUPLICO al Tribunal que tenga por presentado este escrito, en unión de los documentos que adjunto se acompañan, y sus copias, tenga por interpuesto en forma recurso contencioso administrativo y formulada al propio tiempo demanda de procedimiento abreviado contra el acto presunto, emitido por silencio administrativo negativo, más arriba identificado, que dicte providencia en la que ordene la admisión de la demanda y su traslado a las demandadas, cite a las partes para la celebración de vista, y, después de los oportunos trámites, dicte sentencia por la que anule el acto impugnado y declare que la ocupación solicitada es en efecto de difícil ocupación, todo ello con expresa imposición de costas a la parte demandada.(Si NO se solicita la celebración de la vista)Por lo anteriormente expuesto,

SUPLICO al Tribunal que tenga por presentado este escrito, en unión de los documentos que adjunto se acompañan, y sus copias, tenga por interpuesto en forma recurso contencioso administrativo y formulada al propio tiempo demanda de procedimiento abreviado contra el acto presunto más arriba identificado, que dicte providencia en la que ordene la admisión de la demanda y su traslado a las demandadas para que la contesten en el plazo de veinte días, ya que esta representación, como se indicará en oportuno otrosí, solicitará que el recurso se falle sin necesidad de prueba ni tampoco celebración de vista, por lo que, después de los oportunos trámites, dicte sentencia por la que anule el acto presunto impugnado y declare que la ocupación solicitada es en efecto de difícil ocupación, todo ello con expresa imposición de costas a la parte demandada.

Conforme a las determinaciones de los arts. 45.2 y 78.2 de la LJCA, adjunto acompaño los siguientes documentos:1º.- Copia del poder otorgado y acreditativo de la representación del compareciente.2º.- Documento justificativo de la condición de legitimado de mi principal, en su condición de causahabiente de [IDENTIFICACIÓN], solo para el caso de la concurrencia de esta circunstancia.3º.- Copia de la solicitud de certificación formulada por esta parte.4º.- Documento que acredita el cumplimiento por mi mandante de los requisitos exigidos para entablar acciones las personas jurídicas [SOLO APLICABLE A LAS PERSONAS JURÍDICAS].5º.- Documentos esenciales en los que esta parte justifica su derecho, conforme a lo dispuesto en el art. 78.2 de la LJCA.PRIMER OTROSÍ: Conforme a los arts. 40 y 42 de la LJCA cifro la cuantía del presente recurso como indeterminada.

[ELEGIR: Si se solicita apertura del procedimiento de prueba]

SEGUNDO OTROSÍ: Conforme al art. 60 de la LJCA, esta parte solicita expresamente la apertura del procedimiento a prueba, señalando los puntos de hecho sobre los que la misma deberá versar, que son los siguientes: [PUNTOS DE HECHO].

Asimismo, conforme al indicado art. 60 LJCA en la redacción dada por la Ley 37/2011, de 10 de octubre, de Medidas de Agilización Procesal, procedo a proponer los siguientes medios probatorios de los que pretendo valerme: [los que procedan, debiendo tener en cuenta que los medios probatorios son los previstos en los arts. 299 y ss de la LEC]
(Si NO se solicita apertura del procedimiento de prueba)

SEGUNDO OTROSÍ: Por interesarle a esta representación y conforme al art. 78.1 de la LJCA solicito que el recurso se falle sin necesidad de prueba ni tampoco celebración de vista.

Por ser de Justicia que pido [LUGAR], a [FECHA].

Firma de Abogado/a

Firma de Procurador/a
