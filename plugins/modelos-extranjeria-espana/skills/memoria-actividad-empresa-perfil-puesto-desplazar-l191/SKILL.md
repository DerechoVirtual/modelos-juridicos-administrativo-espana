---
name: memoria-actividad-empresa-perfil-puesto-desplazar-l191
description: "Redacta el escrito «Memoria de actividad de la empresa y perfil del puesto para desplazar y contratar extranjeros» (formulario 191 (Laboral) de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Memoria de actividad de la empresa y perfil del puesto para desplazar y contratar extranjeros

> Formulario 0191 de la colección de Laboral del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] FECHA
- [ ] NIF
- [ ] LOCALIDAD
- [ ] IMPORTE
- [ ] NOMBRE Y APELLIDOS
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Actividad de la Empresa es una sociedad»; «…ero de Inscripción a la Seguridad Social»; «…. tiene como objeto social»; «…ña se dedica a la actividad principal de»; «…, y como actividades secundarias realiza»; «…. Se rige por el Convenio Colectivo de»; «…() Actualmente la empresa tiene»; «…y cuenta con»; «…r a un trabajador extranjero consiste en»; «…. El objeto de este proyecto es»; «…y cuenta con un equipo de»; «…euros. La duración del proyecto será de»; …

## Elecciones que hay que hacer

- económico / social / laboral

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- [COMPLETAR]…

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, conciliación o mediación previa, reclamación previa o vía administrativa, según el caso).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0191 · Memoria de actividad de la empresa y perfil del puesto para desplazar y contratar extranjeros

- Año del modelo: 2020
- Revisión 17-11-2026: 1 desplegables y casillas convertidos en elección en blanco; 1 párrafos repetibles señalados; 25 campos de relleno marcados en blanco; 1 etiquetas sin dato marcadas en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Actividad de la Empresa
Proyecto para el que se solicita autorización
Concurrencia de razones de interés económico, social o laboral
Funciones y condiciones laborales del trabajador
Firmas

Documento que debe acompañar a la solicitud de autorización de residencia temporal y trabajo en España de extranjeros, cuando concurran razones de interés económico, social o laboral, o para la realización de trabajos de investigación o desarrollo o docentes, que requieran alta cualificación, o de actuaciones artísticas de especial interés cultural.

Actividad de la Empresa

 es una sociedad [COMPLETAR], constituida en fecha [FECHA], NIF [NIF], Número de Inscripción a la Seguridad Social [COMPLETAR] y con domicilio social en [LOCALIDAD].

 tiene como objeto social [COMPLETAR], y en España se dedica a la actividad principal de [COMPLETAR]. Asimismo, y como actividades secundarias realiza [COMPLETAR].

Se rige por el Convenio Colectivo de [COMPLETAR] ()

Actualmente la empresa tiene [COMPLETAR] y cuenta con [COMPLETAR] personas trabajadoras en alta.

Proyecto para el que se solicita autorización

El proyecto concreto para el que se solicita la autorización para contratar a un trabajador extranjero consiste en [COMPLETAR].

El objeto de este proyecto es [COMPLETAR] y cuenta con un equipo de [COMPLETAR] personas y un presupuesto de [IMPORTE] euros.

La duración del proyecto será de [COMPLETAR] y la fecha prevista de entrada del trabajador en España es [COMPLETAR].

Concurrencia de razones de interés económico, social o laboral

Las razones de índole [ELEGIR: económico / social / laboral] para contratar a un trabajador extranjero son las siguientes:

[OPCIONAL — repetir el párrafo siguiente tantas veces como haga falta]

[COMPLETAR]

Funciones y condiciones laborales del trabajador

El trabajador prestará su trabajo como [COMPLETAR], incluido en el grupo profesional [COMPLETAR], mediante un contrato [COMPLETAR] y sujeto a las condiciones establecidas en el convenio colectivo de aplicación.

El lugar de trabajo será [COMPLETAR], con una jornada de [COMPLETAR] distribuidas de la siguiente forma [COMPLETAR].

Fdo.: [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS]

════════════════════════════════════════════════════════════════════════
