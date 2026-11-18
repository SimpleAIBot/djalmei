# Djalmei · DJ en Vigo y Galicia (`djalmei.es`)

Web oficial de **DJ ALMEi** (<https://www.djalmei.es>), DJ en Vigo y toda Galicia para bodas, cenas de empresa, fiestas privadas y verbenas/festas patronais.

---

## 🏗️ Arquitectura del Proyecto (Web + CRM)

El ecosistema de DJ ALMEi está dividido en dos carpetas hermanas dentro de `C:\programas python\`:

```text
C:\programas python\
├── djalmei_website\          ← ESTE REPO: Web pública estática (GitHub Pages)
│   ├── index.html            ← Home principal (manual)
│   ├── bodas.html            ← Landing de bodas (manual)
│   ├── eventos-empresa.html  ← Landing de eventos de empresa / Navidad (manual)
│   ├── calendario.html       ← Página de presupuesto y disponibilidad (manual)
│   ├── styles.css / script.js← Estilos y scripts globales (manual)
│   ├── data\calendario.json  ← Disponibilidad exportada desde el CRM (generado)
│   ├── festas-galicia\       ← Directorio SEO de fiestas (~190 págs, generado)
│   ├── sitemap.xml           ← Mapa del sitio (generado por el script de festas)
│   ├── SEO.md                ← Directrices y estado SEO (lectura obligatoria)
│   ├── SEO_FESTAS.md         ← Diseño del directorio /festas-galicia/
│   └── AGENTS.md             ← Contexto e instrucciones para agentes IA
│
└── djalmei_contactos\        ← CRM LOCAL: Prospección, facturación y generadores
    ├── crm.db                ← Base de datos SQLite (contactos, facturas, fiestas_db)
    ├── crm_server.py         ← Servidor Flask local (http://127.0.0.1:5000)
    └── generar_festas_galicia.py ← Script que genera /festas-galicia/ y sitemap.xml
```

### ¿Qué se edita aquí y qué viene del CRM?
1. **Web principal (`djalmei_website/`)**: `index.html`, `bodas.html`, `eventos-empresa.html`, `calendario.html`, `styles.css` y `script.js` se editan directamente aquí.
2. **Directorio `/festas-galicia/` y `sitemap.xml`**: **NO editar los HTML de `festas-galicia/` a mano**. Se generan ejecutando `python generar_festas_galicia.py` desde `C:\programas python\djalmei_contactos\`, que lee la base de datos `crm.db`, recrea la carpeta `festas-galicia/` completa y actualiza `sitemap.xml`.
3. **Datos de calendario (`data/calendario.json`)**: Se actualizan desde el CRM local.

---

## 🚀 Cómo probar y desplegar

### Probar en local
Desde `C:\programas python\djalmei_website`:
```bash
python -m http.server 8000
```
Abrir <http://localhost:8000>.

### Regenerar el directorio `/festas-galicia/`
Desde `C:\programas python\djalmei_contactos`:
```bash
python generar_festas_galicia.py          # Solo genera los HTML y sitemap.xml
python generar_festas_galicia.py --push   # Genera + git commit + git push
```

### Despliegue (GitHub Pages + Cloudflare)
El repositorio despliega automáticamente desde la rama `main` en GitHub (`SimpleAIBot/djalmei`) bajo el dominio `www.djalmei.es`.

| Tipo  | Nombre | Contenido                |
|-------|--------|--------------------------|
| CNAME | www    | simpleaibot.github.io    |
| A     | @      | 185.199.108.153 / 109.153 / 110.153 / 111.153 |

---

## 🎨 Variables de diseño (`styles.css`)

```css
:root {
  --accent: #ff2e63;     /* color principal */
  --accent-2: #08d9d6;   /* color secundario */
  --bg: #0a0a0f;         /* fondo */
}
```
