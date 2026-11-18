---
name: indice
description: "Índice de los 78 formularios de recursos contra multas de tráfico por señales, alumbrado, carga, alcohol y documentación. Úsala cuando el usuario pida un escrito de esta materia y no esté claro qué formulario usar: elige la skill del formulario adecuado. Requiere Jurisprudenciator."
---

# Recurrir multas por señales, alumbrado, alcohol y documentación: índice de formularios

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

Busca por tipo de documento y título. Cada formulario es una skill de este plugin (`/modelos-recursos-multas-senales-y-vehiculo-espana:<skill>`). Si dudas entre dos, elige el más reciente o el que mejor encaje con los hechos y dilo; si la petición es ambigua, propón al usuario los dos o tres formularios que mejor encajan y pregúntale cuál quiere. Las reglas del tema están en `marco.md`.

## Cómo usar el formulario elegido

Invoca su skill. Si esa skill no aparece en tu lista de skills disponibles (puede pasar cuando hay muchas skills instaladas), lee directamente su fichero `SKILL.md`: está en `skills/<skill>/SKILL.md` dentro de este plugin, en la carpeta hermana de la de esta skill `indice` (`../<skill>/SKILL.md`). Síguelo igual que si la hubieras invocado, con el «Texto del formulario» que lleva al final y el `marco.md` de esta skill `indice`.

## Otros plugins de multas de tráfico

Los formularios de multas de tráfico están repartidos en cuatro plugins. Si el escrito que se pide no está en este índice, búscalo en estos:

- `modelos-recursos-multas-circulacion-espana`: Recurrir multas de circulación, velocidad y maniobras · España
- `modelos-alegaciones-multas-trafico-espana`: Alegaciones y descargos contra denuncias de tráfico · España
- `modelos-multas-trafico-espana`: Multas de tráfico: demandas, solicitudes y trámites · España

