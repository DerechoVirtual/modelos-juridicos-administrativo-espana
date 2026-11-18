---
name: alzada-contra-denegar-renovar-residencia-trabajo-informe-709
description: "Redacta el escrito «Alzada contra denegar renovar residencia y trabajo por informe gubernativo desfavorable» (formulario 709 de extranjería, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzada contra denegar renovar residencia y trabajo por informe gubernativo desfavorable

> Formulario 0709 del plugin **Extranjería** · revisado el 17-11-2026.

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

- Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (5 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AL EXCMO. SR. DELEGADO DEL GOBIERNO DE»; «…,,»; «…ctada por el Subdelegado del Gobierno de»; «…da en base a los siguientes fundamentos:»; «…ambién resultan vulnerados los artículos»; «…ctada por el Subdelegado del Gobierno de»

## Elecciones que hay que hacer

- nulidad / anulabilidad

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 80 del Real Decreto 1155/2024
- arts. 78 y 80 del Real Decreto 1155/2024
- art. 24 de la Constitución
- art. 24 de la CE
- Ley Orgánica 4/2000
- Ley 39/2015

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

### Formulario 0709 · Alzada contra denegar renovar residencia y trabajo por informe gubernativo desfavorable

- Año del modelo: 2009
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 16 campos de relleno marcados en blanco
- Avisos de la revisión: Renovación por cuenta ajena: hoy art. 80 RD 1155/2024 (plazos en meses; solo «nueve meses en doce»; denegación por orden público con informe policial motivado, art. 78.1.e).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL EXCMO. SR. DELEGADO DEL GOBIERNO DE [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS] mayor de edad, con DNI n.º [DNI/NIE], y domicilio a efectos de notificaciones sito en [LOCALIDAD],, [COMPLETAR], ante la Delegación del Gobierno de [LOCALIDAD] comparece y como mejor proceda en Derecho, DICE:

Que en virtud de este escrito interpone RECURSO DE ALZADA contra la resolución de fecha [FECHA], dictada por el Subdelegado del Gobierno de [COMPLETAR] por no encontrarla ajustada a Derecho, con fundamento en los siguientes antecedentes y consideraciones jurídicas.

ANTECEDENTES DE HECHO

PRIMERO.- Mediante escrito de fecha [FECHA] presentó solicitud de renovación del permiso de residencia y trabajo ante [ÓRGANO], de conformidad con la legislación sustantiva y el procedimiento aplicable, acompañando la documentación que acreditaba el cumplimiento de los requisitos exigidos en el art. 80 del Real Decreto 1155/2024, de 19 de noviembre, por el que se aprueba el Reglamento de la Ley Orgánica 4/2000, de 11 de enero, sobre derechos y libertades de los extranjeros en España y su integración social.

SEGUNDO.- Con fecha [FECHA], se ha realizado la notificación de la resolución que pone fin al expediente, por la que se deniega la renovación solicitada en base a los siguientes fundamentos: [COMPLETAR], contrariamente a lo solicitado por esta parte.

FUNDAMENTOS DE DERECHO

PRIMERO.- La resolución impugnada en este recurso de alzada es nula de pleno derecho o anulable por cuanto infringe los arts. 78 y 80 del Real Decreto 1155/2024, en relación con el art. 47 o 48 de la Ley 39/2015, y el derecho a la presunción de inocencia del art. 24 de la Constitución, y la jurisprudencia que los interpreta.

La resolución administrativa, que se fundaba en los ya citados arts. 78 y 80 del Real Decreto 1155/2024, se basa en un informe desfavorable de la Comisaría de Extranjería y Documentación para la renovación, al constarle a mi representado dos detenciones policiales.

No obstante, ello no es suficiente para denegar la solicitud, cumplidos que han sido los demás requisitos del art. 80 del Real Decreto 1155/2024, como pone de manifiesto reiterada jurisprudencia que interpreta que la mera existencia de antecedentes policiales no es suficiente para justificar un informe desfavorable, sobre todo cuando el carácter desfavorable del mismo se apoya de forma exclusiva en el hecho de existir proceso judicial en trámite, en el que no consta, al tiempo de dictarse la resolución administrativa denegatoria del permiso en cuestión, que haya recaído sentencia firme, en un sentido u otro. La jurisprudencia interpreta que el informe desfavorable, sin mediar antecedentes penales y una sentencia firme, quebranta la presunción de inocencia establecida por el art. 24 de la CE, por cuanto que se está concediendo a tales antecedentes policiales un valor que no respeta tal presunción de inocencia.

Esta interpretación se recoge, entre otras, en la STS Sala 3.ª, secc. 4.ª, en su sentencia de fecha 5 de marzo de 2003, Rec. 10558/1998, la cual establece que «este Tribunal ha tenido ocasión de pronunciarse reiteradamente en estos últimos tiempos sobre la correcta interpretación del concepto de «orden público» en relación con la denegación de permisos de trabajo y residencia a extranjeros (Sentencias de 8 de febrero de 1999, 4 y 14 de marzo, 18 de abril, 9 de octubre de 2000, 27 de noviembre de 2002 y 17 de febrero de 2003), huyendo tanto de incluirlo en definiciones preconstitucionales y trasnochadas como de la excesiva laxitud que supone el limitarlo a las conductas más graves y directamente atentatorias contra la tranquilidad pública». En el mismo sentido, la STS de la Sala Tercera de 8 de enero de 2004, Rec. 2581/2001, indica que «se aplica también a los extranjeros la garantía que supone el principio de presunción de inocencia».

La resolución administrativa, al desconocer esta jurisprudencia y denegar la renovación en base a antecedentes policiales por detención, vulnera los preceptos invocados, por lo que incurre en causa de nulidad de pleno derecho.

SEGUNDO.- También resultan vulnerados los artículos [COMPLETAR], en los siguientes términos:

Por todo lo expuesto, y de conformidad con las previsiones de los artículos 121 y siguientes de la Ley 39/2015, de 1 de octubre del Procedimiento Administrativo Común de las Administraciones Públicas,

SOLICITO

Que se admita el presente recurso de alzada, junto con los documentos que se acompañan y, previos los trámites legales oportunos, se declare la [ELEGIR: nulidad / anulabilidad] de la resolución de fecha [FECHA], dictada por el Subdelegado del Gobierno de [COMPLETAR] por la cual se deniega la renovación de la autorización de residencia y trabajo, y en su lugar se dicte otro acuerdo por el que se acceda a lo pedido por esta parte en el escrito de iniciación del procedimiento, acordando la renovación solicitada.

En [LUGAR], a [FECHA].

Fdo.:
