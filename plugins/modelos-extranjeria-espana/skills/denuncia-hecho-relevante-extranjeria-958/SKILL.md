---
name: denuncia-hecho-relevante-extranjeria-958
description: "Redacta el escrito «Denuncia de un hecho relevante en extranjería» (formulario 958 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia de un hecho relevante en extranjería

> Formulario 0958 del plugin **Extranjería** · revisado el 17-11-2026.

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

- La denuncia se rige por el art. 62 LPACAP. Sancionador de extranjería: numeración del RD 1155/2024 desplazada un número respecto del RD 557/2011.
- Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…antedichos hechos pueden ser comprobados»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 218.2 del Real Decreto 1155/2024
- artículo 66 Ley 39/2015
- art. 62 LPACAP
- art. 218 del Real Decreto 1155/2024
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

### Formulario 0958 · Denuncia de un hecho relevante en extranjería

- Año del modelo: 2008
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 bloques de alternativas señalados; 6 campos de relleno marcados en blanco
- Avisos de la revisión: La denuncia se rige por el art. 62 LPACAP. Sancionador de extranjería: numeración del RD 1155/2024 desplazada un número respecto del RD 557/2011. · Expedientes presentados antes del 20-5-2025: se tramitan con la norma vigente al presentarse (RD 557/2011) salvo que el interesado pida la nueva (DT 2.ª RD 1155/2024); en esos casos la cita al RD 557/2011 puede ser la correcta.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

[ELEGIR UNA DE ESTAS ALTERNATIVAS Y SUPRIMIR LAS DEMÁS:]
— (El encabezamiento del escrito se rellenará con la identidad de la autoridad que haya acordado la incoación del procedimiento conforme al art. 218.2 del Real Decreto 1155/2024, de 19 de noviembre [NOTA DE REVISIÓN: Mismo contenido (órganos competentes para ordenar la incoación). Fuente: RD 1155/2024, art. 218.2 (BOE-A-2024-24099); RD 557/2011, art. 219.2 (BOE-A-2011-7703).])

Subdelegado del Gobierno

Comisario General de Extranjería y Documentación

Jefe Superior de Policía

Comisarios Provinciales

Titulares de las comisarías locales y puestos fronterizos

D./Dña. [NOMBRE Y APELLIDOS], con DNI/NIF/NIE nº [DNI/NIE], con domicilio en [LOCALIDAD], el cual señalo a efectos de notificaciones conforme al artículo 66 Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), a través del presente escrito comparece, y como mejor proceda en derecho formula la presente

DENUNCIA

en virtud de lo dispuesto en el art. 62 LPACAP y art. 218 del Real Decreto 1155/2024, de 19 de noviembre [NOTA DE REVISIÓN: La denuncia como forma de inicio está en el art. 62 de la Ley 39/2015; el 55.1 regula las actuaciones previas. El art. 218.1 RD 1155/2024 recoge la iniciación por denuncia. Fuente: Ley 39/2015, arts. 55 y 62 (BOE-A-2015-10565); RD 1155/2024, art. 218 (BOE-A-2024-24099).], por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social, a fin de poner en conocimiento de ese órgano los siguientes:

Los antedichos hechos pueden ser comprobados [COMPLETAR]

Todo ello se comunica al órgano administrativo por si los hechos narrados debieran dar lugar a la iniciación del correspondiente expediente administrativo sancionador y con el objeto de que, previas las comprobaciones e informaciones necesarias, se adopten las medidas oportunas y legalmente procedentes, cuyo resultado se solicita se comunique a este denunciante.

En [LUGAR], a [FECHA].

Fdo: D./D.ª [NOMBRE Y APELLIDOS]
