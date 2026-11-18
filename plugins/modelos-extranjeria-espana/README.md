# Extranjería: arraigo, residencia, nacionalidad y expulsiones · España

> Plugin de Claude Code `modelos-extranjeria-espana` · **97 formularios** · área: Administrativo (incluye 6 formularios de Laboral, marcados «(Laboral)» y 1 formulario de Civil, marcado «(Civil)») · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para tramitar y recurrir expedientes de extranjería: solicitudes de residencia y trabajo, arraigo, reagrupación familiar, renovaciones, tarjetas de familiar de ciudadano de la UE, nacionalidad y asilo, y la defensa frente a denegaciones y expulsiones, en vía administrativa y en el contencioso. Incluye 6 formularios de Laboral (autorizaciones de trabajo, larga duración, expulsión y visados).

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 97 está al final):

- **Demandas, interposiciones y peticiones iniciales** (27). Por ejemplo: Contencioso contra la denegación del certificado de insuficiencia de demandantes de empleo; Contencioso por denegar renovar residencia y trabajo por cuenta ajena (antecedentes policiales); Contencioso contra el silencio en el certificado de insuficiencia de demandantes de empleo.
- **Recursos e impugnaciones** (19). Por ejemplo: Alzada contra denegar la tarjeta de residencia temporal de familiar de ciudadano UE; Reposición contra denegación de residencia permanente (silencio positivo); Alzada contra denegación de entrada en España con carta de invitación.
- **Contestaciones, oposiciones y alegaciones** (6). Por ejemplo: Alegaciones en expulsión de extranjero condenado a pena de prisión; Alegaciones en expulsión por procedimiento preferente; Alegaciones en expulsión por arraigo familiar.
- **Solicitudes y expedientes** (16). Por ejemplo: Medida cautelarísima para suspender la orden de expulsión de un extranjero; Pedir certificado escolar para obtener la residencia legal; Revocar la resolución de expulsión: solicitud.
- **Escritos de trámite** (5). Por ejemplo: Conclusiones: nacionalidad denegada por falta de integración; Solicitar el retorno voluntario; Otrosí de demanda pidiendo suspender la expulsión.
- **Actos y resoluciones de la Administración o del órgano judicial** (4). Por ejemplo: Certificado de silencio positivo en la renovación de residencia y trabajo; Silencio positivo en la modificación de autorización: certificado; Solicitar autorización de residencia comunitaria.
- **Contratos, escrituras y documentos** (7). Por ejemplo: Designar representante para tramitar visados; Mandato con poder de representación para tramitar la nacionalidad española; Convenio de colaboración para estancia en España por voluntariado.
- **Comunicaciones, requerimientos y reclamaciones** (2). Por ejemplo: Frente a la denegación de visado de reagrupación familiar comunitaria; Denuncia de un hecho relevante en extranjería.
- **Otros** (11). Por ejemplo: Memoria de actividad de la empresa y perfil del puesto para desplazar y contratar extranjeros; Revocar la expulsión por matrimonio con español; Silencio positivo en la residencia de larga duración: certificado.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Recurso de reposición contra la denegación de una residencia temporal por arraigo»
   - «Alegaciones de defensa en un expediente de expulsión preferente»
   - «Recurso contencioso ante la Audiencia Nacional por el silencio en una solicitud de nacionalidad»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-extranjeria-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-extranjeria-espana:contencioso-contra-denegacion-certificado-insuficiencia-1`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 8.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-extranjeria-espana@plugins-dv`).

## Instalación

Solo la primera vez, añade el catálogo de plugins (sirve para todos). Cambia la ruta por la carpeta donde esté el catálogo (la que contiene `.claude-plugin`); si es un zip, descomprímelo antes en una ruta corta, porque hay nombres de archivo largos:

```bash
claude plugin marketplace add "C:\plugins-dv"
```

Después, instala este plugin:

```bash
claude plugin install modelos-extranjeria-espana@plugins-dv
```

