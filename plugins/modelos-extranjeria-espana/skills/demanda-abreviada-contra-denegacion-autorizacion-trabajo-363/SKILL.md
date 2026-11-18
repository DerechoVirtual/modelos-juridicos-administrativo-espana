---
name: demanda-abreviada-contra-denegacion-autorizacion-trabajo-363
description: "Redacta el escrito «Demanda abreviada contra la denegación de autorización de trabajo y residencia» (formulario 363 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda abreviada contra la denegación de autorización de trabajo y residencia

> Formulario 0363 del plugin **Extranjería** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] COLEGIO
- [ ] FECHA (8 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NACIONALIDAD
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] ÓRGANO O PERSONA
- [ ] NÚMERO (3 veces)
- [ ] artículo 19.1.a) de la LJCA
- [ ] LUGAR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…solución del Subdelegado del Gobierno de»; «…de fecha [FECHA], notificada el»; «…, la empresa»; «…domiciliada en la localidad de»; «…rta de empleo en la Oficina del INAEM de»; «… un puesto de trabajo en la ocupación de»; «…ón realizada por la oficina de empleo de»; «…rcado de trabajo exterior. Docs. núms. y»; «…tivo visado en el Consulado de España en»; «…. Tercero.- Es evidente que la empresa»; «…, notificada el»; «…ro de trabajo situado en la localidad de»; …

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO: Que de conformidad con lo prevenido en los arts. 45.2 y 78.2 de la LJCA, a la presente demanda se…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 78.1 LJCA
- art. 75 del Real Decreto 1155/2024
- art. 8.4 de la Ley 29/1998
- artículo 19.1.a) de la LJCA
- art. 38.2 de la Ley Orgánica 4/2000
- art. 139 LJCA
- arts. 45.2 y 78.2 de la LJCA
- Ley Orgánica 19/2003
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

### Formulario 0363 · Demanda abreviada contra la denegación de autorización de trabajo y residencia

- Año del modelo: 2013
- Revisión 17-11-2026: 1 párrafos opcionales señalados; 36 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 4 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 4 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: Situación nacional de empleo: el art. 75 RD 1155/2024 se mantiene en lo esencial (catálogo por comunidad autónoma).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del R. e I. Colegio de Abogados de [COLEGIO] y de D./Dña. [NOMBRE Y APELLIDOS], según acredito con la escritura de poder que acompaño y cuya devolución solicito una vez compulsada la copia que asimismo se adjunta, ante el Tribunal que por turno corresponda comparezco y, como mejor en Derecho proceda, DIGO:

Que, en la representación que ostento, dentro del plazo legal y al amparo de lo dispuesto en el art. 78.2 de la vigente Ley Reguladora de la Jurisdicción Contencioso-Administrativa de 13 de julio de 1998, interpongo Demanda de Recurso Contencioso-Administrativo por el procedimiento abreviado, de acuerdo con el art. 78.1 LJCA, en la redacción dada por la Ley Orgánica 19/2003, de 23 de diciembre, de modificación de la LOPJ, contra la resolución del Subdelegado del Gobierno de [COMPLETAR] de fecha [FECHA], notificada el [COMPLETAR], que acuerda denegar la solicitud de permiso de trabajo y residencia solicitada en fecha [FECHA].

Que dentro del plazo conferido al efecto por el art. 46.1 de la vigente Ley Reguladora de la Jurisdicción Contencioso-Administrativa, a evacuar el trámite mediante el presente escrito, el cual baso y fundamento en los siguientes

HECHOS

Primero.- Con fecha [FECHA], la empresa [COMPLETAR] domiciliada en la localidad de [COMPLETAR], solicitó a través del Área de Trabajo y Asuntos Sociales de la Delegación del Gobierno en [LOCALIDAD] autorización administrativa para la contratación del trabajador extranjero extracomunitario recurrente, de nacionalidad [NACIONALIDAD], D. Doc. núm. [Nº DE DOCUMENTO]

