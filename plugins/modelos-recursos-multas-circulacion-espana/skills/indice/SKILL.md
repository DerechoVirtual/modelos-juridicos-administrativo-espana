---
name: indice
description: "Índice de los 61 formularios de recursos de reposición contra multas de tráfico por circulación, velocidad y maniobras. Úsala cuando el usuario pida un escrito de esta materia y no esté claro qué formulario usar: elige la skill del formulario adecuado. Requiere Jurisprudenciator."
---

# Recurrir multas de circulación, velocidad y maniobras: índice de formularios

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

Busca por tipo de documento y título. Cada formulario es una skill de este plugin (`/modelos-recursos-multas-circulacion-espana:<skill>`). Si dudas entre dos, elige el más reciente o el que mejor encaje con los hechos y dilo; si la petición es ambigua, propón al usuario los dos o tres formularios que mejor encajan y pregúntale cuál quiere. Las reglas del tema están en `marco.md`.

## Cómo usar el formulario elegido

Invoca su skill. Si esa skill no aparece en tu lista de skills disponibles (puede pasar cuando hay muchas skills instaladas), lee directamente su fichero `SKILL.md`: está en `skills/<skill>/SKILL.md` dentro de este plugin, en la carpeta hermana de la de esta skill `indice` (`../<skill>/SKILL.md`). Síguelo igual que si la hubieras invocado, con el «Texto del formulario» que lleva al final y el `marco.md` de esta skill `indice`.

## Otros plugins de multas de tráfico

Los formularios de multas de tráfico están repartidos en cuatro plugins. Si el escrito que se pide no está en este índice, búscalo en estos:

- `modelos-recursos-multas-senales-y-vehiculo-espana`: Recurrir multas por señales, alumbrado, alcohol y documentación · España
- `modelos-alegaciones-multas-trafico-espana`: Alegaciones y descargos contra denuncias de tráfico · España
- `modelos-multas-trafico-espana`: Multas de tráfico: demandas, solicitudes y trámites · España

