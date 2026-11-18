---
name: alegaciones-descargos-sancionador-trafico-704
description: "Redacta el escrito «Alegaciones o descargos en sancionador de tráfico» (formulario 704 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones o descargos en sancionador de tráfico

> Formulario 0704 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] FECHA (3 veces)
- [ ] CALLE (2 veces)
- [ ] Nº
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Expediente»; «…opio (o en representación de según poder»; «…, expediente»; «…, expediente [COMPLETAR], referencia»; «…olución dejando sin efecto el expediente»; «…(Referencia)»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 139 del Reglamento General de Circulación
- art. 12.1 del Real Decreto Legislativo 6/2015

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

### Formulario 0704 · Alegaciones o descargos en sancionador de tráfico

- Año del modelo: 2010
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente [COMPLETAR]

AYUNTAMIENTO DE [LOCALIDAD]

D.\D.ª [NOMBRE Y APELLIDOS], mayor de edad, provisto del D.N.I., con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES] (además, en su caso, teléfono, fax y/o correo electrónico), en nombre propio (o en representación de según poder [COMPLETAR]) EXPONE:

Que he sido notificado de la denuncia de fecha [FECHA], expediente [COMPLETAR], referencia [COMPLETAR], concediéndome el plazo de veinte días naturales para presentar escrito de alegaciones y es por lo que, de conformidad con lo prevenido en los arts. 87 y 95 de la Ley sobre Tráfico (Real Decreto Legislativo 6/2015, de 30 de octubre), formulo [NOTA DE REVISIÓN: El art. 12 RD 320/1994 (15 días) está desplazado por el art. 95 TR LSV (20 días naturales). Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 arts. 87 y 95.] en mi defensa las siguientes:

ALEGACIONES

PRIMERA.- La denuncia se formula el día [FECHA] por estacionar en espacio prohibido en la calle [CALLE] a las [Nº] horas.

Efectivamente, reconozco que mi vehículo lo dejé estacionado en la citada calle el día anterior por la noche, pero no había ninguna señalización o, si había alguna señal, no estaba visible.

He de significar que al recoger el vehículo me percato que hay una señal acostada en el suelo, lo cual indica claramente que si la situación era la misma el día 24 por la noche, era imposible ver la señal.

Por tanto, alego en primer lugar la total ausencia de culpa en mi conducta por no ser visible la señal de prohibición de estacionamiento.

SEGUNDA.- Como segunda alegación, invoco la infracción del art. 139 del Reglamento General de Circulación (RD 1428/2003, de 21 de noviembre) que establece que «corresponde al titular de la vía la responsabilidad de su mantenimiento en las mejores condiciones posibles de seguridad para la circulación y la instalación y conservación en ella de las adecuadas señales y marcas viales».

El lugar del estacionamiento normalmente es de aparcamiento autorizado en batería. En mitad del aparcamiento había un andamio que al parecer motivó la prohibición de estacionamiento. Sin embargo, este andamio no estaba señalizado ni balizado luminosamente en las horas en que estacioné el vehículo, tal como exige el art. 140 del Reglamento General de la Circulación. En este caso, la señalización compete al titular de las obras.

No niego que cuando el agente denuncia los hechos la señal se halle levantada, pero lo cierto es que por la noche cuando aparqué no existía ni señalización ni balizamiento luminoso, con lo cual no pude percatarme de la prohibición de estacionamiento.

Posteriormente, como ya he referido, cuando fui a recoger el vehículo me encuentro la señal en el suelo y boca abajo.

TERCERA.- Como tercera alegación, invoco la posible infracción del art. 12.1 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial, a resultas de lo que se acredite en la fase probatoria de este expediente.

Según el citado art. 12.1 la realización de instalaciones u obras en la vía pública requiere la autorización previa del titular de las mismas, cuando establece que “la realización de obras, instalaciones, colocación de contenedores, mobiliario urbano o cualquier otro elemento u objeto de forma permanente o provisional en las vías objeto de esta Ley necesitará la autorización previa del titular de las mismas y se regirán por lo dispuesto en la Ley de Carreteras y su Reglamento, y en las normas municipales”.

Es frecuente encontrarse con prohibiciones de estacionamiento que, si bien obedecen a obras o instalaciones, no están autorizadas por el respectivo Ayuntamiento quien, además de autorizar la ocupación de la vía pública, ha de acordar que la obra o instalación conlleva la prohibición de estacionamiento.

En este caso, ignoro si la obra estaba autorizada y, si lo estaba, si el Ayuntamiento acordó la prohibición de estacionamiento, por lo que invoco cautelarmente, a resultas de la prueba, la infracción de este precepto.

Por todo lo expuesto,

SOLICITO tenga por presentado escrito y, en virtud de las alegaciones contenidas en el mismo y previos los trámites legales, dicte resolución dejando sin efecto el expediente [COMPLETAR] (Referencia) [COMPLETAR], y no dando lugar a la imposición de sanción alguna.

OTROSI que solicito que se reciba el expediente administrativo a prueba practicando las siguientes diligencias:

a) Que se dé traslado al agente denunciante [ÓRGANO] para que informe sobre el escrito de alegaciones presentado.

b) Que por la Concejalía de Urbanismo se informe si había autorización o licencia para la instalación de un andamio con ocupación de la calzada en fecha [FECHA] en la calle [CALLE] Asimismo, deberá informar, de existir dicha autorización o licencia, si la misma facultaba a prohibir el estacionamiento en la citada calle.

DE NUEVO SOLICITO acuerde la práctica de la prueba referida.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmado:

EXCMO. AYUNTAMIENTO DE [LOCALIDAD]
