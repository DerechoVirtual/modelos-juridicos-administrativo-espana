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

- **Dónde funciona:** en Claude Code y en Claude (web, escritorio y Cowork).
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 5.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-recursos-administrativos-espana@modelos-juridicos-administrativo-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
claude plugin install modelos-recursos-administrativos-espana@modelos-juridicos-administrativo-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

