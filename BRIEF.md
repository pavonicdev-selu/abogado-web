# Despacho Abogado Málaga
## Brief técnico interno

---

**Confidencialidad:** Uso interno
**Fecha:** 29 de abril de 2026
**Cliente:** Despacho boutique Málaga
**Áreas:** Civil · Laboral · Penal
**Equipo:** 3 titulares (1 abogado + 2 abogadas)

---

## 1. Estado del proyecto

| Fase | Estado |
|---|---|
| 1. Investigación competencia | ✅ Completada |
| 2. Diseño visual (mockups) | ⏳ Siguiente |
| 3. Implementación | ⏳ Pendiente |
| 4. Lanzamiento | ⏳ Pendiente |

---

## 2. Metodología de investigación

Scraping vía WebFetch (Claude Code) sobre 5 competidores directos en Málaga:

- bufetededamas.com
- gbaabogados.com
- vazquezabogados.es
- oderizabogados.es
- mayorgaabogados.es

Ejes analizados: estructura, hero, servicios, confianza, CTAs/formularios, SEO local, tono, aciertos/debilidades.

---

## 3. Patrones y carencias detectadas

### Patrones comunes (commodities)
- "+20-30 años experiencia"
- "Primera consulta gratis"
- 3 áreas comunes con el cliente: civil, laboral, penal
- Tono híbrido formal-cercano
- Teléfono visible en hero
- Dirección prestigiosa (Larios)

### Carencias compartidas (oportunidad)
- Schema.org Attorney/LegalService → ninguno lo hace bien
- Testimonios reales con nombre+foto → solo Bufete de Damas
- Fotos del equipo → solo Vázquez (1 persona)
- WhatsApp Business → solo GBA y Mayorga
- Mapa Google embebido → solo Bufete de Damas
- Casos éxito cuantificados → solo Odériz
- FAQ amplia → ninguno
- Pages separadas por área legal → ninguno

---

## 4. Stack técnico propuesto

### Frontend
- **Astro** (preferido por SEO + velocidad de carga) o Next.js si necesitamos blog dinámico con ISR.
- **Tailwind CSS** para estilos.
- **MDX** para blog (soporta componentes React dentro de markdown).

### Hosting / Despliegue
- Vercel o Netlify (gratis para sitio estático con tráfico bajo-medio).
- Dominio .es preferido (mejor SEO local España).

### Formulario contacto
- Formspree (gratis hasta 50 envíos/mes), Netlify Forms (gratis con Netlify) o Resend con endpoint propio.

### Integraciones
- Google Maps embed.
- Google Business Profile (clave para SEO local).
- Google Search Console + Analytics 4.
- WhatsApp Business deeplink (`wa.me/34XXXXXXXXX`).

### SEO técnico
- Schema.org: `LegalService` + `Attorney` (uno por titular) + `LocalBusiness` + `FAQPage` + `Article`.
- sitemap.xml + robots.txt.
- Open Graph + Twitter Cards.
- Core Web Vitals optimizados (Astro lo hace solo).
- Hreflang ES si añadimos inglés (turismo Marbella, expats).

### Compliance
- LSSI: aviso legal con NIF, número colegiación de los 3 titulares, dirección física.
- RGPD: política privacidad, cookies banner.
- Texto: *"Servicios prestados por abogados colegiados en el Ilustre Colegio de Abogados de Málaga (nº XXXX, XXXX, XXXX)"*.

---

## 5. Arquitectura del sitio

### Páginas principales

| Ruta | Propósito | Schema |
|---|---|---|
| `/` | Home — hero, áreas, equipo, testimonios, CTA | `LegalService` + `LocalBusiness` |
| `/areas/civil` | Página dedicada área civil | `Service` |
| `/areas/laboral` | Página dedicada área laboral | `Service` |
| `/areas/penal` | Página dedicada área penal | `Service` |
| `/equipo` | Bios de los 3 titulares con foto | `Attorney` ×3 |
| `/equipo/[slug]` | Ficha individual de cada abogado/a | `Attorney` |
| `/casos` | Casos de éxito cuantificados (anonimizados) | — |
| `/blog` | Listado de artículos | `Blog` |
| `/blog/[slug]` | Artículo individual MDX | `Article` |
| `/faq` | Preguntas frecuentes amplias | `FAQPage` |
| `/contacto` | Form + mapa + WhatsApp + tlf | `ContactPage` |
| `/aviso-legal` | LSSI | — |
| `/privacidad` | RGPD | — |
| `/cookies` | Política cookies | — |

### Componentes clave

- `Hero` con tlf clickable + WhatsApp + CTA "Primera consulta gratis"
- `AreaCard` (3 áreas en home)
- `TeamMember` (foto, nombre, nº colegiado, áreas, LinkedIn)
- `Testimonial` (nombre real + foto + caso resuelto)
- `CaseStudy` (problema → acción → resultado cuantificado)
- `FAQItem` (acordeón, schema FAQPage automático)
- `ContactForm` (Formspree/Resend, honeypot anti-spam)
- `WhatsAppFloat` (botón flotante `wa.me/...`)
- `MapEmbed` (Google Maps Larios)
- `CookieBanner` (consentimiento granular RGPD)

---

## 6. Diseño visual (siguiente fase)

### Dirección creativa propuesta
- **Tono:** profesional + cercano (huir del "mármol y columnas griegas")
- **Paleta:** neutros cálidos + un acento (azul tinta o burdeos) — diferenciarse del azul corporativo genérico
- **Tipografía:** serif para titulares (autoridad) + sans-serif para cuerpo (legibilidad)
- **Fotografía:** equipo real, oficina real, Málaga reconocible (no stock)
- **Densidad:** generosa en blancos, no abrumar con texto

### Entregables fase 2
- Moodboard
- Mockups Figma: home + 1 área + equipo + contacto (desktop + mobile)
- Sistema de diseño mínimo (colores, tipos, espaciado, botones)

---

## 7. Roadmap

| Semana | Hito |
|---|---|
| 1 | Mockups Figma + aprobación cliente |
| 2 | Scaffold Astro + sistema de diseño + home |
| 3 | Páginas de áreas + equipo + casos |
| 4 | Blog + FAQ + contacto + legal |
| 5 | SEO técnico, schema, sitemap, GA4, GSC |
| 6 | QA, Lighthouse ≥95, despliegue producción |

---

## 8. Datos pendientes del cliente

- [ ] Nombres, fotos, números de colegiado de los 3 titulares
- [ ] Dirección exacta del despacho
- [ ] Teléfono fijo + WhatsApp Business
- [ ] NIF / razón social para LSSI
- [ ] 3-5 testimonios reales con autorización firmada
- [ ] 3-5 casos de éxito anonimizados con cifras
- [ ] Logo (o briefing para crearlo)
- [ ] Tarifas o política de honorarios (si quieren mostrarlas)
