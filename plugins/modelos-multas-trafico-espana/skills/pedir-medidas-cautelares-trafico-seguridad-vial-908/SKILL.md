---
name: pedir-medidas-cautelares-trafico-seguridad-vial-908
description: "Redacta el escrito «Pedir medidas cautelares en tráfico y seguridad vial» (formulario 908 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir medidas cautelares en tráfico y seguridad vial

> Formulario 0908 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº
- [ ] AÑO
- [ ] FECHA (3 veces)
- [ ] ÓRGANO O PERSONA (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do el control de legalidad instado en la»; «…dad legítima del recurso y en el caso de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 129 LJCA
- artículo 130 LJCA

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

### Formulario 0908 · Pedir medidas cautelares en tráfico y seguridad vial

- Año del modelo: 2009
- Revisión 17-11-2026: 9 campos de relleno marcados en blanco; encabezamiento adaptado a los Tribunales de Instancia (LO 1/2025); 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO CONTENCIOSO-ADMINISTRATIVO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: desde el 31-12-2025 los Juzgados de lo Contencioso-administrativo son Secciones de lo Contencioso-Administrativo de los Tribunales de Instancia (LO 1/2025, DA 1.ª y DT 1.ª; LOPJ arts. 84 y 93). Si el asunto ya está repartido, indicar la plaza, que conserva el número del antiguo Juzgado.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], cuya representación ostento según lo acreditado en el Proceso Contencioso Administrativo núm. [Nº]/[AÑO], por mí interpuesto frente a la resolución de fecha [FECHA] dictada por [ÓRGANO O PERSONA], por lo que desestimado el Recurso de Alzada frente a la Resolución de fecha [FECHA], dictada por [ÓRGANO O PERSONA], ante este Órgano Jurisdiccional comparezco, y como mejor proceda en Derecho, MANIFIESTO QUE:

I.-Según se pone en el artículo 129 LJCA, los interesados en un Proceso Contencioso Administrativo, podrán pedir en cualquier estado del proceso la adaptación de medidas cautelares, no sólo de la suspensión de la eficacia de la actividad impugnada.

II.-Que las mencionadas medidas se acordaron cuando no se afecte una costumbre en interés general y cuando en caso de ejecución de ese acto impugnado antes de su control de legalidad pueda darse la pérdida de la finalidad legítima al Recurso y así lo recoge el artículo 130 LJCA en sus dos párrafos insistiendo el apartado primero de este precepto que en todo caso habrán de valorarse los intereses en conflicto y por todo, no sólo el perjuicio, el interés público sino el interés particular del recurrente debe de ser ponderado.

III.-Aplicando la doctrina anterior al caso, la ejecución del acto impugnado a través del cual se privaría a mi representado del permiso de conducir, le causaría perjuicio de irreparable reparación, ya que para el desempeño de la profesión habitual de conductor de autobuses le es imprescindible la autorización referida.

A nuestro entender, este perjuicio evidente justificaría de por sí la medida de suspensión solicitada, debiendo de añadirse que en nada se perturbaría el interés público si la sanción se ejercitara una vez retirado el control de legalidad instado en la [COMPLETAR] principal.

Además de ejecutarse la resolución, se perdería la finalidad legítima del recurso y en el caso de [COMPLETAR] del mismo el perjuicio sería irreparable al haberse privado a mi mandante de un permiso para conducir.

En su virtud, de todo lo expuesto, al Tribunal

SUPLICO

se tenga por presentado este escrito con los documentos que lo acompañan y en consecuencia se acuerde la medida cautelar de suspensión del acto impugnado en la pieza principal de este Proceso Contencioso Administrativo, sin exigencia de garantía en los particulares referentes a la sanción de multa impuesta.

Es Justicia que se pide en [LUGAR], a [FECHA].

Firma de Abogado y Procurador
