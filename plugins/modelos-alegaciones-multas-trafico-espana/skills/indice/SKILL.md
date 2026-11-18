---
name: indice
description: "Índice de los 157 formularios de alegaciones y descargos frente a denuncias de tráfico. Úsala cuando el usuario pida un escrito de esta materia y no esté claro qué formulario usar: elige la skill del formulario adecuado. Requiere Jurisprudenciator."
---

# Alegaciones y descargos contra denuncias de tráfico: índice de formularios

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

Busca por tipo de documento y título. Cada formulario es una skill de este plugin (`/modelos-alegaciones-multas-trafico-espana:<skill>`). Si dudas entre dos, elige el más reciente o el que mejor encaje con los hechos y dilo; si la petición es ambigua, propón al usuario los dos o tres formularios que mejor encajan y pregúntale cuál quiere. Las reglas del tema están en `marco.md`.

## Cómo usar el formulario elegido

Invoca su skill. Si esa skill no aparece en tu lista de skills disponibles (puede pasar cuando hay muchas skills instaladas), lee directamente su fichero `SKILL.md`: está en `skills/<skill>/SKILL.md` dentro de este plugin, en la carpeta hermana de la de esta skill `indice` (`../<skill>/SKILL.md`). Síguelo igual que si la hubieras invocado, con el «Texto del formulario» que lleva al final y el `marco.md` de esta skill `indice`.

## Otros plugins de multas de tráfico

Los formularios de multas de tráfico están repartidos en cuatro plugins. Si el escrito que se pide no está en este índice, búscalo en estos:

- `modelos-recursos-multas-circulacion-espana`: Recurrir multas de circulación, velocidad y maniobras · España
- `modelos-recursos-multas-senales-y-vehiculo-espana`: Recurrir multas por señales, alumbrado, alcohol y documentación · España
- `modelos-multas-trafico-espana`: Multas de tráfico: demandas, solicitudes y trámites · España

## Contestaciones, oposiciones y alegaciones (157)

