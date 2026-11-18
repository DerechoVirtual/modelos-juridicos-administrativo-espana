---
name: reposicion-contra-visado-reagrupacion-denegado-no-373
description: "Redacta el escrito «Reposición contra visado de reagrupación denegado por no acreditar edad o parentesco» (formulario 373 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra visado de reagrupación denegado por no acreditar edad o parentesco

> Formulario 0373 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Reagrupación: la autorización está en los arts. 67-68 RD 1155/2024 y el visado en el art. 40.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AL CONSULADO GENERAL DE ESPAÑA EN»; «…, que le ha sido notificada el»; «…, arts. 40, 67 y 68 (BOE-A-2024-24099).]»; «…ada. Tercero.- El Consulado de España en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 40 del Real Decreto 1155/2024
- art. 124 de la Ley 39/2015
- art. 123 de la Ley 39/2015
- art. 35 de la Ley 39/2015
- art. 48 de la Ley 39/2015
- Ley Orgánica 4/2000

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

### Formulario 0373 · Reposición contra visado de reagrupación denegado por no acreditar edad o parentesco

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 10 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Reagrupación: la autorización está en los arts. 67-68 RD 1155/2024 y el visado en el art. 40.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL CONSULADO GENERAL DE ESPAÑA EN [COMPLETAR]

N/ REF:

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad [NACIONALIDAD], con pasaporte n.º [DNI/NIE], en nombre y representación de su hijo, D. [NOMBRE Y APELLIDOS], ante este organismo comparece para interponer RECURSO DE REPOSICIÓN contra la resolución de fecha [FECHA], que le ha sido notificada el [COMPLETAR] por la que se denegaba la solicitud de visado.

Dicha denegación se basa en que «por su complexión física y su aspecto facial el solicitante tiene una edad superior a la edad declarada en la solicitud. Por todo ello existen indicios suficientes para dudar de la identidad de la persona que solicita el visado, así como de la validez de los documentos aportados y de la veracidad de los motivos alegados para solicitar el visado, pues o bien la persona presentada no es la que dice ser, o bien la documentación aportada no se corresponde con la persona que la aporta o presenta graves inexactitudes, causas todas ellas y cada una por sí misma suficientes para desestimar la solicitud».

Se adjunta copia de la resolución denegatoria.

Fundamento este recurso en base a los siguientes

HECHOS

Primero.- Se presentó solicitud visado por reagrupación familiar el día [FECHA].

Segundo.- Previamente, se había obtenido, de acuerdo con lo dispuesto en la Ley Orgánica 4/2000 y en el art. 40 del Real Decreto 1155/2024 que aprueba su Reglamento de desarrollo [NOTA DE REVISIÓN (comprobar): La resolución favorable de la autorización de reagrupación se dicta conforme a los arts. 67-68. El art. 40 regula solo la tramitación del visado de reagrupación. Las otras dos menciones del art. 40 (tramitación del visado) sí son correctas. Fuente: RD 1155/2024, arts. 40, 67 y 68 (BOE-A-2024-24099).] [COMPLETAR], resolución favorable de la Administración española con valor de autorización de residencia.

Se adjunta a efectos de prueba copia de la resolución mencionada.

Tercero.- El Consulado de España en [COMPLETAR], sin más trámites, y sin requerir para la subsanación de posibles defectos o carencias de la solicitud de visado, emitió resolución denegando el visado.

Cuarto.- A efectos de notificaciones, se designa el siguiente domicilio:

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el art. 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el art. 123 de la Ley 39/2015, de 1 de octubre, este recurso se presenta ante el órgano que dictó la resolución.

III

En la solicitud de autorización de residencia por reagrupación familiar y en la tramitación del visado, se ha seguido lo dispuesto en el art. 40 del Real Decreto 1155/2024

IV

La resolución recurrida se considera totalmente falta de motivación, pues no puede considerarse tal una mera duda sobre la edad del solicitante, ya que se limita a exponer que en opinión de los funcionarios ésta no corresponde con la manifestada por el solicitante, pero sin manifestar si existe algún otro motivo relevante que apoye dicha presunción y sin requerir que se aporte algún otro documento que pueda acreditar la edad del interesado, como una prueba médica oseométrica.

