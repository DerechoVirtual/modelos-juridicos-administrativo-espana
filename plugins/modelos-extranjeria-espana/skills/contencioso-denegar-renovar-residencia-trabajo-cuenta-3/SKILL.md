---
name: contencioso-denegar-renovar-residencia-trabajo-cuenta-3
description: "Redacta el escrito «Contencioso por denegar renovar residencia y trabajo por cuenta ajena (antecedentes policiales)» (formulario 3 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso por denegar renovar residencia y trabajo por cuenta ajena (antecedentes policiales)

> Formulario 0003 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce», desaparece «dieciocho en veinticuatro»; la denegación por orden público exige informe policial motivado, art. 78.1.e).

## Nota explicativa: puntualizaciones de la revisión

La nota explicativa de este formulario se ha revisado en el BOE. Tenlo en cuenta al redactar:

- El art. 8.4 LJCA vigente atribuye a estos órganos todas las resoluciones de extranjería dictadas por la Administración periférica del Estado «o por los órganos competentes de las Comunidades Autónomas»; no hace falta acudir al art. 8.2 LJCA (que solo cubre personal, sanciones y responsabilidad patrimonial) cuando la autorización la resuelva la Comunidad Autónoma.
- Desde el 31-12-2025 los Juzgados de lo Contencioso-Administrativo son Secciones de lo Contencioso-Administrativo del Tribunal de Instancia (LO 1/2025, DT 1.ª y DA 1.ª; arts. 84.2.h y 93 LOPJ); la plaza conserva el número del antiguo Juzgado. El procedimiento abreviado en extranjería sigue en el art. 78.1 LJCA (redacción de la LO 1/2025, vigente desde el 3-4-2025).
- En el RD 1155/2024 (vigente desde el 20-5-2025), el art. 78 regula la denegación de las autorizaciones iniciales de residencia temporal y trabajo por cuenta ajena y el art. 80 su renovación; el art. 80.8 extiende a la renovación las causas del art. 78 (entre ellas, la amenaza para el orden público acreditada y motivada en informe policial, art. 78.1.e), y el art. 80.5.a), como el art. 31.7.a) LO 4/2000, ordena valorar los antecedentes penales y la condena cumplida, indultada, remitida o suspendida.
- El INEM ya no existe: el Servicio Público de Empleo Estatal está pendiente de transformarse en la Agencia Española de Empleo (Ley 3/2023, de Empleo, art. 18).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión. Empieza con una nota explicativa (para qué sirve el escrito y cuándo se usa) y acaba con sus notas al pie, revisadas en el BOE: léela antes de redactar, pero no la copies en el escrito.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (5 veces)
- [ ] LUGAR (2 veces)
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…ro de Tarjeta de Identidad de Extranjero»; «…y cuya duración concluía el»; «…mporal y trabajo. SEGUNDO.- Por ello, en»; «…esidencia y trabajo. En el presente caso»; «…mposible o difícil reparación a causa de»; «…probatorios de los que pretendo valerme:»

## Elecciones que hay que hacer

- Procurador/a de los Tribunales / Letrado/a dotado/a de representación conforme al art. 23.1 de la LJCA
- Delegado del Gobierno / Subdelegado del Gobierno o autoridad autonómica
- Delegado del Gobierno / Subdelegado del Gobierno / autoridad autonómica de la Comunidad Autónoma

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si NO solicita la apertura del procedimiento a prueba / Si solicita la apertura del procedimiento a prueba — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTROSÍ: Que solicito la adopción de la medida cautelar de suspensión de la ejecutividad de la resolució…
- SEGUNDO OTROSÍ: Conforme a los arts. 40 y 42 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 23.1 de la LJCA
- art. 78 de la Ley 29/1998
- art. 78.1 del Real Decreto 1155/2024
- art. 19.1 de la Ley 29/1998
- art. 8 de la Ley 29/1998
- art. 14 de la Ley 29/1998
- art. 31.5 de la Ley Orgánica 4/2000
- art. 31.7 de la Ley Orgánica 4/2000
- art. 139 de la Ley 29/1998
- arts. 45.2 y 78.2 de la Ley 29/1998
- art. 78.2 de la LJCA
- art. 129 de la Ley 29/1998
- arts. 40 y 42 de la Ley 29/1998

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

### Formulario 0003 · Contencioso por denegar renovar residencia y trabajo por cuenta ajena (antecedentes policiales)

- Año del modelo: 2025
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 llamadas a nota sin texto retiradas; 3 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 2 párrafos opcionales señalados; 16 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 3 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)
- Avisos de la revisión: Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce», desaparece «dieciocho en veinticuatro»; la denegación por orden público exige informe policial motivado, art. 78.1.e).
- Nota explicativa incorporada desde la colección Procesal (formulario 29) y revisada en el BOE el 17-11-2026

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

#### Nota explicativa: para qué sirve este escrito

Escrito mediante el cual se interpone demanda, a tramitar por el procedimiento abreviado, en el orden contencioso-administrativo contra resolución que deniega la renovación de autorización de trabajo y residencia a extranjero detenido. Escrito mediante el cual se interpone demanda, a tramitar por el procedimiento abreviado, en el orden contencioso-administrativo contra resolución que deniega la

---

A la Sección de lo Contencioso-Administrativo del Tribunal de Instancia de [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [ELEGIR: Procurador/a de los Tribunales / Letrado/a dotado/a de representación conforme al art. 23.1 de la LJCA], actuando en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según copia de poder general para pleitos que acompaño adjunta como Documento n.º Uno, solicitando que, una vez testimoniada y por necesitarla para otros usos me sea devuelta, por el presente escrito, y, de acuerdo con lo dispuesto en el art. 78 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativa (en adelante, LJCA), comparezco y DIGO

Que procedo a interponer recurso contencioso administrativo, directamente por escrito de demanda iniciadora de procedimiento abreviado, contra la resolución del [ELEGIR: Delegado del Gobierno / Subdelegado del Gobierno o autoridad autonómica] de [COMPLETAR], de fecha [FECHA], por la que se deniega a D./Dña. [NOMBRE Y APELLIDOS] la renovación de la autorización de residencia y trabajo por cuenta ajena de que disfrutaba por alguna de las causas previstas en los arts. 78 u 80 del Reglamento [NOTA DE REVISIÓN: Numeración correcta en el RD 1155/2024: art. 78 (denegación de autorizaciones iniciales por cuenta ajena) y art. 80 (renovación por cuenta ajena; equivale al art. 71 RD 557/2011). Solo se corrige la errata «u80». Fuente: RD 1155/2024, arts. 78 y 80 (BOE-A-2024-24099).] de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, aprobado Real Decreto 1155/2024, de 19 de noviembre.

HECHOS

PRIMERO.- D./Dña. [NOMBRE Y APELLIDOS] y número de Tarjeta de Identidad de Extranjero [COMPLETAR] era titular de un permiso de residencia temporal y trabajo, que le fue otorgado en fecha [FECHA] y cuya duración concluía el [COMPLETAR]. Acompaño, como documento número Dos, copia de dicha autorización de residencia temporal y trabajo.

SEGUNDO.- Por ello, en [COMPLETAR] formuló solicitud de renovación de dicha autorización en el tiempo hábil previsto por el art. 80 del Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, aprobado Real Decreto 1155/2024, de 19 de noviembre. Acompaño como Documento n.º Tres copia de dicha solicitud.

TERCERO.- Por resolución del [ELEGIR: Delegado del Gobierno / Subdelegado del Gobierno / autoridad autonómica de la Comunidad Autónoma], de fecha [FECHA], ha sido denegada dicha solicitud con fundamento en la posesión de antecedentes policiales por parte del solicitante y en aplicación del art. 80.8 en relación con el art. 78.1 del Real Decreto 1155/2024, de 19 de noviembre. Acompaño como Documento n.º Cuatro copia de la resolución denegatoria.

FUNDAMENTOS DE DERECHO

PRIMERO.- LEGITIMACIÓN

Esta parte posee la oportuna legitimación, según el art. 19.1 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativa, por afectar la actividad administrativa que es objeto de impugnación a sus derechos o intereses legítimos.

SEGUNDO.- COMPETENCIA Y PROCEDIMIENTO

La competencia funcional y objetiva para el conocimiento del presente recurso les corresponde a los Tribunales de Instancia (Secciones de lo Contencioso-Administrativo), al amparo de la atribución competencial contenida en el art. 8 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativa.

La competencia territorial reside en el Tribunal al que esta parte tiene el honor de dirigirse conforme al art. 14 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativa.

El procedimiento ajustado a derecho para la tramitación de este recurso será el abreviado, regulado en el art. 78 de la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso Administrativa, por versar la cuestión controvertida sobre extranjería.

TERCERO.- FONDO DE LA CUESTIÓN CONTROVERTIDA

El art. 31.5 de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, dispone que para autorizar la residencia temporal de un extranjero «será preciso que carezca de antecedentes penales en España o en los países anteriores de residencia, por delitos existentes en el ordenamiento español, y no figurar como rechazable en el espacio territorial de países con los que España tenga firmado un convenio en tal sentido». Como cabe ver, la norma legal no contiene previsión alguna en orden a la denegación de la autorización por estar incurso en diligencias policiales.

Lo propio puede obtenerse del art. 31.7 de la Ley Orgánica 4/2000, de 11 de enero, que tampoco recoge esa posesión de antecedentes policiales como obstativa para la renovación de las autorizaciones de residencia y trabajo.

En el presente caso [COMPLETAR].

CUARTO.- COSTAS

Procede imponer las costas a la Administración demandada conforme al art. 139 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa.

Por lo anteriormente expuesto,

SUPLICO AL TRIBUNAL

Que tenga por presentado este escrito, en unión de los documentos que adjunto se acompañan y sus copias, tenga por interpuesto en forma recurso contencioso administrativo y formulada al propio tiempo demanda de procedimiento abreviado contra el acto más arriba identificado, que dicte providencia en la que ordene la admisión de la demanda y su traslado a las demandadas, cite a las partes para la celebración de vista, y, después de los oportunos trámites dicte Sentencia por la que anule el acto impugnado y, en su lugar, proceda a otorgar al recurrente la renovación de su autorización de residencia y trabajo, condenando a la Administración a estar y pasar por dicho reconocimiento.

Conforme a las determinaciones de los arts. 45.2 y 78.2 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa, adjunto acompaño, además de los más arriba indicados, los siguientes documentos:

1º.- Copia del poder otorgado y acreditativo de la representación del compareciente.
2º.- Copia del acto impugnado.
3º.- Documentos esenciales en los que esta parte justifica su derecho, conforme a lo dispuesto en el art. 78.2 de la LJCA.

Es de Justicia que pido en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

PRIMER OTROSÍ: Que solicito la adopción de la medida cautelar de suspensión de la ejecutividad de la resolución recurrida al amparo de lo dispuesto en el art. 129 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, para su tramitación en pieza separada, por cuanto la ejecución del acto recurrido causaría a mi mandante perjuicios de imposible o difícil reparación a causa de [COMPLETAR], por lo que de no adoptarse tales medidas el presente recurso perdería su finalidad legítima.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSÍ: Conforme a los arts. 40 y 42 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-administrativa cifro la cuantía del presente recurso como indeterminada.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si NO solicita la apertura del procedimiento a prueba / Si solicita la apertura del procedimiento a prueba — el texto de cada opción no venía en el formulario original]

