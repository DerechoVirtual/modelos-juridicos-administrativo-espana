---
name: reclamar-administracion-accidente-circulacion-vehiculo-213
description: "Redacta el escrito «Reclamar a la Administración por accidente de circulación con vehículo de su propiedad» (formulario 213 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamar a la Administración por accidente de circulación con vehículo de su propiedad

> Formulario 0213 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] PROVINCIA
- [ ] C.P.
- [ ] FECHA (2 veces)
- [ ] MATRÍCULA (3 veces)
- [ ] IMPORTE (5 veces)
- [ ] Nº (2 veces)
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA ADMINISTRACIÓN PÚBLICA»; «…, de la localidad»; «…e los vehículos siguientes: — El turismo»; «…l concertado con la compañía aseguradora»; «…hículos Automóviles como DOCUMENTOS NÚMS»; «…. — El turismo de mi propiedad»; «…ente se produjo de la siguiente forma: —»; «…latados resultan debidamente acreditados»; «…OCUMENTOS respectivamente numerados como»; «…días, de los cuales»; «…alario, padezco las siguientes secuelas:»; «…ñan los siguientes justificantes médicos»; …

## Elecciones que hay que hacer

- de la Administración pública a la que me dirijo / de un particular

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- I. OTROSÍ DIGO…
- II. OTROSÍ DIGO…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 66 y 67 de la Ley 39/2015

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

### Formulario 0213 · Reclamar a la Administración por accidente de circulación con vehículo de su propiedad

- Año del modelo: 2016
- Revisión 17-11-2026: 1 llamadas a nota sin texto retiradas; 1 desplegables convertidos en elección en blanco; 2 párrafos opcionales señalados; 33 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA ADMINISTRACIÓN PÚBLICA [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS],

con domicilio electrónico a efectos de notificaciones

con domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], provincia [PROVINCIA], C.P [C.P.], con Documento Nacional de Identidad número [NÚMERO], comparezco en nombre y representación propia y, como mejor proceda en Derecho, y con las formalidades previstas en los artículos 66 y 67 de la Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas (en lo sucesivo, LPACAP) para los procedimientos de RESPONSABILIDAD PATRIMONIAL, formulo la siguiente:

SOLICITUD

Primero. Descripción de los hechos y relación de causalidad entre los daños producidos y el funcionamiento del servicio público

1.1.- En fecha [FECHA] se produjo un accidente de circulación en la calle [CALLE], de la localidad [COMPLETAR], entre los vehículos siguientes:

— El turismo [COMPLETAR] matrícula [MATRÍCULA], propiedad [ELEGIR: de la Administración pública a la que me dirijo / de un particular], y conducido por D./Dña. [NOMBRE Y APELLIDOS], que en esa fecha tenía contrato de seguro de responsabilidad civil concertado con la compañía aseguradora [COMPLETAR]. Acompaño certificado de Tráfico y certificado emitido por el Fichero Informativo de Vehículos Automóviles como DOCUMENTOS NÚMS [COMPLETAR].
— El turismo de mi propiedad [COMPLETAR] matrícula [MATRÍCULA], conducido por quien suscribe en la fecha de autos. Acompaño certificado de Tráfico como DOCUMENTO N.º [NÚMERO].

1.2. El accidente se produjo de la siguiente forma:

— [COMPLETAR].
— Los hechos relatados resultan debidamente acreditados [COMPLETAR]. Acompaño los referidos DOCUMENTOS respectivamente numerados como [COMPLETAR]

Segundo. Daños y perjuicios ocasionados y evaluación económica de la responsabilidad patrimonial

Como consecuencia de los hechos descritos, se le han ocasionado a quien suscribe los siguientes daños:

Daños materiales

en el vehículo matrícula [MATRÍCULA] que, debidamente peritados, fueron reparados, ascendiendo el importe de la factura a la suma de [IMPORTE] euros Euros. Adjunto justificantes (p.e., peritaje, factura de reparación y recibo) como DOCUMENTOS NÚMS

Daños corporales:

— Como consecuencia de la colisión descrita, sufrí las siguientes lesiones: Actualmente, y tras un período de baja de [Nº] días, de los cuales [COMPLETAR] precisé reposo hospitalario, padezco las siguientes secuelas: [COMPLETAR]. En consecuencia, la cantidad que se reclama por este concepto es la siguiente:

1. días de baja, de los cuales [Nº] días precisé reposo hospitalario. A razón de [IMPORTE] euros los primeros, y [IMPORTE] euros los segundos, suponen un total de [IMPORTE] euros.
2. Secuelas:
3. Gastos médicos:

Se acompañan los siguientes justificantes médicos [COMPLETAR] como DOCUMENTOS NÚMS [COMPLETAR]

Total reclamado:euros.

En su virtud,

SOLICITO

Que, teniendo por presentado este escrito, se sirva admitirlo, tenga por formulada reclamación por responsabilidad patrimonial contra la Administración pública a la que me dirijo y, previos los trámites legales oportunos, acuerde indemnizarme en la cantidad de [IMPORTE] euros.

[OPCIONAL — incluir si procede]

I. OTROSÍ DIGO

que, para mi defensa y representación, designo al Letrado (D./Dña. [NOMBRE Y APELLIDOS]).

[OPCIONAL — incluir si procede]

II. OTROSÍ DIGO

que, a fin de acreditar los hechos ocasionados, los daños causados y la relación de causalidad entre los daños y el funcionamiento del servicio público, solicito la práctica de la siguiente prueba:

En [LUGAR], a [FECHA].

Firma:
