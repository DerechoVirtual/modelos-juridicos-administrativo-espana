---
name: indice
description: "Índice de los 108 formularios de el expediente sancionador de tráfico: demandas, solicitudes, trámites, notificaciones y resoluciones. Úsala cuando el usuario pida un escrito de esta materia y no esté claro qué formulario usar: elige la skill del formulario adecuado. Requiere Jurisprudenciator."
---

# Multas de tráfico: demandas, solicitudes y trámites: índice de formularios

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

## Cómo elegir

Busca por tipo de documento y título. Cada formulario es una skill de este plugin (`/modelos-multas-trafico-espana:<skill>`). Si dudas entre dos, elige el más reciente o el que mejor encaje con los hechos y dilo; si la petición es ambigua, propón al usuario los dos o tres formularios que mejor encajan y pregúntale cuál quiere. Las reglas del tema están en `marco.md`.

## Cómo usar el formulario elegido

Invoca su skill. Si esa skill no aparece en tu lista de skills disponibles (puede pasar cuando hay muchas skills instaladas), lee directamente su fichero `SKILL.md`: está en `skills/<skill>/SKILL.md` dentro de este plugin, en la carpeta hermana de la de esta skill `indice` (`../<skill>/SKILL.md`). Síguelo igual que si la hubieras invocado, con el «Texto del formulario» que lleva al final y el `marco.md` de esta skill `indice`.

## Otros plugins de multas de tráfico

Los formularios de multas de tráfico están repartidos en cuatro plugins. Si el escrito que se pide no está en este índice, búscalo en estos:

- `modelos-recursos-multas-circulacion-espana`: Recurrir multas de circulación, velocidad y maniobras · España
- `modelos-recursos-multas-senales-y-vehiculo-espana`: Recurrir multas por señales, alumbrado, alcohol y documentación · España
- `modelos-alegaciones-multas-trafico-espana`: Alegaciones y descargos contra denuncias de tráfico · España

## Demandas, interposiciones y peticiones iniciales (2)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 55 | Demanda abreviada contra multa por circular por Madrid Central | 2020 | `demanda-abreviada-contra-multa-circular-madrid-central-55` |
| 1740 | Recurso extraordinario de revisión contra sanciones de tráfico | 2004 | `recurso-extraordinario-revision-contra-sanciones-trafico-1740` |

## Solicitudes y expedientes (24)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 168 | Petición de información al juzgado por proceso penal sobre los mismos hechos | 2017 | `peticion-informacion-juzgado-proceso-penal-sobre-mismos-168` |
| 213 | Reclamar a la Administración por accidente de circulación con vehículo de su propiedad | 2016 | `reclamar-administracion-accidente-circulacion-vehiculo-213` |
| 227 | Petición razonada de otros órganos para iniciar un sancionador de tráfico | 2016 | `peticion-razonada-otros-organos-iniciar-sancionador-227` |
| 321 | Pedir la baja de la dirección electrónica vial | 2013 | `pedir-baja-direccion-electronica-vial-321` |
| 322 | Pedir la dirección electrónica vial | 2013 | `pedir-direccion-electronica-vial-322` |
| 908 | Pedir medidas cautelares en tráfico y seguridad vial | 2009 | `pedir-medidas-cautelares-trafico-seguridad-vial-908` |
| 1711 | Solicitud de autorización administrativa en materia de reglamentación de vehículos | 2004 | `solicitud-autorizacion-administrativa-materia-1711` |
| 1712 | Solicitud de autorización administrativa para actividades sujetas a la reglamentación de conductores | 2004 | `solicitud-autorizacion-administrativa-actividades-1712` |
| 1714 | Petición de dictamen al órgano consultivo en la responsabilidad patrimonial por daños de circulación | 2004 | `peticion-dictamen-organo-consultivo-responsabilidad-1714` |
| 1716 | Solicitud de autorización para una escuela particular de conductores | 2004 | `solicitud-autorizacion-escuela-particular-conductores-1716` |
| 1718 | Solicitud de autorización de apertura de una Inspección Técnica de Vehículos | 2004 | `solicitud-autorizacion-apertura-inspeccion-tecnica-1718` |
| 1721 | Solicitud de autorización para un centro de reconocimiento de conductores | 2004 | `solicitud-autorizacion-centro-reconocimiento-conductores-1721` |
| 1722 | Solicitud de autorización para inscribir, ampliar o trasladar talleres de reparación de vehículos | 2004 | `solicitud-autorizacion-inscribir-ampliar-trasladar-1722` |
| 1723 | Solicitud de autorización para un centro de recogida de vehículos fuera de uso | 2004 | `solicitud-autorizacion-centro-recogida-vehiculos-fuera-1723` |
| 1725 | Solicitud de autorización de pruebas deportivas por el casco urbano | 2004 | `solicitud-autorizacion-pruebas-deportivas-casco-urbano-1725` |
| 1726 | Solicitud de autorización para una prueba deportiva | 2004 | `solicitud-autorizacion-prueba-deportiva-1726` |
| 1730 | Solicitud de incorporación de una entidad privada al Consejo Superior de Tráfico y Seguridad Vial | 2004 | `solicitud-incorporacion-entidad-privada-consejo-superior-1730` |
| 1733 | Pedir la rectificación de errores en una autorización de tráfico | 2004 | `pedir-rectificacion-errores-autorizacion-trafico-1733` |
| 1734 | Solicitud de medalla al mérito de la seguridad vial | 2004 | `solicitud-medalla-merito-seguridad-vial-1734` |
| 1736 | Pedir certificación de sanciones anotadas en Registros | 2004 | `pedir-certificacion-sanciones-anotadas-registros-1736` |
| 1737 | Pedir la cancelación de anotación en el Registro de Conductores e Infractores | 2004 | `pedir-cancelacion-anotacion-registro-conductores-e-1737` |
| 1746 | Pedir que se declare de oficio la nulidad de una sanción de tráfico | 2004 | `pedir-declare-oficio-nulidad-sancion-trafico-1746` |
| 1817 | Pedir la revocación de una sanción dictada por una Jefatura de Tráfico | 2004 | `pedir-revocacion-sancion-dictada-jefatura-trafico-1817` |
| 1824 | Pedir certificación de caducidad del procedimiento sancionador | 2004 | `pedir-certificacion-caducidad-procedimiento-sancionador-1824` |