Y es que dejar la valoración de la minoría de edad al mero criterio de un funcionario abre la puerta a una discrecionalidad inadmisible, que rayaría con la arbitrariedad.

Dicha actuación supone, pues, una vulneración del art. 35 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, por su falta de motivación y es causa de anulabilidad de la resolución recurrida.

V

En la actualidad existen procedimientos para acreditar científicamente la edad de una persona o su parentesco con otras, sin que conste que en el presente caso se haya requerido al solicitante para que aporte otras pruebas que acreditaran su identidad ni su minoría de edad.

Tampoco consta que se haya realizado trámite alguno con las autoridades senegalesas para comprobar la autenticidad de la documentación aportada con la solicitud de visado.

Todo ello contraviene lo establecido en el art. 48 de la Ley 39/2015, de 1 de octubre, y causa a su vez de anulabilidad de la resolución recurrida.

Debe, pues recordarse que la STS, Sala de lo Contencioso-Administrativo, Sección 5ª, de 30 abril 2008, Rec. 7805/2004, afirmaba que:

«Es preciso señalar en primer lugar que como mas arriba se ha señalado en el expediente administrativo consta el pasaporte del hijo con fecha de nacimiento 12 de marzo de 1984, documento Oficial que no ha sido impugnado por la demandada, según el cual a la fecha de iniciarse la primera solicitud 30 de noviembre de 2000, tendría 16 años y ocho meses».

«Pues bien, siendo este el único documento con el que la administración pretende acreditar su tesis denegatoria, pues no hay en el expediente ningún otro documento acerca de otra prueba practicada al solicitante, y con la información contenida en el citado informe, que no ha sido impugnado por la demandada no puede colegirse que el reagrupable excediera la edad de 18 años requerida conforme a la normativa vigente, como una de las condiciones para la reagrupación, pues no hay que olvidar, como ya se ha señalado por esta Sección en varias Sentencias entre otras la Sentencia de 3 de julio de 2003, dictada en el recurso 1635/2002, y en la Sentencia dictada el 27 de junio de 2003, dictada en el recurso 3835 de 2001, que la maduración ósea de los individuos es mas temprana en las poblaciones subsaharianas (negroides), en relación a las poblaciones europeas (conforme a las tablas de Greulich y Pype para la estimación de la maduración ósea) y siendo el visado solicitado para reagrupación familiar y constando en el expediente el pasaporte Oficial expedido por las autoridades de la República de Senegal procede la estimación del Recurso, ya que, las dudas mostradas por la parte demandada en orden a la edad del reagrupable quedan despejadas con la documentación aportada, debiendo declararse la nulidad de la resolución recurrida en cuanto se produjo una errónea valoración y apreciación de la documentación aportada, anulándose la resolución impugnada y declarando como solicita la actora, el derecho del demandante a que se reconozca a su hijo Sebastián el visado por reagrupación familiar, al no haberse opuesto como motivo denegatorio de su concesión ningún otro más que el ya expuestos de la edad, cumplimentándose el resto de requisitos determinados por la norma para su concesión».

Debe remarcarse que esta sentencia resolvía un supuesto similar al presente, pero en el cual se había presentado una prueba médica referida a la edad del reagrupado, mientras que en el presente caso ni siquiera se requirió prueba alguna, sino que se consideró prueba suficiente de la mayoría de edad del interesado la complexión física y el aspecto facial del solicitante, que a juicio del funcionario competente, evidenciaban la mayoría de edad del interesado, lo que resulta inaceptable desde el punto de vista de la seguridad jurídica del solicitante.

VI

En el presente caso, además, el procedimiento había pasado un trámite previo, obteniéndose resolución favorable de otra administración concediendo lo solicitado y sin que se cuestionara en ningún momento la validez o autenticidad de la documentación aportada.

Se considera, pues, que en este caso se ha vulnerado el principio de los actos propios de la Administración, pues una Administración parece cuestionar una decisión tomada por otra Administración sin exponer motivadamente las razones que le llevan a ello.

VII

Por todo lo expuesto,

SOLICITO

Que se tenga por presentado el presente recurso con la documentación que se adjunta y previos los trámites oportunos sea concedido el visado solicitado, al considerar que los hechos y la documentación adjunta, desvirtúan los fundamentos de derecho de la resolución recurrida.

En [LUGAR], a [FECHA].

Fdo.:
