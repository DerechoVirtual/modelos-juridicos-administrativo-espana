---
name: solicitud-autorizacion-centro-recogida-vehiculos-fuera-1723
description: "Redacta el escrito «Solicitud de autorización para un centro de recogida de vehículos fuera de uso» (formulario 1723 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de autorización para un centro de recogida de vehículos fuera de uso

> Formulario 1723 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] FECHA

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

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

### Formulario 1723 · Solicitud de autorización para un centro de recogida de vehículos fuera de uso

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito solicitando a la Administración la autorización para la instalación de un centro de recogida y almacenamiento de vehículos fuera de uso, para su posterior desguace, reciclado y achatarramiento, de acuerdo con la legislación protectora del medio ambiente.

Ilmo. Sr./Sra.

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.], ante [ÓRGANO], órgano competente, comparece y

EXPONE:

Que pretende realizar la siguiente actividad sometida a autorización administrativa previa de conformidad con legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial:

Apertura y funcionamiento de un centro para la recogida y almacenamiento de vehículos fuera de uso, para su posterior desguace, reciclado de piezas y achatarramiento de los elementos inservibles, de conformidad con la legislación protectora del medio ambiente aplicable a este sector.

Que reúne los requisitos establecidos en la legislación vigente para que se le conceda la autorización indicada y así se acredita con la siguiente documentación que se adjunta a este escrito de solicitud:

En virtud de lo expuesto y de conformidad con las previsiones de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas y demás normas aplicables,

SOLICITA:

Que se tenga por presentado este escrito con la documentación que se acompaña, y previa la tramitación que proceda se conceda interesado autorización administrativa para el ejercicio de la actividad mencionada, con el alcance reglamentariamente establecido, en los términos solicitados. (1)

En [LUGAR], a [FECHA].

Firma

NOTAS DEL FORMULARIO

(1) Los centros de almacenamiento de vehículos fuera de uso pretenden ser modernas instalaciones que tratan de poner fin a los denominados "cementerios de coches", que proliferan en las orillas de las carreteras como simples vertederos de chatarra, sin permisos ambientales de ningún tipo y sin respeto a la legislación sobre reciclado de piezas y adecuada gestión de los residuos peligrosos que contiene el automóvil, singularmente los aceites usados y las baterías, pero también otros como los neumáticos y las demás piezas que no podrán ser recicladas de forma satisfactoria para un segundo empleo en vehículos nuevos o usados. La autorización de este tipo de centros para la gestión ordenada de los vehículos fuera de uso requiere las correspondientes licencias municipales para controlar la legalidad urbanística del uso y de los órganos competentes en materia de calificación o impacto ambiental, para la ubicación de un centro de residuos urbanos, según la dimensión de la instalación proyectada. Por tanto, la autorización a que se refiere este formulario es únicamente la que se refiere a la inscripción registral de la actividad en la forma que se establezca en la legislación europea, estatal o regional que sea aplicable y, en consecuencia, su otorgamiento no excluye ni elimina la necesidad de pedir y obtener las demás autorizaciones necesarias para la apertura y puesta en marcha de un centro de estas características.