En la pestaña Code de la app de Claude también puedes pedírselo a Claude con esas palabras: «instala el plugin modelos-extranjeria-espana del catálogo plugins-dv que está en C:\plugins-dv». Al terminar, abre una conversación nueva para que aparezcan sus skills.

## Lista de formularios

Para usar uno directamente: `/modelos-extranjeria-espana:<skill>`.

### Demandas, interposiciones y peticiones iniciales (27)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1 | Contencioso contra la denegación del certificado de insuficiencia de demandantes de empleo | 2025 | `contencioso-contra-denegacion-certificado-insuficiencia-1` |
| 3 | Contencioso por denegar renovar residencia y trabajo por cuenta ajena (antecedentes policiales) | 2025 | `contencioso-denegar-renovar-residencia-trabajo-cuenta-3` |
| 4 | Contencioso contra el silencio en el certificado de insuficiencia de demandantes de empleo | 2025 | `contencioso-contra-silencio-certificado-insuficiencia-4` |
| 43 | Demanda contra denegar la tarjeta de residencia permanente de familiar de ciudadano UE | 2021 | `demanda-contra-denegar-tarjeta-residencia-permanente-43` |
| 79 | Contencioso ante la Audiencia Nacional por silencio negativo en nacionalidad | 2019 | `contencioso-ante-audiencia-nacional-silencio-negativo-79` |
| 80 | Demanda contra la expulsión del art. 57.2 LO 4/2000 | 2019 | `demanda-contra-expulsion-art-57-2-lo-4-2000-80` |
| 191 | Demanda contra denegar visados en régimen comunitario | 2016 | `demanda-contra-denegar-visados-regimen-comunitario-191` |
| 279 | Demanda contra la denegación de visado | 2016 | `demanda-contra-denegacion-visado-279` |
| 283 | Demanda en un expediente de expulsión | 2015 | `demanda-expediente-expulsion-283` |
| 294 | Demanda contra denegar la nacionalidad por falta de integración | 2014 | `demanda-contra-denegar-nacionalidad-falta-integracion-294` |
| 301 | Demanda contra visado de reagrupación familiar denegado (modelo 1) | 2014 | `demanda-contra-visado-reagrupacion-familiar-denegado-301` |
| 327 | Interponer contencioso contra la denegación de nacionalidad | 2013 | `interponer-contencioso-contra-denegacion-nacionalidad-327` |
| 340 | Demanda para obtener la nacionalidad por opción | 2013 | `demanda-obtener-nacionalidad-opcion-340` |
| 341 | Contencioso para obtener la nacionalidad por opción | 2013 | `contencioso-obtener-nacionalidad-opcion-341` |
| 363 | Demanda abreviada contra la denegación de autorización de trabajo y residencia | 2013 | `demanda-abreviada-contra-denegacion-autorizacion-trabajo-363` |
| 364 | Contencioso abreviado contra resolución de expulsión | 2013 | `contencioso-abreviado-contra-resolucion-expulsion-364` |
| 365 | Contencioso ante la Audiencia Nacional en nacionalidad (procedimiento ordinario) | 2013 | `contencioso-ante-audiencia-nacional-nacionalidad-365` |
| 366 | Demanda contra decreto de expulsión | 2013 | `demanda-contra-decreto-expulsion-366` |
| 377 | Demanda contra visado de reagrupación familiar denegado (modelo 2) | 2013 | `demanda-contra-visado-reagrupacion-familiar-denegado-377` |
| 385 | Contencioso con medida cautelarísima por internamiento | 2013 | `contencioso-medida-cautelarisima-internamiento-385` |
| 387 | Demanda de nacionalidad: acreditar buena conducta cívica | 2013 | `demanda-nacionalidad-acreditar-buena-conducta-civica-387` |
| 389 | Contencioso contra la denegación de entrada | 2013 | `contencioso-contra-denegacion-entrada-389` |
| 710 | Alzada contra la denegación de entrada y retorno del servicio fronterizo | 2009 | `alzada-contra-denegacion-entrada-retorno-servicio-710` |
| 713 | Demanda abreviada en extranjería: autorización de residencia y trabajo | 2009 | `demanda-abreviada-extranjeria-autorizacion-residencia-713` |
| 963 | Contencioso contra la inadmisión de residencia y trabajo en la regularización extraordinaria | 2008 | `contencioso-contra-inadmision-residencia-trabajo-963` |
| 226 (Laboral) | Residencia de larga duración denegada por antecedentes penales: demanda | 2019 | `residencia-larga-duracion-denegada-antecedentes-penales-l226` |
| 513 (Civil) | Recurso contencioso contra la denegación de visado de régimen comunitario | 2016 | `recurso-contencioso-contra-denegacion-visado-regimen-c513` |

