# SEO — DJ ALMEi · djalmei.es

Plan vivo. Cuando un punto se cierra, marca con ✓ y deja la fecha entre paréntesis.

---

## ✅ Hecho

- **HTTPS** (GitHub Pages lo da gratis vía Let's Encrypt)
- **Meta básico** en home: title, description, keywords, theme-color, canonical
- **Open Graph + Twitter Card** en home y `/calendario.html`
- **JSON-LD `LocalBusiness`** con teléfono, geo, áreas servidas, sameAs, makesOffer
- **JSON-LD `FAQPage`** con 4-5 preguntas frecuentes
- **`sitemap.xml`** con home (weekly, 1.0) + calendario (daily, 0.9)
- **`robots.txt`** permite todo y apunta al sitemap
- **`/calendario.html`** SEO completo: title con keywords, description, canonical, OG/Twitter, fix de `noindex` heredado de pruebas (2026-06-03)
- **Google Business Profile**: alta + verificación + descripción + horario + zona + productos (6 servicios con copy + categoría + URL al calendario)
- **Google Search Console**: alta + sitemap enviado + indexación pedida para calendario

## 🟡 Pendiente — ACCIÓN MÍA (no requiere inputs)

- **JSON-LD `Service`** por cada tipo de evento (bodas, festas patronais, cumpleaños, empresa, sala). Replicar el copy de los productos GBP en schema dentro del `<head>` de la home. SEO de cola larga sin necesidad de fechas concretas.
- **Enriquecer `LocalBusiness`** existente con: `priceRange`, `aggregateRating` (cuando haya reseñas), `image` (varias), `openingHours` específicos
- **Internal linking** desde la home a `/calendario.html` con anchor text variado ("ver fechas libres", "reserva tu fecha", "calendario de disponibilidad")

## 🔴 Pendiente — REQUIERE INPUTS / FOTOS

### Páginas dedicadas (cuando haya fotos buenas de eventos)

Por orden de impacto comercial:

1. **`/bodas.html`** — landing dedicada
   - Hero específico de boda + foto de cabina/pista llena en boda real
   - Cómo trabajo: contacto → presupuesto → lista de canciones → ceremonia → cóctel → banquete → barra libre
   - Equipo que llevo (con foto)
   - Música: estilos, gallego sí/no, sorpresas / primer baile
   - Zona de servicio con ciudades (links internos)
   - FAQ específica de bodas (5-6 preguntas)
   - Testimonios (placeholder hasta tener reseñas de Google a embebir)
   - CTA al calendario + WhatsApp
   - SEO: title/desc/canonical/OG + Schema.org `Service` específico + JSON-LD `BreadcrumbList`
   - Enlazada desde home (Servicios) y desde el producto GBP "DJ para bodas"

2. **`/festas-patronais.html`** — mismo patrón aplicado a verbenas / festas tradicionales
   - Repertorio en gallego, sesión vermú + sesión nocturna
   - Cobertura por comarcas (Baixo Miño, Rías Baixas, etc.)
   - Foto de sesión de verbena con público

3. **`/eventos-empresa.html`** — bodas y festas son B2C; empresa es B2B
   - Factura formal, IVA, profesionalidad, discreción
   - Casos: cena de empresa, fiesta navidad, presentación, team building
   - Pedir presupuesto formal

### Schema.org `Event` (sesiones programadas concretas)

Cuando tengas 2-3 sesiones futuras confirmadas y públicas (no privadas tipo bodas), me das:
- Nombre del evento
- Fecha y hora
- Lugar (nombre, ciudad, dirección si pública)
- Si lleva entrada o es libre
- URL del evento si la hay

Las meto como JSON-LD `Event` en la home. Aparecen como rich snippets en Google ("qué hacer este finde en Vigo").

## 📈 Roadmap continuo (acciones del DJ)

- **Reseñas Google**: pedir a clientes pasados con link directo a Google Maps. Cada reseña empuja el ranking local. Objetivo: 10 reseñas en 90 días.
- **Backlinks locales**: bodas.net (perfil gratuito), listings de DJs Galicia, asociaciones culturales con las que colabore, prensa local (Faro de Vigo, Atlántico Diario).
- **Publicaciones en GBP**: cada 7-15 días un post nuevo (sesión próxima, foto reciente, anuncio).
- **Reseñas embebidas**: cuando haya >= 5 reseñas Google, embebidas en la home (widget o screenshots con schema `Review`).
- **Sesiones / portfolio**: ir generando contenido propio en `/sesiones` con fotos y videos cortos.

## 📊 Métricas que vigilar (Search Console, mensual)

- Impresiones totales (crecimiento mes a mes)
- Clics totales
- CTR medio (objetivo > 5%)
- Posición media de las keywords clave:
  - "dj vigo"
  - "dj galicia"
  - "dj para bodas vigo"
  - "dj festas patronais"
  - "dj almei"
- Cobertura: páginas indexadas vs excluidas
- Errores móviles / Core Web Vitals
