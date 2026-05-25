# Djalmei · DJ en Vigo y Galicia

Web personal de **Djalmei**, DJ joven afincado en Vigo, disponible para:

- 💍 Bodas
- 🎂 Cumpleaños
- 🥂 Fiestas privadas
- 🏢 Eventos de empresa
- 💃 Bailes y verbenas

**Zona de actuación:** Vigo, Pontevedra, A Coruña, Santiago, Ourense, Lugo y toda Galicia.

- 🌐 Web: <https://djalmei.eu.org>
- 📸 Instagram: [@almei_dj](https://www.instagram.com/almei_dj/)

---

## Stack

Sitio estático: HTML + CSS + JS puro. Sin build, sin dependencias.

```
.
├── index.html      # estructura
├── styles.css      # estilos (estética nocturna/neón)
├── script.js       # animaciones de scroll + año dinámico
├── favicon.svg     # icono
├── CNAME           # dominio personalizado para GitHub Pages
└── .nojekyll       # evita procesamiento Jekyll
```

## Cómo desplegar (GitHub Pages + Cloudflare)

### 1. Subir el código al repo

```bash
git init
git add .
git commit -m "Primera versión de djalmei.eu.org"
git branch -M main
git remote add origin https://github.com/SimpleAIBot/djalmei.git
git push -u origin main
```

### 2. Activar GitHub Pages

1. En GitHub → repo `SimpleAIBot/djalmei` → **Settings** → **Pages**.
2. En *Source* elige **Deploy from a branch**.
3. Branch: `main` / carpeta `/ (root)` → **Save**.
4. En *Custom domain* escribe `djalmei.eu.org` y guarda.
5. Marca **Enforce HTTPS** cuando esté disponible.

### 3. Configurar Cloudflare (DNS hacia GitHub Pages)

En el panel de Cloudflare del dominio `djalmei.eu.org` añade estos registros:

| Tipo  | Nombre | Contenido                | Proxy        |
|-------|--------|--------------------------|--------------|
| A     | @      | 185.199.108.153          | DNS only (☁ gris) |
| A     | @      | 185.199.109.153          | DNS only |
| A     | @      | 185.199.110.153          | DNS only |
| A     | @      | 185.199.111.153          | DNS only |
| CNAME | www    | simpleaibot.github.io    | DNS only |

> **Importante:** mientras GitHub verifica el dominio, mantén el proxy de Cloudflare en **DNS only** (nube gris). Cuando ya esté validado y HTTPS activo, puedes activar el proxy (nube naranja) si quieres usar las funciones de Cloudflare.

En Cloudflare → **SSL/TLS** → modo **Full**. Y en **Rules → Always Use HTTPS** activado.

### 4. Probar local

Cualquier servidor estático sirve. Con Python:

```bash
python -m http.server 8000
```

Y abre <http://localhost:8000>.

## Editar contenido

Todo el texto está en `index.html`. Para cambiar colores, edita las variables CSS al inicio de `styles.css`:

```css
:root {
  --accent: #ff2e63;     /* color principal */
  --accent-2: #08d9d6;   /* color secundario */
  --bg: #0a0a0f;         /* fondo */
}
```