## Recursos e impugnaciones (61)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 1436 | Reposición contra multa por prioridad de paso en obras y estrechamientos | 2004 | `reposicion-contra-multa-prioridad-paso-obras-1436` |
| 1438 | Reposición contra multa por sentido de circulación en refugios, isletas y dispositivos de guía | 2004 | `reposicion-contra-multa-sentido-circulacion-refugios-1438` |
| 1442 | Reposición contra multa por incorporación a la circulación | 2004 | `reposicion-contra-multa-incorporacion-circulacion-1442` |
| 1443 | Reposición contra multa por conducta ante vehículos prioritarios | 2004 | `reposicion-contra-multa-conducta-ante-vehiculos-1443` |
| 1459 | Reposición contra multa por entorpecer la circulación o causar peligro, molestias o daños | 2004 | `reposicion-contra-multa-entorpecer-circulacion-causar-1459` |
| 1478 | Reposición contra multa por circulación de animales: normas especiales | 2004 | `reposicion-contra-multa-circulacion-animales-normas-1478` |
| 1481 | Reposición contra multa por animales en autopistas y autovías | 2004 | `reposicion-contra-multa-animales-autopistas-autovias-1481` |
| 1486 | Reposición contra multa por detenerse en paso a nivel, puente móvil o túnel | 2004 | `reposicion-contra-multa-detenerse-paso-nivel-puente-1486` |
| 1487 | Reposición contra multa por pasos a nivel y puentes móviles | 2004 | `reposicion-contra-multa-pasos-nivel-puentes-moviles-1487` |
| 1491 | Reposición contra multa por maniobra de parada y estacionamiento | 2004 | `reposicion-contra-multa-maniobra-parada-estacionamiento-1491` |
| 1492 | Reposición contra multa por maniobra de adelantamiento | 2004 | `reposicion-contra-multa-maniobra-adelantamiento-1492` |
| 1493 | Reposición contra multa por colocación del vehículo al estacionar | 2004 | `reposicion-contra-multa-colocacion-vehiculo-estacionar-1493` |
| 1494 | Reposición contra multa por parada y estacionamiento | 2004 | `reposicion-contra-multa-parada-estacionamiento-1494` |
| 1495 | Reposición contra multa por adelantar donde está prohibido | 2004 | `reposicion-contra-multa-adelantar-donde-esta-prohibido-1495` |
| 1496 | Reposición contra multa por parar o estacionar en lugar prohibido | 2004 | `reposicion-contra-multa-parar-estacionar-lugar-prohibido-1496` |
| 1497 | Reposición contra multa por adelantar con obstáculos | 2004 | `reposicion-contra-multa-adelantar-obstaculos-1497` |
| 1498 | Reposición contra multa por adelantamiento en supuestos especiales | 2004 | `reposicion-contra-multa-adelantamiento-supuestos-1498` |
| 1499 | Reposición contra multa por obligaciones del conductor adelantado | 2004 | `reposicion-contra-multa-obligaciones-conductor-1499` |
| 1507 | Reposición contra multa por circulación de animales: normas generales | 2004 | `reposicion-contra-multa-circulacion-animales-normas-1507` |
| 1508 | Reposición contra multa a peatón por circular de noche | 2004 | `reposicion-contra-multa-peaton-circular-noche-1508` |
| 1509 | Reposición contra multa a peatón por circular por calzada o arcén | 2004 | `reposicion-contra-multa-peaton-circular-calzada-arcen-1509` |
| 1510 | Reposición contra multa a peatón por circular en autopista o autovía | 2004 | `reposicion-contra-multa-peaton-circular-autopista-1510` |
| 1511 | Reposición contra multa por circular por zona peatonal | 2004 | `reposicion-contra-multa-circular-zona-peatonal-1511` |
| 1513 | Reposición contra multa a peatón por cruzar la calzada | 2004 | `reposicion-contra-multa-peaton-cruzar-calzada-1513` |
| 1514 | Reposición contra multa por uso indebido de carriles en poblado con más de un carril por sentido | 2004 | `reposicion-contra-multa-uso-indebido-carriles-poblado-1514` |
| 1517 | Reposición contra multa por carriles fuera de poblado con más de un carril por sentido | 2004 | `reposicion-contra-multa-carriles-fuera-poblado-mas-1517` |
| 1518 | Reposición contra multa por utilización de carriles en calzadas de doble sentido | 2004 | `reposicion-contra-multa-utilizacion-carriles-calzadas-1518` |
| 1519 | Reposición contra multa por infracción en carriles de doble sentido de circulación | 2004 | `reposicion-contra-multa-infraccion-carriles-doble-1519` |
| 1521 | Reposición contra multa por carriles fuera de poblado con tres o más carriles por sentido | 2004 | `reposicion-contra-multa-carriles-fuera-poblado-tres-mas-1521` |
| 1524 | Reposición contra multa por obligaciones de quien adelanta | 2004 | `reposicion-contra-multa-obligaciones-quien-adelanta-1524` |
| 1525 | Reposición contra multa por maniobra de cambio de sentido | 2004 | `reposicion-contra-multa-maniobra-cambio-sentido-1525` |
| 1526 | Reposición contra multa por cambio de dirección en supuestos especiales | 2004 | `reposicion-contra-multa-cambio-direccion-supuestos-1526` |
| 1527 | Reposición contra multa por marcha atrás: normas generales | 2004 | `reposicion-contra-multa-marcha-atras-normas-generales-1527` |
| 1528 | Reposición contra multa por adelantar en calzada de varios carriles | 2004 | `reposicion-contra-multa-adelantar-calzada-varios-1528` |
| 1529 | Reposición contra multa por cambio de sentido en supuestos especiales | 2004 | `reposicion-contra-multa-cambio-sentido-supuestos-1529` |
| 1530 | Reposición contra multa por maniobra de marcha atrás | 2004 | `reposicion-contra-multa-maniobra-marcha-atras-1530` |
| 1531 | Reposición contra multa por adelantar por la izquierda | 2004 | `reposicion-contra-multa-adelantar-izquierda-1531` |
| 1532 | Reposición contra multa por carril de deceleración | 2004 | `reposicion-contra-multa-carril-deceleracion-1532` |
| 1533 | Reposición contra multa por detenerse indebidamente en una intersección | 2004 | `reposicion-contra-multa-detenerse-indebidamente-1533` |
| 1534 | Reposición contra multa por no ceder prioridad a peatones | 2004 | `reposicion-contra-multa-no-ceder-prioridad-peatones-1534` |
| 1535 | Reposición contra multa por no ceder prioridad a animales | 2004 | `reposicion-contra-multa-no-ceder-prioridad-animales-1535` |
| 1539 | Reposición contra multa por prioridad en tramos de gran pendiente | 2004 | `reposicion-contra-multa-prioridad-tramos-gran-pendiente-1539` |
| 1540 | Reposición contra multa por normas generales de prioridad de paso | 2004 | `reposicion-contra-multa-normas-generales-prioridad-paso-1540` |
| 1541 | Reposición contra multa por no guardar la distancia entre vehículos | 2004 | `reposicion-contra-multa-no-guardar-distancia-entre-1541` |
| 1542 | Reposición contra multa por exceso de velocidad en vía urbana o travesía | 2004 | `reposicion-contra-multa-exceso-velocidad-via-urbana-1542` |
| 1543 | Reposición contra multa por velocidades prevalentes sobre la máxima | 2004 | `reposicion-contra-multa-velocidades-prevalentes-sobre-1543` |
| 1544 | Reposición contra multa por velocidad mínima | 2004 | `reposicion-contra-multa-velocidad-minima-1544` |
| 1545 | Reposición contra multa por la forma de reducir la velocidad | 2004 | `reposicion-contra-multa-forma-reducir-velocidad-1545` |
| 1548 | Reposición contra multa por carriles en sentido contrario al habitual | 2004 | `reposicion-contra-multa-carriles-sentido-contrario-1548` |
| 1550 | Reposición contra multa por uso del arcén | 2004 | `reposicion-contra-multa-uso-arcen-1550` |
| 1551 | Reposición contra multa por uso indebido de vías divididas en dos o tres calzadas | 2004 | `reposicion-contra-multa-uso-indebido-vias-divididas-dos-1551` |
| 1552 | Reposición contra multa por carriles reversibles | 2004 | `reposicion-contra-multa-carriles-reversibles-1552` |
| 1553 | Reposición contra multa por circulación en autopistas y autovías | 2004 | `reposicion-contra-multa-circulacion-autopistas-autovias-1553` |
| 1554 | Reposición contra multa por exceso de velocidad fuera de poblado | 2004 | `reposicion-contra-multa-exceso-velocidad-fuera-poblado-1554` |
| 1555 | Reposición contra multa por no moderar la velocidad | 2004 | `reposicion-contra-multa-no-moderar-velocidad-1555` |
| 1560 | Reposición contra multa por falta de control del vehículo o los animales | 2004 | `reposicion-contra-multa-falta-control-vehiculo-animales-1560` |
| 1578 | Reposición contra multa por cambio de dirección: normas generales | 2004 | `reposicion-contra-multa-cambio-direccion-normas-1578` |
| 1579 | Reposición contra multa por facultades de conductores de vehículos prioritarios | 2004 | `reposicion-contra-multa-facultades-conductores-vehiculos-1579` |
| 1580 | Reposición contra multa por maniobra de cambio de dirección | 2004 | `reposicion-contra-multa-maniobra-cambio-direccion-1580` |
| 1582 | Reposición contra multa por vehículos prioritarios | 2004 | `reposicion-contra-multa-vehiculos-prioritarios-1582` |
| 1584 | Reposición contra multa por vehículos no prioritarios en servicio de urgencia | 2004 | `reposicion-contra-multa-vehiculos-no-prioritarios-1584` |