Previamente había efectuado oferta de empleo en la Oficina del INAEM de [COMPLETAR] para cubrir un puesto de trabajo en la ocupación de [COMPLETAR], resultando negativa la gestión realizada por la oficina de empleo de [COMPLETAR], haciendo imposible cubrir el puesto de trabajo ofertado por no existir demandantes de empleo disponibles. A pesar que la Oficina de empleo certifica que síexisten demandantes de empleo disponibles, ninguno de los candidatos llegaron a presentarse en la empresa, pues según Certifica el INAEM «se presentan en la Oficina los trabajadores y no les interesaba a ninguno la oferta».

Es por ello, ante la imposibilidad de cubrir la plaza por un trabajador español o extranjero residente desempleado, que la empresa optó por acudir al mercado de trabajo exterior. Docs. núms. y [COMPLETAR].

Segundo.- A la solicitud se acompañó toda la documentación preceptiva para este tipo de autorizaciones administrativas. Pese a ello la administración encargada del Registro no asignó el NEV (número de enlace de visado), por lo que el recurrente no pudo solicitar el preceptivo visado en el Consulado de España en [COMPLETAR].

Tercero.- Es evidente que la empresa [COMPLETAR] considera que el recurrente posee los requisitos exigidos, puesto que le hace una oferta de trabajo en firme. Doc. núm. [Nº DE DOCUMENTO]

Sin embargo, y pese a lo expuesto, con fecha [FECHA], notificada el [COMPLETAR], la Subdelegación del Gobierno de [LOCALIDAD], acuerda denegar la solicitud formulada «al concurrir la causa prevista en el art. 75 del Real Decreto 1155/2024, al haberse valorado la situación nacional del mercado de trabajo en base a la certificación expedida por [ÓRGANO O PERSONA], en la cual se constata la existencia de demandantes de empleo para la ocupación solicitada».

Cuarto.- En la resolución de este caso tienen una importancia decisiva los siguientes hechos:

1. Se trata de una oferta nominativa de empleo dirigida a atender una necesidad real de mano de obra extranjera que se efectúa para un centro de trabajo situado en la localidad de [COMPLETAR].
2. La gestión de los Servicios Públicos de empleo fue infructuosa, pues no permitió cubrir la oferta, dado que a ninguno de los trabajadores disponibles les interesó la Oferta. Doc. núm [NÚMERO].

FUNDAMENTOS DE DERECHO

I

Es competente el Tribunal al que nos dirigimos, en aplicación del art. 8.4 de la Ley 29/1998, de 13 de julio, reguladora de la Jurisdicción Contencioso-Administrativa, en relación con el art. 14 de la vigente Ley Jurisdiccional que establecen la competencia funcional y la regla de atribuir la competencia al órgano jurisdiccional en cuya circunscripción se hubiese realizado el acto originariamente impugnado.

II

Está legitimado de forma activa mi mandante para interponer el presente recurso, por cuanto se trata de la persona titular del derecho que se considera vulnerado y teniendo interés legítimo y directo en la pretensión que se solicita [artículo 19.1.a) de la LJCA].

Pasivamente lo está el órgano contra quien me dirijo de acuerdo con el art. 21.1.a) y ccLJCA, de quien depende la concesión del permiso de trabajo y residencia.

III

La Disposición Adicional novena del Real Decreto 1155/2024, establece que:

Las resoluciones que dicten los órganos competentes de los Ministerios de Asuntos Exteriores y de Cooperación, del Interior, y de Trabajo e Inmigración, los Delegados del Gobierno y Subdelegados del Gobierno, bajo la dependencia funcional de estos dos últimos Ministerios, con base en lo dispuesto en este Reglamento, sobre concesión o denegación de visados, prórrogas de estancia o autorizaciones de residencia y de trabajo, cédulas de inscripción, así como sobre sanciones gubernativas y expulsiones de extranjeros, pondrán fin a la vía administrativa, y contra éstas podrán interponerse los recursos administrativos o jurisdiccionales legalmente previstos. Se exceptúan las resoluciones sobre denegación de entrada y devolución, las cuales no agotan la vía administrativa.

IV

En cuanto al fondo, alegamos:

I. Infracción de los arts. 31, 36 y 38.1 de la Ley Orgánica sobre Derechos y Libertades de los Extranjeros en España y su Integración Social (LOE 4/2000), modificada por Ley Orgánica 2/2009, de 11 de diciembre, en relación con el art. 75 del Real Decreto 1155/2024.

1. La denegación se produce por la alegación de una hipotética situación nacional de empleo que desaconsejaría la contratación del trabajador recurrente.

