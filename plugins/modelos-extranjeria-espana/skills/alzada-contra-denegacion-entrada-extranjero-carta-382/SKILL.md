---
name: alzada-contra-denegacion-entrada-extranjero-carta-382
description: "Redacta el escrito «Alzada contra denegación de entrada a un extranjero con carta de invitación» (formulario 382 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra denegación de entrada a un extranjero con carta de invitación

> Formulario 0382 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] NACIONALIDAD
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] IMPORTE
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…euros y»; «…n el puesto fronterizo del aeropuerto de»; «…, con domicilio en [LOCALIDAD],»; «…, [COMPLETAR],»; «…ades policiales del puesto fronterizo de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 122 de la Ley 39/2015
- art. 121 de la Ley 39/2015
- art. 32 de la Ley 40/2015
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

### Formulario 0382 · Alzada contra denegación de entrada a un extranjero con carta de invitación

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco
- Avisos de la revisión: El art. 4 RD 1155/2024 está reescrito conforme al art. 6 del Reglamento (UE) 2016/399. Si los hechos son anteriores al 20-5-2025, citar el RD 557/2011.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA DIRECCIÓN GENERAL DE LA POLICÍA

Reg:

D./Dña. [NOMBRE Y APELLIDOS], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], de nacionalidad [NACIONALIDAD], ante este organismo comparezco para formular

RECURSO DE ALZADA

Contra la resolución de fecha [FECHA] por la que se denegaba a D./Dña. [NOMBRE Y APELLIDOS] la entrada en el territorio nacional, así como el retorno al lugar de procedencia de su vuelo, copia de la cual se adjunta con el presente escrito.

Fundamento este recurso en base a los siguientes

HECHOS

Primero.- D./Dña. [NOMBRE Y APELLIDOS] tenía intención de realizar un viaje a España por un período de [Nº] días, disponiendo de billete de vuelta, carta de invitación de ciudadano español y [IMPORTE] euros y [COMPLETAR] dólares en efectivo.

Segundo.- A pesar de lo expuesto, en el puesto fronterizo del aeropuerto de [COMPLETAR], se dictó resolución por la que se acordó denegar la entrada en territorio español del recurrente y su retorno al lugar de procedencia por considerar que el pasajero «no reunía el requisito de presentar los documentos que justifiquen el objeto y las condiciones de la estancia prevista».

Tercero.- A efectos de notificaciones, se designa el despacho profesional del/de la letrado/a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], [COMPLETAR], [COMPLETAR].

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el art. 122 de la Ley 39/2015, de 1 de octubre, del procedimiento administrativo común de las Administraciones Públicas, se este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el art. 121 de la Ley 39/2015, este recurso se presenta ante el órgano competente para resolver el recurso.

III

Se encuentra expresamente autorizado el letrado D./Dña. [NOMBRE Y APELLIDOS] para interponer este recurso en nombre y representación del recurrente, según consta en la declaración prestada por el mismo ante las autoridades policiales del puesto fronterizo de [COMPLETAR].

IV

En lo relativo a la entrada en España de ciudadanos extranjeros, es de aplicación la siguiente normativa:

Arts. 3 y siguientes del convenio de aplicación del Acuerdo de Schengen.

Art. 25 de la Ley Orgánica 4/2000, en su redacción en el momento en que los hechos tuvieron lugar.

Arts. 4 a 15 del Real Decreto 1155/2024 [NOTA DE REVISIÓN: Rango válido (requisitos de entrada a denegación de entrada). Si los hechos son anteriores al 20-5-2025, la norma aplicable «en el momento de los hechos» es el RD 557/2011. Fuente: RD 1155/2024, arts. 4-15 (BOE-A-2024-24099).], de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000 .

Instrucción consular común dirigida a las misiones diplomáticas y oficinas consulares de carrera de las partes contratantes del Convenio de Schengen (2005/C 326/01).

Pues bien, en el presente caso debe concluirse que el recurrente cumplía con los requisitos exigidos por la legislación vigente, toda vez que disponía de billete de vuelta, carta de invitación y de medios económicos suficientes para el período previsto de estancia.

V

En el presente caso debe ser de aplicación el art. 32 de la Ley 40/2015, de 1 de octubre, de Régimen Jurídico del Sector Público, que establece que «los particulares tendrán derecho a ser indemnizados por las Administraciones Públicas correspondientes de toda lesión que sufran en cualesquiera de sus bienes y derechos, siempre que la lesión sea consecuencia del funcionamiento normal o anormal de los servicios públicos salvo en los casos de fuerza mayor o de daños que el particular tenga el deber jurídico de soportar de acuerdo con la Ley».

La lesión sufrida por el recurrente ha sido efectiva, por cuanto se le ha impedido la entrada en territorio español, haciéndole perder el importe del billete de avión, además de los días de vacaciones que el incidente le ha hecho perder.

VI

El art. 117.1 y 2.a) de la Ley 39/2015 establece que:

«1. La interposición de cualquier recurso, excepto en los casos en que una disposición establezca lo contrario, no suspenderá la ejecución del acto impugnado.
2. No obstante lo dispuesto en el apartado anterior, el órgano a quien competa resolver el recurso, previa ponderación, suficientemente razonada, entre el perjuicio que causaría al interés público o a terceros la suspensión y el ocasionado al recurrente como consecuencia de la eficacia inmediata del acto recurrido, podrá suspender, de oficio o a solicitud del recurrente, la ejecución del acto impugnado cuando concurran alguna de las siguientes circunstancias:
a) Que la ejecución pudiera causar perjuicios de imposible o difícil reparación.»

En el presente caso, resulta evidente que la ejecución del retorno de la recurrente le causaría un perjuicio cierto y que dicho perjuicio es de imposible reparación, pues una vez ejecutado el retorno, una eventual resolución estimatoria del recurso resultaría inejecutable, con lo que dicho perjuicio sería de imposible reparación.

Por ello, debería procederse a adoptar la medida de suspensión de la ejecución del retorno de la interesada a su lugar de procedencia, ya que dicha medida no causaría ningún perjuicio a terceros ni al interés público.

VII

Dado que la resolución parece estar motivada en la falta de credibilidad que la Administración le da a la documentación aportada por el viajero, se propone al instructor del recurso la realización de la siguiente PRUEBA:

– Que se tome declaración a D./Dña. [NOMBRE Y APELLIDOS], quien firmó la carta de invitación que figura en el expediente, a fin de que se reitere en los motivos de la invitación, las circunstancias en que se conoció con el recurrente y cualquier otra circunstancia que pueda haber hecho dudar de la veracidad de lo manifestado en la carta de invitación o en la declaración del recurrente en el puesto fronterizo.

Por lo expuesto SOLICITO que, teniendo por presentado este recurso con los documentos que se adjuntan, se sirva admitirlo y previos los trámites oportunos, se dicte resolución por la que se declare la nulidad de la resolución recurrida, declarándose el derecho del recurrente a entrar en España en calidad de turista e indemnizando al mismo en cantidad equivalente al importe del billete de avión más la cantidad deeuros por el daño moral sufrido, así como que, mientras se resuelve el presente recurso, se suspenda la ejecución del retorno del interesado a su país de origen.

En [LUGAR], a [FECHA].

Fdo.:
