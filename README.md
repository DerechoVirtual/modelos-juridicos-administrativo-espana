# Modelos jurídicos de España para Claude · Administrativo

5 plugins de modelos de escritos de Administrativo, uno por tema. Cada modelo es una skill que Claude rellena paso a paso con los datos del caso: 938 skills en total, más una skill `indice` por plugin para encontrar el modelo adecuado.

Todas las skills trabajan con **Jurisprudenciator** (https://jurisprudenciator.lexiaipro.org): antes de redactar comprueban que el conector responde, verifican en fuentes oficiales los artículos y la jurisprudencia que se citan y revisan el escrito con `verificar_escrito` antes de entregarlo. Sin Jurisprudenciator conectado, las skills no redactan.

Las demás jurisdicciones están en repositorios propios: [Civil](https://github.com/DerechoVirtual/modelos-juridicos-civil-espana), [Laboral](https://github.com/DerechoVirtual/modelos-juridicos-laboral-espana), [Penal](https://github.com/DerechoVirtual/modelos-juridicos-penal-espana).

## Instalación

En Claude Code:

```
/plugin marketplace add DerechoVirtual/modelos-juridicos-administrativo-espana
/plugin install modelos-escritos-administracion-espana@modelos-juridicos-administrativo-espana
```

Cada plugin ocupa contexto en la conversación, así que conviene instalar solo los de los temas con los que se trabaja.

En Claude (web y escritorio) también se puede subir cada plugin como ZIP desde **Personalizar → Plugins**. Los ZIP están en la página de [versiones](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest): uno por plugin y [Administrativo.zip](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/Administrativo.zip) con todos.

## Plugins

| Plugin | Contenido | Skills | ZIP |
|---|---|---:|---|
| `modelos-escritos-administracion-espana` | Escritos ante la Administración (Ley 39/2015) · España | 278 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/modelos-escritos-administracion-espana.zip) |
| `modelos-extranjeria-espana` | Extranjería: arraigo, residencia, nacionalidad y expulsiones · España | 98 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/modelos-extranjeria-espana.zip) |
| `modelos-multas-trafico-espana` | Recurrir multas de tráfico · España | 405 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/modelos-multas-trafico-espana.zip) |
| `modelos-personacion-contencioso-espana` | Contencioso: personaciones, competencia y representación · España | 97 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/modelos-personacion-contencioso-espana.zip) |
| `modelos-recursos-administrativos-espana` | Recursos de alzada, reposición y revisión · España | 60 | [descargar](https://github.com/DerechoVirtual/modelos-juridicos-administrativo-espana/releases/latest/download/modelos-recursos-administrativos-espana.zip) |

## Estructura

```
.claude-plugin/marketplace.json  catálogo del marketplace
plugins/<plugin>/                .claude-plugin/plugin.json, .mcp.json, skills/, README.md, PRIVACY.md, LICENSE
```

## Aviso

Los escritos que se generan son borradores que debe revisar un abogado; no constituyen asesoramiento jurídico. Las skills no guardan datos del cliente y las consultas a Jurisprudenciator describen el problema jurídico, no los datos personales.

Soporte: https://jurisprudenciator.lexiaipro.org/incidencias · Licencia: ver [LICENSE](LICENSE).