## Escritos de trámite (20)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 165 | Propuesta de resolución en sancionador de tráfico | 2017 | `propuesta-resolucion-sancionador-trafico-165` |
| 169 | Queja por defectos de tramitación en el expediente sancionador | 2017 | `queja-defectos-tramitacion-expediente-sancionador-169` |
| 171 | Instructor que pide colaboración a otros órganos en el expediente sancionador | 2017 | `instructor-pide-colaboracion-otros-organos-expediente-171` |
| 175 | Comunicar el pago voluntario de la multa y pedir la terminación del procedimiento | 2017 | `comunicar-pago-voluntario-multa-pedir-terminacion-175` |
| 184 | Descargos generales contra denuncia de tráfico ante la Jefatura de Tráfico | 2016 | `descargos-generales-contra-denuncia-trafico-ante-184` |
| 189 | Alegaciones generales contra denuncia de tráfico ante una Alcaldía | 2016 | `alegaciones-generales-contra-denuncia-trafico-ante-189` |
| 194 | Recusación del instructor en un sancionador de tráfico | 2016 | `recusacion-instructor-sancionador-trafico-194` |
| 209 | Contestar excusando la identificación del conductor responsable | 2016 | `contestar-excusando-identificacion-conductor-responsable-209` |
| 212 | Devolver una denuncia de tráfico notificada indebidamente | 2016 | `devolver-denuncia-trafico-notificada-indebidamente-212` |
| 215 | Denuncia de un particular por hechos ajenos a la circulación | 2016 | `denuncia-particular-hechos-ajenos-circulacion-215` |
| 221 | Personación de terceros interesados en un sancionador de tráfico | 2016 | `personacion-terceros-interesados-sancionador-trafico-221` |
| 225 | Contestación al requerimiento de información previa en una denuncia de tráfico | 2016 | `contestacion-requerimiento-informacion-previa-denuncia-225` |
| 297 | Anunciar recurso en sancionador abreviado de tráfico | 2014 | `anunciar-recurso-sancionador-abreviado-trafico-297` |
| 309 | Reposición contra multa de tráfico | 2013 | `reposicion-contra-multa-trafico-309` |
| 325 | Alegaciones generales contra denuncia de tráfico | 2013 | `alegaciones-generales-contra-denuncia-trafico-325` |
| 704 | Alegaciones o descargos en sancionador de tráfico | 2010 | `alegaciones-descargos-sancionador-trafico-704` |
| 1731 | Solicitud de subvención para actividades de seguridad vial o transporte por carretera | 2004 | `solicitud-subvencion-actividades-seguridad-vial-1731` |
| 1735 | Oferta de convenio de colaboración con la Administración de tráfico para fomentar la seguridad vial | 2004 | `oferta-convenio-colaboracion-administracion-trafico-1735` |
| 1747 | Pedir certificado del transcurso del plazo para resolver la reposición contra una sanción de tráfico | 2004 | `pedir-certificado-transcurso-plazo-resolver-reposicion-1747` |
| 1816 | Remisión de la autorización suspendida en un procedimiento sancionador | 2004 | `remision-autorizacion-suspendida-procedimiento-1816` |

