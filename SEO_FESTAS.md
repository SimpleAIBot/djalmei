# Directorio de festas de Galicia — diseño

Plan vivo para el directorio `/festas-galicia/`. Generado desde la BD `fiestas_db` del CRM (~656 fiestas en ~342 concellos).

---

## Objetivo

Captar tráfico orgánico SEO long-tail (búsquedas tipo *"festas patronais Cuntis"*, *"verbena Ribadumia"*, *"qué hacer en Bueu este finde"*) y convertir parte de ese tráfico en leads para DJ ALMEi.

**Doble beneficio:**
1. SEO masivo (cientos de páginas únicas con contenido real)
2. Autoridad de marca: "el DJ que conoce las festas de Galicia"

---

## Estructura de URLs

```
/festas-galicia/                              ← Índice principal
/festas-galicia/{concello}/                   ← 1 por concello (342 max)
/festas-galicia/mes/{año-mes}/                ← 1 por mes (12 al año)
/festas-galicia/categoria/{cat}/              ← 5-8 por categoría
```

**Por qué con carpetas** (`/vigo/` y no `/vigo.html`):
- URL más limpia y reutilizable
- Permite extensiones futuras (`/vigo/festa-do-carme/` si quieres fichas individuales)
- Estándar para directorios

**Slugs**:
- Concello: `vigo`, `pontevedra`, `santiago-de-compostela`, `a-coruna`, `tomino` (sin tildes, sin caracteres especiales)
- Mes: `2026-07`, `2026-08`, etc.
- Categoría: `patronais`, `gastronomicas`, `romarias`, `carnaval`, `religiosas`

---

## Tipos de página

### A) Índice principal `/festas-galicia/`

Bloques:
1. **Hero**: "Calendario completo de festas en Galicia · DJ ALMEi"
2. **Buscador** (JS client-side, sin backend): filtra concello/mes/categoría
3. **Próximas fiestas** (próximas 10-15)
4. **Por mes**: links a `/festas-galicia/mes/2026-07/` etc.
5. **Por categoría**: links a `/festas-galicia/categoria/patronais/` etc.
6. **Concellos destacados** (los que tienen más fiestas: A Coruña, Pontevedra, Vigo, Ourense, etc.)
7. **CTA DJ**: "Soy Daniel, DJ ALMEi. Mantengo este calendario porque trabajo en festas de toda Galicia. Mira mi calendario de disponibilidad →"

### B) Página por concello `/festas-galicia/{concello}/`

Bloques:
1. **Hero**: "Festas en {Concello} · Calendario {año}"
2. **Listado de fiestas** del concello con:
   - Nombre, fecha, mes, categoría
   - Descripción (si hay)
   - Organizador (si hay)
   - URL origen (link a fuente)
3. **CTA contextual**: "¿Eres de la comisión de festas de {Concello}? Si necesitáis DJ profesional para vuestra festa, mira mi calendario →"
4. **Concellos cercanos**: links a 4-5 concellos limítrofes (internal linking)
5. **Sobre el DJ**: 2-3 líneas con CTA al calendario

### C) Página por mes `/festas-galicia/mes/{año-mes}/`

Bloques:
1. **Hero**: "Festas en Galicia · {mes} {año}"
2. **Lista de fiestas del mes**, ordenadas por fecha, agrupadas por semana
3. Cada item con link al concello correspondiente
4. **CTA**: "¿Necesitas DJ para alguna de estas festas? Calendario →"
5. **Mes anterior / mes siguiente**

### D) Página por categoría `/festas-galicia/categoria/{cat}/`

Igual que mes pero filtrado por categoría.

---

## SEO técnico por página

Cada tipo de página debe tener:

| Tag | Contenido |
|---|---|
| `<title>` | "Festas en {Concello} · Calendario {año} · DJ ALMEi" |
| `<meta description>` | "Calendario de festas patronais, verbenas y eventos tradicionais en {Concello}. Fechas, descripciones y contacto." |
| `<link rel="canonical">` | URL absoluta de la página |
| OG title + description + image | Para compartir en redes |
| Schema.org `BreadcrumbList` | Inicio > Festas Galicia > Concello |
| Schema.org `Event` | Por cada fiesta (con startDate, location, organizer si hay) |
| `<h1>` único | Con keyword principal |
| Internal linking | Mínimo 3-5 links a otros concellos / meses / home |

---

## Filtrado de calidad (qué publicamos y qué no)

De las 656 fiestas en BD:
- **318 con fecha + descripción**: publicamos sin duda
- **338 solo con nombre**: o las omitimos, o las publicamos con menos detalle dentro de la página del concello

