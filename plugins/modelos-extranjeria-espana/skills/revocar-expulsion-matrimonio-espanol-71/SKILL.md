---
name: revocar-expulsion-matrimonio-espanol-71
description: "Redacta el escrito «Revocar la expulsión por matrimonio con español» (formulario 71 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revocar la expulsión por matrimonio con español

> Formulario 0071 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Si el cónyuge es español sin libre circulación previa, rige el régimen de familiares de españoles de los arts. 93-99 RD 1155/2024 (DT 3.ª y 4.ª).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (3 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NACIONALIDAD
- [ ] DNI/NIE
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… el Delegado/Subdelegado del Gobierno en»; «…, con prohibición de entrada por»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 53.1.a) de la Ley Orgánica 4/2000
- artículo 15.1.c) del Real Decreto 240/2007
- artículo 105.1 de la Ley 39/2015
- artículo 55.2 de la Ley Orgánica 4/2000

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

### Formulario 0071 · Revocar la expulsión por matrimonio con español

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco
- Avisos de la revisión: Si el cónyuge es español sin libre circulación previa, rige el régimen de familiares de españoles de los arts. 93-99 RD 1155/2024 (DT 3.ª y 4.ª).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA DELEGACIÓN / SUBDELEGACIÓN DEL GOBIERNO EN [LOCALIDAD]

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad [NACIONALIDAD] con N.I.E./ pasaporte n.º [DNI/NIE] ante este organismo comparece y

EXPONE:

Primero.— Que el día [FECHA] la Subdelegación del Gobierno en [LOCALIDAD] decretó la expulsión del solicitante del territorio español, con prohibición de entrada por 3 años, por la infracción del artículo 53.1.a) de la Ley Orgánica 4/2000. Se adjunta a efectos de prueba copia de la citada resolución.

Segundo.— Que en fecha [FECHA] el interesado ha contraído matrimonio con el/la ciudadano/a española D.ª [NOMBRE Y APELLIDOS], como se acredita mediante certificación literal de matrimonio del Registro Civil de [LOCALIDAD], copia de la cual se adjunta al presente escrito.

Tercero.— Que el matrimonio de ciudadano extranjero con ciudadano español, siempre que no exista separación de derecho, permite legalizar la situación del cónyuge extranjero, por quedar incluido el mismo dentro del ámbito de aplicación de la normativa comunitaria.

Y según establece el artículo 15.1.c) del Real Decreto 240/2007 [NOTA DE REVISIÓN (comprobar): Cita correcta (el texto citado es el párrafo que sigue a la letra c) del art. 15.1). Si el cónyuge es español y no ha ejercido la libre circulación, comprobar si se aplica el régimen de familiares de españoles (arts. 93 a 99 RD 1155/2024) en lugar del comunitario. Fuente: RD 240/2007, art. 15.1 (BOE-A-2007-4184); RD 1155/2024, arts. 93-99 (BOE-A-2024-24099).], de 16 de febrero: Únicamente podrá adoptarse una decisión de expulsión respecto a ciudadanos de un Estado miembro de la Unión Europea o de otro Estado parte en el Acuerdo sobre el Espacio Económico Europeo, o a miembros de su familia, con independencia de su nacionalidad, que hayan adquirido el derecho de residencia permanente en España, si existen motivos graves de orden público o seguridad pública.

No existiendo dichos motivos graves de orden público o seguridad pública, quedarían desvirtuados los supuestos por los cuales se dictó la resolución de expulsión y prohibición de entrada en territorio español.

Cuarto.— En el presente caso es de aplicación lo dispuesto en el artículo 105.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas que establece que:

Las Administraciones Públicas podrán revocar, mientras no haya transcurrido el plazo de prescripción, sus actos de gravamen o desfavorables, siempre que tal revocación no constituya dispensa o exención no permitida por las leyes, ni sea contraria al principio de igualdad, al interés público o al ordenamiento jurídico.

Quinto.— Es competente para conocer de la solicitud de renovación el Delegado/Subdelegado del Gobierno en [COMPLETAR] según dispone el artículo 55.2 de la Ley Orgánica 4/2000, por ser el órgano que dictó la resolución de expulsión.

Por lo expuesto SOLICITA QUE SE REVOQUE LA RESOLUCIÓN DE EXPULSIÓN DE D./ D.ª [NOMBRE Y APELLIDOS], con prohibición de entrada por [COMPLETAR] año/s, de fecha [FECHA]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo.:
