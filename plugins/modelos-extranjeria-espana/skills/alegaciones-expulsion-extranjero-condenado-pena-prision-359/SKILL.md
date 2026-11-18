---
name: alegaciones-expulsion-extranjero-condenado-pena-prision-359
description: "Redacta el escrito «Alegaciones en expulsión de extranjero condenado a pena de prisión» (formulario 359 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones en expulsión de extranjero condenado a pena de prisión

> Formulario 0359 del plugin **Extranjería** · revisado el 17-11-2026.

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
- [ ] NÚMERO
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Nº DE COLEGIADO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en nombre y representación de D.»; «…, mayor de edad, nacional de»; «…te administrativo de expulsión contra D.»; «…incial de Extranjería y Documentación de»; «…ga duración, la cual está en vigor hasta»; «…. • Sus hermanos,»; «…. • Sus hermanos, [COMPLETAR] y»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 57.2 de la LO 4/2000
- artículo 241.1 del Real Decreto 1155/2024
- artículo 57.5 de la LO 4/2000
- artículo 54.1.a) de la LO 4/2000
- artículo 234 del Real Decreto 1155/2024
- artículo 66 de la Ley 39/2015

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

### Formulario 0359 · Alegaciones en expulsión de extranjero condenado a pena de prisión

- Año del modelo: 2013
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (DNI/NIE, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA BRIGADA PROVINCIAL DE EXTRANJERÍA Y DOCUMENTACIÓN

D./Dña. [NOMBRE Y APELLIDOS], abogado/a colegiado/a por el Ilustre Colegio de Abogados de [COLEGIO] con el n.º [NÚMERO], en nombre y representación de D. [COMPLETAR], mayor de edad, nacional de [COMPLETAR], con NIE N.º [DNI/NIE]

EXPONE

Que, habiendo sido notificada incoación de expediente administrativo de expulsión contra D. [COMPLETAR], formulo dentro del plazo legalmente establecido las siguientes

ALEGACIONES

Primera.- El día [FECHA], se ha incoado expediente sancionador por la Brigada Provincial de Extranjería y Documentación de [COMPLETAR] por la presunta infracción del artículo 57.2 de la LO 4/2000.

Se adjunta copia del mencionado escrito.

Segunda.- La condena por la que el interesado estaba cumpliendo pena de prisión era de 10 meses, derivada de dos condenas a 4 y 6 meses, respectivamente, por sendos delitos de violencia de género y quebrantamiento de condena.

No se cumple, por tanto, el requisito del artículo 57.2 de la LO 4/2000 ni del artículo 241.1 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba su reglamento de desarrollo, dado que ambas condenas son inferiores a un año.

Tercera.- En el presente caso, debe tenerse en cuenta, como criterios favorables al interesado los siguientes:

— El interesado es titular de residencia de larga duración, la cual está en vigor hasta [COMPLETAR].
— Tiempo de residencia en España, donde se encuentra desde hace trece años.
— Arraigo social y familiar, pues reside en España con sus padres y tres hermanos, todos los cuales ha adquirido la nacionalidad española por residencia.

No procedería, pues, en ningún caso la sanción de expulsión, dado que el interesado es titular de autorización de residencia de larga duración, y según establece el artículo 57.5 de la LO 4/2000, la sanción de expulsión no podrá ser impuesta a los residentes de larga duración.

En estos casos, tan sólo sería procedente la sanción de expulsión por la infracción del artículo 54.1.a) de la LO 4/2000 o cuando exista una reincidencia en la comisión en el término de un año de una infracción de la misma naturaleza sancionable con expulsión. En el presente caso no concurre ninguna de las dos circunstancias.

Incluso en estos casos, se impone la obligación, antes de adoptar la decisión de expulsión, de tomar en consideración el tiempo de su residencia en España y los vínculos creados, su edad, las consecuencias para el interesado y para los miembros de su familia y los vínculos con el país al que va a ser expulsado.

Circunstancias que, en el presente caso, acreditan un especial arraigo y una falta de vinculación con el país de origen, ya que el interesado lleva 13 años en España y todos sus familiares directos viven en España y han obtenido la nacionalidad española por residencia.

Cuarta.- De acuerdo con lo establecido en el artículo 234 del Real Decreto 1155/2024, de 19 de noviembre, se propone, para acreditar lo expuesto en estas alegaciones, la realización de la siguiente PRUEBA:

• Que se requiera al Registro Civil Central para que acredite la nacionalidad española de los siguientes familiares del interesado:
• Sus padres, D. y Dña. [NOMBRE Y APELLIDOS].
• Sus hermanos, [COMPLETAR] y [COMPLETAR]
• Que se requiera a la Brigada Provincial de Extranjería y Documentación para que acredite que el interesado es titular de autorización de residencia de larga duración.

Quinta.- A efectos de notificaciones, según preceptúa el artículo 66 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, se señala el domicilio del/de la letrado/a D./Dña. [NOMBRE Y APELLIDOS]:

Por lo expuesto,

SOLICITO

Que teniendo por presentado este escrito en tiempo y forma, se sirva admitirlo, tenga por interpuesto escrito de alegaciones y que se dicte en el momento procesal oportuno resolución por la que se archive el procedimiento sancionador incoado.

En [LUGAR], a [FECHA].

Fdo.:

Colegiado/a n.º [Nº DE COLEGIADO]
