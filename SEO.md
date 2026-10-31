# SEO — DJ ALMEi · djalmei.es

Plan vivo y manual de directrices para agentes IA y desarrollo. Cuando un punto se cierra, marca con ✓ y deja la fecha entre paréntesis.

---

## 🏆 Estado y Posicionamiento Actual (Octubre 2026)

- **`DJ Vigo`** ➔ **#1 Posición absoluta en Google** 🥇
- **`Cena navidad vigo dj`** ➔ **#1 Posición absoluta en Google** 🥇
- **Autoridad local en Vigo/comarca:** Imbatible y plenamente consolidada.

> [!CAUTION]
> ### 🛑 PROTOCOLO OBLIGATORIO PARA AGENTES IA (REGLAS DE ORO)
> 1. **PROHIBIDO tocar los títulos, H1 o meta description de la Home (`index.html`) y `/eventos-empresa.html`** sin aprobación explícita. Están en el puesto #1 para las búsquedas comerciales de mayor valor económico.
> 2. **NO canibalizar la intención de búsqueda (Search Intent):** Las páginas del directorio `/festas-galicia/` deben responder primero al usuario que busca la fiesta del concello (`Festas en {Concello} · Calendario`). DJ ALMEi figura como mantenedor y opción de contratación recomendada, **no secuestrando el H1 con "DJ para festas..."**.
> 3. **PROHIBIDO el keyword stuffing y textos clónicos:** Nunca generar bloques de texto masivo idéntico (como el antiguo `.seo-final`) que puedan ser calificados por Google como *Doorway Pages* o *Scaled Content Abuse*.
> 4. **GitHub Pages no tiene redirecciones 301 server-side:** Nunca cambies la URL de un HTML indexado si hay enlaces externos o productos apuntando a ella.

---

## 🔍 Análisis de la Fluctuación de Clics (Otoño / Invierno)

La bajada de clics detectada en octubre **no se debe a una pérdida de posiciones en el core del negocio** (que sigue #1), sino a:
1. **Estacionalidad natural gallega:** Entre mayo y septiembre, el directorio `/festas-galicia/` (168 concellos) atraía miles de búsquedas por el pico estival de verbenas y fiestas patronales. En otoño/invierno la búsqueda de fiestas de pueblo cae más de un 85% en Galicia.
2. **Eventos de 2026 caducados:** A finales de octubre, la inmensa mayoría de las fichas muestran "Edición pasada", lo que reduce el CTR y el tiempo en página.
3. **Sobreoptimización en `generar_festas_galicia.py` (Commit `d07adcc`):** Forzar "DJ" en los títulos de fiesta alejó a vecinos que buscaban fechas informativas.

---

## ✅ Hecho

- **HTTPS** (GitHub Pages vía Let's Encrypt)
- **Meta básicos y Open Graph** en home, bodas, empresa y calendario
- **JSON-LD `LocalBusiness`** completo en Home
- **JSON-LD `Service`** individualizado para bodas, festas patronais, cumpleaños, empresa y salas en la Home (2026-06)
- **JSON-LD `FAQPage`** y **`BreadcrumbList`**
- **`sitemap.xml`** y **`robots.txt`** optimizados
- **`/bodas.html`** landing dedicada SEO completa + schema `Service` (2026-06-03)
- **`/calendario.html`** reconvertida en página de contratación ("contratar dj vigo" / "presupuesto dj galicia") con formulario y FAQ (2026-09-16)
- **`/eventos-empresa.html`** landing B2B con foco en cenas de Navidad (#1 en Google) (2026-09-16)
- **Directorio `/festas-galicia/`** 168 páginas generadas por concello + mes + categoría (2026-06)
- **Google Business Profile (GBP)** y **Google Search Console (GSC)** dados de alta y verificados

---

## 🟡 Acciones en Curso — Temporada Alta Otoño/Invierno

### 1. Campaña Cenas de Navidad y Fin de Año (Pico comercial: Noviembre - Diciembre)
- [x] Landing `/eventos-empresa.html` posicionada #1.
- [ ] Reforzar en la Home y `/calendario.html` disponibilidad para Fin de Año / Cotillón en Vigo y comarcas limítrofes.
- [ ] Promover enlaces internos desde los concellos limítrofes hacia eventos de empresa.

### 2. Captación de Bodas 2027 (Pico de contratación: Octubre - Febrero)
- [ ] Optimizar interlinking hacia `/bodas.html` con anclajes geolocalizados: *"DJ para bodas en Vigo"*, *"DJ bodas Pontevedra"*, *"DJ pazos Rías Baixas"*.
- [ ] Cuando haya fotos reales de bodas, sustituir las imágenes de stock.

### 3. Reajuste del Directorio `/festas-galicia/` (En `generar_festas_galicia.py`)
- [x] **Restablecer el título natural en las 168 páginas:** `Festas en {Concello} · Calendario {Año} · DJ ALMEi` ✓ (2026-10-31).
- [x] **Restablecer el H1:** `Festas en {Concello} · Calendario {Año}` ✓ (2026-10-31).
- [x] **Eliminar el bloque repetitivo de 150 palabras `.seo-final`** para evitar banderas de *Doorway Pages* ✓ (2026-10-31).
- [x] **Limpiar anclajes del pie de página:** cambiar `DJ para festas gastronómica` por `Festas gastronómicas` ✓ (2026-10-31).
- [x] **Modo puente 2027:** Para fiestas concluidas en 2026, mostrar *"Edición finalizada · Próxima edición estimada en 2027"* ✓ (2026-10-31).
- [x] **Destacar eventos inmediatos:** Magostos (noviembre), Fin de Año (diciembre), Reyes y Entroido / Carnaval 2027 (febrero) ✓ (2026-10-31).

---

## 📈 Roadmap Continuo (Acciones del DJ)

- **Reseñas en Google Maps (Prioridad máxima):** Como la web ya está en el puesto #1 para "DJ Vigo", las reseñas de clientes reales con texto (*"contratamos a Daniel para una fiesta en Vigo..."*) son el factor #1 para que el usuario llame inmediatamente por WhatsApp.
- **Publicaciones periódicas en Google Business:** 1 post cada 10-15 días con fotos de cabina y mención a la disponibilidad para cenas de empresa y bodas.

### 📌 Plataformas y Directorios Externos (Plan para el futuro)
- [ ] **Bodas.net (Ficha básica gratuita):** Crear perfil con fotos profesionales de cabina/pista y enlace hacia `https://www.djalmei.es/bodas.html` para captar parejas de Vigo y provincia de Pontevedra.
- [ ] **Wallapop (Sección Servicios en Vigo/comarca):** Anuncio profesional para cumpleaños, aniversarios y fiestas privadas. Filtro con precio de salida *"Desde 180 €"*, fotos de equipo limpio y mención a web `djalmei.es` e Instagram `@almei_dj`.
- [ ] **Milanuncios (Clasificados para fechas sueltas):** Anuncio serio enfocado a cubrir fines de semana libres de última hora (cumpleaños, fiestas de peñas). Enfoque profesional con factura legal, equipo propio y microfonía (prohibido usar "barato" o "económico").
- [ ] **Citaciones y Directorios Locales (Refuerzo NAP):** Páginas Amarillas, QDQ o directorios locales de Vigo con nombre comercial, teléfono y web idénticos para reforzar la autoridad de negocio local.