### Recursos e impugnaciones (19)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 58 | Alzada contra denegar la tarjeta de residencia temporal de familiar de ciudadano UE | 2020 | `alzada-contra-denegar-tarjeta-residencia-temporal-58` |
| 247 | Reposición contra denegación de residencia permanente (silencio positivo) | 2016 | `reposicion-contra-denegacion-residencia-permanente-247` |
| 261 | Alzada contra denegación de entrada en España con carta de invitación | 2016 | `alzada-contra-denegacion-entrada-espana-carta-invitacion-261` |
| 284 | Apelación en procedimiento de expulsión | 2015 | `apelacion-procedimiento-expulsion-284` |
| 300 | Reposición contra visado de reagrupación familiar denegado | 2014 | `reposicion-contra-visado-reagrupacion-familiar-denegado-300` |
| 342 | Reposición en nacionalidad española por residencia | 2013 | `reposicion-nacionalidad-espanola-residencia-342` |
| 360 | Reposición en residencia de larga duración por antecedentes penales | 2013 | `reposicion-residencia-larga-duracion-antecedentes-360` |
| 370 | Apelación en materia de asilo | 2013 | `apelacion-materia-asilo-370` |
| 371 | Reposición contra denegar renovar residencia y trabajo por cuenta propia | 2013 | `reposicion-contra-denegar-renovar-residencia-trabajo-371` |
| 373 | Reposición contra visado de reagrupación denegado por no acreditar edad o parentesco | 2013 | `reposicion-contra-visado-reagrupacion-denegado-no-373` |
| 374 | Reposición ante la Subdelegación en expulsión preferente | 2013 | `reposicion-ante-subdelegacion-expulsion-preferente-374` |
| 382 | Alzada contra denegación de entrada a un extranjero con carta de invitación | 2013 | `alzada-contra-denegacion-entrada-extranjero-carta-382` |
| 383 | Reposición contra multa por estancia irregular | 2013 | `reposicion-contra-multa-estancia-irregular-383` |
| 537 | Reposición contra denegación de permiso de trabajo a un extranjero | 2011 | `reposicion-contra-denegacion-permiso-trabajo-extranjero-537` |
| 584 | Reposición contra denegación de residencia temporal por arraigo | 2011 | `reposicion-contra-denegacion-residencia-temporal-arraigo-584` |
| 709 | Alzada contra denegar renovar residencia y trabajo por informe gubernativo desfavorable | 2009 | `alzada-contra-denegar-renovar-residencia-trabajo-informe-709` |
| 717 | Reposición contra sanción de expulsión por estancia ilegal (art. 53.a Ley de Extranjería) | 2009 | `reposicion-contra-sancion-expulsion-estancia-ilegal-art-717` |
| 957 | Reposición contra inadmisión por falta de empadronamiento | 2008 | `reposicion-contra-inadmision-falta-empadronamiento-957` |
| 966 | Recurso contra la expulsión del procedimiento preferente | 2008 | `recurso-contra-expulsion-procedimiento-preferente-966` |

