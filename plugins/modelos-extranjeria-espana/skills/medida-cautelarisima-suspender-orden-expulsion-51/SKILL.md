---
name: medida-cautelarisima-suspender-orden-expulsion-51
description: "Redacta el escrito «Medida cautelarísima para suspender la orden de expulsión de un extranjero» (formulario 51 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medida cautelarísima para suspender la orden de expulsión de un extranjero

> Formulario 0051 del plugin **Extranjería** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] COLEGIO
- [ ] DIRECCIÓN ELECTRÓNICA
- [ ] LOCALIDAD
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] ÓRGANO
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…con domicilio en [LOCALIDAD],»; «…rezco y DIGO: Primero.- Que con fecha de»; «…, por la comisión de infracción de»; «…, tipificada en el artículo»; «… realidad, especialmente en razón de que»; «…ereses generales o de tercero por cuanto»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de [COLEGIO]…
- D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de D./Dña. […

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 135 LJCA
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

### Formulario 0051 · Medida cautelarísima para suspender la orden de expulsión de un extranjero

- Año del modelo: 2021
- Revisión 17-11-2026: 2 párrafos opcionales señalados; 21 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

[OPCIONAL — incluir si procede]

D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de [COLEGIO]

con domicilio electrónico a efectos de notificaciones [DIRECCIÓN ELECTRÓNICA]

con domicilio en [LOCALIDAD], [COMPLETAR], en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS]

[OPCIONAL — incluir si procede]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], como tengo acreditado en autos de recurso contencioso-administrativo número [Nº DE PROCEDIMIENTO]/[AÑO], ante [ÓRGANO], comparezco y

DIGO:

Primero.- Que con fecha de [COMPLETAR] se ha dictado por [ÓRGANO O PERSONA] orden de expulsión contra mi mandante, D./Dña. [NOMBRE Y APELLIDOS], por la comisión de infracción de [COMPLETAR], tipificada en el artículo [COMPLETAR] de la Ley Orgánica 4/2000, de 11 de enero, sobre Derechos y Libertades de los Extranjeros en España y su Integración Social.

Segundo.- Que al amparo del art. 135 y concordantes LJCA vengo a interesar la medida cautelar de suspensión de la ejecución del acto administrativo recurrido lo que fundamento en las siguientes

ALEGACIONES

Primera.- La adopción de la medida cautelarísima "in audita altera parte" establecida en el art. 135 LJCA requiere la concurrencia de circunstancias de especial o extraordinaria urgencia.

Segunda.- En el caso que nos ocupa se desprende con toda claridad la necesidad de acordar la suspensión de la ejecución del acto administrativo ya que la no suspensión pudiera hacer perder su finalidad legítima al recurso a interponer contra dicho acto, sin que una eventual estimación posterior en sentencia pudiera mitigar esa realidad, especialmente en razón de que [COMPLETAR].

Tercera.- Por otra parte la suspensión de la ejecución pretendida no ocasiona perjuicios a la Administración y de adoptarse la medida cautelar no se produciría tampoco ningún perjuicio o perturbación grave de los intereses generales o de tercero por cuanto [COMPLETAR].

Por el contrario, la ejecución inmediata de la orden le ocasionaría a mi mandante los siguientes perjuicios, todos ellos de difícil, si no imposible, reparación.

Cuarta.- Además, concurren en este caso los siguientes datos que ponen de manifiesto la aplicación de criterios de "fumus boni iuris" o apariencia del buen derecho

Quinta.- En atención a todas las circunstancias objetivas y subjetivas que concurren en el presente caso, entendemos que ha de adoptarse la medida cautelar solicitada.

En su virtud,

SUPLICO AL TRIBUNAL

que tenga por hechas las anteriores alegaciones junto con los documentos que se acompañan, se sirva a admitir todos ellos, y previos los trámites legales acuerde la adopción de la MEDIDA CAUTELAR SOLICITADA, consistente en la SUSPENSIÓN DE LA RESOLUCIÓN de fecha [FECHA] dictada por [ÓRGANO O PERSONA], por la que se impone a D./Dña. [NOMBRE Y APELLIDOS] la sanción de expulsión del territorio español de mi mandante.

Es Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
