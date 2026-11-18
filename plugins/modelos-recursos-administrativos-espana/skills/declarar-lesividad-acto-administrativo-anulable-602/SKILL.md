---
name: declarar-lesividad-acto-administrativo-anulable-602
description: "Redacta el escrito «Declarar la lesividad de un acto administrativo anulable» (formulario 602 de recursos administrativos, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declarar la lesividad de un acto administrativo anulable

> Formulario 0602 del plugin **Recursos administrativos** · revisado el 17-11-2026.

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

- [ ] FECHA DEL ACUERDO
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… comporta un acto favorable para los Srs»; «…ntrario a derecho por infringir los arts»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0602 · Declarar la lesividad de un acto administrativo anulable

- Año del modelo: 2010
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); 3 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA DEL ACUERDO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Visto el informe del interventor y de la asesoría jurídica y resultando los siguientes,ANTECEDENTESI.- Que en virtud de acuerdo de fecha [FECHA DEL ACUERDO] se dicto el siguiente acto administrativo (trascribir el acto o acuerdo).II.- La anterior resolución, comporta un acto favorable para los Srs [COMPLETAR]. Si bien resulta contrario a derecho por infringir los arts [COMPLETAR], por lo que existiendo terceros interesados se ha procedido a darles un plazo de audiencia por plazo de quince días, que finalizo en fecha [FECHA], siendo evacuado conforme a las alegaciones que obran en el expediente, debidamente informadas por el Sr. Interventor.A los anteriores hechos le resultan de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

Declaración de lesividad de los actos anulables como diligencia preliminar de carácter jurisdiccionalLa Administración puede declarar lesivos para el interés público sus actos y resoluciones favorables a los interesados que incurran en cualquier infracción del Ordenamiento Jurídico, a fin de proceder a su posterior impugnación en vía contencioso-administrativa.

Fuera de los casos previstos en los arts. 217 y 220, la Administración no pueda anular sus propios actos declarativos de derechos. Para conseguir su anulación deberá previamente declararlos lesivos para el interés público e impugnarlos en sede jurisdiccional.

La declaración de lesividad es un acto administrativo con carácter de diligencia preliminar o presupuesto procesal de actividad, la Administración no puede acudir al proceso contencioso-administrativo sin dicha declaración, de no hacerlo así, el recurso contencioso-administrativo se considerará inadmisible. La ausencia de la previa declaración de lesividad, podrá ser opuesta por el demandado como causa de inadmisibilidad e incluso apreciada de oficio por el órgano jurisdiccional.

ProcedimientoEl inicio del procedimiento solo puede hacerse de oficio mediante acuerdo del órgano competente al efecto. El inicio se notifica al interesado, y al órgano competente para tramitar así como aquél que dictó el acto objeto del procedimiento, quien deberá remitir al competente para su tramitación copia cotejada del expediente e informe sobre los antecedentes relevantes para la adecuada resolución. Recibida la documentación, se dará audiencia a los interesados por plazo de quince días a fin de que aleguen y presenten los documentos y justificantes en los que basen su oposición.

Concluido el trámite de audiencia, el órgano competente para tramitar el procedimiento, formulará propuesta de resolución, solicitando informe del Interventor y una vez recibido el informe, remitirá copia del expediente completo al órgano competente para resolver.

La lesividad debe declararse por la propia Administración autora del acto, en concreto, el Pleno de la Corporación, sin que se exija quórum especial (basta la mayoría simple). El acuerdo ha de estar precedido de informe preceptivo del Secretario o, en su caso, de la Asesoría Jurídica y, en defecto de ambos, de un Letrado (art. 54.3 TRRL y 221.1 del ROF) en la medida que no deja de constituir el ejercicio de una acción en defensa de los derechos de la Entidad Local. La jurisprudencia ha evolucionado desde posiciones de mucho rigor hasta el punto de declarar inadmisible el recurso contencioso-administrativo (STS de 5 de noviembre de 1986, RJ 1986 y STSJ de Extremadura, de 25 de octubre de 1998, Rec. 542/92) hasta posiciones más flexibles (STS de 14 de mayo de 2001).

Como requisitos objetivos es de tener en cuenta que la lesividad viene referida a actos administrativos favorables para los interesados y que no sean nulos de pleno derecho, pero que incurran en infracción del Ordenamiento Jurídico; no es necesario que venga referida a intereses económicos, pues ésta se presenta como una garantía de la Administración, si bien no podrá ser declarada lesiva ni impugnarse mediante recurso Contencioso-Administrativo de lesividad, una liquidación que haya sido impugnada en vía económico-administrativa, cuando en tal vía no haya recaído resolución definitiva.

El plazo para la declaración de lesividad, es de cuatro años, contados desde que se notificó.

Transcurrido el plazo de tres meses desde la iniciación del procedimiento, sin que haya recaído declaración de lesividad, se produce la caducidad del mismo.

Una vez declarada la lesividad, la Administración procederá a impugnarla en sede jurisdiccional, en los plazos que resultan del art. 46.5 de la LJ.De la instrucción del expedienteSe ha tramitado el correspondiente expediente administrativo, evacuado el trámite de audiencia y tras los informes de la intervención municipal y la asesoría jurídica con propuesta de resolución favorable a la declaración de lesisividad, siendo competente el Ayuntamiento Pleno en los términos que resultan del art. 110 de la LBRL el Pleno del Ayuntamiento,ACUERDA:1.- Declarar lesivo para el interés público el acto administrativo a que se ha hecho mención en el antecedente I de este acuerdo.2.- Procédase a su impugnación en vía jurisdiccional conforme a lo dispuesto en los arts. 45.4, 19.2, 43 y 46.5 de la Ley Reguladora de la Jurisdicción Contencioso Administrativa
