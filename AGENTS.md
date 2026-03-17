# AGENTS.md — mlp-web

**Proyecto**: Landing page institucional del Dr. Rolando Zagret Risco Valera  
**Estudio**: Media & Legal Planning Chamber  
**URL destino**: `https://mlpperu.com`  
**Stack**: Astro 6 · Tailwind CSS v4 · TypeScript · Deploy en Cloudflare Pages (pendiente configurar)  
**Working directory**: `/Users/sebastian/Desktop/WEBS/WEBS APPS/mlp-web/`  
**Repo git**: local, rama `main` — **todavía no tiene remote en GitHub**

---

## Cliente

- **Nombre completo**: Dr. Rolando Zagret Risco Valera
- **Relación con Sebastian**: papá (familia — NO es cliente externo, es familia)
- **Estudio**: Media & Legal Planning Chamber (MLP)
- **Email de contacto**: `consultas@mlpperu.com`
- **WhatsApp**: +51 953 869 245 (número confirmado, en producción)
- **LinkedIn**: https://www.linkedin.com/in/rolando-zagret-risco-valera-6024731aa/
- **CAL**: N° 35124 (Colegio de Abogados de Lima)
- **Dirección**: Canaval y Moreyra 290, San Isidro, Lima
- **Dominio**: `mlpperu.com` — registrado en **GoDaddy** (no en Cloudflare)

### Perfil del cliente
- Minimalista — no le gusta mucha información, nada llamativo ni sombrío
- Quiere transmitir: seriedad, confianza, tranquilidad
- Audiencia: personas naturales (mayoría) y empresas

### Especialidades legales
- **Penal** ← principal, la mayoría de sus casos
- Civil
- Laboral
- Administrativo

### Formación académica (completa)
| # | Título | Institución |
|---|--------|------------|
| 01 | Abogado — Derecho | PUCP (1990–1997) |
| 02 | Maestría en Ciencias Penales | UNMSM (2005–2006) |
| 03 | Master en Gerencia Pública | EUCIM Business School (2017–2018) |
| 04 | Máster en Alta Dirección Empresarial | European Open Business School (2020–2021) |
| 05 | Máster en Política Criminal | Universidad de Salamanca (2023–2025) |

### Stats verificados
- **28+** años de ejercicio profesional
- **116+** casos gestionados (dato real de producción)
- **5** maestrías y posgrados
- **4** áreas de práctica

---

## Logo

- Tricolor: **M** amarillo/dorado `#E8B84B` · **L** verde `#3A7D44` · **P** azul `#2B6CB0`
- Archivo PNG 1024×1024 disponible (Sebastian lo tiene)
- En la web se usa como texto renderizado con CSS — no hay SVG todavía

### Paleta de colores

| Variable CSS | Hex | Uso |
|---|---|---|
| `--color-gold` | `#E8B84B` | M del logo, acento dorado |
| `--color-green` | `#3A7D44` | L del logo, acento verde |
| `--color-blue` | `#2B6CB0` | P del logo, color principal |
| `--color-blue-dark` | `#1E4E8C` | Hover del azul |
| `--color-cream` | `#FAFAF8` | Fondo principal |
| `--color-surface` | `#F3F2EF` | Fondo alternado de secciones |
| `--color-text` | `#1A1A2E` | Texto principal |
| `--color-text-muted` | `#5A6478` | Texto secundario/subtítulos |

---

## Stack técnico

| Capa | Tecnología |
|------|-----------|
| Framework | Astro 6.x (SSG) |
| Estilos | Tailwind CSS v4 via `@tailwindcss/vite` |
| TypeScript | Sí (strict) |
| Fuente | Inter (Google Fonts) |
| Sitemap | `@astrojs/sitemap` |
| Deploy destino | Cloudflare Pages (pendiente) |
| Node | >=22.12.0 |

### Reglas de desarrollo
- **NUNCA buildear local** — solo `commit + push`
- **Conventional commits** siempre, sin Co-Authored-By
- Tailwind v4 — variables en `@theme {}`, NO en `tailwind.config.js`
- CSS puro para animaciones — sin librerías JS
- Intersection Observer vanilla para scroll reveal

---

## Estructura de archivos actual

```
mlp-web/
├── astro.config.mjs          ← site: 'https://mlpperu.com'
├── src/
│   ├── pages/index.astro     ← Nav → Hero → Servicios → Nosotros → Contacto → Footer
│   ├── layouts/Layout.astro  ← SEO, OG, Inter, scroll reveal script, botón WhatsApp flotante
│   ├── styles/global.css     ← @theme variables, .reveal, .bg-pattern, .bg-pattern-surface
│   └── components/
│       ├── Nav.astro          ← navbar fija, logo MLP tricolor CSS + links + botón Consultar
│       ├── Footer.astro       ← logo + copyright + email + LinkedIn
│       └── sections/
│           ├── Hero.astro     ← centrado, logo cuadrado, nombre, tagline, CTAs, stats row
│           ├── Servicios.astro ← 4 cards con SVG icons profesionales (sin emojis)
│           ├── Nosotros.astro  ← foto circular Dr. Rolando + badge CAL + formación numerada
│           └── Contacto.astro  ← email + WhatsApp + LinkedIn + formulario mailto
└── public/
    └── dr-rolando.jpg        ← 176×176px, foto de evento social del LinkedIn
```

---

## Estado del diseño (sesión 2026-03-15)

### ✅ Funcionando
- Toda la info real del Dr. Rolando en producción
- SVG icons profesionales en Servicios (sin emojis)
- Foto circular con badge "CAL N° 35124"
- Botón flotante WhatsApp verde
- Patrón de puntos en fondo (`bg-pattern`)
- Stats en Hero: 28+ / 116+ / 5 / 4
- LinkedIn en Contacto y Footer

### ✅ Rediseño visual completado (sesión 2026-03-16)
- Hero con foto de oficina (`hero-oficina.png`) + parallax + overlay oscuro + texto blanco + serif H1
- Nav transparente sobre hero, se vuelve sólida al scrollear (80px threshold)
- Servicios con foto de biblioteca a la izquierda + grid de cards
- Nosotros con foto panorámica de sala de reuniones arriba
- Contacto con franja visual con foto del despacho + cita
- Logo MLP siempre tricolor (M=gold, L=green, P=blue) — fix aplicado en Nav y Hero

### 🔴 Bloqueado esperando assets del Doctor
| Asset | Dónde guardar | Para qué |
|-------|--------------|----------|
| **Foto corporativa** (headshot profesional) | `public/dr-rolando.jpg` (reemplaza la actual) | Sección Nosotros — foto actual es baja calidad |
| **5 fotos/escaneos de diplomas** | `public/diplomas/` | Rediseñar formación académica como catálogo de certificados |
| **Logo SVG** | `public/favicon.svg` | Favicon + reemplazar texto CSS |

### 🟡 Sin bloqueo — se puede hacer ahora
1. **Crear repo GitHub** → `github.com/notclapxz/mlp-web`
2. **Conectar Cloudflare Pages** y configurar DNS en GoDaddy
3. **Mejorar formulario** — reemplazar `mailto:` por Web3Forms o Formspree (gratis, sin backend)
4. **Agregar .gitignore** — excluir `*-check.png` y `public/fotos-oficina/`

### 📐 Decisión de diseño pendiente — Catálogo de certificados
Cuando lleguen las fotos de diplomas, reemplazar la lista numerada de formación académica por un **carrusel/grid de tarjetas** con:
- Foto real del diploma/certificado
- Título + institución + año debajo
- Lightbox para ver en grande
- CSS scroll-snap para carrusel, sin librerías JS

---

## Formulario de contacto

Actualmente usa `action="mailto:..."` — abre el cliente de email del usuario. En mobile casi no funciona.

**Opciones para reemplazarlo (sin backend):**
- **Web3Forms** — gratis hasta 250 envíos/mes, solo HTML, llega al email directo
- **Formspree** — gratis hasta 50 envíos/mes
- **Resend** — requiere API endpoint en Astro (`src/pages/api/contact.ts`)

Recomendación: **Web3Forms** — más fácil, solo agregar `action="https://api.web3forms.com/submit"` y una clave de acceso gratis.

---

## Deploy — ✅ CONFIGURADO

### Infraestructura actual
- **GitHub**: https://github.com/notclapxz/mlp-web (public)
- **Vercel**: proyecto `mlp-web` en team `sevas-projects-fd0ea484`
- **URL Vercel**: https://mlp-web.vercel.app
- **Dominio**: `mlpperu.com` → DNS A record apunta a `76.76.21.21` (Vercel)
- **SSL**: automático via Vercel
- **Deploy**: automático — `git push origin main` deploya a producción

### DNS en GoDaddy (estado actual)
| Tipo | Nombre | Apunta a | Estado |
|------|--------|----------|--------|
| **A** | `@` | `76.76.21.21` | ✅ Vercel — landing mlp-web |
| **A** | `agenda` | `76.76.21.21` | ✅ Vercel — agenda-legal — **INTOCABLE** |
| **A** | `mail` | `50.63.177.14` | ✅ GoDaddy hosting — email — **INTOCABLE** |
| **MX** | `@` | `mail.mlpperu.com` | ✅ Email — **INTOCABLE** |
| **CNAME** | `www` | `mlpperu.com` | ✅ Redirige al raíz |

### Email
- `consultas@mlpperu.com` corre en **cPanel del Web Hosting Economy de GoDaddy** (NO en Titan)
- MX apunta a `mail.mlpperu.com` → `50.63.177.14` (IP del hosting)
- **NUNCA tocar registros MX, TXT (SPF), SRV, ni el A record de `mail`**
- Si se cancela el hosting, el email SE CAE
- El Doctor dijo textualmente: **no tocar los correos**

### GoDaddy — productos activos
| Producto | Necesario | Nota |
|----------|-----------|------|
| Dominio `mlpperu.com` | ✅ Sí | ~$20/año |
| Web Hosting Economy | ✅ Sí (por email) | Renueva 4/14/2026, ~$6-8/mes |
| Titan Email (4 cuentas) | ❌ Sin usar | Disponible si se quisiera migrar |

---

## Relación con otros proyectos

| Proyecto | Relación |
|----------|----------|
| `agenda-legal` (Vercel) | Agendai del Dr. Rolando — `agenda.mlpperu.com` — **INTOCABLE** |
| `abogados-app/despacho-web` | LexDesk (CRM) — **INTOCABLE** |
| `clapxz-landing` | Landing de Sebastian |

---

## Comandos útiles

```bash
# Dev server (puerto 4322 para no chocar con clapxz-landing en 4321)
npm run dev -- --port 4322

# Ver estado git
git log --oneline
```
