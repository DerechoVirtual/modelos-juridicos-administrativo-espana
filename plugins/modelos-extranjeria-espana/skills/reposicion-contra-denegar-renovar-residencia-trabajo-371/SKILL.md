---
name: reposicion-contra-denegar-renovar-residencia-trabajo-371
description: "Redacta el escrito «Reposición contra denegar renovar residencia y trabajo por cuenta propia» (formulario 371 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra denegar renovar residencia y trabajo por cuenta propia

> Formulario 0371 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (9 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR (2 veces)
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, el Subdelegado del Gobierno de»; «…HECHOS 1.º—La recurrente es esposa de D.»; «…enta propia, administrador de la empresa»; «…, con CIF B»; «…, el Subdelegado del Gobierno de»; «… la Declaración anual del IRPF ejercicio»; «…oralmente, durante algunos meses del año»; «…, notificada el»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO: Que, a la vista del contenido de lo alegado y en tanto se resuelva el recurso, solicita expresame…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 86 del RD 1155/2024
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

### Formulario 0371 · Reposición contra denegar renovar residencia y trabajo por cuenta propia

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 párrafos opcionales señalados; 26 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A la Subdelegación del Gobierno de [LOCALIDAD]

Dña. [NOMBRE Y APELLIDOS], mayor de edad, casada, de nacionalidad marroquí, con NIE X-, con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], calle [CALLE], n.º [NÚMERO], ante esa Oficina Única de Extranjeros de la Delegación del Gobierno comparece y, del modo más procedente, DICE:

1.º—Que con fecha [FECHA] la compareciente solicitó la renovación de la autorización administrativa de residencia y trabajo por cuenta propia de la que era titular.

2.º—Que por resolución de fecha [FECHA], notificada el día [FECHA], el Subdelegado del Gobierno de [COMPLETAR] resuelve denegar la renovación de la autorización de residencia y trabajo por cuenta propia solicitada. Advirtiendo a la interesada la obligación de abandonar el territorio español en el plazo de quince días, a no ser que se encuentre en alguno de los supuestos previstos en el Real Decreto 1155/2024 que dan derecho a la obtención de una autorización de residencia.

Que siendo la citada resolución contraria a los intereses del compareciente y resultando al criterio de esta parte no ajustada a derecho. Dentro de plazo hábil interpongo recurso de reposición ante esa Subdelegación del Gobierno en base a los hechos y fundamentos que de forma sucinta paso a exponer:

HECHOS

1.º—La recurrente es esposa de D. [COMPLETAR], residente con autorización de residencia y trabajo por cuenta propia, administrador de la empresa [COMPLETAR], con CIF B [COMPLETAR] y domicilio social en [LOCALIDAD], calle [CALLE], n.º [NÚMERO] constituida en fecha [FECHA].

2.º—Que por resolución de fecha [FECHA], notificada el día [FECHA], el Subdelegado del Gobierno de [COMPLETAR] resuelve denegar la renovación de la autorización de residencia y trabajo por cuenta propia solicitada. Advirtiendo a la interesada la obligación de abandonar el territorio español en el plazo de quince días, a no ser que se encuentre en alguno de los supuestos previstos en el Real Decreto 1155/2024 que dan derecho a la obtención de una autorización de residencia.

3.º—Asimismo se encuentra al corriente en el plago de sus obligaciones tributarias, tal y como se comprueba con los documentos que se acompañan: Certificado de la Declaración anual del IRPF ejercicio [COMPLETAR] (Doc. núm. [Nº DE DOCUMENTO]).

4.º—Actualmente se encuentra de alta en la actividad y en el régimen de autónomos. Únicamente permaneció de baja, temporalmente, durante algunos meses del año [COMPLETAR], a consecuencia de haberse sometido a pruebas médicas.

5.º—El artículo 86 del RD 1155/2024 [NOTA DE REVISIÓN (comprobar): El art. 86 regula la renovación de la autorización por cuenta propia. Si se trata de un trabajador por cuenta ajena (como sugiere la «baja temporal»), la cita es el art. 80.2 («La autorización de residencia y trabajo por cuenta ajena se renovará a su expiración...»). Ajustar también el texto entrecomillado. Fuente: RD 1155/2024, arts. 80.2 y 86.2 (BOE-A-2024-24099).] señala que «La autorización de residencia y trabajo por cuenta propia podrá ser renovada en los siguientes supuestos: a) Cuando se acredite la continuidad en la actividad que dio lugar a la autorización que se renueva, previa comprobación de oficio del cumplimiento de sus obligaciones tributarias y de Seguridad Social».

En el presente caso, la compareciente continúa en la actividad objeto de renovación, de alta en el régimen de autónomos y acredita el cumplimiento de sus obligaciones tributarias.

La buena marcha de la empresa que ha ampliado su actividad en el último año a dos nuevos establecimientos dedicados a la prestación de servicios telefónicos para uso público y servicios de Internet aseguran la actividad de la compareciente como colaboradora en la empresa

6.º—En cualesquiera de los casos y para el supuesto de que no fuera atendido el presente recurso, por medio del presente escrito y dentro del plazo de quince días hábiles conferido por la resolución, se acompaña impreso de solicitud de autorización de residencia que permita la permanencia en España de la recurrente.

Por lo expuesto,

SOLICITA DE ESA SUBDELEGACIÓN DEL GOBIERNO, que tenga por presentado este escrito, junto con los documentos que se acompañan y por interpuesto Recurso de Reposición frente a la resolución del Subdelegado del Gobierno de fecha [FECHA], notificada el [COMPLETAR], y a la vista de lo manifestado, y previos los trámites correspondientes acuerde:

A) Revocar la resolución impugnada dictando en su lugar una nueva por la que se acceda a la solicitud en su día instada relativa a la renovación de la autorización de trabajo y residencia para la realización de actividades por cuenta propia a favor de la compareciente Dña. [NOMBRE Y APELLIDOS].

B) Subsidiariamente, y para el caso de no ver atendido el recurso, se deberá acordar autorizar la permanencia en España de la compareciente en situación de residencia temporal.

En [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que, a la vista del contenido de lo alegado y en tanto se resuelva el recurso, solicita expresamente la suspensión de la obligación de salida del territorio nacional y el mantenimiento de los efectos de la autorización objeto de renovación, posibilitando de esta manera la continuidad en la actividad y régimen de autónomos.

En [LUGAR], a [FECHA].
