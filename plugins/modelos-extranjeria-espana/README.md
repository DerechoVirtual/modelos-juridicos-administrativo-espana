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

- **Dónde funciona:** en Claude Code y en Claude (web, escritorio y Cowork).
- **Jurisprudenciator es imprescindible:** el plugin trae el conector y cada skill trabaja siempre con él, igual que los plugins de Jurisprudenciator del directorio de Claude. Sin una cuenta de Jurisprudenciator conectada, las skills se paran y no redactan nada. La primera vez hay que iniciar sesión (en Claude Code, con `/mcp`; o con tu URL personal: https://jurisprudenciator.lexiaipro.org/instalacion). Si ya tienes Jurisprudenciator conectado en Claude, las skills usan ese.
- **Espacio que ocupa:** unos 8.000 tokens en cada conversación mientras esté activado, porque Claude lleva en memoria la descripción de cada skill. Activa solo los plugins que vayas a usar; los demás puedes desactivarlos sin desinstalarlos (`claude plugin disable modelos-extranjeria-espana@modelos-juridicos-administrativo-espana`).

## Instalación

**En Claude Code**, añade una vez el catálogo de este repositorio y después instala el plugin:

```bash
claude plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
claude plugin install modelos-extranjeria-espana@modelos-juridicos-administrativo-espana
```

Al terminar, abre una conversación nueva para que aparezcan sus skills.

**En Claude (web y escritorio)** también puedes subirlo como ZIP desde **Personalizar → Plugins**. El ZIP de este plugin está en la página de versiones del repositorio: https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest

## Qué hay dentro de cada skill

- `SKILL.md`: los datos que hay que pedir, las elecciones, los párrafos opcionales, los avisos de la revisión, las normas que hay que comprobar y el flujo;
- al final de ese mismo `SKILL.md`, el texto revisado del formulario.

La guía del tema, con las reglas y plazos vigentes comprobados en el BOE, es común a todas las skills del plugin y está en `skills/indice/marco.md`.

