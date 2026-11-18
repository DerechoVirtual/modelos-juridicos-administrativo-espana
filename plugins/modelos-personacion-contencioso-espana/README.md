# Contencioso: personaciones, competencia y representación · España

> Plugin de Claude Code `modelos-personacion-contencioso-espana` · **96 formularios** · área: Administrativo · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para los escritos sobre partes, órgano y representación en el contencioso-administrativo: personaciones (codemandados, Administraciones, entidades locales), representación y defensa, competencia del órgano tras la implantación de los Tribunales de Instancia, cuestiones de incompetencia y suspensión del procedimiento mientras se resuelve un recurso de casación con el mismo objeto.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 96 está al final):

- **Recursos e impugnaciones** (10). Por ejemplo: Impugnar por defecto de jurisdicción; Reposición contra el auto que declara falta de competencia a favor del TSJ; Reposición contra la orden a la Diputación de comparecer con procurador (órganos colegiados).
- **Contestaciones, oposiciones y alegaciones** (8). Por ejemplo: Alegaciones de las partes sobre el efecto de la sentencia de casación en el procedimiento; Alegaciones sobre suspender el procedimiento por un recurso de casación similar admitido; Alegaciones ante declinatoria de jurisdicción en contratos públicos.
- **Solicitudes y expedientes** (5). Por ejemplo: Abogado del Estado pide suspender por posible prescripción de la sanción; Pedir testimonio al abogado del Estado para el apremio administrativo; Nulidad por infracción de las normas de reparto.
- **Escritos de trámite** (28). Por ejemplo: Comparecer como recurrido y oponerse a la admisión de la casación; Impugnar la denegación de asistencia jurídica gratuita; Personación y alegaciones de la Administración en protección de derechos fundamentales.
- **Actos y resoluciones de la Administración o del órgano judicial** (40). Por ejemplo: Diligencia que da plazo para alegar sobre suspender el pleito por una casación similar; Auto que alza la suspensión y da traslado para alegar sobre la sentencia de casación; Auto que suspende el procedimiento por identidad con un recurso de casación admitido.
- **Contratos, escrituras y documentos** (1). Por ejemplo: Acreditar los requisitos para que una persona jurídica litigue ante lo contencioso.
- **Otros** (4). Por ejemplo: Asistencia jurídica gratuita: impugnación por la parte contraria de la resolución estimatoria; Conflicto de competencia territorial entre órganos (negativo); Asistencia jurídica gratuita: pedir suspender el procedimiento hasta resolver la Comisión.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Personación de un codemandado particular en un recurso contencioso»
   - «Alegaciones previas por falta de competencia del órgano»
   - «Personación ante la Audiencia Nacional después de que el TSJ se declare incompetente»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-personacion-contencioso-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-personacion-contencioso-espana:diligencia-da-plazo-alegar-sobre-suspender-pleito-7`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 10.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-personacion-contencioso-espana@modelos-juridicos-administrativo-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
claude plugin install modelos-personacion-contencioso-espana@modelos-juridicos-administrativo-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