**Regla propuesta**:
- Páginas por concello: incluir todas las fiestas del concello, pero **destacar las que tienen info rica** (fecha + descripción + categoría)
- Páginas por mes/categoría: solo fiestas con fecha confirmada (las 318)
- Si un concello tiene **0 fiestas con info**, no generar página

Esto deja:
- ~200-250 páginas de concello con calidad
- 12 páginas de mes
- 5-8 páginas de categoría

---

## CTAs (cómo convertimos tráfico en leads)

**Principio**: NO ser intrusivo. El visitante viene buscando info de fiestas, dale eso primero. CTAs aparecen DESPUÉS del contenido útil.

**Patrón por página de concello:**

```
[Contenido útil: lista de fiestas]

▔▔▔ Bloque CTA contextual ▔▔▔
¿Eres de una comisión de festas de {Concello}?
Soy Daniel, DJ ALMEi. Trabajo festas patronais en
toda Galicia. Si buscáis DJ profesional, mira mi
calendario de disponibilidad.

[Reserva tu fecha →]  [WhatsApp]
▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔
```

**Patrón por página de mes:**

```
[Lista de fiestas del mes]

▔▔▔ Bloque CTA ▔▔▔
¿Necesitas DJ para alguna de estas festas?
Reserva tu fecha en mi calendario.
▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔
```

**Sticky bottom (opcional, móvil)**: barra fija discreta abajo con "Soy DJ ALMEi · Reserva →" — aparece tras 30s en página.

---

## Generación técnica

**Script Python en el CRM** que:
1. Lee `fiestas_db` de la BD
2. Genera N archivos HTML estáticos en `djalmei_website/festas-galicia/`
3. Genera entrada en sitemap.xml por cada URL nueva
4. Hace `git add + commit + push` (igual que el publicador de calendario)

**Plantilla**: Jinja2 (1 plantilla por tipo: índice, concello, mes, categoría)

**Ejecución manual**: el DJ pulsa "Publicar directorio festas" en el CRM (botón nuevo) cuando añada/edite fiestas.

**Coste técnico estimado**: ~5h dividido en:
- Plantilla HTML base + estilos: 1h
- Generador Python con Jinja2: 2h
- Integración con CRM + sitemap + push: 1h
- Testing y ajustes: 1h

---

## Plan de roll-out

### Fase 1 — Boceto (HOY)
- Documento de diseño (este archivo)
- 1 página de muestra estática (Vigo) — sin generador automático
- Validación visual y de estructura

### Fase 2 — Implementación (sesión separada ~5h)
- Generador Python con plantillas Jinja2
- Generar las ~250 páginas de concello + 12 de mes + 5-8 de categoría
- Integrar con sitemap
- Push masivo

### Fase 3 — Monitorización (continuo)
- Search Console: revisar cobertura, posición de keywords, errores
- Iterar copy de CTAs según conversión
- Añadir fiestas nuevas a la BD según las vas descubriendo
- Regenerar y publicar mensualmente

---

## Riesgos y mitigaciones

| Riesgo | Mitigación |
|---|---|
| Contenido duplicado entre páginas | Cada página tiene texto único (concello, mes, descripción de fiesta) |
| Páginas con poco contenido (concello con 1-2 fiestas) | Filtrar: si <2 fiestas con info, no generar página |
| Datos desactualizados (fecha del año pasado) | Mes/año visible. Si la fecha pasó, marcar "edición pasada — próxima edición típicamente en {mes}" |
| Google penaliza por "doorway pages" (páginas creadas solo para SEO) | Mitigamos con contenido útil real + descripciones ricas. NO son doorway si dan valor al visitante |
| Mantenimiento del directorio | Regeneración 1x/mes. Automatizable. |

---

## Métricas que vigilar (Search Console)

- **Impresiones por concello**: ¿qué concellos generan más búsquedas?
- **Top queries del directorio**: ¿qué buscan los visitantes? Eso guía qué expandir
- **CTR** medio en el directorio: si <2%, mejorar titles
- **Conversión a calendario**: cuántos visitantes del directorio van al /calendario.html (Google Analytics o similar)

---

## Apertura futura

Si el directorio funciona, expandimos:
- **Páginas por parroquia** (para concellos grandes con muchas parroquias)
- **Fichas individuales por fiesta** con galería, historia, etc.
- **Subscripción** ("avísame antes de la próxima edición")
- **Mapa interactivo** con todas las fiestas geolocalizadas
