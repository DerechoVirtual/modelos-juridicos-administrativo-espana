# Multas de tráfico: demandas, solicitudes y trámites · España

> Plugin de Claude Code `modelos-multas-trafico-espana` · **108 formularios** · área: Administrativo · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para el resto del expediente sancionador de tráfico: la demanda contra la sanción y el recurso extraordinario de revisión, la identificación del conductor, solicitudes y escritos de trámite, quejas por defectos de tramitación, notificaciones y resoluciones de la Administración, y otros documentos de seguridad vial.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 108 está al final):

- **Demandas, interposiciones y peticiones iniciales** (2). Por ejemplo: Demanda abreviada contra multa por circular por Madrid Central; Recurso extraordinario de revisión contra sanciones de tráfico.
- **Solicitudes y expedientes** (24). Por ejemplo: Petición de información al juzgado por proceso penal sobre los mismos hechos; Reclamar a la Administración por accidente de circulación con vehículo de su propiedad; Petición razonada de otros órganos para iniciar un sancionador de tráfico.
- **Escritos de trámite** (20). Por ejemplo: Propuesta de resolución en sancionador de tráfico; Queja por defectos de tramitación en el expediente sancionador; Instructor que pide colaboración a otros órganos en el expediente sancionador.
- **Actos y resoluciones de la Administración o del órgano judicial** (42). Por ejemplo: Notificación de la resolución sancionadora de la Jefatura de Tráfico; Notificación de la resolución sancionadora de tráfico de una Alcaldía; Resolución sancionadora de una Jefatura de Tráfico.
- **Contratos, escrituras y documentos** (3). Por ejemplo: Convenio entre una Administración y una entidad privada para fomentar la seguridad vial; Modelo de estatutos de asociación de seguridad vial o de víctimas de accidentes de tráfico; Solicitud y adhesión para una distinción honorífica en tráfico, transportes o seguridad vial.
- **Comunicaciones, requerimientos y reclamaciones** (5). Por ejemplo: Comunicar a otros órganos indicios de infracción; Reclamación de la aseguradora por lo pagado a su asegurado en un accidente de circulación; Denuncia de un usuario contra un taller por incumplir las condiciones de su autorización.
- **Otros** (12). Por ejemplo: Remitir al Ministerio Fiscal las actuaciones del sancionador; Titular que identifica al conductor del vehículo; Defecto de tramitación: falta de práctica, solicitud de prueba.

Los demás formularios de multas de tráfico están en estos plugins:

- `modelos-recursos-multas-circulacion-espana`: Recurrir multas de circulación, velocidad y maniobras · España
- `modelos-recursos-multas-senales-y-vehiculo-espana`: Recurrir multas por señales, alumbrado, alcohol y documentación · España
- `modelos-alegaciones-multas-trafico-espana`: Alegaciones y descargos contra denuncias de tráfico · España

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Escrito del titular identificando al conductor del vehículo»
   - «Demanda contra una multa por circular por una zona de bajas emisiones»
   - «Queja por defectos de tramitación en el expediente sancionador»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-multas-trafico-espana:demanda-abreviada-contra-multa-circular-madrid-central-55` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-multas-trafico-espana:demanda-abreviada-contra-multa-circular-madrid-central-55`. Los nombres están en la lista de formularios de abajo.

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

- **Dónde funciona:** en Claude Code y en Claude (web, escritorio y Cowork).
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 9.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-multas-trafico-espana@modelos-juridicos-administrativo-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
claude plugin install modelos-multas-trafico-espana@modelos-juridicos-administrativo-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

