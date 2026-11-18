---
name: contencioso-contra-inadmision-residencia-trabajo-963
description: "Redacta el escrito «Contencioso contra la inadmisión de residencia y trabajo en la regularización extraordinaria» (formulario 963 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso contra la inadmisión de residencia y trabajo en la regularización extraordinaria

> Formulario 0963 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Se refiere a la regularización de 2005 (RD 2393/2004, DT 3.ª): solo tiene valor histórico.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] NACIONALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] LUGAR
- [ ] Otros 22 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, procedente del Delegado»; «…del Gobierno en la Comunidad de»; «…Tesorería General de la Seguridad Social»; «…n derogatoria única (BOE-A-2024-24099).]»; «…, procedente del Delegado»; «…del Gobierno en la Comunidad de»; «…o de reposición formulado contra otra de»; «…, de»; «…a Tercera del Real Decreto 2393/2004, de»; «…procedente del Delegado»; «…del Gobierno en la Comunidad de»; «…Tesorería General de la Seguridad Social»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 19.1 de la LJCA
- art. 14 de la LJCA
- art. 78 de la LJCA
- art. 45.2 de la LJCA
- art. 78.2 de la LJCA
- arts. 40 y 42 de la LJCA
- Ley 29/1998
- Real Decreto 2393/2004

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

### Formulario 0963 · Contencioso contra la inadmisión de residencia y trabajo en la regularización extraordinaria

- Año del modelo: 2008
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 35 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 3 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Se refiere a la regularización de 2005 (RD 2393/2004, DT 3.ª): solo tiene valor histórico.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

(NOTA GENERAL: Como se explica oportunamente en los temas, este cauce debe estimarse ya como concluido. Sin embargo, se mantiene el presente formulario por si pudiera haber aún en la actualidad algún recurso administrativo o judicial pendientes.)

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según copia de poder general para pleitos que acompaño adjunta, solicitando que, una vez testimoniada y por necesitarla para otros usos me sea devuelta, por el presente escrito, y, de acuerdo con lo dispuesto en el art. 78 de la de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa (LJCA), COMPAREZCO Y DIGO

Que procedo a interponer recurso contencioso administrativo, directamente por escrito de demanda iniciadora de procedimiento abreviado, contra la resolución de fecha [FECHA], procedente del Delegado [COMPLETAR] del Gobierno en la Comunidad de [COMPLETAR], por su delegación dictada por [ÓRGANO O PERSONA] adscrito a la Tesorería General de la Seguridad Social [COMPLETAR], que adjunta se acompaña por copia, por la que se decide inadmitir a trámite la solicitud de residencia y trabajo por cuenta ajena formulada por esta misma representación al amparo del proceso extraordinario de regularización previsto en la Disposición Transitoria Tercera del Real Decreto 2393/2004, para [NOTA DE REVISIÓN: Formulario histórico (regularización de 2005, RD 2393/2004 derogado). No tiene equivalente vigente. Conviene añadir la nota que ya lleva el formulario 957. Fuente: RD 1155/2024, disposición derogatoria única (BOE-A-2024-24099).] [COMPLETAR], de nacionalidad [NACIONALIDAD] y número/s de pasaporte [DNI/NIE], o contra la resolución de [FECHA], procedente del Delegado [COMPLETAR] del Gobierno en la Comunidad de [COMPLETAR], por la que se desestima el previo recurso de reposición formulado contra otra de [COMPLETAR], de [COMPLETAR], por la que se vino a inadmitir la solicitud de residencia y trabajo por cuenta ajena formulada, al amparo del proceso extraordinario de regularización previsto en la Disposición Transitoria Tercera del Real Decreto 2393/2004, de [COMPLETAR], de nacionalidad [NACIONALIDAD] y número/s de pasaporte [DNI/NIE], lo que efectúo al amparo de los siguientes:

HECHOS

PRIMERO.- Esta parte interesada no presentó en su momento, ante la Oficina de la Tesorería General de la Seguridad Social a la que fue asignada la labor de recepción de las solicitudes formuladas por la Resolución de 4 de febrero de 2005, de la Subsecretaría del Ministerio de la Presidencia (por la que se dispone la Publicación del convenio de colaboración entre la Secretaría de Estado de Inmigración y Emigración, la Secretaría de Estado de la Seguridad Social y la Subsecretaría de Administraciones públicas —BOE núm. 31, de 5 de febrero de 2005—), certificado de empadronamiento del/los trabajador/es cuya regularización se pretende y que, en efecto, fuera de fecha anterior al 8 de agosto de 2004.