## Recursos e impugnaciones (78)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 22 | Reposición contra multa por incumplir restricciones de circulación por contaminación | 2022 | `reposicion-contra-multa-incumplir-restricciones-22` |
| 24 | Reposición contra sanción por incumplir las normas del alcoholímetro antiarranque | 2022 | `reposicion-contra-sancion-incumplir-normas-alcoholimetro-24` |
| 25 | Reposición contra sanción por usar dispositivos de intercomunicación en pruebas de permisos | 2022 | `reposicion-contra-sancion-usar-dispositivos-25` |
| 138 | Reposición contra sanción por incumplir normas de transporte terrestre por carretera | 2017 | `reposicion-contra-sancion-incumplir-normas-transporte-138` |
| 1305 | Alzada contra la pérdida de vigencia del permiso declarada por la Jefatura Provincial de Tráfico | 2006 | `alzada-contra-perdida-vigencia-permiso-declarada-1305` |
| 1437 | Reposición contra multa por falta de visibilidad del vehículo | 2004 | `reposicion-contra-multa-falta-visibilidad-vehiculo-1437` |
| 1439 | Reposición contra multa por emplazamiento y acondicionamiento de personas | 2004 | `reposicion-contra-multa-emplazamiento-acondicionamiento-1439` |
| 1440 | Reposición contra multa por arrojar a la vía un objeto que puede causar incendio o peligro | 2004 | `reposicion-contra-multa-arrojar-via-objeto-puede-causar-1440` |
| 1444 | Reposición contra multa por retirar, sustituir o alterar señales | 2004 | `reposicion-contra-multa-retirar-sustituir-alterar-1444` |
| 1445 | Reposición contra multa por alumbrado de cruce | 2004 | `reposicion-contra-multa-alumbrado-cruce-1445` |
| 1446 | Reposición contra multa por otras marcas e inscripciones blancas | 2004 | `reposicion-contra-multa-otras-marcas-e-inscripciones-1446` |
| 1447 | Reposición contra multa por matrículas | 2004 | `reposicion-contra-multa-matriculas-1447` |
| 1448 | Reposición contra multa por semáforos reservados | 2004 | `reposicion-contra-multa-semaforos-reservados-1448` |
| 1449 | Reposición contra multa por señales de indicaciones generales | 2004 | `reposicion-contra-multa-senales-indicaciones-generales-1449` |
| 1450 | Reposición contra multa por señales de restricción de paso | 2004 | `reposicion-contra-multa-senales-restriccion-paso-1450` |
| 1451 | Reposición contra multa por inmovilizaciones | 2004 | `reposicion-contra-multa-inmovilizaciones-1451` |
| 1458 | Reposición contra multa por no auxiliar en accidente | 2004 | `reposicion-contra-multa-no-auxiliar-accidente-1458` |
| 1460 | Reposición contra multa por advertencias a otros vehículos | 2004 | `reposicion-contra-multa-advertencias-otros-vehiculos-1460` |
| 1461 | Reposición contra multa por alumbrado inutilizado o averiado | 2004 | `reposicion-contra-multa-alumbrado-inutilizado-averiado-1461` |
| 1462 | Reposición contra multa por advertencias acústicas | 2004 | `reposicion-contra-multa-advertencias-acusticas-1462` |
| 1463 | Reposición contra multa por advertencias ópticas | 2004 | `reposicion-contra-multa-advertencias-opticas-1463` |
| 1464 | Reposición contra multa por puertas del vehículo | 2004 | `reposicion-contra-multa-puertas-vehiculo-1464` |
| 1465 | Reposición contra multa por supuestos especiales de alumbrado | 2004 | `reposicion-contra-multa-supuestos-especiales-alumbrado-1465` |
| 1466 | Reposición contra multa por no apagar el motor | 2004 | `reposicion-contra-multa-no-apagar-motor-1466` |
| 1467 | Reposición contra multa por advertencias de vehículos de urgencia y especiales | 2004 | `reposicion-contra-multa-advertencias-vehiculos-urgencia-1467` |
| 1468 | Reposición contra multa por autorizaciones para conducir | 2004 | `reposicion-contra-multa-autorizaciones-conducir-1468` |
| 1469 | Reposición contra multa por marcas de otros colores | 2004 | `reposicion-contra-multa-marcas-otros-colores-1469` |
| 1470 | Reposición contra multa por señales horizontales de circulación | 2004 | `reposicion-contra-multa-senales-horizontales-circulacion-1470` |
| 1471 | Reposición contra multa por marcas blancas transversales | 2004 | `reposicion-contra-multa-marcas-blancas-transversales-1471` |
| 1472 | Reposición contra multa por marcas blancas longitudinales | 2004 | `reposicion-contra-multa-marcas-blancas-longitudinales-1472` |
| 1473 | Reposición contra multa por autorizaciones administrativas generales | 2004 | `reposicion-contra-multa-autorizaciones-administrativas-1473` |
| 1474 | Reposición contra multa por permiso de circulación y documentación del vehículo | 2004 | `reposicion-contra-multa-permiso-circulacion-1474` |
| 1475 | Reposición contra multa por inmovilizar el vehículo y caída de la carga | 2004 | `reposicion-contra-multa-inmovilizar-vehiculo-caida-carga-1475` |
| 1476 | Reposición contra multa por formato de las señales | 2004 | `reposicion-contra-multa-formato-senales-1476` |
| 1477 | Reposición contra multa por señales de balizamiento | 2004 | `reposicion-contra-multa-senales-balizamiento-1477` |
| 1479 | Reposición contra multa por semáforo para peatones | 2004 | `reposicion-contra-multa-semaforo-peatones-1479` |
| 1480 | Reposición contra multa por desobedecer señales u órdenes de la autoridad o sus agentes | 2004 | `reposicion-contra-multa-desobedecer-senales-u-ordenes-1480` |
| 1482 | Reposición contra multa por semáforo circular | 2004 | `reposicion-contra-multa-semaforo-circular-1482` |
| 1483 | Reposición contra multa por deslumbramiento | 2004 | `reposicion-contra-multa-deslumbramiento-1483` |
| 1484 | Reposición contra multa por barreras, semibarreras y semáforos | 2004 | `reposicion-contra-multa-barreras-semibarreras-semaforos-1484` |
| 1485 | Reposición contra multa por alumbrado de carretera | 2004 | `reposicion-contra-multa-alumbrado-carretera-1485` |
| 1488 | Reposición contra multa por alumbrado de la placa de matrícula | 2004 | `reposicion-contra-multa-alumbrado-placa-matricula-1488` |
| 1489 | Reposición contra multa por no usar el alumbrado durante el día | 2004 | `reposicion-contra-multa-no-usar-alumbrado-durante-dia-1489` |
| 1490 | Reposición contra multa por alumbrado de posición y gálibo | 2004 | `reposicion-contra-multa-alumbrado-posicion-galibo-1490` |
| 1500 | Reposición contra multa por señales de carriles | 2004 | `reposicion-contra-multa-senales-carriles-1500` |
| 1501 | Reposición contra multa por señales de prioridad | 2004 | `reposicion-contra-multa-senales-prioridad-1501` |
| 1502 | Reposición contra multa por señales de prohibición de entrada | 2004 | `reposicion-contra-multa-senales-prohibicion-entrada-1502` |
| 1503 | Reposición contra multa por otras señales de prohibición o restricción | 2004 | `reposicion-contra-multa-otras-senales-prohibicion-1503` |
| 1504 | Reposición contra multa por señales de obligación | 2004 | `reposicion-contra-multa-senales-obligacion-1504` |
| 1505 | Reposición contra multa por semáforos cuadrados o de carril | 2004 | `reposicion-contra-multa-semaforos-cuadrados-carril-1505` |
| 1506 | Reposición contra multa por cinturón o sistema de retención infantil | 2004 | `reposicion-contra-multa-cinturon-sistema-retencion-1506` |
| 1512 | Reposición contra multa por casco y otros elementos de protección | 2004 | `reposicion-contra-multa-casco-otros-elementos-proteccion-1512` |
| 1515 | Reposición contra multa por conducir con estupefacientes, psicotrópicos o sustancias análogas | 2004 | `reposicion-contra-multa-conducir-estupefacientes-1515` |
| 1516 | Reposición contra multa por incumplimientos del personal sanitario sobre bebidas alcohólicas | 2004 | `reposicion-contra-multa-incumplimientos-personal-1516` |
| 1520 | Reposición contra multa por tasa de alcohol en sangre o aire espirado | 2004 | `reposicion-contra-multa-tasa-alcohol-sangre-aire-1520` |
| 1522 | Reposición contra multa por la investigación de la alcoholemia | 2004 | `reposicion-contra-multa-investigacion-alcoholemia-1522` |
| 1523 | Reposición contra multa por pruebas de detección de estupefacientes | 2004 | `reposicion-contra-multa-pruebas-deteccion-1523` |
| 1536 | Reposición contra multa por prioridad de paso sin señalización | 2004 | `reposicion-contra-multa-prioridad-paso-sin-senalizacion-1536` |
| 1537 | Reposición contra multa por prioridad en puentes y obras señalizadas | 2004 | `reposicion-contra-multa-prioridad-puentes-obras-1537` |
| 1538 | Reposición contra multa por prioridad en intersección sin señalizar | 2004 | `reposicion-contra-multa-prioridad-interseccion-sin-1538` |
| 1546 | Reposición contra multa por competiciones deportivas | 2004 | `reposicion-contra-multa-competiciones-deportivas-1546` |
| 1547 | Reposición contra multa por prioridad de paso en intersección señalizada | 2004 | `reposicion-contra-multa-prioridad-paso-interseccion-1547` |
| 1549 | Reposición contra multa por limitaciones a la circulación | 2004 | `reposicion-contra-multa-limitaciones-circulacion-1549` |
| 1556 | Reposición contra multa por libertad de movimientos, atención, posición, animales y auriculares | 2004 | `reposicion-contra-multa-libertad-movimientos-atencion-1556` |
| 1557 | Reposición contra multa por carga y descarga | 2004 | `reposicion-contra-multa-carga-descarga-1557` |
| 1558 | Reposición contra multa por disposición de la carga | 2004 | `reposicion-contra-multa-disposicion-carga-1558` |
| 1559 | Reposición contra multa por dimensiones del vehículo y su carga | 2004 | `reposicion-contra-multa-dimensiones-vehiculo-carga-1559` |
| 1561 | Reposición contra multa por transporte en ciclos, ciclomotores y motocicletas | 2004 | `reposicion-contra-multa-transporte-ciclos-ciclomotores-1561` |
| 1562 | Reposición contra multa por transporte colectivo de personas | 2004 | `reposicion-contra-multa-transporte-colectivo-personas-1562` |
| 1563 | Reposición contra multa por dimensiones de la carga | 2004 | `reposicion-contra-multa-dimensiones-carga-1563` |
| 1565 | Reposición contra multa por perturbaciones y contaminación | 2004 | `reposicion-contra-multa-perturbaciones-contaminacion-1565` |
| 1566 | Reposición contra multa por dejar en la vía objetos que afectan a la seguridad | 2004 | `reposicion-contra-multa-dejar-via-objetos-afectan-1566` |
| 1567 | Reposición contra multa por conducción negligente o temeraria | 2004 | `reposicion-contra-multa-conduccion-negligente-temeraria-1567` |
| 1568 | Reposición contra multa por transporte de personas | 2004 | `reposicion-contra-multa-transporte-personas-1568` |
| 1569 | Reposición contra multa por no señalizar obstáculos o peligros creados en la vía | 2004 | `reposicion-contra-multa-no-senalizar-obstaculos-peligros-1569` |
| 1581 | Reposición contra multa por incorporación de vehículos de transporte de viajeros | 2004 | `reposicion-contra-multa-incorporacion-vehiculos-1581` |
| 1583 | Reposición contra multa por vehículos y transportes especiales | 2004 | `reposicion-contra-multa-vehiculos-transportes-especiales-1583` |
| 1743 | Reposición contra sanción de tráfico y seguridad vial | 2004 | `reposicion-contra-sancion-trafico-seguridad-vial-1743` |
