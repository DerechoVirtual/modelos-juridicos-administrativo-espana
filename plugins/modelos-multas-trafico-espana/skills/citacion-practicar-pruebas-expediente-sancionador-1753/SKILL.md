---
name: citacion-practicar-pruebas-expediente-sancionador-1753
description: "Redacta el escrito «Citación para practicar las pruebas del expediente sancionador» (formulario 1753 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Citación para practicar las pruebas del expediente sancionador

> Formulario 1753 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] FECHA (7 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº (6 veces)
- [ ] DESCRIBIR
- [ ] IMPORTE (2 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, referencia»; «…, en el que se»; «…, a fin de acreditar que»; «…nal correspondiente, en el que se afirma»; «…ructor del expediente para comprobar que»; «… supuesta infracción, será realizado por»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 13 del Real Decreto 320/1994
- art. 13.1 RD 320/1994

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

### Formulario 1753 · Citación para practicar las pruebas del expediente sancionador

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (2); 27 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de citación por el que se admiten las pruebas solicitadas por el inculpado en el expediente sancionador de tráfico, y se acuerda la apertura del periodo de prueba, emplazando al inculpado y demás interesados a la práctica de cada uno de los medios propuestos.

En su escrito de alegaciones de fecha [FECHA], referencia [COMPLETAR], expediente número [Nº DE PROCEDIMIENTO]/[AÑO], se propone, para acreditar sus manifestaciones de descargo, la admisión y práctica de los siguientes medios de prueba:

1. Documental, consistente en escrito de fecha [FECHA], expedido por [ÓRGANO O PERSONA], en el que se [COMPLETAR], circunstancia relevante para este procedimiento sancionador.
2. Testifical, consistente en que se tome declaración a D./Dña. [NOMBRE Y APELLIDOS], a fin de acreditar que [COMPLETAR], en razón del conocimiento directo de los hechos por haber sido testigos presenciales de los mismos.
3. Pericial, consistente en dictamen de fecha [FECHA] suscrito por [ÓRGANO O PERSONA], con el visado del colegio profesional correspondiente, en el que se afirma [COMPLETAR], dato de interés para la adecuada valoración de la conducta objeto de expediente sancionador.
4. Reconocimiento sobre el terreno, por parte del Instructor del expediente para comprobar que [COMPLETAR] y las demás circunstancias relevantes.

De conformidad con las previsiones del artículo 13 del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial, procede adoptar el siguiente

ACUERDO:

Primero.- Se admiten las pruebas propuestas por el inculpado en el expediente sancionador referenciado para la averiguación y calificación de los hechos, así como para la determinación de las posibles responsabilidades.

Segundo.- Se acuerda la apertura de un periodo de prueba por un plazo de [Nº] días (no superior a 30 días ni inferior a 10 días) para que puedan practicarse de forma adecuada en los siguientes términos:

A) La prueba testifical se practicará el día [FECHA] a las [Nº] horas, en las dependencias de este órgano, para lo que, en el plazo de [Nº] días deberá aportar el interrogatorio de preguntas que por parte del inculpado pretende que sean formuladas a los testigos presentados.
B) La prueba pericial, propuesta, consistente en [DESCRIBIR], y en la toma de muestras y análisis de las sustancias mencionadas en el escrito de alegaciones, se realizará el día [FECHA] a las [Nº] horas en el lugar propuesto.

La prueba pericial indicada comporta gastos, en la cuantía de [IMPORTE] euros, que no debe soportar esta Administración, por lo que procedemos a exigir anticipadamente el importe de dicha cantidad, a reserva de la liquidación definitiva, una vez practicada la prueba. Este requerimiento de anticipo de gastos se hará efectivo en el plazo de [Nº] días, mediante el ingreso de [IMPORTE] euros en la cuenta número [NÚMERO], a disposición de este centro directivo, entendiendo que renuncia a dicha prueba si en el plazo indicado no adelanta el importe de los gastos correspondientes cuya cuantía se justifica documentalmente en el informe que se adjunta a este escrito. (1)

C) El reconocimiento sobre el terreno en que se cometió la supuesta infracción, será realizado por [COMPLETAR], el próximo día [FECHA], a las [Nº] horas, acto de reconocimiento para el que quedan convocados, y podrán los interesados acudir acompañados, si así lo desean, de técnicos para que los asistan.

Pongo en su conocimiento que una vez finalizado este periodo probatorio se dictará la propuesta de resolución para continuar el expediente sancionador en sus demás trámites reglamentarios. (2)

En [LUGAR], a [FECHA].

Firma del instructor:

NOTAS DEL FORMULARIO

(1) La exigencia de anticipo de gastos no es una diligencia sencilla, sino de difícil instrumentación, ya que los órganos administrativos sancionadores carecen, como es lógico, de una Tesorería propia, por lo que el ingreso debe efectuarse en la tesorería general de la Administración Pública actuante y, a partir de ahí, se genera un proceso de transferencias de crédito a los programas de gasto del órgano sancionador a efectos de acometer los pagos que comporta la práctica de las pruebas propuestas. Estos pagos que genera la prueba deben atenderse, como no puede ser otra manera, con sujeción a las normas reguladoras del gasto público y la contratación administrativa, con objeto de garantizar la corrección (en términos de legalidad y eficacia) del gasto realizado y que, en definitiva, corre a cargo de los interesados. Por todo ello, no es frecuente la implementación de este proceso para los expedientes sancionadores de tráfico, no sólo por su escasa cuantía sino, además, teniendo en cuenta la dilación que comporta seguir cada uno de los trámites para llegar a practicar las pruebas con gastos que la Administración no debe soportar (Antonio Martínez Nieto, "El Procedimiento Sancionador de Tráfico", II Curso de Gestión Administrativa de Sanciones de Tráfico 1999/2000, Fundación Universidad Empresa, Murcia, 2000, pág. 119).

(2) La práctica de las pruebas no es frecuente en materia de tráfico, siendo uno de los motivos de mayor frustración por parte de las personas que de buena fe proponen pruebas en este tipo de expedientes sancionadores. Con carácter general hay que decir que los Ayuntamientos son más receptivos a la admisión y práctica de las pruebas, mientras que estas diligencias son muy raras en el ámbito de los órganos estatales responsables de la tramitación de este tipo de expedientes. En cualquier caso, es muy importante tener en cuenta que la Administración siempre debe pronunciarse de forma expresa sobre las pruebas propuestas, para admitirlas o para denegarlas, sin que sea correcto no pronunciarse al respecto: "El instructor del procedimiento sólo podrá rechazar mediante resolución motivada las pruebas propuestas por los interesados cuando sean improcedentes" (art. 13.1 RD 320/1994).
