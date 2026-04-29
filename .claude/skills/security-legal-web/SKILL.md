---
name: security-legal-web
description: Security checklist and automated checks specific to a lawyer / legal services website in Spain. Use before each deploy to production. Covers RGPD/LSSI compliance, contact form hardening, secret scanning, dependency audit, security headers, accessibility, and Lighthouse pre-flight. Triggered automatically when the user mentions deploy, release, lanzamiento, producción, RGPD, LSSI, vulnerabilidad, seguridad, o auditoría.
---

# Security Checklist — Despacho de Abogados (Málaga)

Pre-deploy security & compliance gate for this lawyer website.
**Run all sections before publishing changes to production.**

## Why this skill exists

A lawyer's website handles personal data (contact form), must comply with
Spanish LSSI + EU RGPD, and projects trust to potential clients.
A single security or compliance miss can mean fines (up to 4% revenue under RGPD)
or loss of credibility. This skill prevents that.

---

## 1 · Pre-deploy automated checks

Run these in order. Stop on first failure.

### 1.1 Secret scan
```bash
# detect leaked tokens / API keys / credentials
grep -rE "(api[_-]?key|secret|password|token|sk_live_|pk_live_)" \
  --include="*.{html,js,ts,jsx,tsx,astro,env}" \
  --exclude-dir={node_modules,.git,dist} \
  c:/Users/pavon/Desktop/Proyectos/abogado-web/
```

### 1.2 Dependency audit (when we add Astro/npm)
```bash
cd c:/Users/pavon/Desktop/Proyectos/abogado-web
npm audit --audit-level=high
```

### 1.3 Lighthouse production audit
- Performance ≥ 90
- Accessibility ≥ 95
- Best practices ≥ 95
- SEO ≥ 95

### 1.4 Run general security review
Trigger the existing `security-review` skill or `/security-review` command.

---

## 2 · LSSI / RGPD compliance checklist

### Aviso Legal (LSSI)
- [ ] Razón social y NIF visibles
- [ ] Nº de colegiación de los 3 titulares (ICAMÁLAGA)
- [ ] Dirección física completa
- [ ] Email de contacto
- [ ] Teléfono

### Política de Privacidad (RGPD)
- [ ] Identidad del responsable
- [ ] Finalidad del tratamiento de datos
- [ ] Base legal (consentimiento)
- [ ] Plazo de conservación de datos
- [ ] Cesión a terceros (none — declarado explícitamente)
- [ ] Derechos ARSULIPO (Acceso, Rectificación, Supresión, Limitación, Portabilidad, Oposición)
- [ ] Dirección donde ejercer derechos

### Política de Cookies
- [ ] Banner de consentimiento granular (técnicas / analíticas / marketing)
- [ ] Posibilidad de rechazar todas excepto técnicas
- [ ] Lista de cookies usadas con propósito
- [ ] Consentimiento NO debe ser pre-marcado por defecto

### Formulario de contacto
- [ ] Casilla RGPD obligatoria (no marcada por defecto)
- [ ] Enlace a política de privacidad junto a la casilla
- [ ] Honeypot anti-bot (campo invisible que humanos no rellenan)
- [ ] Rate limit en endpoint (máx. 5 envíos/min/IP)
- [ ] Validación lado servidor además del lado cliente
- [ ] Email no se almacena en logs en texto plano
- [ ] Confirmación visual al usuario tras envío

---

## 3 · Security headers

Cuando el sitio esté en producción (Astro + Vercel/Netlify/VPS),
verificar que el servidor envía:

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline' https://www.googletagmanager.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data: https://images.unsplash.com; frame-src https://www.openstreetmap.org;
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
```

Test rápido en producción:
```bash
curl -sI https://nunezparejaromero.es | grep -iE "strict-transport|content-security|x-frame|x-content|referrer|permissions"
```

O usar https://securityheaders.com/?q=nunezparejaromero.es&hide=on&followRedirects=on
(Objetivo: nota A o A+)

---

## 4 · Accesibilidad (WCAG 2.1 AA)

- [ ] Contraste mínimo 4.5:1 en texto normal, 3:1 en grandes
- [ ] Todas las imágenes con `alt` descriptivo
- [ ] Formularios con `<label>` asociado a cada `<input>`
- [ ] Navegación por teclado funcional (Tab + Enter)
- [ ] `lang="es"` en `<html>`
- [ ] Sin uso exclusivo de color para transmitir información

---

## 5 · SEO y datos estructurados

- [ ] `schema.org/LegalService` en home
- [ ] `schema.org/Attorney` por cada titular en /equipo
- [ ] `schema.org/LocalBusiness` con dirección Málaga
- [ ] `schema.org/FAQPage` en /faq
- [ ] `schema.org/Article` en cada post de blog
- [ ] sitemap.xml accesible en `/sitemap.xml`
- [ ] robots.txt apunta al sitemap
- [ ] Open Graph + Twitter Cards en cada página

Validar en https://search.google.com/test/rich-results

---

## 6 · Logging y privacidad

- [ ] No log de IPs completas (anonimizar último octeto)
- [ ] No log de campos del formulario en texto plano
- [ ] Backups cifrados
- [ ] Retención máxima 12 meses para logs

---

## 7 · Failure mode

Si cualquier punto falla, **detener el deploy** y crear issue en el repo:

```
https://github.com/pavonicdev-selu/abogado-web/issues/new
```

Con label `security` o `compliance`.

---

## Resources

- AEPD — Agencia Española de Protección de Datos: https://www.aepd.es/
- LSSI — Ley Servicios Sociedad Información: https://www.boe.es/buscar/act.php?id=BOE-A-2002-13758
- Schema.org LegalService: https://schema.org/LegalService
- ICAMÁLAGA — Ilustre Colegio de Abogados de Málaga: https://www.icamalaga.org/
