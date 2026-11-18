---
name: reposicion-contra-inadmision-falta-empadronamiento-957
description: "Redacta el escrito «Reposición contra inadmisión por falta de empadronamiento» (formulario 957 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra inadmisión por falta de empadronamiento

> Formulario 0957 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Se refiere a la regularización de 2005 (RD 2393/2004, DT 3.ª): solo tiene valor histórico.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE (2 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] NACIONALIDAD
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, actuando en nombre propio»; «…, con domicilio»; «…s (en adelante, LPACAP), en la ciudad de»; «…, del Delegado»; «…del Gobierno en la Comunidad de»; «…Tesorería General de la Seguridad Social»; «…Tercera del Real Decreto 2393/2004, para»; «…ientes: HECHOS PRIMERO.- Este interesado»; «…, y hoy lo hace adjuntos a este recurso:»; «…ntados. FUNDAMENTOS DE DERECHO PRIMERO.-»

## Elecciones que hay que hacer

- DELEGADO DEL GOBIERNO / SUBDELEGADO DEL GOBIERNO

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 66 de la Ley 39/2015
- Real Decreto 2393/2004

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

### Formulario 0957 · Reposición contra inadmisión por falta de empadronamiento

- Año del modelo: 2008
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 20 campos de relleno marcados en blanco
- Avisos de la revisión: Se refiere a la regularización de 2005 (RD 2393/2004, DT 3.ª): solo tiene valor histórico.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL [ELEGIR: DELEGADO DEL GOBIERNO / SUBDELEGADO DEL GOBIERNO]

(NOTA: El proceso transitorio de regularización al que se refiere el presente formulario, y que tuvo lugar al amparo de la Disposición Transitoria Tercera del Real Decreto 2393/2004 (ya derogado) [NOTA DE REVISIÓN: Formulario histórico (regularización de 2005). No tiene equivalente en el RD 1155/2024. La última vía extraordinaria (arraigo extraordinario, DA 21.ª añadida por el RD 316/2026) se podía solicitar hasta el 30-6-2026. Fuente: RD 316/2026 (BOE-A-2026-8284).], debe estimarse concluido. Mantenemos sin embargo el presente formulario en cuanto pudiera resultar ilustrativo para el sostenimiento de eventuales recursos judiciales en trámite.)

[NOMBRE Y APELLIDOS], con DNI/NIF/NIE nº [DNI/NIE], actuando en nombre propio [COMPLETAR], con domicilio [COMPLETAR] en [LOCALIDAD], el cual señalo a efectos de notificaciones conforme al artículo 66 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en adelante, LPACAP), en la ciudad de [COMPLETAR], en su calle [CALLE], número [NÚMERO], a través del presente escrito vengo a interponer

RECURSO DE REPOSICION

Contra la resolución de fecha [FECHA], del Delegado [COMPLETAR] del Gobierno en la Comunidad de [COMPLETAR], por su delegación dictada por [ÓRGANO O PERSONA], funcionario adscrito a la Tesorería General de la Seguridad Social [COMPLETAR], que adjunta se acompaña por copia, por la que se viene a inadmitir la solicitud de residencia y trabajo por cuenta ajena formulada al amparo del proceso extraordinario de regularización previsto en la Disposición Transitoria Tercera del Real Decreto 2393/2004, para [COMPLETAR], de nacionalidad [NACIONALIDAD] y número de pasaporte [DNI/NIE], lo que efectúo al amparo de los siguientes:

HECHOS

PRIMERO.- Este interesado [COMPLETAR] no presentó en su momento, ante la Oficina de la Tesorería General de la Seguridad Social a la que fue asignada la labor de recepción de las solicitudes formuladas por imperativo de la Resolución de 4 de febrero de 2005, de la Subsecretaría del Ministerio de la Presidencia (por la que se disponía la Publicación del convenio de colaboración entre la Secretaría de Estado de Inmigración y Emigración, la Secretaría de Estado de la Seguridad Social y la Subsecretaría de Administraciones públicas —BOE núm. 31, de 5 de febrero de 2005—), certificado de empadronamiento del/la trabajador/a cuya regularización se pretende y que, en efecto, sea de fecha anterior al 8 de agosto de 2004.

Pero sí presentaba, y hoy lo hace adjuntos a este recurso: [COMPLETAR].

SEGUNDO.- El resto de los requisitos documentales requeridos por las normas reguladoras del proceso extraordinario de regularización fueron oportunamente presentados.

FUNDAMENTOS DE DERECHO

PRIMERO.- [COMPLETAR].

En [LUGAR], a [FECHA].

Firmado:
