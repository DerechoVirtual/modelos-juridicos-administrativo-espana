---
name: designar-representante-tramitar-visados-l238
description: "Redacta el escrito «Designar representante para tramitar visados» (formulario 238 (Laboral) de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Designar representante para tramitar visados

> Formulario 0238 de la colección de Laboral del plugin **Extranjería** · revisado el 17-11-2026.

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

- Anexo de la orden GECCO 2020: sustituir por el modelo de la orden vigente dictada al amparo de los arts. 113-123 RD 1155/2024 (NO VERIFICADO cuál).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO
- [ ] NIF
- [ ] PROVINCIA (2 veces)
- [ ] ÓRGANO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 29 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…BOLETÍN OFICIAL DEL ESTADO Núm. 314»; «…Martes 31 de diciembre de 2019»; «…PARA MINISTERIO»; «…Seg. Social Denominación Social»; «…Actividad Domicilio»; «…Localidad»; «…Tfno. Fax»; «…mbre y apellidos del representante legal»; «… y apellidos del representante designado»; «…DNI/NIE/PASAPORTE Domicilio»; «…Localidad»; «…Tfno. Fax»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 5 y 66 de la Ley 39/2015
- Ley Orgánica 3/2018
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

### Formulario 0238 · Designar representante para tramitar visados

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 33 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, DÍA, LUGAR, MES)
- Avisos de la revisión: Anexo de la orden GECCO 2020: sustituir por el modelo de la orden vigente dictada al amparo de los arts. 113-123 RD 1155/2024 (NO VERIFICADO cuál).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

BOLETÍN OFICIAL DEL ESTADO
Núm. 314 [COMPLETAR] Martes 31 de diciembre de 2019 [COMPLETAR] Sec. I. Pág. 143820

                                                                                                     ANEXO II

                                                                GESTIÓN COLECTIVA DE CONTRATACIONES EN ORIGEN 2020
                                                                 DOCUMENTO DE DESIGNACIÓN DE REPRESENTANTE PARA
                            MINISTERIO [COMPLETAR] SOLICITUD DE VISADOS
                            DE TRABAJO, MIGRACIONES Y
                            SEGURIDAD SOCIAL

            OFERTA Nº [NÚMERO] Nº DE TRABAJADORES

           A. DATOS DE LA EMPRESA

            NIF/CIF [NIF] C.C.C. Seg. Social

            Denominación Social [COMPLETAR] Actividad

            Domicilio [COMPLETAR] Localidad [COMPLETAR] Código postal

            Provincia [PROVINCIA] Tfno. Fax [COMPLETAR] Correo electrónico

            Nombre y apellidos del representante legal [COMPLETAR] DNI/NIF/NIE

           B. DATOS DEL REPRESENTANTE DESIGNADO

            Nombre y apellidos del representante designado [COMPLETAR] DNI/NIE/PASAPORTE

            Domicilio [COMPLETAR] Localidad [COMPLETAR] Código postal

            Provincia [PROVINCIA] Tfno. Fax [COMPLETAR] Correo electrónico

           El representante legal firmante del presente documento, de conformidad con lo dispuesto en el artículo 18 de la Orden ________________________, cuya
           vigencia ha sido prorrogada por la Orden ____________________________, por la que se regula la gestión colectiva de contrataciones en origen para [NOTA DE REVISIÓN (comprobar): Modelo oficial de la orden GECCO para 2020 (BOE-A-2019-18753). Desde el 20-5-2025 la gestión colectiva se regula en los arts. 113-123 RD 1155/2024 (previsión anual por orden, art. 115). Qué orden y qué anexo están vigentes hoy: NO VERIFICADO. Fuente: RD 1155/2024, BOE-A-2024-24099 (vigente desde 20-5-2025), arts. 113-123.]
           2020, a los efectos de los artículos 5 y 66 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,
           DESIGNA a la persona cuyos datos constan en el apartado B de este documento, como representante para que formule en nombre de la
           empresa/organización empresarial cuya representación legal ostenta, la solicitud agrupada de visados de residencia y trabajo de los trabajadores incluidos
           en el Anexo IV de la Orden ____________, seleccionados en el proceso autorizado por la Dirección General de Migraciones como consecuencia de la
           oferta [COMPLETAR] de [COMPLETAR] empleo [COMPLETAR] arriba [COMPLETAR] indicada, [COMPLETAR] ante [ÓRGANO] la [ÓRGANO] Embajada [COMPLETAR] u [COMPLETAR] Oficina [COMPLETAR] Consular [COMPLETAR] de [COMPLETAR] España [COMPLETAR] en [COMPLETAR] (localidad [COMPLETAR] y [COMPLETAR] país) [COMPLETAR] ……………………
           ……………..…………………………………………….., y le autoriza a presentar y firmar cuantos documentos sean reglamentariamente exigibles así como a
           intervenir en cuantos trámites y diligencias requiera el procedimiento de concesión de visados, salvo aquéllas en que sea necesaria la comparecencia
           personal del solicitante.

           De conformidad con lo establecido Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales, se informa que los datos
           que suministren los interesados en este formulario, necesarios para resolver su petición, pasarán a formar parte del tratamiento cuyos destinatarios serán los órganos de la
           Administración General del Estado con competencias en extranjería, siendo responsables del mismo la Dirección General de Migraciones, la Dirección General de Españoles en
           el Exterior y de Asuntos Consulares y Migratorios y las Delegaciones o Subdelegaciones del Gobierno. El interesado tiene derecho a acceder, rectificar, solicitar portabilidad o
           suprimir sus datos así como a retirar su consentimiento en cualquier momento. Asimismo tiene derecho a presentar una reclamación ante la Agencia Española de Protección de
           Datos si su requerimiento no es atendido. El tratamiento de los datos se realizará sobre la base del ejercicio de poderes públicos autorizado por la disposición adicional quinta de
           la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social.

                                                             En [LUGAR] a [DÍA] de [MES] de 2020.
                                                             El/la Representante Legal de la Empresa/Organización Empresarial.

                                                                  Fdo:[COMPLETAR]

                                 Diligencia para hacer constar que se otorga ante mí esta designación de representación.

                                                                                          En …………...………………….. a ……….. de [COMPLETAR]…..……….. de 2020.
                                                                                                           El/la funcionario/a
                                                                                                                                                                                                                      Verificable en https://www.boe.es

                                                Sello de la Unidad
                                                                                                                                                                                                                      cve: BOE-A-2019-18753

                                                                                            Fdo.: ……………………….……………………………………………………

                                                                                           Puesto de trabajo: ………………………….………………………………….

                    IMPRESO GRATUITO. PROHIBIDA SU VENTA. RELLÉNESE A MÁQUINA O CON LETRA DE IMPRENTA Y PRESÉNTENSE DOS EJEMPLARES.

════════════════════════════════════════════════════════════════════════