Asimismo, procedo a proponer los siguientes medios probatorios de los que pretendo valerme: [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

---

#### Notas al pie

(1) El art. 8.4 de la LJCA atribuye a los Juzgados de lo Contencioso Administrativo el control de legalidad de todas las resoluciones que se dicten en materia de extranjería por la Administración periférica del Estado, y el art. 8.2 de LJCA de los recursos que se deduzcan frente a los actos administrativos de la Administración de las Comunidades Autónomas, salvo cuando procedan del respectivo Consejo de Gobierno. Una u otra regla serían las aplicables cuando los Servicios Públicos de empleo dependan del Estado (Servicio Público de Empleo Estatal) o lo hagan de la Comunidad Autónoma

(2) Supuesto aplicable a los detenidos, pero podría darse la denegación por cualquier causa de los arts. 78 u 80 del Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, aprobado por Real Decreto 1155/2024, de 19 de noviembre

[NOTA DE REVISIÓN: El art. 8.4 LJCA vigente atribuye a estos órganos todas las resoluciones de extranjería dictadas por la Administración periférica del Estado «o por los órganos competentes de las Comunidades Autónomas»; no hace falta acudir al art. 8.2 LJCA (que solo cubre personal, sanciones y responsabilidad patrimonial) cuando la autorización la resuelva la Comunidad Autónoma.]

[NOTA DE REVISIÓN: Desde el 31-12-2025 los Juzgados de lo Contencioso-Administrativo son Secciones de lo Contencioso-Administrativo del Tribunal de Instancia (LO 1/2025, DT 1.ª y DA 1.ª; arts. 84.2.h y 93 LOPJ); la plaza conserva el número del antiguo Juzgado. El procedimiento abreviado en extranjería sigue en el art. 78.1 LJCA (redacción de la LO 1/2025, vigente desde el 3-4-2025).]

[NOTA DE REVISIÓN: En el RD 1155/2024 (vigente desde el 20-5-2025), el art. 78 regula la denegación de las autorizaciones iniciales de residencia temporal y trabajo por cuenta ajena y el art. 80 su renovación; el art. 80.8 extiende a la renovación las causas del art. 78 (entre ellas, la amenaza para el orden público acreditada y motivada en informe policial, art. 78.1.e), y el art. 80.5.a), como el art. 31.7.a) LO 4/2000, ordena valorar los antecedentes penales y la condena cumplida, indultada, remitida o suspendida.]

[NOTA DE REVISIÓN: El INEM ya no existe: el Servicio Público de Empleo Estatal está pendiente de transformarse en la Agencia Española de Empleo (Ley 3/2023, de Empleo, art. 18).]