Pero sí presentaba (y hoy lo hace adjuntos a este recurso) los siguientes documentos que justifican cumplidamente la presencia del trabajador en España antes de la referida fecha.

El resto de los requisitos documentales requeridos por las normas reguladoras del proceso extraordinario de regularización sí fueron oportunamente presentados.

SEGUNDO.- En fecha [FECHA] procedente del Delegado [COMPLETAR] del Gobierno en la Comunidad de [COMPLETAR], por su delegación emitida por [ÓRGANO O PERSONA] adscrito a la Tesorería General de la Seguridad Social [COMPLETAR], que adjunta se acompaña por copia, se dicta resolución por la que se decide inadmitir la solicitud de residencia y trabajo por cuenta ajena formulada al amparo del proceso extraordinario de regularización previsto en la Disposición Transitoria Tercera del Real Decreto 2393/2004, de [COMPLETAR].

FUNDAMENTOS DE DERECHO

PRIMERO.- LEGITIMACIÓN.-

Esta parte posee la oportuna legitimación, según el art. 19.1 de la LJCA, por afectar la actividad administrativa que es objeto de impugnación a sus derechos o intereses legítimos y, en concreto, por tener interés empresarial en la contratación de los indicados trabajadores para el mejor desarrollo de su actividad.

SEGUNDO.- COMPETENCIA Y PROCEDIMIENTO.-

La competencia funcional y objetiva para el conocimiento del presente recurso les corresponde a los Tribunales de Instancia (Secciones de lo Contencioso-Administrativo), al amparo de la atribución competencial contenida en el art. 8 de la misma Ley Reguladora de la Jurisdicción Contencioso Administrativa.

La competencia territorial reside en el Tribunal al que esta parte tiene el honor de dirigirse, conforme al art. 14 de la LJCA, por haber sido dictado el acto por el Delegado del Gobierno [COMPLETAR] en la Comunidad de [COMPLETAR].

El procedimiento ajustado a derecho para la tramitación de este recurso será el abreviado, regulado en el art. 78 de la LJCA, por versar la cuestión controvertida sobre extranjería.

TERCERO.- RECURRIBILIDAD AUTÓNOMA DEL ACTO.-

La resolución de inadmisión [COMPLETAR] cierra de modo definitivo la posibilidad de tramitar y obtener su solicitud de regularización, de modo que el acto es uno de aquellos que, siendo inicialmente calificables como ‘de trámite’, impiden sin embargo la continuación del procedimiento y, en consecuencia y conforme al art. 25.1 de la Ley Jurisdiccional, son susceptibles de impugnación separada.

CUARTO.- FONDO DE LA CUESTIÓN CONTROVERTIDA.-

[COMPLETAR]

En consecuencia [COMPLETAR]

QUINTO.- COSTAS.-

Por lo anteriormente expuesto,

SUPLICO

al Tribunal que tenga por presentado este escrito, en unión de los documentos que adjunto se acompañan, y sus copias, tenga por interpuesto en forma recurso contencioso administrativo y formulada al propio tiempo demanda de procedimiento abreviado contra el acto de inadmisión de solicitud de regularización más arriba identificado [COMPLETAR], que dicte providencia en la que ordene la admisión de la demanda y su traslado a las demandadas, cite a las partes para la celebración de vista, y, después de los oportunos trámites, dicte sentencia por la que anule el acto impugnado y reconozca el derecho a la regularización extraordinaria del trabajador/es [COMPLETAR], todo ello con expresa imposición de costas a la parte demandada.

Conforme a las determinaciones del art. 78.2 y art. 45.2 de la LJCA, adjunto acompaño los siguientes documentos:

1º.- Copia del poder otorgado y acreditativo de la representación del compareciente.
2º.- Documento justificativo de la condición de legitimado de mi principal, en su condición de causahabiente de [COMPLETAR].
3º.- Copia del acto impugnado.
4º.- Documento que acredita el cumplimiento por mi mandante de los requisitos exigidos para entablar acciones las personas jurídicas [COMPLETAR].
5º.- Documentos esenciales en los que esta parte justifica su derecho, conforme a lo dispuesto en el art. 78.2 de la LJCA.

PRIMER OTROSI: Conforme a los arts. 40 y 42 de la LJCA cifro la cuantía del presente recurso como indeterminada.

SEGUNDO OTROSÍ: Al ser la cuestión controvertida básicamente jurídica, esta parte estima innecesaria la apertura del procedimiento a prueba, a salvo de que la autenticidad de los documentos presentados por esta parte sea cuestionada por la Administración demandada.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
