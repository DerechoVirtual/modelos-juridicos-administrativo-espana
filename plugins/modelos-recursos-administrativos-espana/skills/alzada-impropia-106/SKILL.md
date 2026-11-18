---
name: alzada-impropia-106
description: "Redacta el escrito «Alzada impropia» (formulario 106 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada impropia

> Formulario 0106 del plugin **Recursos administrativos** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] ÓRGANO AL QUE SE DIRIGE
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] DESCRIBIR (2 veces)
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ropio Objeto: expediente de contratación»; «…, nº expediente»; «…D./Dña. [NOMBRE Y APELLIDOS], con DNI n°»; «…, señalando como medio de notificación»; «…de fecha [FECHA] por el que se»; «…menta en los siguientes HECHOS PRIMERO.-»; «…la resolución del»; «…hazo de la oferta decide la adjudicación»; «… Primero. Competencia. El acto recurrido»; «…control o participación mayoritaria." El»; «…e para resolver el presente recurso como»; «…del»; …

## Elecciones que hay que hacer

- de la mesa de contratación / del órgano de contratación
- se ha publicado / le ha sido notificada
- por un poder adjudicador que no tiene la consideración de Administración Pública / por un ente del sector público que no tiene el carácter de poder adjudicador
- se han visto perjudicados / puedan resultar afectados

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 44.6 de la Ley 9/2017
- artículo 121 de la Ley 39/2015
- artículo 44 de la Ley 9/2017
- artículo 122 de la Ley 39/2015
- artículo 4 de la Ley 39/2015
- artículo 117 de la Ley 39/2015
- Ley 29/1998

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

### Formulario 0106 · Alzada impropia

- Año del modelo: 2018
- Revisión 17-11-2026: 9 llamadas a nota sin texto retiradas; 4 desplegables convertidos en elección en blanco; 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al [ÓRGANO AL QUE SE DIRIGE]

Asunto: Recurso de alzada impropio

Objeto: expediente de contratación [COMPLETAR], nº expediente [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], con DNI n° [COMPLETAR], actuando

en su propio nombre y derecho

en representación de [NOMBRE DEL REPRESENTADO/A],

señalando como medio de notificación [COMPLETAR], según lo dispuesto en el artículo 44.6 de la Ley 9/2017, de 8 de noviembre, de Contratos del Sector Público, por la que se transponen al ordenamiento jurídico español las Directivas del Parlamento Europeo y del Consejo 2014/23/UE y 2014/24/UE, de 26 de febrero de 2014, en relación con lo dispuesto en el artículo 121 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, por medio del presente escrito interpone:

RECURSO DE ALZADA

Contra el acuerdo [ELEGIR: de la mesa de contratación / del órgano de contratación] de fecha [FECHA] por el que se [COMPLETAR]

El presente recurso se fundamenta en los siguientes

HECHOS

PRIMERO.- [COMPLETAR]

SEGUNDO.- Que el día [ELEGIR: se ha publicado / le ha sido notificada] la resolución del [COMPLETAR] de fecha [FECHA], cuya copia se adjunta, por la que se

convoca la licitación

decide la inadmisión

decide la exclusión

decide el rechazo de la oferta

decide la adjudicación

[COMPLETAR]

FUNDAMENTOS DE DERECHO

I. Procesales

Primero. Competencia. El acto recurrido [COMPLETAR] fue dictado [ELEGIR: por un poder adjudicador que no tiene la consideración de Administración Pública / por un ente del sector público que no tiene el carácter de poder adjudicador], dentro del procedimiento de adjudicación de un contrato no susceptible del recurso especial en materia de contratación regulado en el artículo 44 de la Ley 9/2017.

Según dispone el apartado 6 del mencionado artículo 44 de la Ley 9/2017:

6. Los actos que se dicten en los procedimientos de adjudicación de contratos de las Administraciones Públicas que no reúnan los requisitos del apartado 1 podrán ser objeto de recurso de conformidad con lo dispuesto en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas; así como en la Ley 29/1998, de 13 de julio, Reguladora de la Jurisdicción Contencioso-administrativa.

