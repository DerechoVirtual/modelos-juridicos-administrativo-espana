---
name: alegaciones-defensa-expulsion-preferente-infraccion-ley-715
description: "Redacta el escrito «Alegaciones de defensa en expulsión preferente por infracción de la Ley de Extranjería» (formulario 715 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones de defensa en expulsión preferente por infracción de la Ley de Extranjería

> Formulario 0715 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Sancionador de extranjería: la numeración del RD 1155/2024 se desplaza un número respecto del RD 557/2011 (219→218, 231→230 … 242→241). Novedades: riesgo de incomparecencia concretado (art. 233), procedimiento simplificado (237-239), cumplimiento voluntario de 7 a 30 días (245.2).
- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] COLEGIO
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA
- [ ] DESCRIBIR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA JEFATURA SUPERIOR DE POLICIA DE»; «…procedimiento por este motivo. TERCERA.-»; «…CUMENTAL, consistente en que se oficie a»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 1155/2024
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

### Formulario 0715 · Alegaciones de defensa en expulsión preferente por infracción de la Ley de Extranjería

- Año del modelo: 2009
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 12 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Sancionador de extranjería: la numeración del RD 1155/2024 se desplaza un número respecto del RD 557/2011 (219→218, 231→230 … 242→241). Novedades: riesgo de incomparecencia concretado (art. 233), procedimiento simplificado (237-239), cumplimiento voluntario de 7 a 30 días (245.2). · Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA JEFATURA SUPERIOR DE POLICIA DE [COMPLETAR]

D./D.ª [NOMBRE Y APELLIDOS], Letrado del Colegio de Abogados de [COLEGIO], colegiado número [Nº DE COLEGIADO/A], con domicilio a efectos de notificaciones sito en [LOCALIDAD] pudiendo ser notificado vía lexnet o en el correo electrónico [CORREO ELECTRÓNICO], y con teléfono [TELÉFONO], en representación de D. [NOMBRE Y APELLIDOS], la cual me ha sido conferida por turno de oficio, en el procedimiento nº [Nº DE PROCEDIMIENTO]/[AÑO], que se sigue por infracción del art. de la Ley de Extranjería, comparece y como mejor proceda, DICE:

Que habiendo sido notificado en fecha [FECHA] del acuerdo de iniciación del procedimiento sancionador preferente de la misma fecha contra mi representado, para la expulsión del territorio nacional, dentro del plazo concedido, formulo las siguientes

ALEGACIONES

PRIMERA.- La utilización de la vía del procedimiento preferente del art. 233 del Reglamento de Extranjería aprobado por el Real Decreto 1155/2024, de 19 de noviembre [NOTA DE REVISIÓN: Los supuestos del procedimiento preferente están en el art. 233 RD 1155/2024 (antes art. 234 RD 557/2011). El texto es igual, pero ahora el «riesgo de incomparecencia» se concreta: falta de domicilio o de documentación, no constar entrada legal en Schengen o haber incumplido una salida obligatoria. Fuente: RD 1155/2024, art. 233 (BOE-A-2024-24099); RD 557/2011, art. 234 (BOE-A-2011-7703).], con la sustancial reducción de plazos, limitaciones del derecho de defensa e inmediata ejecutividad de la sanción, sólo se justifica por el hecho de que la infracción imputada sea una de las expresamente contempladas en el citado precepto.

En el caso, la resolución de incoación del procedimiento no indica cuál puede ser la infracción cometida por mi representado, refiriéndose genéricamente a que carecía de documentación, lo cual deja a esta parte en una situación de absoluta indefensión, puesto que desconoce la infracción que se le imputa e, incluso, en el negado supuesto de haberse cometido, no será ninguna de las que el art. 234 del Reglamento contempla como habilitantes de la incoación del procedimiento sumario.

Por tanto, procede dictar resolución archivando el expediente por no ser procedente el procedimiento preferente.

SEGUNDA.- El art. 233 del Reglamento de Extranjería contempla, de forma tasada, los supuestos en que procede el procedimiento preferente que son concretamente los de imputación de infracciones prevista en los párrafos a) y b) del art. 54.1 de la Ley, así como los párrafos a), d) y f) del artículo 53 [NOTA DE REVISIÓN: Precisar. El preferente procede por las letras d) y f) del art. 53.1. La letra a) solo procede si hay riesgo de incomparecencia, obstrucción de la expulsión o riesgo para el orden público o la seguridad (art. 63.1 LO y art. 233 RD 1155/2024). El 53.1.h) (no pedir la TIE, art. 4.2 LO) no figura entre esos supuestos, lo que refuerza el argumento. Fuente: LO 4/2000, arts. 4.2, 53.1 y 63.1 (BOE-A-2000-544); RD 1155/2024, art. 233 (BOE-A-2024-24099).] y en el artículo 57.2 de la Ley de Extranjería aprobada por la Ley Orgánica 4/2000, de 11 de enero.

En el caso de mi representado, la infracción imputada sólo podría tener encaje en el apartado h) del art. 53 de la Ley, por cuanto, según la imputación que se le realiza, no cumplió la obligación de solicitar la tarjeta de identidad de extranjeros en el plazo de un mes en los términos contemplados en el art. 4.2 de la Ley de Extranjería.

Por ello la incoación del procedimiento preferente debe ser declarada improcedente, por cuanto afecta al derecho de defensa de mi representado, en tanto que la reducción de plazos, su carácter sumario y la inmediata ejecutividad de la sanción sólo se justifica por el encaje de la conducta en las infracciones expresamente contempladas en el art. 233 del Reglamento de Extranjería, lo cual no se produce en este caso, por cuanto la infracción imputada queda extramuros del citado precepto.

En consecuencia, también deberá acordarse el archivo del procedimiento por este motivo.

TERCERA.- [COMPLETAR].

En virtud de lo expuesto,

SOLICITO:

Que teniendo por presentado este escrito se digne admitirlo a trámite y se tengan por formuladas alegaciones (en su caso, con los documentos que con el escrito se acompañan; o, en su caso, recibiendo el procedimiento a prueba según expreso en el otrosí) y, previos los trámites legales, acuerde dictar en su día resolución de archivo del expediente.

OTROSÍ PRIMERO DIGO: Que esta parte interesa proponer los siguientes medios de prueba en el procedimiento:

1) DOCUMENTAL, consistente en que se admitan los documentos acompañados a este escrito.

2) MÁS DOCUMENTAL, consistente en que se oficie a [COMPLETAR]. para que emita certificado sobre [DESCRIBIR].

3) TESTIFICAL, a fin de que se cite a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]., el cual podrá declarar sobre las circunstancias de arraigo de mi representado, concretamente que

Por lo que, SOLICITO que se tengan por propuestos estos medios probatorios, acordándose su admisión y lo conducente a su práctica.

lugar, fecha y firma