## Actos y resoluciones de la Administración o del órgano judicial (42)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 144 | Notificación de la resolución sancionadora de la Jefatura de Tráfico | 2017 | `notificacion-resolucion-sancionadora-jefatura-trafico-144` |
| 145 | Notificación de la resolución sancionadora de tráfico de una Alcaldía | 2017 | `notificacion-resolucion-sancionadora-trafico-alcaldia-145` |
| 150 | Resolución sancionadora de una Jefatura de Tráfico | 2017 | `resolucion-sancionadora-jefatura-trafico-150` |
| 151 | Resolución que declara improcedente sancionar si no se identifica al autor | 2017 | `resolucion-declara-improcedente-sancionar-si-no-151` |
| 152 | Resolución sancionadora de tráfico de una Alcaldía | 2017 | `resolucion-sancionadora-trafico-alcaldia-152` |
| 154 | Resolución que declara inexistente la infracción por hechos no constitutivos de ella | 2017 | `resolucion-declara-inexistente-infraccion-hechos-no-154` |
| 166 | Acuerdo que paraliza el sancionador por proceso penal sobre los mismos hechos | 2017 | `acuerdo-paraliza-sancionador-proceso-penal-sobre-mismos-166` |
| 167 | Traslado de actuaciones del instructor al órgano resolutor | 2017 | `traslado-actuaciones-instructor-organo-resolutor-167` |
| 170 | Notificar al interesado la propuesta de resolución | 2017 | `notificar-interesado-propuesta-resolucion-170` |
| 172 | Resolución que deniega las pruebas propuestas por el inculpado | 2017 | `resolucion-deniega-pruebas-propuestas-inculpado-172` |
| 173 | Informe del instructor que propone sobreseer por no ser infracción los hechos | 2017 | `informe-instructor-propone-sobreseer-no-ser-infraccion-173` |
| 186 | Pedir al agente denunciante que ratifique la denuncia | 2016 | `pedir-agente-denunciante-ratifique-denuncia-186` |
| 188 | Resolución que adopta medidas cautelares en tráfico y seguridad vial | 2016 | `resolucion-adopta-medidas-cautelares-trafico-seguridad-188` |
| 190 | Acuerdo que inicia o reanuda el sancionador tras proceso penal sin responsabilidad penal | 2016 | `acuerdo-inicia-reanuda-sancionador-tras-proceso-penal-190` |
| 203 | Notificación por edictos de denuncia o incoación en sancionador de tráfico | 2016 | `notificacion-edictos-denuncia-incoacion-sancionador-203` |
| 208 | Notificar al inculpado el inicio del sancionador acordado de oficio | 2016 | `notificar-inculpado-inicio-sancionador-acordado-oficio-208` |
| 210 | Diligencia de comparecencia del titular del vehículo que identifica al responsable | 2016 | `diligencia-comparecencia-titular-vehiculo-identifica-210` |
| 211 | Incoación de oficio de sancionador de tráfico y seguridad vial | 2016 | `incoacion-oficio-sancionador-trafico-seguridad-vial-211` |
| 216 | Boletín de denuncia de tráfico y seguridad vial | 2016 | `boletin-denuncia-trafico-seguridad-vial-216` |
| 217 | Requerir al titular que identifique al conductor infractor | 2016 | `requerir-titular-identifique-conductor-infractor-217` |
| 218 | Notificar denuncia y requerir la identificación del conductor | 2016 | `notificar-denuncia-requerir-identificacion-conductor-218` |
| 219 | Acuerdo que declara improcedente iniciar sancionador por prescripción | 2016 | `acuerdo-declara-improcedente-iniciar-sancionador-219` |
| 220 | Requerimiento de información previa a los presuntos responsables de la infracción de tráfico | 2016 | `requerimiento-informacion-previa-presuntos-responsables-220` |
| 222 | Oficio que informa de la incoación al órgano autor de la petición razonada | 2016 | `oficio-informa-incoacion-organo-autor-peticion-razonada-222` |
| 224 | Iniciar sancionador de tráfico por orden superior | 2016 | `iniciar-sancionador-trafico-orden-superior-224` |
| 323 | Requerir la baja o anulación de la dirección electrónica vial | 2013 | `requerir-baja-anulacion-direccion-electronica-vial-323` |
| 1710 | Dictamen del órgano consultivo sobre responsabilidad patrimonial por daños de circulación | 2004 | `dictamen-organo-consultivo-sobre-responsabilidad-1710` |
| 1720 | Autorización para una actividad regulada por la legislación de tráfico y seguridad vial | 2004 | `autorizacion-actividad-regulada-legislacion-trafico-1720` |
| 1744 | Oficio para comprobar la veracidad de una denuncia anónima | 2004 | `oficio-comprobar-veracidad-denuncia-anonima-1744` |
| 1745 | Certificación de descubierto para iniciar la vía de apremio | 2004 | `certificacion-descubierto-iniciar-via-apremio-1745` |
| 1751 | Acuerdo de inicio de oficio de la revisión de sanciones de tráfico nulas | 2004 | `acuerdo-inicio-oficio-revision-sanciones-trafico-nulas-1751` |
| 1753 | Citación para practicar las pruebas del expediente sancionador | 2004 | `citacion-practicar-pruebas-expediente-sancionador-1753` |
| 1755 | Acta de ratificación del agente denunciante | 2004 | `acta-ratificacion-agente-denunciante-1755` |
| 1756 | Traslado al denunciante de las alegaciones del inculpado a la propuesta de resolución | 2004 | `traslado-denunciante-alegaciones-inculpado-propuesta-1756` |
| 1757 | Informe del denunciante frente a las alegaciones del denunciado a la propuesta | 2004 | `informe-denunciante-frente-alegaciones-denunciado-1757` |
| 1762 | Sobreseimiento del expediente por prescripción de la sanción | 2004 | `sobreseimiento-expediente-prescripcion-sancion-1762` |
| 1812 | Acta de la denuncia verbal de un particular | 2004 | `acta-denuncia-verbal-particular-1812` |
| 1813 | Sobreseimiento de una denuncia anónima de tráfico | 2004 | `sobreseimiento-denuncia-anonima-trafico-1813` |
| 1818 | Resolución que anula actos de tráfico gravemente contrarios al ordenamiento | 2004 | `resolucion-anula-actos-trafico-gravemente-contrarios-1818` |
| 1819 | Suspensión de la ejecución de un acto de tráfico en la revisión de actos nulos | 2004 | `suspension-ejecucion-acto-trafico-revision-actos-nulos-1819` |
| 1822 | Traslado de la reposición contra sanción de tráfico a los demás interesados | 2004 | `traslado-reposicion-contra-sancion-trafico-demas-1822` |
| 1823 | Sobreseimiento del expediente sancionador por perención | 2004 | `sobreseimiento-expediente-sancionador-perencion-1823` |

