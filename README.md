# b-style

Sistema de estilos basado en Bulma con componentes Alpine.js.

## Instalación

Desde GitHub (SSH):

```bash
npm install git+ssh://git@github.com:aavendano/b-style.git
```

HTTPS alternativo:

```bash
npm install github:aavendano/b-style
```

Fijar rama o versión:

```bash
npm install git+ssh://git@github.com:aavendano/b-style.git#main
npm install git+ssh://git@github.com:aavendano/b-style.git#v0.1.0
```

Al instalar, npm ejecuta el script `prepare` y genera `dist/` (CSS y bundle Alpine).

## Uso

### CSS precompilado

```html
<link rel="stylesheet" href="node_modules/b-style/dist/b-style.min.css">
```

O la versión sin minificar:

```html
<link rel="stylesheet" href="node_modules/b-style/dist/b-style.css">
```

### SCSS (personalización)

Requiere `sass` en el proyecto consumidor:

```bash
npm install -D sass
```

```scss
@use "b-style/bulma" as *;
```

Con Vite, Webpack o Shopify CLI, `node_modules` se resuelve automáticamente.

### Alpine.js

Bundle IIFE (Shopify, `<script>` directo):

```html
<script src="node_modules/b-style/dist/alpine.js" defer></script>
```

Bundle ESM (Vite, Webpack):

```js
import 'b-style/alpine/esm';
```

Fuente sin empaquetar (bundler propio del consumidor):

```js
import 'b-style/alpine/source';
```

### Componentes

Los componentes se distribuyen como fuente en `src/components/`:

```js
import bNavbar from 'b-style/components/navbar/navbar.js';
```

```scss
@use "b-style/components/button/button";
```

### PostCSS / PurgeCSS (temas Shopify)

Los configs en `src/postcss.config.cjs` y `src/postcss.config.base.cjs` están pensados para ejecutarse en la **raíz del tema consumidor**, donde existen `layout/*.liquid`, `sections/*.liquid`, etc.

Copia o extiende el config en tu tema:

```js
// postcss.config.cjs del tema
module.exports = require('b-style/postcss');
```

## Versionado

1. Actualiza `"version"` en `package.json`.
2. Crea y publica el tag:

```bash
git tag v0.1.0
git push origin v0.1.0
```

3. Instala la versión fijada:

```bash
npm install git+ssh://git@github.com:aavendano/b-style.git#v0.1.0
```

## Desarrollo local

```bash
npm install
npm run build
```

Artefactos generados en `dist/`:

- `b-style.css` / `b-style.min.css`
- `alpine.js` (IIFE)
- `alpine.esm.js` (ESM)

## Documentación

El catálogo interactivo en [`index.html`](index.html) es la referencia principal de componentes. Tras compilar (`npm run build`), ábrelo con un servidor estático local.

Cada sección incluye una demo visual y un snippet HTML copiable con el botón **Copy**.

| Categoría | Ancla |
|-----------|-------|
| Instalación y setup | `#getting-started` |
| Tipografía y colores | `#typography`, `#colors` |
| Elementos | `#buttons`, `#tags`, `#notifications`, `#messages`, `#progress`, `#box`, `#titles` |
| Componentes | `#cards`, `#tables`, `#forms`, `#tabs`, `#breadcrumb`, `#panel`, `#navbar` |
| Layout | `#columns`, `#section-hero` |
| Helpers | `#helpers` |

El README cubre instalación y consumo del paquete; el catálogo documenta el markup y las clases `b-*` de cada componente.

### Guía para agentes AI

- [`LLM.md`](LLM.md) — instrucciones densas para modelos LLM (solo clases `b-*`, reglas, ejemplos, anti-patterns). Incluido en el paquete npm.
- [`LLM.short.md`](LLM.short.md) — guía compacta (≤4000 caracteres) para **contenido editorial**: artículos, secciones CMS, landing blocks.
- [`llm.html`](llm.html) — guía completa con botón **Copy all**; enlazada desde el navbar del catálogo como **AI guide**.
- [`llm-short.html`](llm-short.html) — versión editorial short con **Copy all**.

Al generar UI con un agente, incluye `LLM.md` o `LLM.short.md` en el contexto del proyecto según el tipo de contenido.

## Licencia

MIT