En el caso de actuaciones realizadas por poderes adjudicadores que no tengan la condición de Administraciones Públicas, aquellas se impugnarán en vía administrativa de conformidad con lo dispuesto en la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas ante el titular del departamento, órgano, ente u organismo al que esté adscrita la entidad contratante o al que corresponda su tutela. Si la entidad contratante estuviera vinculada a más de una Administración, será competente el órgano correspondiente de la que ostente el control o participación mayoritaria."

El [COMPLETAR] es el competente para resolver el presente recurso como [COMPLETAR] del [COMPLETAR], de acuerdo con lo establecido en [COMPLETAR].

Segundo. Recurso procedente. En cuanto a la procedencia del recurso de alzada y la competencia de ese órgano para su resolución cabe recordar que el Dictamen de la Abogacía General del Estado de 17 de enero de 2018 (ref.: A.G. Entes Públicos 2/18 (R-32/2018), tras reproducir el citado artículo 44.6 señala:

"Pues bien, el régimen de impugnación regulado en el artículo 44.6, párrafo segundo de la LCSP prevalece, en tanto norma del mismo rango legal, pero posterior en el tiempo y especial, por razón de la materia, sobre lo dispuesto con carácter general en el artículo 114.2.d) de la ley 39/2015 que, además, admite expresamente excepciones por norma con rango legal, como es el caso ("...en el ámbito estatal ponen fin a la vía administrativa los actos y resoluciones siguientes: d) En los organismos públicos y entidades de derecho público vinculados o dependientes de la Administración General del Estado, los emanados de los máximos órganos de dirección unipersonales o colegiados, de acuerdo con lo que establezcan sus estatutos, salvo que por ley se establezca otra cosa").

Tercero. Plazo. El recurso se interpone dentro del plazo de un mes previsto en el artículo 122 de la Ley 39/2015.

Cuarto. Legitimación activa. EL recurrente está legitimado para la interposición del recurso porque sus derechos o intereses legítimos [ELEGIR: se han visto perjudicados / puedan resultar afectados] toda vez que [COMPLETAR] ostentando al efecto la condición de interesado definida en los términos del artículo 4 de la Ley 39/2015.

II. Cuestiones de fondo

Quinto. En cuanto al fondo del recurso, este se dirige contra [ACTO O RESOLUCIÓN] por incumplir los preceptos [COMPLETAR].

Sexto. Medidas cautelares. El artículo 117 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común dispone que:

"1. La interposición de cualquier recurso, excepto en los casos en que una disposición establezca lo contrario, no suspenderá la ejecución del acto impugnado.
2. No obstante lo dispuesto en el apartado anterior, el órgano a quien competa resolver el recurso, previa ponderación, suficientemente razonada, entre el perjuicio que causaría al interés público o a terceros la suspensión y el ocasionado al recurrente como consecuencia de la eficacia inmediata del acto recurrido, podrá suspender, de oficio o a solicitud del recurrente, la ejecución del acto impugnado cuando concurran alguna de las siguientes circunstancias:
a) Que la ejecución pudiera causar perjuicios de imposible o difícil reparación.
b) Que la impugnación se fundamente en alguna de las causas de nulidad de pleno derecho previstas en el artículo 47.1 de esta Ley.
3. La ejecución del acto impugnado se entenderá suspendida si transcurrido un mes desde que la solicitud de suspensión haya tenido entrada en el registro electrónico de la Administración u Organismo competente para decidir sobre la misma, el órgano a quien competa resolver el recurso no ha dictado y notificado resolución expresa al respecto. En estos casos, no será de aplicación lo establecido en el artículo 21.4 segundo párrafo, de esta Ley.

Séptimo. En su caso, medios de prueba que se proponen.

Por cuanto ha quedado expuesto,

SOLICITA

Primero.- La estimación del recurso acordando la anulación del acto impugnado y la retroacción de las actuaciones al momento de [COMPLETAR]

Segundo.- La adopción de la medida cautela consistente en [DESCRIBIR]

Tercero.- Que se practique prueba consistente en [DESCRIBIR]

Firma digital:
