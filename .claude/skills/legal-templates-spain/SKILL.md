---
name: legal-templates-spain
description: Generate the legal text required by Spanish law (LSSI/RGPD/cookies) for a lawyer website. Produces ready-to-use markdown for "Aviso Legal", "Política de Privacidad" and "Política de Cookies" pages, customized with the client's NIF, colegiación, address, and contact data. Trigger when the user mentions aviso legal, política de privacidad, política de cookies, RGPD textos, LSSI textos, generar legales, or asks to draft any of these documents.
---

# Legal Templates — Spain (Lawyer Website)

This skill outputs Spanish legal pages ready to publish.
Reflects current AEPD guidelines and ICAMÁLAGA bar rules.

## Required client data (ask if missing)

```
[firm_name]      → razón social completa (ej. "Núñez Pareja Romero S.L.P.")
[trade_name]     → nombre comercial (ej. "Núñez · Pareja · Romero · Abogados")
[nif]            → CIF/NIF (ej. "B-00000000")
[address]        → dirección fiscal (ej. "Calle Larios 5, 2ª planta, 29005 Málaga")
[email]          → email contacto (ej. "contacto@nunezparejaromero.es")
[phone]          → teléfono (ej. "+34 952 00 00 00")
[domain]         → dominio web (ej. "nunezparejaromero.es")
[lawyers]        → lista de titulares con nº de colegiado
                   (ej. "Andrés Núñez Lara — ICAMÁLAGA 4421;
                         Lucía Pareja Ortega — ICAMÁLAGA 5108;
                         Carmen Romero Salas — ICAMÁLAGA 5742")
[register_data]  → datos registro mercantil si aplica (opcional)
[hosting]        → proveedor de hosting (ej. "GitHub Pages — GitHub, Inc.")
[analytics]      → herramientas de analítica (ej. "Google Analytics 4 / ninguna")
```

If the user has NOT provided these yet, **ask first** with the placeholder list.
Don't generate text with `[placeholders]` left in.

---

## Document 1 · Aviso Legal (LSSI-CE)

```markdown
# Aviso Legal

## 1. Identificación del titular

En cumplimiento de la Ley 34/2002, de 11 de julio, de Servicios de la Sociedad
de la Información y Comercio Electrónico (LSSI-CE), se informa que este sitio web
**[domain]** es titularidad de:

- **Razón social:** [firm_name]
- **Nombre comercial:** [trade_name]
- **NIF:** [nif]
- **Domicilio profesional:** [address]
- **Correo electrónico:** [email]
- **Teléfono:** [phone]
[register_data si aplica → · Inscrita en el Registro Mercantil de Málaga, ...]

## 2. Servicios prestados

Los servicios prestados por **[trade_name]** son ejercidos por abogados/as
colegiados/as en el Ilustre Colegio de Abogados de Málaga (ICAMÁLAGA),
sometidos a las normas deontológicas del Estatuto General de la Abogacía Española
y al Código Deontológico de los abogados.

Titulares colegiados:

[para cada lawyer en lawyers:]
- **[nombre]** — Colegiado/a nº [num_col] del ICAMÁLAGA

Pueden verificar la condición de colegiado en https://www.icamalaga.org/

## 3. Condiciones de uso

El acceso a este sitio web es libre y gratuito. La información publicada tiene
carácter meramente informativo y no constituye asesoramiento jurídico.
Para recibir asesoramiento concreto sobre un asunto, es necesario formalizar
una consulta presencial, telefónica o por videollamada con uno de los titulares.

## 4. Propiedad intelectual

Todos los contenidos del sitio (textos, imágenes, logotipos, diseño, código)
son titularidad de [firm_name] o de terceros que han autorizado su uso.
Queda prohibida su reproducción total o parcial sin autorización expresa.

## 5. Responsabilidad

[firm_name] no se responsabiliza de los contenidos enlazados desde este sitio
hacia páginas de terceros. La información jurídica publicada se ofrece sin
garantía de exhaustividad o vigencia normativa.

## 6. Legislación aplicable y jurisdicción

Este aviso legal se rige por la legislación española. Cualquier controversia
derivada del uso de este sitio web se someterá a los Juzgados y Tribunales
de Málaga capital.

---
*Última actualización: [fecha]*
```

---

## Document 2 · Política de Privacidad (RGPD)

```markdown
# Política de Privacidad

## 1. Responsable del tratamiento

En cumplimiento del Reglamento (UE) 2016/679 (RGPD) y de la Ley Orgánica 3/2018
de Protección de Datos Personales y garantía de los derechos digitales (LOPDGDD),
se informa de los siguientes datos del responsable del tratamiento:

- **Responsable:** [firm_name]
- **NIF:** [nif]
- **Dirección:** [address]
- **Email de contacto en materia de protección de datos:** [email]

## 2. Datos que tratamos

Los datos personales que tratamos provienen de:

- **Formulario de contacto:** nombre, teléfono, email, área de la consulta
  y mensaje libre.
- **Cookies técnicas y, si lo autoriza, analíticas:** ver Política de Cookies.

## 3. Finalidad y base legal

| Finalidad | Base legal |
|---|---|
| Atender su consulta | Consentimiento del interesado (art. 6.1.a RGPD) |
| Facturación si pasa a ser cliente | Ejecución de contrato (art. 6.1.b RGPD) |
| Cumplimiento de obligaciones legales (deontología, fiscalidad) | Obligación legal (art. 6.1.c RGPD) |
| Mejora del sitio web | Interés legítimo (art. 6.1.f RGPD) |

## 4. Conservación

- Datos del formulario de contacto sin conversión a cliente: **12 meses**
  desde el último contacto, después se borran.
- Datos de clientes en activo: durante toda la relación profesional.
- Datos archivados (clientes pasados): **5 años** según obligaciones del
  Estatuto General de la Abogacía y normativa fiscal.

## 5. Cesión a terceros

**No cedemos sus datos a terceros** salvo obligación legal o necesidad
procesal (presentación ante juzgados, comunicación a la parte contraria,
etc.) y siempre dentro del marco de la relación profesional autorizada.

Encargados del tratamiento (proveedores tecnológicos):
- **Hosting:** [hosting]
- **Email:** [proveedor email, ej. Google Workspace, IONOS]
- **Analítica:** [analytics]

Todos los encargados firman contrato bajo art. 28 RGPD.

## 6. Derechos del interesado (ARSULIPO)

Puede ejercer en cualquier momento sus derechos de:

- **A**cceso
- **R**ectificación
- **S**upresión
- Oposici**ón**
- **L**imitación del tratamiento
- Portab**i**lidad
- **N**o ser objeto de decisiones automatizadas

Cómo ejercerlos: enviando un correo a **[email]** con el asunto
"Protección de Datos" y copia de su DNI o documento equivalente.

Si considera que sus derechos no han sido atendidos, puede reclamar ante la
**Agencia Española de Protección de Datos (AEPD)** en https://www.aepd.es/

## 7. Seguridad

Aplicamos medidas técnicas y organizativas adecuadas (cifrado HTTPS, control
de accesos, copias de seguridad cifradas, registro de actividad) para proteger
sus datos frente a accesos no autorizados, pérdida o destrucción.

---
*Última actualización: [fecha]*
```

---

## Document 3 · Política de Cookies

```markdown
# Política de Cookies

## 1. Qué son las cookies

Las cookies son pequeños archivos de texto que un sitio web guarda en su
dispositivo cuando lo visita. Se usan para que el sitio funcione, recordar
sus preferencias o medir cómo se usa.

## 2. Tipos de cookies que usamos

| Cookie | Tipo | Propósito | Duración |
|---|---|---|---|
| `cookie_consent` | Técnica · propia | Recordar su elección de cookies | 12 meses |
| `_ga` | Analítica · Google | Distinguir usuarios únicos (anonimizado) | 13 meses |
| `_ga_XXXXXXX` | Analítica · Google | Persistencia de sesión GA4 | 13 meses |

[ELIMINAR la fila de Google Analytics si no se va a usar GA4]

## 3. Cookies técnicas

Necesarias para el funcionamiento del sitio. **No requieren consentimiento.**

## 4. Cookies analíticas

Sólo se activan si **acepta expresamente** en el banner de cookies.
Los datos recolectados son anónimos y agregados — no identifican
personalmente a ningún usuario. Anonimizamos la dirección IP completa.

## 5. Gestión y revocación del consentimiento

Puede revocar su consentimiento en cualquier momento:

1. Pulsando el botón "Cookies" del pie de página.
2. Borrando las cookies desde la configuración de su navegador:
   - **Chrome:** Configuración → Privacidad → Cookies y otros datos
   - **Firefox:** Ajustes → Privacidad y seguridad → Cookies
   - **Safari:** Preferencias → Privacidad → Cookies y datos del sitio
   - **Edge:** Configuración → Cookies y permisos del sitio

## 6. Más información

Para más información sobre cookies y su privacidad, consulte la guía de la
AEPD: https://www.aepd.es/guias/guia-cookies.pdf

---
*Última actualización: [fecha]*
```

---

## How to use this skill

1. **Ask the user for missing data** (NIF, colegiación, etc.) using the
   `Required client data` block at the top.
2. **Replace every `[placeholder]`** with the real value.
3. **Set the date** in `[fecha]` to today's date in format `DD de MMMM de YYYY`
   (Spanish).
4. **Output three files** at:
   - `src/pages/aviso-legal.md` (or `.astro` once we have Astro)
   - `src/pages/privacidad.md`
   - `src/pages/cookies.md`
5. **Generate `<a href>` links** in the footer of every page pointing to these.

## Verification before publishing

- [ ] No queda ningún `[placeholder]` sin sustituir
- [ ] La fecha está actualizada
- [ ] Los nombres de colegiados son los reales y verificables
- [ ] El email de contacto es funcional
- [ ] El banner de cookies enlaza a esta política
- [ ] El formulario de contacto tiene casilla RGPD enlazando aquí
- [ ] La AEPD es citada con su URL correcta

## References

- LSSI-CE: https://www.boe.es/buscar/act.php?id=BOE-A-2002-13758
- RGPD: https://eur-lex.europa.eu/legal-content/ES/TXT/?uri=CELEX%3A32016R0679
- LOPDGDD: https://www.boe.es/buscar/act.php?id=BOE-A-2018-16673
- AEPD: https://www.aepd.es/
- ICAMÁLAGA: https://www.icamalaga.org/
- Estatuto General de la Abogacía: https://www.abogacia.es/estatuto-general/
