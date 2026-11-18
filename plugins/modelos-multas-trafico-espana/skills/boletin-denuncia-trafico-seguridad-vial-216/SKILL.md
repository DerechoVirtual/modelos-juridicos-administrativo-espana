---
name: boletin-denuncia-trafico-seguridad-vial-216
description: "Redacta el escrito «Boletín de denuncia de tráfico y seguridad vial» (formulario 216 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Boletín de denuncia de tráfico y seguridad vial

> Formulario 0216 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] MATRÍCULA
- [ ] MARCA/MODELO (2 veces)
- [ ] PROFESIÓN
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] DNI/NIE
- [ ] FECHA
- [ ] HORA
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Clase»; «…Modelo [MARCA/MODELO] Color»; «…Color [COMPLETAR] Tara»; «…Color [COMPLETAR] Tara [COMPLETAR] PMA»; «…entidad del conductor denunciado. Nombre»; «…Calle o Plaza Número [NÚMERO] piso»; «…piso [COMPLETAR] Localidad»; «…Provincia [PROVINCIA] C. Postal»; «…Clase»; «…Clase [COMPLETAR] Fecha de nacimiento»; «…n del lugar o tramo, fecha y hora. Lugar»; «… antena, cuyo prototipo fue aprobado por»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 80 del Real Decreto Legislativo 6/2015

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

### Formulario 0216 · Boletín de denuncia de tráfico y seguridad vial

- Año del modelo: 2016
- Revisión 17-11-2026: 5 llamadas a nota sin texto retiradas; 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

I. Denuncia por hecho de la circulación:

A) Identificación del vehículo con el que se ha cometido la supuesta infracción:

Matrícula [MATRÍCULA] Clase [COMPLETAR] Marca [MARCA/MODELO]

Modelo [MARCA/MODELO] Color [COMPLETAR] Tara [COMPLETAR] PMA [COMPLETAR]

B) Identidad del conductor denunciado.

Nombre [COMPLETAR] Apellidos Profesión [PROFESIÓN]

Calle o Plaza Número [NÚMERO] piso [COMPLETAR]

Localidad [COMPLETAR] Provincia [PROVINCIA] C. Postal [COMPLETAR]

Permiso de conducir o DNI [DNI/NIE]

Clase [COMPLETAR]

Fecha de nacimiento [COMPLETAR]

C) Descripción sucinta del hecho, con expresión del lugar o tramo, fecha y hora.

Lugar [COMPLETAR] Fecha [FECHA] Hora [HORA]

Descripción del hecho:

Circular akm/h, estando limitada la velocidad akm/h, existiendo una limitación: Genérica en vía interurbana/Genérica en vía urbana o travesía/Específica fijada por señal. Velocidad medida por el cinemómetro, antena, cuyo prototipo fue aprobado por [COMPLETAR] con fecha

Para la graduación de la sanción se han tenido en cuenta los márgenes de error admitidos reglamentariamente.

D) Identificación del denunciante.

Denunciante notificador/Nº Identificación/Unidad [COMPLETAR]

Testigo/Nº Identificación/Unidad [COMPLETAR]

Nombre, domicilio y profesión del denunciante particular:

II. Denuncia notificada en el acto al denunciado por Agente de la Autoridad:

A) Infracción presuntamente cometida, sanción que pudiera corresponder y número de puntos cuya pérdida lleve aparejada la infracción, conforme a lo dispuesto en la Ley.
B) Órgano competente para imponer la sanción y la norma que le atribuye tal competencia.
C) Cantidad abonada y las consecuencias derivadas del pago de la sanción previstas en el artículo 80 si el denunciado procede al abono de la sanción en el acto,
D) Indicación, en caso de impago, de que la denuncia inicia el procedimiento sancionador y que dispone de un plazo de veinte días naturales para efectuar el pago, con la reducción y las consecuencias establecidas en el artículo 80 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial (en lo sucesivo, TR LTCVMSV), o para formular las alegaciones y proponer las pruebas que estime convenientes.
E) Domicilio que, en su caso, indique el interesado a efectos de notificaciones. Este domicilio no se tendrá en cuenta si el denunciado tuviese asignada una Dirección Electrónica Vial, ello sin perjuicio de lo previsto en la normativa sobre acceso electrónico de los ciudadanos a los servicios públicos.
F) Advertencias legales y diligencia de notificación personal.

Lo que se notifica en este acto al denunciado indicándole que con esta denuncia queda iniciado el expediente y, en consecuencia, dispone de un plazo de veinte días naturales para efectuar el pago, con la reducción y las consecuencias establecidas en la ley o para formular las alegaciones y proponer o aportar las pruebas que estime oportunas.

EL AGENTE DENUNCIANTE,

EL DENUNCIADO,
