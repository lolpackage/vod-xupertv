# Magis VOD — Nuvio

Plugin de catálogo **Magis VOD** para Nuvio (películas, series y animación).

- Home (novedades + últimas películas / series / animación)
- Descubrir con filtros por tipo y categoría
- Búsqueda
- Ficha completa (todas las temporadas y capítulos)
- Streams con subtítulos e intro/outro (IntroDB al reproducir)
- Sesión automática vía seeds (no hace falta activar dispositivo)

Requiere **CryptoJS** en el runtime (Nuvio lo carga si el código menciona `CryptoJS`).

## Cómo agregarlo en Nuvio

1. Sube este repositorio a **GitHub** (público), por ejemplo:
   - `tu-usuario/magis-vod-nuvio`
2. Copia la URL del manifest en raw:
   ```
   https://raw.githubusercontent.com/TU-USUARIO/magis-vod-nuvio/main/manifest.json
   ```
3. En Nuvio (versión **sideloaded**, no la de tienda):
   - **Ajustes → Content & Discovery → Plugins** (o *Local Scrapers*)
   - **Add repository** / **Agregar repositorio**
   - Pega la URL del `manifest.json`
   - Activa el scraper **Magis VOD**

> Nota: los plugins solo funcionan en builds sideloaded de Nuvio. Las versiones de Play Store / App Store no permiten plugins.

## Estructura

```
magis-vod-nuvio/
├── manifest.json   ← URL que pegas en Nuvio
├── magis-vod.js    ← lógica del proveedor
└── README.md
```

## Configuración opcional

El runtime puede inyectar config en `globalThis.__nuvioConfig['magis-vod']`:

| Clave | Default | Descripción |
|-------|---------|-------------|
| `hosts` | hosts del portal | Lista separada por comas |
| `seedsUrl` | seeds de xuper-plugin | JSON de tokens de sesión |
| `tmdbApiKey` | incluida | Para logos / stills / orden de temporadas |
| `tmdbEnrichMeta` | `true` | Enriquecer meta con TMDB |
| `maxSeasonsMeta` | `30` | Máx. temporadas a cargar en la ficha |
| `userToken` / `sn` | — | Token manual (opcional; si no, usa seeds) |

## API exportada

```js
module.exports = {
  getNews, getHome, getDiscoverFilters, getDiscover,
  getCatalog, getCatalogs, search, getMeta, getStreams
};
```