### Contestaciones, oposiciones y alegaciones (6)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 359 | Alegaciones en expulsión de extranjero condenado a pena de prisión | 2013 | `alegaciones-expulsion-extranjero-condenado-pena-prision-359` |
| 388 | Alegaciones en expulsión por procedimiento preferente | 2013 | `alegaciones-expulsion-procedimiento-preferente-388` |
| 536 | Alegaciones en expulsión por arraigo familiar | 2011 | `alegaciones-expulsion-arraigo-familiar-536` |
| 715 | Alegaciones de defensa en expulsión preferente por infracción de la Ley de Extranjería | 2009 | `alegaciones-defensa-expulsion-preferente-infraccion-ley-715` |
| 716 | Alegaciones en expulsión por estancia ilegal (art. 53.a Ley de Extranjería) | 2009 | `alegaciones-expulsion-estancia-ilegal-art-53-ley-716` |
| 959 | Alegaciones en actuaciones complementarias de extranjería | 2008 | `alegaciones-actuaciones-complementarias-extranjeria-959` |

### Solicitudes y expedientes (16)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 51 | Medida cautelarísima para suspender la orden de expulsión de un extranjero | 2021 | `medida-cautelarisima-suspender-orden-expulsion-51` |
| 69 | Pedir certificado escolar para obtener la residencia legal | 2019 | `pedir-certificado-escolar-obtener-residencia-legal-69` |
| 369 | Pedir informe de escolarización para renovar residencia y trabajo | 2013 | `pedir-informe-escolarizacion-renovar-residencia-trabajo-369` |
| 375 | Pedir que se declare prescrita la sanción de expulsión | 2013 | `pedir-declare-prescrita-sancion-expulsion-375` |
| 386 | Pedir la caducidad del expediente de expulsión | 2013 | `pedir-caducidad-expediente-expulsion-386` |
| 390 | Pedir revocar la devolución por arraigo | 2013 | `pedir-revocar-devolucion-arraigo-390` |
| 391 | Pedir modificar la autorización de residencia y trabajo | 2013 | `pedir-modificar-autorizacion-residencia-trabajo-391` |
| 587 | Pedir cédula de inscripción o título de viaje (EX16) | 2011 | `pedir-cedula-inscripcion-titulo-viaje-ex16-587` |
| 588 | Pedir tarjeta de residencia de familiar de ciudadano comunitario (EX19) | 2011 | `pedir-tarjeta-residencia-familiar-ciudadano-comunitario-588` |
| 589 | Pedir certificado de registro de residencia comunitaria (EX18) | 2011 | `pedir-certificado-registro-residencia-comunitaria-ex18-589` |
| 878 | Pedir ejecución provisional de sentencia en extranjería | 2009 | `pedir-ejecucion-provisional-sentencia-extranjeria-878` |
| 955 | Reexamen de la denegación de asilo | 2008 | `reexamen-denegacion-asilo-955` |
| 956 | Reexamen de la inadmisión a trámite de asilo | 2008 | `reexamen-inadmision-tramite-asilo-956` |
| 960 | Archivo por colaborar con la justicia: alegaciones a propuesta de expulsión (ordinario) | 2008 | `archivo-colaborar-justicia-alegaciones-propuesta-960` |
| 962 | Archivo por colaborar con la justicia: alegaciones a propuesta de expulsión (preferente) | 2008 | `archivo-colaborar-justicia-alegaciones-propuesta-962` |
| 227 (Laboral) | Revocar la resolución de expulsión: solicitud | 2019 | `revocar-resolucion-expulsion-solicitud-l227` |

### Escritos de trámite (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 295 | Conclusiones: nacionalidad denegada por falta de integración | 2014 | `conclusiones-nacionalidad-denegada-falta-integracion-295` |
| 392 | Solicitar el retorno voluntario | 2013 | `solicitar-retorno-voluntario-392` |
| 711 | Otrosí de demanda pidiendo suspender la expulsión | 2009 | `otrosi-demanda-pidiendo-suspender-expulsion-711` |
| 712 | Apelación contra auto que deniega suspender la expulsión (extranjería) | 2009 | `apelacion-contra-auto-deniega-suspender-expulsion-712` |
| 714 | Apelación contra sentencia que confirma una expulsión (extranjería) | 2009 | `apelacion-contra-sentencia-confirma-expulsion-714` |

