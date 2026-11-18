---
name: reposicion-contra-multa-estancia-irregular-383
description: "Redacta el escrito «Reposición contra multa por estancia irregular» (formulario 383 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra multa por estancia irregular

> Formulario 0383 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] COLEGIO
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] IMPORTE
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, nacional de»; «…pulsión por la Comisaría del distrito de»; «…realización de prueba, consistente en: -»; «…-»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 53.1.a) de la Ley Orgánica 4/2000
- art. 124 de la Ley 39/2015
- art. 123.1 de la Ley 39/2015
- arts. 63 de la Ley Orgánica 4/2000
- art. 20.2 de la Ley Orgánica 4/2000
- art. 234.4 Real Decreto 1155/2024
- art. 48 de la Ley 39/2015
- art. 47 LPACAP
- Ley Orgánica 2/2009

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

### Formulario 0383 · Reposición contra multa por estancia irregular

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SUBDELEGACIÓN DEL GOBIERNO EN [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], abogado/a colegiado/a por el Ilustre Colegio de Abogados de [COLEGIO] con el n.º [NÚMERO], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, nacional de [COMPLETAR], ante este organismo comparezco para formular RECURSO DE REPOSICIÓN contra la resolución de fecha [FECHA], que ha sido notificada el día [FECHA] por la que se impone a D./Dña. [NOMBRE Y APELLIDOS] la sanción de multa de [IMPORTE] euros, con orden de abandonar el territorio español en el plazo de [Nº] días, copia de la cual se adjunta con el presente escrito.

HECHOS

Primero.- El día [FECHA], fue incoado Expediente Administrativo de Expulsión por la Comisaría del distrito de [COMPLETAR], por la presunta infracción del art. 53.1.a) de la Ley Orgánica 4/2000, reformada por Ley Orgánica 2/2009.

Segundo.- El motivo de la detención de D. fue el carecer de autorización de residencia en España, sin que constara ninguna otra circunstancia en la notificación de acuerdo de inicio del expediente sancionador.

Además, se hizo constar la existencia de una situación de arraigo social y laboral del interesado en España.

Tercero.- Se formularon alegaciones dentro del plazo de 48 horas previsto por la legislación vigente, alegando la existencia de una situación de arraigo familiar en España del interesado.

Cuarto.- Sin más trámites, se ha dictado la resolución que ahora se recurre.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I

De conformidad con lo establecido en el art. 124 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta dentro del plazo de un mes posterior a su notificación.

II

De acuerdo con lo dispuesto en el art. 123.1 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas, este recurso se presenta ante el órgano que dictó la resolución.

III

La legislación aplicable al presente procedimiento es la Ley Orgánica 4/2000 sobre Derechos y Libertades de los Extranjeros en España, el del Real Decreto 1155/2024 por el que se aprueba su Reglamento y las normas de general aplicación. En lo relativo al procedimiento preferente de expulsión son de aplicación los arts. 63 de la Ley Orgánica 4/2000 y 233 y ss del Real Decreto 1155/2024 .

En particular es de aplicación el art. 20.2 de la Ley Orgánica 4/2000, que garantiza el principio de contradicción, audiencia al interesado y motivación de las resoluciones, la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.

IV

En la instrucción del procedimiento no se notificó al interesado ni a su representante la propuesta de resolución, tal como establece el art. 234.4 Real Decreto 1155/2024 [NOTA DE REVISIÓN: La notificación de la propuesta de resolución en el procedimiento preferente es el art. 234.4, párrafo cuarto; el 234.2 regula la asistencia letrada e intérprete. Fuente: RD 1155/2024, art. 234 (BOE-A-2024-24099).], no pudiendo por tanto formularse alegaciones respecto a la misma.

Por otra parte, en el escrito de alegaciones se había propuesto la realización de prueba, consistente en:

- [COMPLETAR]
- [COMPLETAR]

Respecto a la proposición de prueba, se ha incumplido lo dispuesto en el mencionado artículo, pues no se ha notificado al interesado la decisión adoptada al respecto, ni estimando ni desestimando su realización.

Dicha omisión del procedimiento legalmente establecido es causa de indefensión del recurrente, y causa de anulabilidad de la resolución recurrida, en virtud de lo establecido en el art. 48 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas(al ser un procedimiento sancionador pordría valorarse la nulidad de pleno derecho del art. 47 LPACAP).

Así lo ha establecido la STS, Sala 3.ª de lo Contencioso-administrativo, Secc. 5.ª, de 16 de marzo de 2006, Rec. 7269/2002, anulando la resolución administrativa que decretaba la expulsión por dichos motivos.

V

A efectos de notificaciones, según preceptúan los arts. 40 y siguientes de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común, se señala el despacho del/de la letrado/a D./Dña. [NOMBRE Y APELLIDOS], sito en [LOCALIDAD].

Por lo expuesto,

SOLICITO

Que sea anulada la resolución recurrida, por considerar que los hechos relatados y los fundamentos de derecho expuestos, desvirtúan los fundamentos de derecho de la resolución recurrida.

En [LUGAR], a [FECHA].

Fdo.:
