---
name: solicitud-autorizacion-centro-reconocimiento-conductores-1721
description: "Redacta el escrito «Solicitud de autorización para un centro de reconocimiento de conductores» (formulario 1721 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de autorización para un centro de reconocimiento de conductores

> Formulario 1721 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] C.P.
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] FECHA

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 4 del Real Decreto 170/2010
- artículo 8 del Real Decreto 170/2010
- artículo 62.4 del Real Decreto Legislativo 6/2015
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

### Formulario 1721 · Solicitud de autorización para un centro de reconocimiento de conductores

- Año del modelo: 2004
- Revisión 17-11-2026: 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud realizada por un centro sanitario privado, con el objeto de obtener la autorización administrativa que le permita llevar a cabo actividades de reconocimiento de aptitud física y psíquica de los conductores, para la obtención de los permisos de conducción previstos en la normativa de circulación

Ilmo. Sr./Sra.

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.], ante [ÓRGANO], órgano competente, comparece y

EXPONE:

Que pretende realizar la siguiente actividad sometida a autorización administrativa previa de conformidad con legislación reguladora del tráfico, circulación de vehículos a motor y seguridad vial:

Establecimiento de un Centro de Reconocimiento para la constatación de las aptitudes psicofísicas de los conductores, al amparo de lo establecido en el Real Decreto 170/2010, de 19 de febrero, por el que se aprueba el Reglamento de centros de reconocimiento destinados a verificar las aptitudes psicofísicas de los conductores

Que, de conformidad con lo previsto en la normativa de aplicación, se pone en conocimiento de esa Jefatura de Tráfico los siguientes datos:

1. Nombre comercial del centro sanitario privado y domicilio:
2. Nombre, apellidos y DNI de la persona o personas físicas propietarias del centro:

3. Horario de funcionamiento del centro para el servicio de reconocimiento de conductores, que será el horario de permanencia en aquél para los facultativos adscritos al mismo:

Que reúne los requisitos establecidos en la legislación vigente para que se le conceda la autorización indicada y así se acredita con la siguiente documentación que se adjunta a este escrito de solicitud:

a) Fotocopia de las autorizaciones sanitarias de instalación y funcionamiento como centro de reconocimiento otorgada por la autoridad sanitaria competente.

b) Fotocopia del certificado de inscripción en el Registro sanitario correspondiente como centro de reconocimiento.

c) Relación del personal autorizado por la autoridad sanitaria competente.

d) Fotocopia del contrato con la clínica que vaya a prestar los servicios de oftalmología (en el supuesto en que se vaya a prescindir del médico oftalmólogo de acuerdo con lo dispuesto en el artículo 4 del Real Decreto 170/2010).

e) Declaraciones por escrito del titular, del director, del director facultativo, en su caso, así como de los facultativos de no estar incursos en las incompatibilidades que se indican en el artículo 8 del Real Decreto 170/2010.

Que el órgano competente para la expedición de la acreditación solicitada es la Jefatura de Tráfico de [LOCALIDAD], de conformidad con el artículo 62.4 del Real Decreto Legislativo 6/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley sobre Tráfico, Circulación de Vehículos a Motor y Seguridad Vial y de acuerdo con lo que reglamentariamente se determina.

En virtud de lo expuesto y de conformidad con las previsiones de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante LPACAP) y demás normas aplicables,

SOLICITA:

Que se tenga por presentado este escrito con la documentación que se acompaña, y previa la tramitación que proceda se conceda al interesado la inscripción del centro de reconocimiento sanitario privado referenciado, para la realización de las funciones que reglamentariamente correspondan, en los términos solicitados.

En [LUGAR], a [FECHA].

Firma
