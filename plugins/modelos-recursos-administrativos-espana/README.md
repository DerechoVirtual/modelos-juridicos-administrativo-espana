# Recursos de alzada, reposición y revisión · España

> Plugin de Claude Code `modelos-recursos-administrativos-espana` · **59 formularios** · área: Administrativo · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para recurrir los actos de cualquier Administración sin ir todavía a los tribunales: recurso de alzada, recurso potestativo de reposición (también contra el silencio), recurso extraordinario de revisión, revisión de oficio de actos nulos y declaración de lesividad.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 59 está al final):

- **Demandas, interposiciones y peticiones iniciales** (3). Por ejemplo: Reposición contra acto de la Administración Local; Interposición del recurso de reposición; Interposición del recurso extraordinario de revisión.
- **Recursos e impugnaciones** (17). Por ejemplo: Reposición contra desestimación por silencio negativo; Alzada impropia; Reposición potestativa genérica.
- **Solicitudes y expedientes** (12). Por ejemplo: Revisión de oficio de actos nulos por la STC sobre el estado de alarma; Revisión de oficio de un acto nulo a instancia del interesado; Nulidad de acto que vulnera derechos susceptibles de amparo constitucional.
- **Escritos de trámite** (3). Por ejemplo: Reposición potestativa por nulidad de resolución que vulnera el derecho a la prueba; Reposición en disciplinario por falta de tipicidad de los hechos probados; Propuesta de resolución en la reposición.
- **Actos y resoluciones de la Administración o del órgano judicial** (19). Por ejemplo: Inadmitir el recurso de alzada contra resolución presunta; Inadmitir el recurso de alzada contra resolución expresa; Resolver el expediente de nulidad de un acto.
- **Contratos, escrituras y documentos** (1). Por ejemplo: Modelo de informe del órgano instructor sobre el recurso de alzada o reposición.
- **Comunicaciones, requerimientos y reclamaciones** (1). Por ejemplo: Aviso de audiencia tras la instrucción del recurso administrativo.
- **Otros** (3). Por ejemplo: Revisión de oficio de disposiciones y actos nulos por iniciativa de la Administración; Declarar la lesividad de un acto administrativo anulable; Audiencia a los interesados para resolver el recurso administrativo.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Recurso de alzada contra una resolución administrativa»
   - «Recurso de reposición contra una desestimación por silencio administrativo»
   - «Solicitud de revisión de oficio de un acto nulo»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-recursos-administrativos-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-recursos-administrativos-espana:inadmitir-recurso-alzada-contra-resolucion-presunta-33`. Los nombres están en la lista de formularios de abajo.

## Qué hace Claude cuando usas un formulario

1. Comprueba que Jurisprudenciator está conectado. Si no lo está, se para y te dice cómo conectarlo: no redacta nada sin él.
   Todos los datos jurídicos del escrito (artículos vigentes, sentencias con su ECLI, convenios, datos registrales) salen de Jurisprudenciator; nunca de memoria.
2. Te pide en una sola tanda los datos del caso (partes, órgano, fechas, importes…). Lo que no sepas queda como hueco visible.
3. Resuelve contigo las opciones que el formulario deja abiertas y decide qué párrafos opcionales entran según los hechos.
4. Aplica las correcciones y avisos de la revisión del 17-11-2026 (reformas legales, órganos, plazos).
5. Comprueba en el BOE, con Jurisprudenciator, cada norma que cita el escrito; si alguna ha cambiado, usa la redacción vigente y te lo dice.
6. Te indica el plazo y ante quién se presenta, y te entrega el escrito en Word con un resumen de lo que queda pendiente.

El resultado es un borrador para que lo revise un profesional antes de presentarlo.

## Antes de empezar

- **Dónde funciona:** en Claude Code, en la terminal o en la pestaña Code de la app de Claude. Desde esta carpeta no se puede instalar en el chat ni en Cowork: para eso habría que publicarlo en un repositorio de GitHub.
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 5.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-recursos-administrativos-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-recursos-administrativos-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-recursos-administrativos-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-recursos-administrativos-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 708 | Reposición contra acto de la Administración Local | 2009 | `reposicion-contra-acto-administracion-local-708` |
| 1300 | Interposición del recurso de reposición | 2006 | `interposicion-recurso-reposicion-1300` |
| 1321 | Interposición del recurso extraordinario de revisión | 2004 | `interposicion-recurso-extraordinario-revision-1321` |

### Recursos e impugnaciones (17)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 74 | Reposición contra desestimación por silencio negativo | 2019 | `reposicion-contra-desestimacion-silencio-negativo-74` |
| 106 | Alzada impropia | 2018 | `alzada-impropia-106` |
| 111 | Reposición potestativa genérica | 2018 | `reposicion-potestativa-generica-111` |
| 122 | Reposición con petición de suspensión, prueba y trámite de audiencia | 2017 | `reposicion-peticion-suspension-prueba-tramite-audiencia-122` |
| 256 | Reposición contra nómina por descuento indebido de haberes | 2016 | `reposicion-contra-nomina-descuento-indebido-haberes-256` |
| 303 | Reposición contra desestimación presunta por silencio administrativo | 2014 | `reposicion-contra-desestimacion-presunta-silencio-303` |
| 367 | Reposición contra resolución notificada por el Tablón Edictal Único | 2013 | `reposicion-contra-resolucion-notificada-tablon-edictal-367` |
| 455 | Reposición contra denegación de admisión en un centro educativo | 2012 | `reposicion-contra-denegacion-admision-centro-educativo-455` |
| 458 | Reposición contra denegación de beca de estudios | 2012 | `reposicion-contra-denegacion-beca-estudios-458` |
| 545 | Reposición potestativa contra corrección de errores | 2011 | `reposicion-potestativa-contra-correccion-errores-545` |
| 548 | Reposición potestativa contra resolución desfavorable sin motivación | 2011 | `reposicion-potestativa-contra-resolucion-desfavorable-548` |
| 572 | Reposición por omitir la audiencia al revocar y caducar una licencia | 2011 | `reposicion-omitir-audiencia-revocar-caducar-licencia-572` |
| 1010 | Alzada contra resolución administrativa | 2008 | `alzada-contra-resolucion-administrativa-1010` |
| 1212 | Reposición contra resolución administrativa | 2008 | `reposicion-contra-resolucion-administrativa-1212` |
| 1295 | Alzada sobre órganos de selección de personal | 2008 | `alzada-sobre-organos-seleccion-personal-1295` |
| 1348 | Alzada o reposición contra la declaración de caducidad del expediente | 2004 | `alzada-reposicion-contra-declaracion-caducidad-1348` |
| 1360 | Alzada contra el acuerdo de medidas provisionales | 2004 | `alzada-contra-acuerdo-medidas-provisionales-1360` |

### Solicitudes y expedientes (12)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 41 | Revisión de oficio de actos nulos por la STC sobre el estado de alarma | 2021 | `revision-oficio-actos-nulos-stc-sobre-estado-alarma-41` |
| 123 | Revisión de oficio de un acto nulo a instancia del interesado | 2017 | `revision-oficio-acto-nulo-instancia-interesado-123` |
| 156 | Nulidad de acto que vulnera derechos susceptibles de amparo constitucional | 2017 | `nulidad-acto-vulnera-derechos-susceptibles-amparo-156` |
| 157 | Nulidad de acto dictado por órgano manifiestamente incompetente | 2017 | `nulidad-acto-dictado-organo-manifiestamente-incompetente-157` |
| 158 | Nulidad de acto dictado prescindiendo totalmente del procedimiento | 2017 | `nulidad-acto-dictado-prescindiendo-totalmente-158` |
| 160 | Nulidad de acto contrario al ordenamiento que concede derechos sin requisitos esenciales | 2017 | `nulidad-acto-contrario-ordenamiento-concede-derechos-sin-160` |
| 161 | Nulidad de acto por causa prevista en una norma con rango de ley | 2017 | `nulidad-acto-causa-prevista-norma-rango-ley-161` |
| 162 | Nulidad de acto de contenido imposible | 2017 | `nulidad-acto-contenido-imposible-162` |
| 571 | Pedir rectificar errores materiales, de hecho y aritméticos | 2011 | `pedir-rectificar-errores-materiales-hecho-aritmeticos-571` |
| 629 | Pedir revocar un acto o resolución administrativa | 2010 | `pedir-revocar-acto-resolucion-administrativa-629` |
| 1410 | Pedir la rectificación de errores materiales o aritméticos | 2004 | `pedir-rectificacion-errores-materiales-aritmeticos-1410` |
| 1415 | Pedir que se declare de oficio la nulidad de pleno derecho | 2004 | `pedir-declare-oficio-nulidad-pleno-derecho-1415` |

### Escritos de trámite (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 335 | Reposición potestativa por nulidad de resolución que vulnera el derecho a la prueba | 2013 | `reposicion-potestativa-nulidad-resolucion-vulnera-335` |
| 553 | Reposición en disciplinario por falta de tipicidad de los hechos probados | 2011 | `reposicion-disciplinario-falta-tipicidad-hechos-probados-553` |
| 1299 | Propuesta de resolución en la reposición | 2006 | `propuesta-resolucion-reposicion-1299` |

### Actos y resoluciones de la Administración o del órgano judicial (19)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 33 | Inadmitir el recurso de alzada contra resolución presunta | 2022 | `inadmitir-recurso-alzada-contra-resolucion-presunta-33` |
| 34 | Inadmitir el recurso de alzada contra resolución expresa | 2022 | `inadmitir-recurso-alzada-contra-resolucion-expresa-34` |
| 124 | Resolver el expediente de nulidad de un acto | 2017 | `resolver-expediente-nulidad-acto-124` |
| 128 | Inadmitir la solicitud de nulidad de disposiciones y actos | 2017 | `inadmitir-solicitud-nulidad-disposiciones-actos-128` |
| 192 | Resolución que inicia el expediente de declaración de lesividad | 2016 | `resolucion-inicia-expediente-declaracion-lesividad-192` |
| 1012 | Resolución del recurso de alzada o reposición | 2008 | `resolucion-recurso-alzada-reposicion-1012` |
| 1073 | Traslado de la alzada o reposición a los demás interesados | 2008 | `traslado-alzada-reposicion-demas-interesados-1073` |
| 1236 | Traslado del recurso de alzada o reposición al resto de interesados | 2008 | `traslado-recurso-alzada-reposicion-resto-interesados-1236` |
| 1296 | Informe sobre ampliar el plazo para resolver la reposición | 2006 | `informe-sobre-ampliar-plazo-resolver-reposicion-1296` |
| 1297 | Resolución que amplía el plazo máximo para resolver la reposición | 2006 | `resolucion-amplia-plazo-maximo-resolver-reposicion-1297` |
| 1298 | Notificación de la ampliación de plazo en la reposición | 2006 | `notificacion-ampliacion-plazo-reposicion-1298` |
| 1302 | Acuerdo de declaración de lesividad | 2006 | `acuerdo-declaracion-lesividad-1302` |
| 1322 | Resolución que declara la nulidad de pleno derecho de un acto administrativo | 2004 | `resolucion-declara-nulidad-pleno-derecho-acto-1322` |
| 1403 | Acuerdo de inadmisión del recurso extraordinario de revisión | 2004 | `acuerdo-inadmision-recurso-extraordinario-revision-1403` |
| 1411 | Acuerdo de rectificación de errores materiales, de hecho o aritméticos | 2004 | `acuerdo-rectificacion-errores-materiales-hecho-1411` |
| 1412 | Resolución de revocación de actos de gravamen o desfavorables | 2004 | `resolucion-revocacion-actos-gravamen-desfavorables-1412` |
| 1414 | Acuerdo de inadmisión de la revisión de oficio de actos nulos | 2004 | `acuerdo-inadmision-revision-oficio-actos-nulos-1414` |
| 1749 | Resolución de revocación de actos de gravamen | 2004 | `resolucion-revocacion-actos-gravamen-1749` |
| 1761 | Resolución que estima total o parcialmente la reposición | 2004 | `resolucion-estima-total-parcialmente-reposicion-1761` |

### Contratos, escrituras y documentos (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1234 | Modelo de informe del órgano instructor sobre el recurso de alzada o reposición | 2008 | `modelo-informe-organo-instructor-sobre-recurso-alzada-1234` |

### Comunicaciones, requerimientos y reclamaciones (1)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1029 | Aviso de audiencia tras la instrucción del recurso administrativo | 2008 | `aviso-audiencia-tras-instruccion-recurso-administrativo-1029` |

### Otros (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 127 | Revisión de oficio de disposiciones y actos nulos por iniciativa de la Administración | 2017 | `revision-oficio-disposiciones-actos-nulos-iniciativa-127` |
| 602 | Declarar la lesividad de un acto administrativo anulable | 2010 | `declarar-lesividad-acto-administrativo-anulable-602` |
| 1759 | Audiencia a los interesados para resolver el recurso administrativo | 2004 | `audiencia-interesados-resolver-recurso-administrativo-1759` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

