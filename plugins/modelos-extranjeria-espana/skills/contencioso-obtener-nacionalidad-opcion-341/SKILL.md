---
name: contencioso-obtener-nacionalidad-opcion-341
description: "Redacta el escrito «Contencioso para obtener la nacionalidad por opción» (formulario 341 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contencioso para obtener la nacionalidad por opción

> Formulario 0341 del plugin **Extranjería** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (4 veces)
- [ ] FECHA DE LA DILIGENCIA
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… nacionalidad española por residencia el»; «…olicitud de inscripción de nacimiento de»; «…de inscripción de su matrimonio, su hija»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 7.3 de la LJCA
- art. 19.1.a) de la LJCA
- art. 139.1 de la LJCA

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

### Formulario 0341 · Contencioso para obtener la nacionalidad por opción

- Año del modelo: 2013
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA DE LA DILIGENCIA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

RECURSO CONTENCIOSO-ADMINISTRATIVO: NACIONALIDAD POR OPCIÓN

Procedimiento Ordinario /20

A LA AUDIENCIA NACIONAL SALA DE LO CONTENCIOSO-ADMINISTRATIVO SECCIÓN TERCERA

D./Dña. [NOMBRE Y APELLIDOS], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en el procedimiento referenciado, ante la Sala comparezco y como mejor proceda en Derecho DIGO:

Que el día [FECHA] me ha sido notificada diligencia de ordenación de fecha [FECHA DE LA DILIGENCIA] por la que se otorga el plazo de veinte días para formular demanda, por lo que, dentro del plazo conferido formalizo la DEMANDA basándome en los siguientes

HECHOS

D./Dña. [NOMBRE Y APELLIDOS] solicitó concesión de nacionalidad española por residencia el [COMPLETAR], la cual le fue denegada por resolución de fecha [FECHA].

Contra dicha resolución se interpuso recurso de apelación, el cual fue desestimado por resolución de fecha [FECHA], contra la que se interpuso recurso contencioso-administrativo.

La solicitud fue denegada por dos motivos:

a) Se alega en la resolución recurrida que ya se había denegado una previa solicitud de inscripción para la interesada.

b) La existencia de dudas sobre la realidad del hecho inscrito, dado que la madre de la interesada no había mencionado en su solicitud de nacionalidad española, ni en su solicitud de inscripción de matrimonio la existencia de esta hija.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

La competencia para conocer del recurso corresponde a la sala de lo Contencioso-Administrativo de la Audiencia Nacional según lo dispuesto en el art. 11 de la LJC-A.

No obstante, para el supuesto que no se entendiera así, procederá que se remitan las actuaciones al órgano jurisdiccional competente, en aplicación de lo dispuesto en el art. 7.3 de la LJCA.

Legitimación

Está legitimado mi representado en virtud de lo establecido en el art. 19.1.a) de la LJCA, por tener interés legítimo y directo en la anulación del acto objeto de impugnación.

En el presente caso, al ser el hijo del recurrente menor de 14 años la solicitud de inscripción de nacionalidad española por opción la debía instar el representante legal del menor.

Plazo de formulación de la demanda

Se ha respetado lo establecido en la LJCA respecto al plazo para formular demanda.

Costas

En lo relativo a la imposición de costas, es de aplicación el art. 139.1 de la LJCA. Caso de oponerse al presente recurso, debe estimarse que la Administración actúa con mala fe o temeridad, por lo que deberán imponerse las costas del presente proceso a la Administración demandada.

En cuanto al fondo del asunto, esta parte discrepa de los motivos alegados para denegar lo solicitado.

En primer lugar, por existir un error de hecho, pues en contra de lo que se alega en la resolución recurrida, no ha existido una previa solicitud de inscripción de nacimiento de [COMPLETAR], desconociéndose el porqué se realiza dicha afirmación.

Y por otra parte, porque considera que la resolución no está suficientemente motivada, pues infiere que el hecho de que la madre de la interesada no mencionara a esta hija en su solicitud de nacionalidad o en su inscripción de matrimonio es suficiente como para desvirtuar la presunción de veracidad de los hechos alegados, y de los documentos aportados en el procedimiento (certificados de nacimiento debidamente legalizados).

El motivo de dicha omisión fue, sencillamente, que tanto en el momento de la solicitud de nacionalidad de la madre, como en el de la solicitud de inscripción de su matrimonio, su hija [COMPLETAR] no se encontraba en España, por lo que erróneamente pensó que no debía mencionarla en ninguno de los formularios presentados al efecto en estos procedimientos.

Si esta circunstancia genera algún tipo de duda en la instrucción del expediente, lo procedente hubiera sido requerir a la madre de la interesada para que aclarara el motivo de dicha omisión, o para que aportara documentación adicional en apoyo de lo expuesto en la solicitud.

Pero al denegar de plano la relación filial se genera una situación de indefensión de la interesada, a la que no se le otorga la posibilidad de alegar lo que considere conveniente o de aportar lo que pueda apoyar sus alegaciones y, lo que es peor, se impide subsanar el error cometido, imposibilitando definitivamente que la menor pueda acogerse a su derecho de opción por la nacionalidad española.

Además, no podemos olvidar que en la solicitud se presentó un documento debidamente legalizado por las autoridades españolas que en ningún momento han cuestionado su autenticidad durante dicho trámite de legalización, por lo que debería presumirse su autenticidad salvo que la Administración aportara prueba en contrario, cosa que no ha hecho, pues se ha limitado a impugnar la autenticidad de dicho documento en base a una mera sospecha por un acto que, aunque erróneo, no puede considerarse suficiente para sustentar dicha sospecha.

Debemos recordar, además, que la hija del recurrente es residente legal en España, siendo titular de una autorización de residencia en España en régimen comunitario, la cual le fue concedida en base al parentesco con el recurrente.

Existe, pues una flagrante contradicción en el hecho de que para la misma Administración española la relación filial de la interesada se considere suficientemente acreditada suficiente para otorgarle la residencia legal en España pero no para solicitar la opción a la nacionalidad española.

Por tanto, al cuestionar la misma documentación que ha servido para otorgar una autorización de residencia, la Administración estaría yendo contra sus propios actos.

Prueba

No existiendo disconformidad en los hechos y tratándose de una mera controversia jurídica, no procede solicitar recibimiento a prueba.

En su virtud SUPLICO A LA SALA que tenga por formalizada la demanda en el procedimiento referenciado y previos los trámites procesales oportunos dicte sentencia por la que anule la resolución recurrida y se declare el derecho a la autorización de la inscripción de nacimiento y opción por la nacionalidad española de

Por ser Justicia que pido en [LUGAR], a [FECHA].

OTROSI DIGO que se estima que la cuantía del recurso es indeterminada, al constituir el objeto del mismo la impugnación de un acto administrativo que no tiene cuantía.

En su virtud SUPLICO A LA SALA que se fije la cuantía del recurso en indeterminada.

Por ser Justicia que reitero en lugar y fecha ut supra.

D./Dña. [NOMBRE Y APELLIDOS]

Procurador/a

D./Dña. [NOMBRE Y APELLIDOS]