### Actos y resoluciones de la Administración o del órgano judicial (4)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 68 | Certificado de silencio positivo en la renovación de residencia y trabajo | 2019 | `certificado-silencio-positivo-renovacion-residencia-68` |
| 362 | Solicitar autorización de residencia comunitaria | 2013 | `solicitar-autorizacion-residencia-comunitaria-362` |
| 376 | Acta de manifestaciones para reagrupación familiar comunitaria | 2013 | `acta-manifestaciones-reagrupacion-familiar-comunitaria-376` |
| 224 (Laboral) | Silencio positivo en la modificación de autorización: certificado | 2019 | `silencio-positivo-modificacion-autorizacion-certificado-l224` |

### Contratos, escrituras y documentos (7)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 262 | Mandato con poder de representación para tramitar la nacionalidad española | 2016 | `mandato-poder-representacion-tramitar-nacionalidad-262` |
| 282 | Convenio de colaboración para estancia en España por voluntariado | 2015 | `convenio-colaboracion-estancia-espana-voluntariado-282` |
| 357 | Recurso contra la denegación de asilo | 2013 | `recurso-contra-denegacion-asilo-357` |
| 358 | Demanda contra la denegación de asilo | 2013 | `demanda-contra-denegacion-asilo-358` |
| 493 | Solicitud oficial del Estatuto de Apátrida | 2012 | `solicitud-oficial-estatuto-apatrida-493` |
| 586 | Modelos oficiales para iniciar trámites de documentación de extranjeros | 2011 | `modelos-oficiales-iniciar-tramites-documentacion-586` |
| 238 (Laboral) | Designar representante para tramitar visados | 2019 | `designar-representante-tramitar-visados-l238` |

### Comunicaciones, requerimientos y reclamaciones (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 280 | Frente a la denegación de visado de reagrupación familiar comunitaria | 2015 | `frente-denegacion-visado-reagrupacion-familiar-280` |
| 958 | Denuncia de un hecho relevante en extranjería | 2008 | `denuncia-hecho-relevante-extranjeria-958` |

### Otros (11)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 71 | Revocar la expulsión por matrimonio con español | 2019 | `revocar-expulsion-matrimonio-espanol-71` |
| 94 | Declaración de empresas extranjeras de someterse a los tribunales españoles (contratos públicos) | 2018 | `declaracion-empresas-extranjeras-someterse-tribunales-94` |
| 361 | Residencia comunitaria de familiar de ciudadano de la Unión | 2013 | `residencia-comunitaria-familiar-ciudadano-union-361` |
| 372 | Revocar la expulsión por circunstancias excepcionales | 2013 | `revocar-expulsion-circunstancias-excepcionales-372` |
| 378 | Certificado de solicitante de asilo para pedir la nacionalidad | 2013 | `certificado-solicitante-asilo-pedir-nacionalidad-378` |
| 379 | Certificado de solicitante de asilo para casarse | 2013 | `certificado-solicitante-asilo-casarse-379` |
| 380 | Matrimonio de un solicitante de asilo | 2013 | `matrimonio-solicitante-asilo-380` |
| 381 | Periodo de reflexión en casos de trata de seres humanos | 2013 | `periodo-reflexion-casos-trata-seres-humanos-381` |
| 393 | Internamiento de extranjeros: reforma y apelación contra el auto | 2013 | `internamiento-extranjeros-reforma-apelacion-contra-auto-393` |
| 191 (Laboral) | Memoria de actividad de la empresa y perfil del puesto para desplazar y contratar extranjeros | 2020 | `memoria-actividad-empresa-perfil-puesto-desplazar-l191` |
| 225 (Laboral) | Silencio positivo en la residencia de larga duración: certificado | 2019 | `silencio-positivo-residencia-larga-duracion-certificado-l225` |

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- `formulario.md`: el texto revisado del formulario;
- `marco.md`: la guía del tema, con las reglas y plazos vigentes comprobados en el BOE.

## Uso interno

Plugin de uso interno. Antes de venderlo o dárselo a alumnos, hay que sustituir los textos por plantillas de redacción propia.
