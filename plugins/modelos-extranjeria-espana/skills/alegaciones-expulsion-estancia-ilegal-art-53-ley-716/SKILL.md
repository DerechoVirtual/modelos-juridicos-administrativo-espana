---
name: alegaciones-expulsion-estancia-ilegal-art-53-ley-716
description: "Redacta el escrito «Alegaciones en expulsión por estancia ilegal (art. 53.a Ley de Extranjería)» (formulario 716 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones en expulsión por estancia ilegal (art. 53.a Ley de Extranjería)

> Formulario 0716 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] COLEGIO
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (3 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA
- [ ] Nº
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA JEFATURA SUPERIOR DE POLICIA DE»; «…encuentra empadronado en el municipio de»; «… cuenta corriente en la entidad bancaria»; «…4) tiene oferta de trabajo de la empresa»; «… de los hermanos de mi representado). 6)»; «…anción más grave de expulsión. TERCERA.-»; «…CUMENTAL, consistente en que se oficie a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 13 de la Constitución
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

### Formulario 0716 · Alegaciones en expulsión por estancia ilegal (art. 53.a Ley de Extranjería)

- Año del modelo: 2009
- Revisión 17-11-2026: 19 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA SUPERIOR DE POLICIA DE [COMPLETAR]

D.\D.ª [NOMBRE Y APELLIDOS], Letrado del Colegio de Abogados de [COLEGIO], colegiado número [Nº DE COLEGIADO/A], con domicilio a efectos de notificaciones sito en [LOCALIDAD] pudiendo ser notificado vía lexnet o en el correo electrónico [CORREO ELECTRÓNICO], y con teléfono [TELÉFONO], en representación de D. [NOMBRE Y APELLIDOS], la cual me ha sido conferida por turno de oficio, en el procedimiento nº [Nº DE PROCEDIMIENTO]/[AÑO], que se sigue por infracción del art. de la Ley de Extranjería, comparece y como mejor proceda, DICE:

Que habiendo sido notificado en fecha [FECHA] del acuerdo de iniciación del procedimiento sancionador preferente de la misma fecha contra mi representado, para la expulsión del territorio nacional, dentro del plazo concedido, formulo las siguientes

ALEGACIONES

PRIMERA.- La notificación del expediente sancionador con propuesta de expulsión parte del presupuesto de que mi representado se encuentra irregularmente en España, lo cual, sin perjuicio de que pueda ser tipificado como infracción grave, no determina que deba imponerse la sanción de expulsión, por cuanto concurren circunstancias personales y de arraigo que hacen improcedente la expulsión.

En efecto, mi representado reside en España desde hace [Nº] años, no tiene antecedentes policiales según consta en el expediente y tiene un arraigo familiar, económico y social que se funda en las siguientes circunstancias:

1) tiene domicilio conocido y se encuentra empadronado en el municipio de [COMPLETAR], tal como se justifica por el certificado de empadronamiento que se acompaña como documento número 1.

2) es titular de una tarjeta sanitaria, según se acredita por el certificado que se acompaña como documento número 2.

3) tiene medios económicos, siendo titular de la cuenta corriente en la entidad bancaria [COMPLETAR] con un saldo de [IMPORTE] euros, lo que pone de manifiesto que dispone de medios suficientes para hacer frente, en su caso, a una sanción pecuniaria ( se acompañan como documentos números 3 y 4 contrato bancario y extracto).

4) tiene oferta de trabajo de la empresa [COMPLETAR], habiendo solicitado autorización de residencia y trabajo (se acompañan como documentos número 5 y 6 oferta de trabajo e solicitud presentada ante la Subdelegación del Gobierno de [LOCALIDAD])

5) tiene arraigo familiar pues convive con sus hermanos, los cuales se encuentran en situación de residencia legal en España (se acompañan como documentos 7 a 9 permisos de residencia y trabajo de los hermanos de mi representado).

6) [COMPLETAR]

De todos estos hechos, que acreditaremos en el expediente con la prueba aportada y con la que proponemos mediante otrosí en este escrito, resulta que concurren en mi representado circunstancias personales y de arraigo que hacen totalmente improcedente la imposición de una sanción de expulsión.

SEGUNDA.- En cualquier caso, también es improcedente la medida de expulsión por cuanto, por razones de proporcionalidad, sólo procedería en su caso imponer la sanción de multa por la estancia irregular.

Así, el art. 13 de la Constitución establece que los extranjeros gozan en España de las libertades que garantiza el Título I, habiendo interpretado tanto el Tribunal Constitucional como el Tribunal Supremo.

La Ley Orgánica 4/2000, de 11 de Enero, prescribe en su art. 55.3 unos criterios de graduación de la sanción, a cuyo tenor "para la graduación de las sanciones, el órgano competente en imponerlas se ajustará a criterios de proporcionalidad, valorando el grado de culpabilidad, y, en su caso, el daño producido o el riesgo derivado de la infracción y su trascendencia".

Estos criterios han sido aplicados por el Tribunal Supremo, entre otras, en sentencias de 14 y 22 de diciembre de 2005, el cual indica que "en el sistema de la Ley la sanción principal es la de multa, pues así se deduce de su artículo 55-1 y de la propia literalidad de su artículo 57.1, a cuyo tenor, y en los casos, (entre otros) de permanencia ilegal, "podrá aplicarse en lugar de la sanción de multa la expulsión del territorio nacional", de manera que " la sanción más grave y secundaria, la expulsión, requiere una motivación específica, y distinta o complementaria de la pura permanencia ilegal, ya que ésta es castigada simplemente con multa. Según lo que dispone el artículo 55.3, la Administración ha de especificar, si impone la expulsión, cuáles son las razones de proporcionalidad, de grado de subjetividad, de daño o riesgo derivado de la infracción y, en general, añadimos nosotros, cuáles son las circunstancias jurídicas o fácticas que concurren para la expulsión y prohibición de entrada, que es una sanción más grave que la de multa".

En este expediente, mi representado acredita las circunstancias de arraigo expuesta anteriormente, además que no consta en el expediente dato negativo alguno sobre su conducta durante su estancia en España, por lo que resulta improcedente imponer la sanción más grave de expulsión.

TERCERA.- [COMPLETAR]

En virtud de lo expuesto,

SOLICITO:

Que teniendo por presentado este escrito se digne admitirlo a trámite y se tengan por formuladas alegaciones (en su caso, con los documentos que con el escrito se acompañan; o, en su caso, recibiendo el procedimiento a prueba según expreso en el otrosí) y, previos los trámites legales, acuerde dictar en su día resolución de archivo del expediente o bien, subsidiariamente, imponer la sanción de multa en su cuantía mínima.

OTROSÍ PRIMERO DIGO: Que esta parte interesa proponer los siguientes medios de prueba en el procedimiento:

1) DOCUMENTAL, consistente en que se admitan los documentos acompañados a este escrito.

2) MÁS DOCUMENTAL, consistente en que se oficie a [COMPLETAR] para que emita certificado sobre [DESCRIBIR]

3) TESTIFICAL, a fin de que se cite a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], el cual podrá declarar sobre las circunstancias de arraigo de mi representado, concretamente que

Por lo que, SOLICITO que se tengan por propuestos estos medios probatorios, acordándose su admisión y lo conducente a su práctica.

Lugar, fecha y firma
