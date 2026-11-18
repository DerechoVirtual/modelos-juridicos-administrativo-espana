---
name: pedir-garantias-encargado-tratamiento-datos-73
description: "Redacta el escrito «Pedir garantías al encargado del tratamiento de datos» (formulario 73 de procedimiento administrativo común, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir garantías al encargado del tratamiento de datos

> Formulario 0073 del plugin **Procedimiento administrativo común** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Ordenanzas municipales** (tráfico, urbanismo, tributos locales, convivencia) → `buscar_ordenanzas` → `leer_ordenanza`.
- **Criterio de Hacienda y del TEAC** → `buscar_consultas_hacienda` → `leer_consulta_hacienda`; `buscar_doctrina_teac` → `leer_resolucion_teac`.

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

El formulario no tiene campos marcados: revisa el texto por si hay datos implícitos.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 28 RGPD

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

### Formulario 0073 · Pedir garantías al encargado del tratamiento de datos

- Año del modelo: 2019
- Revisión 17-11-2026: sin cambios

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

El art. 28 RGPD obliga a los Responsables de Tratamiento a que únicamente elija encargados de tratamiento que ofrezcan garantías suficientes para que el tratamiento sea conforme con los requisitos indicados en el RGPD y que garantice la protección de los derechos de los interesados.

Con el fin de facilitar la aportación de esta información le presentamos el siguiente listado de posibles garantías que rogamos lo completen.

Documente las preguntas que conteste afirmativamente.

Preguntas	Respuestas
Cuestionario	Si	No
¿Tienen nombrada una persona, empresa, para que sea delegado de protección de datos?
¿Ha pasado alguna auditoría de protección de datos? En caso afirmativo aporte el último informe de auditoría.

¿Han hecho un análisis de riesgos?

En caso afirmativo, aporte resumen del mismo.

¿Tiene hecho el registro de actividades de tratamiento como encargado que nos presta servicios? Aporte copia del mismo, con breve indicación de las medidas de seguridad técnicas y organizativas que tiene
¿Su organización tiene algún tipo de certificación o está adherido a algún código de conducta para garantizar que tienen adoptadas medidas de seguridad? Aporte copia del mismo.

En el caso que haya respondido negativamente a todas las anteriores preguntas por favor responda a las siguientes.

Preguntas	Respuestas
Cuestionario	Si	No
¿Tienen nombrada una persona, empresa, para que sea delegado de protección de datos?
En caso de una respuesta negativa a la anterior pregunta. ¿sabe si está obligado a tenerlo?
¿Conoce la norma que ampara esa decisión? En el apartado observaciones indíquela.
¿Tienen un procedimiento para informar sobre posibles brechas de seguridad?
¿Tienen un procedimiento para atender el ejercicio de los derechos de los interesados?
¿Todos los usuarios/trabajadores de su empresa pueden acceder a la misma información?
¿Se ha establecido diferentes perfiles de acceso y permiten identificar a los usuarios?
¿Cambian las contraseñas para acceder a los equipos y programas de forma periódica?
¿Las contraseñas tienen más de 8 dígitos y contienen letras y números, símbolos, mayúsculas y minúsculas?
¿Tiene un sistema de copias de seguridad que le permita recuperar la información?
¿Conserva el dispositivo sobre el que hace las copias en otro lugar diferente al que se encuentra el servidor?
¿Utilizan alguna plataforma, servidor, que esté en la “nube” para prestar sus servicios? Si la respuesta es afirmativa indique el proveedor.
¿Tiene un contrato para ese servicio de alojamiento en la nube?
¿Contrata servicios de otras empresas para realizar los servicios que tenemos contratados? (subcontratación)
¿Las personas de su organización han recibido formación en materia de protección de datos?
¿Las personas de su organización han firmado un compromiso de confidencialidad? En caso afirmativo aporte el modelo utilizado.

Observaciones:

En este punto se harán los comentarios solicitados y en todo caso se aportará cuanta documentación considere la empresa.
