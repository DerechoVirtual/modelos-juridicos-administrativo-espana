---
name: resolucion-adopta-medidas-cautelares-trafico-seguridad-188
description: "Redacta el escrito «Resolución que adopta medidas cautelares en tráfico y seguridad vial» (formulario 188 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución que adopta medidas cautelares en tráfico y seguridad vial

> Formulario 0188 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (4 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…isitos contenido en la autorización para»; «… Primero.- En orden a la verificación de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 2.2 del Real Decreto 320/1994
- Ley 39/2015

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

### Formulario 0188 · Resolución que adopta medidas cautelares en tráfico y seguridad vial

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el expediente número [Nº DE PROCEDIMIENTO]/[AÑO], seguido en este órgano administrativo a D./Dña. [NOMBRE Y APELLIDOS], DNI número [DNI/NIE], con domicilio en [LOCALIDAD], con objeto de adoptar medidas cautelares en orden a la verificación de los requisitos de las autorizaciones correspondientes, resulta:

Con fecha [FECHA], se acordó la incoación de expediente para la adopción de medidas cautelares para la verificación de los requisitos contenido en la autorización para [COMPLETAR] otorgada al interesado, como consecuencia de la finalización, sin pronunciamiento expreso al respecto, en el proceso penal número [NÚMERO] que ha finalizado con sentencia condenatoria de fecha [FECHA], dictada por el Juzgado de lo Penal.

Con fecha [FECHA], se ha recibido el escrito de alegaciones, dentro del plazo establecido, frente a la propuesta de resolución en la que se indican las medidas cautelares que podrían acordarse definitivamente por este órgano administrativo.

Por la sección de [LOCALIDAD] se ha examinado el escrito de alegaciones presentado por el interesado, habiéndose desestimado tras la práctica de cuantos actos de instrucción se han considerados adecuados para la comprobación de los antecedentes y fundamentos de esta actuación administrativa, con el resultando que obra en el expediente.

Por cuanto antecede y de conformidad con las previsiones del artículo 2.2 del Real Decreto 320/1994, de 25 de febrero, por el que se aprueba el Reglamento de procedimiento sancionador en materia de tráfico, circulación de vehículos a motor y seguridad vial [NOTA DE REVISIÓN (comprobar): El equivalente legal es el art. 85.2-3 TR LSV (archivo tras condena penal; continuación si la absolución no se funda en la inexistencia del hecho). Revisar si el formulario (medidas cautelares) encaja en ese supuesto. Fuente: TR LSV (RDLeg 6/2015), BOE-A-2015-11722 art. 85.], he tenido a bien

RESOLVER:

Primero.- En orden a la verificación de [COMPLETAR], autorización administrativa concedida a D./Dña. [NOMBRE Y APELLIDOS], se adoptan definitivamente las siguientes medidas cautelares que se ejecutarán en la forma y tendrán el periodo de vigencia que seguidamente se indica:

Segundo.- Notifíquese este acuerdo de adopción de medidas cautelares al interesado con indicación de los recursos que procedan de conformidad con las previsiones de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

En [LUGAR], a [FECHA].

Firmado:
