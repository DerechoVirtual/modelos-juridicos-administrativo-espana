---
name: convenio-entre-administracion-entidad-privada-fomentar-1708
description: "Redacta el escrito «Convenio entre una Administración y una entidad privada para fomentar la seguridad vial» (formulario 1708 de multas y expedientes de tráfico, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio entre una Administración y una entidad privada para fomentar la seguridad vial

> Formulario 1708 del plugin **Multas y expedientes de tráfico** · revisado el 17-11-2026.

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
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (3 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…,»; «… el presente acuerdo MANIFIESTAN: Que la»; «…Ministerio de Interior con el número RNA»; «… objeto regular la colaboración entre la»; «… de la siguiente manera: El Instituto de»; «…nes se efectuarán en la Revista titulada»; «…perteneciente al grupo editorial»; «…Las actividades que se desarrollen entre»; «…igencia hasta el 31 de diciembre del año»

## Elecciones que hay que hacer

- el / la

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

### Formulario 1708 · Convenio entre una Administración y una entidad privada para fomentar la seguridad vial

- Año del modelo: 2004
- Revisión 17-11-2026: 1 desplegables convertidos en elección en blanco; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de Convenio de colaboración entre la Administración Pública competente en materia de tráfico y una entidad privada para llevar a cabo conjuntamente actividades de investigación, estudio, divulgación y fomento de las ciencias y técnicas vinculadas a la seguridad vial en todos sus ámbitos.

REUNIDOS

De una parte, [ELEGIR: el / la]

Excelentísimo
Excelentísima

Señor
Sra.
 D./Dña. [NOMBRE Y APELLIDOS], [COMPLETAR], y de otra parte, D./Dña. [NOMBRE Y APELLIDOS], en nombre y representación de [NOMBRE DEL REPRESENTADO/A].

Ambas partes en la representación que ostentan y en ejercicio de las atribuciones que les están conferidas, reconociéndose capacidad para formalizar el presente acuerdo

MANIFIESTAN:

Que la [COMPLETAR] considera necesario afrontar el estudio científico y profesional del fenómeno de la circulación, ya que, por el riesgo y la siniestralidad que genera, ha llegado a ser la primera causa de mortalidad para el segmento de población menor de 35 años y además ocasiona un coste estimado entre seis y doce mil millones de euros anuales.

Que la Agencia Española para la Seguridad Vial es una entidad asociativa, con personalidad jurídica propia, inscrita en el Ministerio de Interior con el número RNA [COMPLETAR], que tiene entre sus fines la colaboración con la Universidad y otras Administraciones Públicas para la investigación, estudio, divulgación y fomento de las ciencias y técnicas vinculadas a la seguridad vial en todos sus ámbitos, jurídicos y técnicos, con especial incidencia en la ordenación del tráfico rodado y sus consecuencias.

Que tanto la Universidad como la Agencia Española de Seguridad Vial consideran que sólo con el estudio de los problemas que genera el tráfico y la circulación de vehículos a motor, se pueden ofrecer soluciones que sirvan al propósito de reducir la accidentalidad y alcanzar mayores cotas de perfeccionamiento profesional en el sistema de empresas y servicios que desarrollan su trabajo en esta materia.

Que, para afrontar este problema, fundamentalmente en lo que se refiere a la necesidad de intercambio científico y profesional sobre las consecuencias de unas normas en constante cambio y reelaboración y que afectan a todos los ciudadanos, ambas entidades consideran oportuno suscribir el presente convenio de colaboración que se regirá por las siguientes

CLÁUSULAS:

Primera

El presente convenio tiene por objeto regular la colaboración entre la [COMPLETAR] y la Universidad de [LOCALIDAD], en orden a realizar actividades de investigación, estudio, divulgación y fomento de las ciencias y técnicas vinculadas a la seguridad vial en todos sus ámbitos, ya sean jurídicos, médico-legales, psicológicos, y en general, todos los saberes que contribuyan al perfeccionamiento de la ordenación del tráfico rodado.

Segunda

A los efectos prevenidos en el apartado anterior los compromisos de colaboración y las aportaciones económicas de las partes se concretan de la siguiente manera:

El Instituto de [COMPLETAR], a través de la Agencia para la Seguridad Vial, facilitará la publicación y remuneración de cuantos trabajos de investigación sean programados conjuntamente, realizados profesores de la Universidad.

Las publicaciones se efectuarán en la Revista titulada [COMPLETAR] perteneciente al grupo editorial [COMPLETAR], quien se hará cargo de las retribuciones en la forma establecida para las publicaciones del grupo.

Se consideran áreas preferentes de investigación las relacionadas con la Medicina Legal y el Derecho de la Circulación en sus aspectos civiles, administrativos, penales y procesales.

Con carácter anual se celebrará un Seminario o Congreso sobre los problemas actuales del tráfico, que será patrocinado por las partes firmantes pudiendo quedar delegada la organización y secretaría técnica del evento a otras entidades dependientes o vinculadas a la Universidad.

Se establecerá, también con carácter anual, un premio al mejor trabajo de investigación sobre seguridad vial, que verse sobre los aspectos legales, médicos o técnicos que inciden sobre esta materia, y que será objeto de publicación y retribución a través de los medios asignados al Instituto de Tráfico y Seguridad Vial o en la forma que de común acuerdo se establezca.

Las actividades que se desarrollen entre [COMPLETAR] y la Universidad de no excluyen la participación de otras entidades y centros de coordinación de la investigación o de práctica jurídica y medicinal legal o cualesquiera otros dependientes o vinculados a la Universidad de [LOCALIDAD] o la Administración Pública.

Tercera

La Agencia para la Seguridad Vial, sin perder su autonomía orgánica y funcional, queda adscrita a la Universidad de [LOCALIDAD], en todo lo que se refiere a la dirección y coordinación científica de sus actividades, debiendo recaer en profesores de esta Universidad la titularidad de los cargos directivos del Instituto que conlleven cualquier género de responsabilidad en estas materias.

Cuarta

Para unificar la imagen institucional y facilitar el intercambio de conocimientos se facilitará un espacio para la Asociación en la página web de la Universidad, de modo que a través de este medio se centralice la información de las actividades del Instituto y la información que se ponga a disposición de los investigadores para la realización de los trabajos que quieran realizarse al amparo del presente convenio.

Quinta

Para el seguimiento de las actuaciones previstas se establece una Comisión integrada por dos representantes de cada una de las partes firmantes del Convenio y que estará encargada de resolver cuantas dudas pudieran plantearse sobre su cumplimiento y efectos.

Sexta

El presente Convenio tendrá vigencia hasta el 31 de diciembre del año [COMPLETAR] y podrá resolverse por alguna de las siguientes causas: Expiración de su vigencia, incumplimiento de su contenido y mutuo acuerdo.

Séptima

El presente Convenio tiene naturaleza administrativa, queda excluido de lo previsto en la legislación de contratos públicos, y el conocimiento de todas las cuestiones litigiosas que puedan surgir en torno a su interpretación, modificación, resolución y efectos correspondientes, corresponderá a la Jurisdicción Contencioso-Administrativa.

Y para que así conste firman el presente Convenio de Colaboración, por triplicado ejemplar en el lugar y fecha indicados al principio.

En [LUGAR], a [FECHA].

Firma
