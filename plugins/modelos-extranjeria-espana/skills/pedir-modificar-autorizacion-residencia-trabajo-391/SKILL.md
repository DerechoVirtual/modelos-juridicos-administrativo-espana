---
name: pedir-modificar-autorizacion-residencia-trabajo-391
description: "Redacta el escrito «Pedir modificar la autorización de residencia y trabajo» (formulario 391 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir modificar la autorización de residencia y trabajo

> Formulario 0391 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…nacional de»; «…do actividades lucrativas, en la empresa»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 192 del Real Decreto 1155/2024

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

### Formulario 0391 · Pedir modificar la autorización de residencia y trabajo

- Año del modelo: 2013
- Revisión 17-11-2026: 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Oficina Extranjería competente
Organismo de la Comunidad Autónoma

D./Dña. [NOMBRE Y APELLIDOS] nacional de [COMPLETAR], titular de autorización de residencia y trabajo temporal por cuenta ajena, con n.º [NÚMERO], con domicilio en [LOCALIDAD], expone en este Organismo.

1. Posee residencia legal en España mediante la referida autorización de residencia y trabajo por cuenta ajena, con la que ha venido desempeñando actividades lucrativas, en la empresa [COMPLETAR] (Se adjunta Anexo I. Copia del contrato de trabajo).
2. La vigencia de la esta tarjeta se extiende hasta el [FECHA].
3. El administrado solicita la mutación del alcance laboral de su tarjeta, para obtener una autorización por cuenta propia, antes del término de su renovación.
4. Que el artículo 192 del Real Decreto 1155/2024, de 19 de noviembre establece que:
1. Durante el primer año de vigencia de las autorizaciones iniciales de residencia y trabajo, el órgano competente por razón del lugar donde se vaya a iniciar la relación laboral o la actividad por cuenta propia que motiva la solicitud, podrá modificar su alcance en cuanto a la ocupación, sector de actividad y ámbito territorial de limitación, siempre a petición de su titular.

En el caso de que se trate de una modificación del alcance de una autorización de residencia temporal y trabajo por cuenta ajena, se tendrá en cuenta la situación nacional de empleo.

Esta solicitud deberá resolverse y notificarse en el plazo máximo de un mes. Transcurrido dicho plazo sin resolución expresa se entenderá que ha sido concedida.

2. Las personas titulares de una autorización de residencia y trabajo por cuenta ajena podrán acceder a una autorización de residencia y trabajo por cuenta propia. Para ello deberán presentar la correspondiente solicitud. La nueva autorización no ampliará la vigencia de la autorización modificada.
5. El interesado acredita de esta forma el acaecimiento de los requisitos para la obtención de la modificación que interese en cada caso.

Por todo ello solicita que sean acreditadas las circunstancias que justifiquen la modificación de la autorización de residencia y trabajo, para la mutación de su autorización de residencia laboral de cuenta ajena a propia, antes del término exigido de su renovación.

En [LUGAR], a [FECHA].