## Contratos, escrituras y documentos (3)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1708 | Convenio entre una Administración y una entidad privada para fomentar la seguridad vial | 2004 | `convenio-entre-administracion-entidad-privada-fomentar-1708` |
| 1728 | Modelo de estatutos de asociación de seguridad vial o de víctimas de accidentes de tráfico | 2004 | `modelo-estatutos-asociacion-seguridad-vial-victimas-1728` |
| 1729 | Solicitud y adhesión para una distinción honorífica en tráfico, transportes o seguridad vial | 2004 | `solicitud-adhesion-distincion-honorifica-trafico-1729` |

## Comunicaciones, requerimientos y reclamaciones (5)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 164 | Comunicar a otros órganos indicios de infracción | 2017 | `comunicar-otros-organos-indicios-infraccion-164` |
| 1707 | Reclamación de la aseguradora por lo pagado a su asegurado en un accidente de circulación | 2004 | `reclamacion-aseguradora-lo-pagado-asegurado-accidente-1707` |
| 1719 | Denuncia de un usuario contra un taller por incumplir las condiciones de su autorización | 2004 | `denuncia-usuario-contra-taller-incumplir-condiciones-1719` |
| 1742 | Denuncia de un particular por infracciones de tráfico y seguridad vial | 2004 | `denuncia-particular-infracciones-trafico-seguridad-vial-1742` |
| 1814 | Oposición del interesado a entregar la autorización administrativa | 2004 | `oposicion-interesado-entregar-autorizacion-1814` |

## Otros (12)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 178 | Remitir al Ministerio Fiscal las actuaciones del sancionador | 2017 | `remitir-ministerio-fiscal-actuaciones-sancionador-178` |
| 591 | Titular que identifica al conductor del vehículo | 2011 | `titular-identifica-conductor-vehiculo-591` |
| 592 | Defecto de tramitación: falta de práctica, solicitud de prueba | 2011 | `defecto-tramitacion-falta-practica-solicitud-prueba-592` |
| 593 | Defecto de tramitación: ausencia de informe del denunciante | 2011 | `defecto-tramitacion-ausencia-informe-denunciante-593` |
| 594 | Alegaciones: multa superior a la prevista | 2011 | `alegaciones-multa-superior-prevista-594` |
| 596 | Defecto de tramitación: no se dio plazo para alegar | 2011 | `defecto-tramitacion-no-dio-plazo-alegar-596` |
| 597 | Alegar la caducidad del procedimiento | 2011 | `alegar-caducidad-procedimiento-597` |
| 598 | Alegaciones por conducir sin la autorización administrativa | 2011 | `alegaciones-conducir-sin-autorizacion-administrativa-598` |
| 599 | Alegaciones por saltarse un semáforo en rojo | 2011 | `alegaciones-saltarse-semaforo-rojo-599` |
| 1732 | Memoria para la incorporación de una entidad privada a un órgano colegiado de seguridad vial | 2004 | `memoria-incorporacion-entidad-privada-organo-colegiado-1732` |
| 1754 | Acuse de recibo e información sobre los trámites de una denuncia de particulares | 2004 | `acuse-recibo-e-informacion-sobre-tramites-denuncia-1754` |
| 1815 | Orden al infractor de entregar el documento de la autorización suspendida | 2004 | `orden-infractor-entregar-documento-autorizacion-1815` |
