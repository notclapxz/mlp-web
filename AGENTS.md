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

### ⚠️ Problema de diseño identificado — NO RESUELTO
**El Hero se ve vacío.** El fondo con puntos apenas se nota en pantallas Retina (Mac M5). El contenido flota en el centro sin anclas visuales.

**Solución acordada para próxima sesión:**
Reemplazar el Hero actual por un **Hero con imagen de fondo de la oficina** — estilo Estudio Rodrigo (`estudiorodrigo.com`). Texto blanco sobre imagen oscura con overlay semitransparente.

**Referencia de inspiración analizada:** `https://www.estudiorodrigo.com/`
- Hero con foto ambiente de sala de reuniones/despacho oscuro y elegante
- Título en blanco sobre imagen con overlay
- Tipografía serif para títulos da autoridad legal
- Fondo blanco puro para el resto del contenido (sin patrones)

**Lo que se necesita para implementar:**
- ⏳ **Foto de la oficina** de Canaval y Moreyra 290 — Sebastian la va a sacar cuando pueda
- Mientras no haya foto real, se puede usar una de Unsplash temporalmente (sala de reuniones oscura)
- Guardar la foto como `public/hero-oficina.jpg`

**Instrucciones para cuando llegue la foto:**
1. Copiar imagen a `public/hero-oficina.jpg`
2. En `Hero.astro`: cambiar `<section>` a tener `background-image: url('/hero-oficina.jpg')`
3. Agregar overlay oscuro semitransparente (`bg-black/50` o similar)
4. Cambiar texto a blanco (`text-white`)
5. Considerar cambiar fuente del H1 a serif (Georgia) para más autoridad

---

## Pendientes para próxima sesión

### 🔴 Bloqueado esperando assets
| Asset | Dónde guardar | Para qué |
|-------|--------------|----------|
| **Foto de la oficina** | `public/hero-oficina.jpg` | Fondo del Hero — el cambio más importante |
| **Logo SVG** | `public/favicon.svg` | Favicon + reemplazar texto CSS |

### 🟡 Sin bloqueo — se puede hacer ahora
1. **Crear repo GitHub** → `github.com/notclapxz/mlp-web`
2. **Conectar Cloudflare Pages** y configurar DNS en GoDaddy
3. **Mejorar formulario** — reemplazar `mailto:` por Web3Forms o Formspree (gratis, sin backend)
4. **Tipografía serif** para H1 del Hero — da más autoridad sin necesitar foto

---

## Formulario de contacto

Actualmente usa `action="mailto:..."` — abre el cliente de email del usuario. En mobile casi no funciona.

**Opciones para reemplazarlo (sin backend):**
- **Web3Forms** — gratis hasta 250 envíos/mes, solo HTML, llega al email directo
- **Formspree** — gratis hasta 50 envíos/mes
- **Resend** — requiere API endpoint en Astro (`src/pages/api/contact.ts`)

Recomendación: **Web3Forms** — más fácil, solo agregar `action="https://api.web3forms.com/submit"` y una clave de acceso gratis.

---

## Deploy (pendiente)

### Situación actual del dominio
- `mlpperu.com` en **GoDaddy** — sin SSL, apunta a web vieja
- `agenda.mlpperu.com` → Vercel (Agendai del Dr. Rolando) — **INTOCABLE**

### Plan
1. Crear repo GitHub: `github.com/notclapxz/mlp-web`
2. Conectar a Cloudflare Pages
3. En GoDaddy: agregar CNAME `mlpperu.com → cname.pages.dev` O mover nameservers a Cloudflare
4. SSL automático con Cloudflare

> ⚠️ Al mover DNS de GoDaddy, verificar que `agenda.mlpperu.com` siga apuntando a Vercel. No tocar ese subdominio.

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