| Nº | Formulario | Año | Skill |
|---|---|---|---|
| 21 | Descargos por incumplir restricciones de circulación por contaminación | 2022 | `descargos-incumplir-restricciones-circulacion-21` |
| 23 | Descargos por incumplir las normas del alcoholímetro antiarranque | 2022 | `descargos-incumplir-normas-alcoholimetro-antiarranque-23` |
| 26 | Descargos por usar dispositivos de intercomunicación en pruebas de permisos | 2022 | `descargos-usar-dispositivos-intercomunicacion-pruebas-26` |
| 163 | Alegaciones adicionales en cualquier fase del expediente | 2017 | `alegaciones-adicionales-cualquier-fase-expediente-163` |
| 174 | Alegaciones frente a la propuesta de resolución | 2017 | `alegaciones-frente-propuesta-resolucion-174` |
| 181 | Alegaciones por calificar mal la infracción en el boletín de denuncia | 2016 | `alegaciones-calificar-mal-infraccion-boletin-denuncia-181` |
| 182 | Alegaciones en audiencia sobre medidas cautelares de tráfico y seguridad vial | 2016 | `alegaciones-audiencia-sobre-medidas-cautelares-trafico-182` |
| 183 | Descargos por no identificar al conductor responsable | 2016 | `descargos-no-identificar-conductor-responsable-183` |
| 223 | Contestar a la petición razonada comunicando que no se incoa sancionador de tráfico | 2016 | `contestar-peticion-razonada-comunicando-no-incoa-223` |
| 260 | Alegaciones contra multa de tráfico en sancionador | 2016 | `alegaciones-contra-multa-trafico-sancionador-260` |
| 298 | Alegaciones en sancionador ordinario de tráfico | 2014 | `alegaciones-sancionador-ordinario-trafico-298` |
| 304 | Alegaciones por usar navegador con detector de radares | 2013 | `alegaciones-usar-navegador-detector-radares-304` |
| 318 | Alegaciones: multa al titular sin detener el vehículo ni requerirle identificar al conductor | 2013 | `alegaciones-multa-titular-sin-detener-vehiculo-ni-318` |
| 320 | Alegaciones por denegarse la prueba propuesta | 2013 | `alegaciones-denegarse-prueba-propuesta-320` |
| 590 | Alegaciones por retirada del vehículo | 2011 | `alegaciones-retirada-vehiculo-590` |
| 1304 | Alegaciones del conductor ante la pérdida de vigencia del permiso por perder todos los puntos | 2006 | `alegaciones-conductor-ante-perdida-vigencia-permiso-1304` |
| 1432 | Descargos por no respetar la prioridad en intersección señalizada | 2004 | `descargos-no-respetar-prioridad-interseccion-senalizada-1432` |
| 1433 | Descargos por dejar en la vía objetos que afectan a la seguridad | 2004 | `descargos-dejar-via-objetos-afectan-seguridad-1433` |
| 1434 | Descargos por exceso de velocidad en vía urbana o travesía | 2004 | `descargos-exceso-velocidad-via-urbana-travesia-1434` |
| 1435 | Descargos por tasa de alcohol en sangre o aire espirado | 2004 | `descargos-tasa-alcohol-sangre-aire-espirado-1435` |
| 1441 | Descargos por incumplir señales de restricción de paso | 2004 | `descargos-incumplir-senales-restriccion-paso-1441` |
| 1452 | Descargos por circulación de animales: normas especiales | 2004 | `descargos-circulacion-animales-normas-especiales-1452` |
| 1453 | Descargos por advertencias acústicas | 2004 | `descargos-advertencias-acusticas-1453` |
| 1454 | Descargos por uso del alumbrado durante el día | 2004 | `descargos-uso-alumbrado-durante-dia-1454` |
| 1455 | Descargos por adelantamiento en lugar prohibido | 2004 | `descargos-adelantamiento-lugar-prohibido-1455` |
| 1456 | Descargos por adelantamiento en calzada de varios carriles | 2004 | `descargos-adelantamiento-calzada-varios-carriles-1456` |
| 1457 | Descargos por cambio de sentido en supuestos especiales | 2004 | `descargos-cambio-sentido-supuestos-especiales-1457` |
| 1564 | Descargos por no tener seguro obligatorio del automóvil | 2004 | `descargos-no-tener-seguro-obligatorio-automovil-1564` |
| 1570 | Descargos por centros de reconocimiento de conductores | 2004 | `descargos-centros-reconocimiento-conductores-1570` |
| 1571 | Descargos por escuelas particulares de conductores | 2004 | `descargos-escuelas-particulares-conductores-1571` |
| 1572 | Descargos por señales horizontales de circulación | 2004 | `descargos-senales-horizontales-circulacion-1572` |
| 1573 | Descargos por marcas de otros colores | 2004 | `descargos-marcas-otros-colores-1573` |
| 1574 | Descargos por permisos de conducción | 2004 | `descargos-permisos-conduccion-1574` |
| 1575 | Descargos por otras marcas e inscripciones blancas | 2004 | `descargos-otras-marcas-e-inscripciones-blancas-1575` |
| 1576 | Descargos por matrículas obligatorias | 2004 | `descargos-matriculas-obligatorias-1576` |
| 1577 | Descargos por permiso de circulación y documentación del vehículo | 2004 | `descargos-permiso-circulacion-documentacion-vehiculo-1577` |
| 1585 | Descargos por señales de indicaciones generales | 2004 | `descargos-senales-indicaciones-generales-1585` |
| 1586 | Descargos por marcas blancas longitudinales | 2004 | `descargos-marcas-blancas-longitudinales-1586` |
| 1587 | Descargos por saltarse una señal de prioridad | 2004 | `descargos-saltarse-senal-prioridad-1587` |
| 1588 | Descargos por señales de obligación | 2004 | `descargos-senales-obligacion-1588` |
| 1589 | Descargos por marcas blancas transversales | 2004 | `descargos-marcas-blancas-transversales-1589` |
| 1590 | Descargos por señales de carriles | 2004 | `descargos-senales-carriles-1590` |
| 1591 | Descargos por otras señales de prohibición o restricción | 2004 | `descargos-otras-senales-prohibicion-restriccion-1591` |
| 1592 | Descargos por señales de prohibición de entrada | 2004 | `descargos-senales-prohibicion-entrada-1592` |
| 1593 | Descargos por circulación en autopistas y autovías | 2004 | `descargos-circulacion-autopistas-autovias-1593` |
| 1594 | Descargos por uso indebido de carriles fuera de poblado con tres o más carriles por sentido | 2004 | `descargos-uso-indebido-carriles-fuera-poblado-tres-mas-1594` |
| 1595 | Descargos por infracción en carriles de doble sentido de circulación | 2004 | `descargos-infraccion-carriles-doble-sentido-circulacion-1595` |
| 1596 | Descargos por limitaciones a la circulación | 2004 | `descargos-limitaciones-circulacion-1596` |
| 1597 | Descargos por uso indebido de carriles en poblado con más de un carril por sentido | 2004 | `descargos-uso-indebido-carriles-poblado-mas-carril-1597` |
| 1598 | Descargos por carriles en sentido contrario al habitual | 2004 | `descargos-carriles-sentido-contrario-habitual-1598` |
| 1599 | Descargos por uso del arcén | 2004 | `descargos-uso-arcen-1599` |
| 1600 | Descargos por uso indebido de carriles fuera de poblado con más de un carril por sentido | 2004 | `descargos-uso-indebido-carriles-fuera-poblado-mas-carril-1600` |
| 1601 | Descargos por carriles reversibles | 2004 | `descargos-carriles-reversibles-1601` |
| 1602 | Descargos por conducir con estupefacientes, psicotrópicos o sustancias análogas | 2004 | `descargos-conducir-estupefacientes-psicotropicos-1602` |
| 1603 | Descargos por utilización de carriles en calzadas de doble sentido | 2004 | `descargos-utilizacion-carriles-calzadas-doble-sentido-1603` |
| 1604 | Descargos por pruebas de detección de estupefacientes | 2004 | `descargos-pruebas-deteccion-estupefacientes-1604` |
| 1605 | Descargos por incumplimientos del personal sanitario sobre bebidas alcohólicas | 2004 | `descargos-incumplimientos-personal-sanitario-sobre-1605` |
| 1606 | Descargos por la investigación de la alcoholemia | 2004 | `descargos-investigacion-alcoholemia-1606` |
| 1607 | Descargos por libertad de movimientos, atención, posición, animales y auriculares | 2004 | `descargos-libertad-movimientos-atencion-posicion-1607` |
| 1608 | Descargos por falta de control del vehículo o los animales | 2004 | `descargos-falta-control-vehiculo-animales-1608` |
| 1609 | Descargos por falta de visibilidad del vehículo | 2004 | `descargos-falta-visibilidad-vehiculo-1609` |
| 1610 | Descargos por disposición de la carga | 2004 | `descargos-disposicion-carga-1610` |
| 1611 | Descargos por transporte de personas | 2004 | `descargos-transporte-personas-1611` |
| 1612 | Descargos por dimensiones del vehículo y su carga | 2004 | `descargos-dimensiones-vehiculo-carga-1612` |
| 1613 | Descargos por transporte colectivo de personas | 2004 | `descargos-transporte-colectivo-personas-1613` |
| 1614 | Descargos por emplazamiento y acondicionamiento de personas | 2004 | `descargos-emplazamiento-acondicionamiento-personas-1614` |
| 1615 | Descargos por dimensiones de la carga | 2004 | `descargos-dimensiones-carga-1615` |
| 1616 | Descargos por carga y descarga | 2004 | `descargos-carga-descarga-1616` |
| 1617 | Descargos por transporte en ciclos, ciclomotores y motocicletas | 2004 | `descargos-transporte-ciclos-ciclomotores-motocicletas-1617` |
| 1618 | Descargos por emisión de perturbaciones y contaminantes sobre los límites | 2004 | `descargos-emision-perturbaciones-contaminantes-sobre-1618` |
| 1619 | Descargos por arrojar a la vía un objeto que puede causar incendio o peligro | 2004 | `descargos-arrojar-via-objeto-puede-causar-incendio-1619` |
| 1620 | Descargos por no señalizar obstáculos o peligros creados en la vía | 2004 | `descargos-no-senalizar-obstaculos-peligros-creados-via-1620` |
| 1621 | Descargos por conducción negligente o temeraria | 2004 | `descargos-conduccion-negligente-temeraria-1621` |
| 1622 | Descargos por entorpecer la circulación o causar peligro, molestias o daños | 2004 | `descargos-entorpecer-circulacion-causar-peligro-1622` |
| 1623 | Descargos por velocidades prevalentes sobre la máxima | 2004 | `descargos-velocidades-prevalentes-sobre-maxima-1623` |
| 1624 | Descargos por sentido de circulación en refugios, isletas y dispositivos de guía | 2004 | `descargos-sentido-circulacion-refugios-isletas-1624` |
| 1625 | Descargos por exceso de velocidad fuera de poblado | 2004 | `descargos-exceso-velocidad-fuera-poblado-1625` |
| 1626 | Descargos por la forma de reducir la velocidad | 2004 | `descargos-forma-reducir-velocidad-1626` |
| 1627 | Descargos por no moderar la velocidad | 2004 | `descargos-no-moderar-velocidad-1627` |
| 1628 | Descargos por velocidad mínima en poblado y fuera de poblado | 2004 | `descargos-velocidad-minima-poblado-fuera-poblado-1628` |
| 1629 | Descargos por uso indebido de vías divididas en dos o tres calzadas | 2004 | `descargos-uso-indebido-vias-divididas-dos-tres-calzadas-1629` |
| 1630 | Descargos por inmovilizar el vehículo y caída de la carga | 2004 | `descargos-inmovilizar-vehiculo-caida-carga-1630` |
| 1631 | Descargos por desobedecer señales u órdenes de la autoridad o sus agentes | 2004 | `descargos-desobedecer-senales-u-ordenes-autoridad-1631` |
| 1632 | Descargos por semáforo para peatones | 2004 | `descargos-semaforo-peatones-1632` |
| 1633 | Descargos por formato de las señales | 2004 | `descargos-formato-senales-1633` |
| 1634 | Descargos por semáforos cuadrados o de carril | 2004 | `descargos-semaforos-cuadrados-carril-1634` |
| 1635 | Descargos por semáforos reservados | 2004 | `descargos-semaforos-reservados-1635` |
| 1636 | Descargos por saltarse un semáforo circular | 2004 | `descargos-saltarse-semaforo-circular-1636` |
| 1637 | Descargos por señales de balizamiento | 2004 | `descargos-senales-balizamiento-1637` |
| 1638 | Descargos por retirar, sustituir o alterar señales | 2004 | `descargos-retirar-sustituir-alterar-senales-1638` |
| 1639 | Descargos por adelantar por la izquierda | 2004 | `descargos-adelantar-izquierda-1639` |
| 1640 | Descargos por adelantar con obstáculos | 2004 | `descargos-adelantar-obstaculos-1640` |
| 1641 | Descargos por obligaciones de quien adelanta | 2004 | `descargos-obligaciones-quien-adelanta-1641` |
| 1642 | Descargos por parada y estacionamiento | 2004 | `descargos-parada-estacionamiento-1642` |
| 1643 | Descargos por obligaciones del conductor adelantado | 2004 | `descargos-obligaciones-conductor-adelantado-1643` |
| 1644 | Descargos por maniobra de parada y estacionamiento | 2004 | `descargos-maniobra-parada-estacionamiento-1644` |
| 1645 | Descargos por adelantamiento en supuestos especiales | 2004 | `descargos-adelantamiento-supuestos-especiales-1645` |
| 1646 | Descargos por maniobra de adelantamiento | 2004 | `descargos-maniobra-adelantamiento-1646` |
| 1647 | Descargos por advertencias ópticas | 2004 | `descargos-advertencias-opticas-1647` |
| 1648 | Descargos por supuestos especiales de alumbrado | 2004 | `descargos-supuestos-especiales-alumbrado-1648` |
| 1649 | Descargos por inmovilizaciones | 2004 | `descargos-inmovilizaciones-1649` |
| 1650 | Descargos por alumbrado de la placa de matrícula | 2004 | `descargos-alumbrado-placa-matricula-1650` |
| 1651 | Descargos por alumbrado de cruce | 2004 | `descargos-alumbrado-cruce-1651` |
| 1652 | Descargos por alumbrado inutilizado o averiado | 2004 | `descargos-alumbrado-inutilizado-averiado-1652` |
| 1653 | Descargos por deslumbramiento | 2004 | `descargos-deslumbramiento-1653` |
| 1654 | Descargos por parar o estacionar en lugar prohibido | 2004 | `descargos-parar-estacionar-lugar-prohibido-1654` |
| 1655 | Descargos por pasos a nivel y puentes móviles | 2004 | `descargos-pasos-nivel-puentes-moviles-1655` |
| 1656 | Descargos por barreras, semibarreras y semáforos | 2004 | `descargos-barreras-semibarreras-semaforos-1656` |
| 1657 | Descargos por alumbrado de posición y gálibo | 2004 | `descargos-alumbrado-posicion-galibo-1657` |
| 1658 | Descargos por infringir ordenanzas municipales de parada y estacionamiento | 2004 | `descargos-infringir-ordenanzas-municipales-parada-1658` |
| 1659 | Descargos por detenerse en paso a nivel, puente móvil o túnel | 2004 | `descargos-detenerse-paso-nivel-puente-movil-tunel-1659` |
| 1660 | Descargos por colocación del vehículo al estacionar | 2004 | `descargos-colocacion-vehiculo-estacionar-1660` |
| 1661 | Descargos por alumbrado de carretera | 2004 | `descargos-alumbrado-carretera-1661` |
| 1662 | Descargos por incorporación a la circulación | 2004 | `descargos-incorporacion-circulacion-1662` |
| 1663 | Descargos por vehículos prioritarios | 2004 | `descargos-vehiculos-prioritarios-1663` |
| 1664 | Descargos por no ceder prioridad a animales | 2004 | `descargos-no-ceder-prioridad-animales-1664` |
| 1665 | Descargos por prioridad en tramos de gran pendiente | 2004 | `descargos-prioridad-tramos-gran-pendiente-1665` |
| 1666 | Descargos por no ceder prioridad a peatones | 2004 | `descargos-no-ceder-prioridad-peatones-1666` |
| 1667 | Descargos por vehículos y transportes especiales | 2004 | `descargos-vehiculos-transportes-especiales-1667` |
| 1668 | Descargos por vehículos no prioritarios en servicio de urgencia | 2004 | `descargos-vehiculos-no-prioritarios-servicio-urgencia-1668` |
| 1669 | Descargos por conducta ante vehículos prioritarios | 2004 | `descargos-conducta-ante-vehiculos-prioritarios-1669` |
| 1670 | Descargos por facultades de conductores de vehículos prioritarios | 2004 | `descargos-facultades-conductores-vehiculos-prioritarios-1670` |
| 1671 | Descargos por transportes terrestres por carretera | 2004 | `descargos-transportes-terrestres-carretera-1671` |
| 1672 | Descargos por casco y otros elementos de protección | 2004 | `descargos-casco-otros-elementos-proteccion-1672` |
| 1673 | Descargos por advertencias a otros vehículos | 2004 | `descargos-advertencias-otros-vehiculos-1673` |
| 1674 | Descargos por no apagar el motor | 2004 | `descargos-no-apagar-motor-1674` |
| 1675 | Descargos por advertencias de vehículos de urgencia y especiales | 2004 | `descargos-advertencias-vehiculos-urgencia-especiales-1675` |
| 1676 | Descargos por puertas del vehículo | 2004 | `descargos-puertas-vehiculo-1676` |
| 1677 | Descargos por cinturón o sistema de retención infantil | 2004 | `descargos-cinturon-sistema-retencion-infantil-1677` |
| 1678 | Descargos por no auxiliar en accidente | 2004 | `descargos-no-auxiliar-accidente-1678` |
| 1679 | Descargos de peatón por circular de noche | 2004 | `descargos-peaton-circular-noche-1679` |
| 1680 | Descargos por animales en autopistas y autovías | 2004 | `descargos-animales-autopistas-autovias-1680` |
| 1681 | Descargos por circular por zona peatonal | 2004 | `descargos-circular-zona-peatonal-1681` |
| 1682 | Descargos de peatón por cruzar la calzada | 2004 | `descargos-peaton-cruzar-calzada-1682` |
| 1683 | Descargos de peatón por circular en autopista o autovía | 2004 | `descargos-peaton-circular-autopista-autovia-1683` |
| 1684 | Descargos de peatón por circular por calzada o arcén | 2004 | `descargos-peaton-circular-calzada-arcen-1684` |
| 1685 | Descargos por circulación de animales: normas generales | 2004 | `descargos-circulacion-animales-normas-generales-1685` |
| 1686 | Descargos por cambio de dirección en supuestos especiales | 2004 | `descargos-cambio-direccion-supuestos-especiales-1686` |
| 1687 | Descargos por maniobra de cambio de dirección | 2004 | `descargos-maniobra-cambio-direccion-1687` |
| 1688 | Descargos por marcha atrás: normas generales | 2004 | `descargos-marcha-atras-normas-generales-1688` |
| 1689 | Descargos por carril de deceleración | 2004 | `descargos-carril-deceleracion-1689` |
| 1690 | Descargos por maniobra de marcha atrás | 2004 | `descargos-maniobra-marcha-atras-1690` |
| 1691 | Descargos por incorporación de vehículos de transporte de viajeros | 2004 | `descargos-incorporacion-vehiculos-transporte-viajeros-1691` |
| 1692 | Descargos por cambio de dirección: normas generales | 2004 | `descargos-cambio-direccion-normas-generales-1692` |
| 1693 | Descargos por maniobra de cambio de sentido | 2004 | `descargos-maniobra-cambio-sentido-1693` |
| 1694 | Descargos por prioridad de paso sin señalización | 2004 | `descargos-prioridad-paso-sin-senalizacion-1694` |
| 1695 | Descargos por prioridad de paso en obras y estrechamientos | 2004 | `descargos-prioridad-paso-obras-estrechamientos-1695` |
| 1696 | Descargos por detenerse indebidamente en una intersección | 2004 | `descargos-detenerse-indebidamente-interseccion-1696` |
| 1697 | Descargos por prioridad en intersección sin señalizar | 2004 | `descargos-prioridad-interseccion-sin-senalizar-1697` |
| 1698 | Descargos por no guardar la distancia entre vehículos | 2004 | `descargos-no-guardar-distancia-entre-vehiculos-1698` |
| 1699 | Descargos por prioridad en puentes y obras señalizadas | 2004 | `descargos-prioridad-puentes-obras-senalizadas-1699` |
| 1700 | Descargos por competiciones deportivas | 2004 | `descargos-competiciones-deportivas-1700` |
| 1701 | Descargos por normas generales de prioridad de paso | 2004 | `descargos-normas-generales-prioridad-paso-1701` |
| 1758 | Alegaciones del interesado en la reposición por infracciones de tráfico | 2004 | `alegaciones-interesado-reposicion-infracciones-trafico-1758` |
| 1908 | Alegaciones al inicio por insuficiencia de prueba de cargo en denuncia de tráfico | 2012 | `alegaciones-inicio-insuficiencia-prueba-cargo-denuncia-1908` |
| 1912 | Alegaciones al inicio pidiendo pruebas sobre el aparato medidor de velocidad | 2012 | `alegaciones-inicio-pidiendo-pruebas-sobre-aparato-1912` |
| 1916 | Alegaciones a la propuesta pidiendo pruebas en denuncia de controlador de estacionamiento | 2012 | `alegaciones-propuesta-pidiendo-pruebas-denuncia-1916` |
