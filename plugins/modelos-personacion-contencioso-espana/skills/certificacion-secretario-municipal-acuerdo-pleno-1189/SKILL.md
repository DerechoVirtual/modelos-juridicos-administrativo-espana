---
name: certificacion-secretario-municipal-acuerdo-pleno-1189
description: "Redacta el escrito «Certificación del secretario municipal: acuerdo del pleno de ejercitar acciones (Galicia)» (formulario 1189 de órgano y postulación en el contencioso-administrativo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificación del secretario municipal: acuerdo del pleno de ejercitar acciones (Galicia)

> Formulario 1189 del plugin **Órgano y postulación en el contencioso-administrativo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (3 veces)
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] ACTO O RESOLUCIÓN
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ada en estas dependencias municipales el»; «… judiciales ante el orden jurisdiccional»; «…por»; «…. Asimismo designa a»; «…, Procurador de los Tribunales»; «…rocedente la interposición de recurso de»; «…efectos, por lo que expido la presente a»

## Elecciones que hay que hacer

- Secretario/a / Secretario/a General del Pleno (solo municipios de gran población, art. 122 LBRL)

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 64.2.l) de la Ley 5/1997
- art. 22.2.j) de la Ley 7/1985
- artículo 220 de la Ley 5/1997
- art. 220 del Real Decreto 2568/1986
- art. 221 del Real Decreto 2568/1986
- art. 54.3 del Real Decreto Legislativo 781/1986

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

### Formulario 1189 · Certificación del secretario municipal: acuerdo del pleno de ejercitar acciones (Galicia)

- Año del modelo: 2008
- Revisión 17-11-2026: 17 campos de relleno marcados en blanco; cargo del fedatario municipal revisado: con carácter general es el Secretario/a de la Corporación (RD 128/2018; LBRL 92 bis); «Secretario General del Pleno» solo en municipios de gran población; título corregido: el fedatario de una entidad local es su Secretario/a, no el Letrado de la Administración de Justicia

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

CERTIFICACIÓN

[NOMBRE Y APELLIDOS], [ELEGIR: Secretario/a / Secretario/a General del Pleno (solo municipios de gran población, art. 122 LBRL)] del Excmo. Ayuntamiento de [LOCALIDAD].

CERTIFICO:

Que de los antecedentes obrantes a mi cargo, en la Secretaría de este Consistorio aparece un Acuerdo Plenario, dictado en fecha [FECHA] conforme a las atribuciones conferidas por el art. 64.2.l) de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, y art. 22.2.j) de la Ley 7/1985, de Bases de Régimen Local, según los cuales corresponde al pleno municipal el «ejercicio de las acciones administrativas y judiciales», que resuelve de conformidad con el dictamen previo al ejercicio de acciones, del tenor siguiente:

PRIMERO.- Visto que en fecha [FECHA], con entrada en estas dependencias municipales el [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS] formulaba requerimiento a esta Corporación Local al amparo del artículo 220 de la Ley 5/1997, de 22 de julio, de Administración Local de Galicia, art. 68 de la Ley estatal 7/1985, de 2 de abril, de Bases de Régimen Local, y art. 220 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de los Entes Locales, para que se procediera al inicio de acciones judiciales ante el orden jurisdiccional [COMPLETAR] para la defensa de los bienes o derechos de titularidad local, consistentes en [DESCRIBIR].

SEGUNDO.- Visto el dictamen previo al ejercicio de acciones emitido en fecha [FECHA] por [COMPLETAR] al amparo del art. 221 del Real Decreto 2568/1986, de 28 de noviembre, Reglamento de Organización, Funcionamiento y Régimen Jurídico de las Entidades Locales, y art. 54.3 del Real Decreto Legislativo 781/1986, de 18 de abril, Texto Refundido de las Disposiciones Vigentes de Régimen Local, dictamen que con claridad refleja la conveniencia y utilidad del ejercicio de dichas acciones.

El Pleno Consistorial ha

DISPUESTO

que por este Excmo. Ayuntamiento se inicien acciones para ante [ÓRGANO], contra [ACTO O RESOLUCIÓN]. Asimismo designa a [COMPLETAR], Procurador de los Tribunales [COMPLETAR], para que ostente la representación en juicio de esta Consistorio, bajo la dirección técnica del Letrado municipal, como también

HA DISPUESTO

que en caso de ser procedente la interposición de recurso de [COMPLETAR] queden facultados, tanto el Procurador de esta Corporación en [LOCALIDAD] como del Letrado Municipal, para proseguir el procedimiento hasta la obtención de sentencia firme.

Lo que hago constar para su notificación y que surta sus efectos, por lo que expido la presente a [COMPLETAR] con el visto bueno del Alcalde/Alcaldesa.

Vº Bº

El/La Alcalde/Alcaldesa:
