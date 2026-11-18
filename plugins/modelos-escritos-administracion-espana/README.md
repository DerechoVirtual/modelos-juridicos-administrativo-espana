# Escritos ante la Administración (Ley 39/2015) · España

> Plugin de Claude Code `modelos-escritos-administracion-espana` · **277 formularios** · área: Administrativo · revisado el 17-11-2026 · requiere Jurisprudenciator

## Para qué sirve

Sirve para los escritos del día a día ante la Administración (Ley 39/2015): solicitudes, alegaciones y trámite de audiencia, acceso y copia del expediente, certificados de silencio, notificaciones y plazos, además de los modelos de los actos que dicta la propia Administración.

Cada formulario es una skill: Claude lo rellena contigo paso a paso y te entrega el escrito en Word, con las normas comprobadas en el BOE.

## Qué puedes hacer con él

Estos son los tipos de escrito que trae, con algunos ejemplos (la lista completa de los 277 está al final):

- **Contestaciones, oposiciones y alegaciones** (20). Por ejemplo: Alegaciones en procedimiento administrativo simplificado; Alegaciones en expediente de contrabando por importar una pieza de fauna; Alegaciones del interesado en actuaciones complementarias ordenadas por el órgano resolutor.
- **Solicitudes y expedientes** (56). Por ejemplo: Pedir garantías al encargado del tratamiento de datos; Pedir certificado de denegación por silencio administrativo; Pedir tramitación ordinaria por necesitar trámites adicionales.
- **Escritos de trámite** (44). Por ejemplo: Subsanar la solicitud de tramitación simplificada; Oposición del particular a la tramitación simplificada acordada de oficio; Comunicar el cambio del medio de notificación.
- **Actos y resoluciones de la Administración o del órgano judicial** (99). Por ejemplo: Resolución final en el procedimiento simplificado; Dictamen del Consejo de Estado u órgano autonómico equivalente sobre nulidad de actos; Notificar al interesado la tramitación simplificada del procedimiento.
- **Contratos, escrituras y documentos** (9). Por ejemplo: Modelo genérico de alegaciones; Pedir la notificación telemática en un expediente administrativo; Otorgar representación ante la Administración.
- **Comunicaciones, requerimientos y reclamaciones** (27). Por ejemplo: Denuncia de un particular para que se inicie un procedimiento administrativo; Requerimiento al inquilino sobre causas de posposición ante la prórroga por necesidad; Reclamación entre propietarios por daños en una vivienda.
- **Otros** (22). Por ejemplo: Actuaciones previas al procedimiento administrativo; Declarar qué datos de la oferta son confidenciales; Convenio de un Ayuntamiento: contenido mínimo.

## Cómo se usa

1. **Pídelo con tus palabras.** Cuéntale a Claude qué escrito necesitas y para qué caso; él elige el formulario. Por ejemplo:
   - «Pedir copia de los documentos del expediente como interesado»
   - «Alegaciones en el trámite de audiencia y vista del expediente»
   - «Pedir un certificado de silencio administrativo»
2. **Si no da con el formulario**, empieza por el índice del plugin: escribe `/modelos-escritos-administracion-espana:indice` y cuéntale lo que necesitas. Te propondrá el formulario que mejor encaja (o dos o tres para que elijas).
3. **Si ya sabes cuál quieres**, llámalo por su nombre de skill, por ejemplo `/modelos-escritos-administracion-espana:resolucion-final-procedimiento-simplificado-35`. Los nombres están en la lista de formularios de abajo.

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
- **Espacio que ocupa:** unos 26.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-escritos-administracion-espana@modelos-juridicos-administrativo-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
claude plugin install modelos-escritos-administracion-espana@modelos-juridicos-administrativo-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