Por lo que respecta al fondo del asunto la resolución impugnada pretende basar su denegación en una hipotética existencia de trabajadores nacionales inscritos en las Oficinas del INEM, que desaconsejaría la contratación del recurrente, habremos de examinar qué actuaciones administrativas se han llevado a cabo para determinar dicha alegación.

1. El empresario se dirige a la Oficina de Empleo de [COMPLETAR], solicitando la cobertura de un puesto de trabajo de auxiliar geriátrico. Entre otros requisitos específicos, tal y como se señalan en el apartado correspondiente del impreso de solicitud de la oferta, se refleja la preferencia de que el trabajador fuera mayor de 45 años.
2. Con fecha [FECHA], la Directora de la Oficina de Empleo emite Certificado Anexo II, doc. núm. [NÚMERO], en el que señala que existen demandantes de empleo disponibles para cubrir dicha oferta, por lo que se continúa el proceso de gestión, que según se desprende del Certificado Anexo III, doc. núm. [NÚMERO], la oferta no pudo cubrirse al no interesarle a ninguno de los trabajadores disponibles. El citado certificado dice expresamente: «se presentan en la oficina los trabajadores y no les interesa a ninguno la oferta».
3. Ante esa falta de disponibilidad el empleador solicita autorización para contratar al Sr. [COMPLETAR], que reúne los requisitos del puesto ofertado.

Con ello, el empleador cumplió con todos los requisitos legales exigidos para la contratación de trabajadores extracomunitarios. En efecto, tal y como señala el art. 38.2 de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social, modificada por Ley Orgánica 2/2009, el empresario español deberá dirigirse, en primer lugar al mercado nacional de empleo, pero en el caso de no poder cubrir sus necesidades en él, podrá intentarlo en el mercado exterior, bien a través del procedimiento o sistema de gestión de contrataciones en origen o a través de la contratación directa nominativa. La finalidad debe ser la de facilitar la contratación, no la de impedir o dificultar la ocupación del puesto de trabajo.

4. La administración recurrida objeta que la gestión realizada por la oficina pública de empleo de [COMPLETAR] constata la existencia de demandantes de empleo para la ocupación solicitada, pero lo que no se señala es que el propio Servicio Público de Empleo certifica que la oferta no interesó a ninguno de los trabajadores que se presentaron en la oficina. Doc. núm. [Nº DE DOCUMENTO]

Por consiguiente, debe considerarse el resultado de la gestión como negativo e infructuoso, dado que no consiguió su objetivo, la cobertura de la plaza ofertada.

2. Conclusión

En conclusión, reuniéndose en el presente caso todos los requisitos normativamente exigidos para la obtención del permiso de trabajo y no constando la existencia de trabajadores nacionales, comunitarios u otros capaces de desarrollar la actividad ofertada, acreditación que debió realizar la Administración mediante la certificación correspondiente, procede conceder el permiso solicitado.

V

Procede que se impongan las costas a la parte que se oponga a las pretensiones que se deducen en el presente Recurso, art. 139 LJCA.

VI

Cuantía.- Que dado el contenido de las pretensiones deducidas mediante el presente recurso su cuantía se considera indeterminada.

Por lo expuesto,

SUPLICO AL TRIBUNAL

Que tenga por presentado este escrito, y su copia, con el expediente administrativo que se devuelve, por deducida la demanda, y previos los trámites legales correspondientes, dictar en su día Sentencia por la que estimando el recurso interpuesto se declare el derecho de los recurrentes a la Autorización de Trabajo y Residencia solicitada.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que de conformidad con lo prevenido en los arts. 45.2 y 78.2 de la LJCA, a la presente demanda se acompañan los siguientes documentos:

1. Escrituras de poder y sus copias.
2. Copia sellada de:
a) Solicitudes de las autorizaciones de trabajo y residencia, de fecha [FECHA]. Doc. núm. [Nº DE DOCUMENTO]
b) Certificaciones de la oficina pública de empleo de [COMPLETAR] de fecha [FECHA]. Docs. núms. y [COMPLETAR]

SUPLICO AL TRIBUNAL que tenga por hechas las anteriores manifestaciones.

En [LUGAR], a [FECHA].

Fdo.:
