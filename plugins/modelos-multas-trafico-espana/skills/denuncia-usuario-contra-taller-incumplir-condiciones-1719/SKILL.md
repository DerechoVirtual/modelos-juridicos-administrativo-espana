---
name: denuncia-usuario-contra-taller-incumplir-condiciones-1719
description: "Redacta el escrito «Denuncia de un usuario contra un taller por incumplir las condiciones de su autorización» (formulario 1719 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia de un usuario contra un taller por incumplir las condiciones de su autorización

> Formulario 1719 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
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
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…er de reparación de vehículos denominado»; «…, ubicado en»

## Párrafos opcionales (10)

Inclúyelos solo si encajan en los hechos:

- Sustitución innecesaria de piezas que suponga un incremento injustificado de los costos para el usuario o una …
- La utilización de piezas, elementos o conjuntos usados sin autorización, inadecuados, o no marcados y/u homolo…
- La negativa a la realización del presupuesto, o cualquier tipo de reticencia, demora o discriminación en la ad…
- La existencia de cláusulas en resguardos, presupuestos, facturas u otros documentos emitidos por el taller, qu…
- La expedición de facturas en que conste la realización de trabajos que no han sido efectuados o la inclusión d…
- La negativa del taller a devolver al cliente las cantidades percibidas en exceso sobre los precios establecido…
- La falta de "hoja de reclamaciones" o la negativa a facilitar las mismas.…
- La utilización del vehículo para asuntos propios, sin la autorización expresa del propietario, por el taller.…
- La ostentación de referencias a marcas de acuerdo con lo establecido en el artículo 8 del Real Decreto 1457/19…
- El incumplimiento de cualquiera de los preceptos contenidos en las normas reguladoras del funcionamiento de lo…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 19 Real Decreto 1457/1986
- artículo 8 del Real Decreto 1457/1986
- artículo 19 del Real Decreto 1457/1986
- artículos 6, 7 y 8 del Real Decreto 1945/1983

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

### Formulario 1719 · Denuncia de un usuario contra un taller por incumplir las condiciones de su autorización

- Año del modelo: 2004
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 10 párrafos opcionales señalados; 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de denuncia de un usuario de taller de reparación de vehículos a motor frente a este por hechos constitutivos de infracción administrativa, de conformidad con lo establecido en el Real Decreto 1457/1986, de 10 de enero, por el que se regula la actividad industrial y la prestación de servicios en los talleres de reparación de vehículos automóviles, de sus equipos y componentes, en relación con las demás normas complementarias establecidas en la legislación de industria y en la legislación protectora de los derechos de los consumidores y usuarios.

Ilmo. Sr./Sra. [NOMBRE Y APELLIDOS]:

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, DNI número [DNI/NIE],

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.], ante [ÓRGANO] autoridad territorial competente en materia de industria, como mejor procede comparece y

EXPONE

Que en virtud de este escrito formula denuncia contra el taller de reparación de vehículos denominado [COMPLETAR], ubicado en [COMPLETAR], como consecuencia de los siguientes hechos comprobados a raíz del servicio prestado a este usuario en la reparación de su vehículo en el día y la fecha que seguidamente se indica:

Que los hechos denunciados pueden ser constitutivos de infracción administrativa, de conformidad con lo establecido en el artículo 19 Real Decreto 1457/1986, de 10 de enero, por el que se regula la actividad industrial y la prestación de servicios en los talleres de reparación de vehículos automóviles, de sus equipos y componentes, en relación con las disposiciones complementarias establecidas en la legislación de industria y en la legislación protectora de los derechos de los consumidores y usuarios:

[OPCIONAL — incluir si procede]

Sustitución innecesaria de piezas que suponga un incremento injustificado de los costos para el usuario o una posible degradación del vehículo y la imposición al usuario de adquisición de accesorios o piezas complementarias no solicitadas.

[OPCIONAL — incluir si procede]

La utilización de piezas, elementos o conjuntos usados sin autorización, inadecuados, o no marcados y/u homologados, cuando estos últimos requisitos sean preceptivos, así como también, la utilización de uso de elementos, partes, accesorios o líquidos de gobierno del vehículo sin consentimiento expreso del propietario del mismo.

[OPCIONAL — incluir si procede]

La negativa a la realización del presupuesto, o cualquier tipo de reticencia, demora o discriminación en la admisión del vehículo por haber sido exigida la realización del mismo o la realización de presupuestos que no respondan en su descripción o valoración a la realidad de las averías o daños del vehículo, cuando tales presupuestos pueden tener efectos perjudiciales para terceros.

[OPCIONAL — incluir si procede]

La existencia de cláusulas en resguardos, presupuestos, facturas u otros documentos emitidos por el taller, que se opongan a lo establecido en esta disposición y demás disposiciones vigentes.

[OPCIONAL — incluir si procede]

La expedición de facturas en que conste la realización de trabajos que no han sido efectuados o la inclusión de repuestos y accesorios que no han sido aportados a la reparación y, asimismo, la aplicación de precios o márgenes comerciales en cuantía superior a los límites autorizados, establecidos o declarados.

[OPCIONAL — incluir si procede]

La negativa del taller a devolver al cliente las cantidades percibidas en exceso sobre los precios establecidos o sobre los presupuestos aceptados.

[OPCIONAL — incluir si procede]

La falta de "hoja de reclamaciones" o la negativa a facilitar las mismas.

[OPCIONAL — incluir si procede]

La utilización del vehículo para asuntos propios, sin la autorización expresa del propietario, por el taller.

[OPCIONAL — incluir si procede]

La ostentación de referencias a marcas de acuerdo con lo establecido en el artículo 8 del Real Decreto 1457/1986.

[OPCIONAL — incluir si procede]

El incumplimiento de cualquiera de los preceptos contenidos en las normas reguladoras del funcionamiento de los servicios de reparación de vehículos a motor.

En virtud de lo expuesto,

SOLICITA

Que se tenga por presentado este escrito de denuncia, con la documentación que se acompaña y, después de comprobar los hechos y tramitar el expediente que corresponda, se califique la infracción que se haya cometido como muy grave, grave o leve, y se imponga al taller autor de la misma la sanción que proceda teniendo a este denunciante como parte en el citado expediente y, en consecuencia, se le dé traslado de cuantas resoluciones se dicten en el mismo. (1)

En [LUGAR], a [FECHA].

Firma

NOTAS DEL FORMULARIO

(1) Las infracciones a que se refiere el artículo 19 del Real Decreto 1457/1986, se calificarán como leves, graves y muy graves, atendiendo a los criterios establecidos en el artículo 48 del RD Legislativo 1/2007, de 16 de noviembre, por el que se aprueba el texto refundido de la Ley General para la Defensa de los Consumidores y Usuarios y otras leyes complementarias, así como en los artículos 6, 7 y 8 del Real Decreto 1945/1983, de 22 de junio, por el que se regulan las infracciones en materia de defensa del consumidor y de la producción agroalimentaria.
