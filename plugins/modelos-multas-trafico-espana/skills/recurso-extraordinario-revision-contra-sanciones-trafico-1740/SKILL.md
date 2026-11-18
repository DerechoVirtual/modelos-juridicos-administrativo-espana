---
name: recurso-extraordinario-revision-contra-sanciones-trafico-1740
description: "Redacta el escrito «Recurso extraordinario de revisión contra sanciones de tráfico» (formulario 1740 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso extraordinario de revisión contra sanciones de tráfico

> Formulario 1740 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] FECHA (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DE»; «…la Jefatura de Tráfico (or: Alcaldía) de»

## Elecciones que hay que hacer

- JEFATURA DE TRÁFICO / ALCALDÍA

## Párrafos opcionales (4)

Inclúyelos solo si encajan en los hechos:

- Que al dictarlo se ha incurrido en error de hecho, que resulta de los propios documentos incorporados al exped…
- Que han aparecido o aportado documentos de valor esencial para la resolución del asunto que, aunque sean poste…
- Que en la resolución han influido esencialmente documentos o testimonios declarados falsos por sentencia judic…
- Que la resolución se ha dictado como consecuencia de prevaricación, cohecho, violencia, maquinación fraudulent…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 125 LPACAP
- artículo 125 Ley 39/2015
- artículos 125 y 126 de la Ley 39/2015
- arts. 125 y 126 LPACAP
- art. 125 LPACAP
- art. 106 LPACAP
- art. 125.3 LPACAP
- art. 126 LPACAP

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

### Formulario 1740 · Recurso extraordinario de revisión contra sanciones de tráfico

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 1 desplegables convertidos en elección en blanco; 4 párrafos opcionales señalados; 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito de interposición del recurso administrativo extraordinario de revisión por la concurrencia, en la resolución sancionadora en materia de tráfico, de alguno de los motivos previstos en el artículo 125 LPACAP. Actualizado a TR LTCVMSV y a Leyes 39 y 40/2015, de 1 de octubre.

A LA [ELEGIR: JEFATURA DE TRÁFICO / ALCALDÍA] DE [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE], con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA] y con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], CP [C.P.], ante la Jefatura de Tráfico (or: Alcaldía) de [COMPLETAR], como mejor proceda comparece y

DICE:

Que por medio de este escrito interpone RECURSO EXTRAORDINARIO DE REVISIÓN contra la resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], que pone fin a la vía administrativa, y que se fundamenta en el siguiente motivo de revisión de conformidad con las causas establecidas en el artículo 125 Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (1):

[OPCIONAL — incluir si procede]

Que al dictarlo se ha incurrido en error de hecho, que resulta de los propios documentos incorporados al expediente.

[OPCIONAL — incluir si procede]

Que han aparecido o aportado documentos de valor esencial para la resolución del asunto que, aunque sean posteriores, evidencian el error de la resolución recurrida.

[OPCIONAL — incluir si procede]

Que en la resolución han influido esencialmente documentos o testimonios declarados falsos por sentencia judicial firme anterior o posterior a aquella resolución.

[OPCIONAL — incluir si procede]

Que la resolución se ha dictado como consecuencia de prevaricación, cohecho, violencia, maquinación fraudulenta u otra conducta punible, y se haya declarado así en virtud de sentencia judicial firme.

Que la causa de revisión invocada concurre en la resolución sancionadora en materia de tráfico, y así se acredita, mediante los siguientes medios de prueba:

Por lo expuesto, y de conformidad con las previsiones de los artículos 125 y 126 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas,

SOLICITA:

Que se admita a trámite este escrito de interposición de recurso extraordinario de revisión y se dicte resolución por la que se declare la nulidad del acto administrativo impugnado, declarando no haber lugar a la exigencia de responsabilidad como consecuencia del expediente sancionador referenciado.

En [LUGAR], a [FECHA].

Firmado:

NOTAS DEL FORMULARIO

(1) Los arts. 125 y 126 LPACAP regulan un recurso extraordinario de revisión que sólo procede en supuestos y por motivos tasados. Constituye un remedio excepcional frente a ciertos actos que han ganado firmeza, pero de cuya legalidad se duda en base a datos o acaecimientos sobrevenidos con posterioridad al momento en que fueron dictados. La simple contemplación de los cuatro motivos del art. 125 LPACAP, pone de inmediato la falta de rigor técnico de que adolece la actual configuración del recurso, que, en su conjunto, constituye una duplicación innecesaria de la acción de nulidad del art. 106 LPACAP. Así resulta, por lo demás, de lo dispuesto en el art. 125.3 LPACAP, según el cual "lo establecido en el presente artículo no perjudica en derecho de los interesados a formular la solicitud y la instancia a que se refieren los arts. 106 y 109.2 de la presente Ley, ni su derecho a que las mismas se sustancien y resuelvan". El plazo para interponerlo es de cuatro años en caso de error de hecho y de tres meses en los demás casos y el plazo para resolverlo también es de tres meses. El órgano al que corresponde conocer del recurso extraordinario de revisión debe pronunciarse no sólo sobre la procedencia del recurso, sino también, en su caso, sobre el fondo de la cuestión resuelta por el acto recurrido. Transcurrido el plazo de tres meses desde la interposición del recurso extraordinario de revisión sin que recaiga resolución, se entenderá desestimado, quedando expedita la vía jurisdiccional contencioso-administrativa (art. 126 LPACAP).
