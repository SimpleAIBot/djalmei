# Contexto para Agentes IA — DJ ALMEi (`djalmei.es`)

Este proyecto consta de **dos repositorios/directorios hermanos** en `C:\programas python\`:

1. **`C:\programas python\djalmei_website`** → **Web pública estática** (`https://www.djalmei.es`), alojada en GitHub Pages (`SimpleAIBot/djalmei`).
2. **`C:\programas python\djalmei_contactos`** → **CRM local + Generadores** (servidor Flask + SQLite `crm.db`), que alimenta las partes dinámicas/programáticas de la web.

---

## 🗺️ Mapa de Arquitectura: ¿Dónde se modifica cada cosa?

### A. Páginas estáticas manuales (Editar en `djalmei_website/`)
Se editan directamente en la raíz de `C:\programas python\djalmei_website\`:
- `index.html` — Home principal (`DJ Vigo` #1 en Google).
- `bodas.html` — Landing de bodas en Vigo, Pontevedra y Galicia.
- `eventos-empresa.html` — Landing B2B y cenas de Navidad (`Cena navidad vigo dj` #1 en Google).
- `calendario.html` — Página de contratación, presupuesto y consulta de disponibilidad.
- `styles.css` y `script.js` — Estilos globales (estética nocturna/neón) y lógica cliente.

### B. Archivos generados desde el CRM (NO editar a mano en `djalmei_website/`)
Estos archivos se sobrescriben automáticamente desde `C:\programas python\djalmei_contactos\`:
- **`festas-galicia/**` y `sitemap.xml`**:
  - **Origen:** `C:\programas python\djalmei_contactos\generar_festas_galicia.py` + tabla `fiestas_db` en `crm.db`.
  - **Importante:** Al ejecutar `generar_festas_galicia.py`, el script **borra y recrea** toda la carpeta `festas-galicia/` (~190 páginas: índice, concellos, meses y categorías) y regenera `sitemap.xml`.
  - Cualquier cambio de diseño, textos o SEO en `/festas-galicia/` **debe hacerse en `C:\programas python\djalmei_contactos\generar_festas_galicia.py`** y luego ejecutarse el script.
- **`data/calendario.json`**:
  - **Origen:** Publicado desde el servidor CRM (`C:\programas python\djalmei_contactos\crm_server.py`) con las fechas ocupadas/reservadas del DJ.

---

## 🛑 Reglas de Oro SEO (Lectura obligatoria en `SEO.md`)

Antes de tocar cualquier HTML o generador, revisa `C:\programas python\djalmei_website\SEO.md` y `SEO_FESTAS.md`:
1. **PROHIBIDO** cambiar `<title>`, `<h1>` o `<meta name="description">` de `index.html` y `eventos-empresa.html` sin permiso explícito del usuario (están en posición #1 en Google).
2. **NO canibalizar Search Intent en `/festas-galicia/`:** Los títulos y H1 del directorio deben responder a la búsqueda informativa (`Festas en {Concello} · Calendario {Año}`), sin forzar "DJ para festas..." en el H1.
3. **PROHIBIDO keyword stuffing / textos clónicos:** Evitar bloques repetitivos idénticos entre concellos que Google penalice como *Doorway Pages*.
4. **URLs inmutables:** GitHub Pages no tiene redirecciones 301 server-side. No cambiar slugs ni rutas de páginas ya indexadas.
