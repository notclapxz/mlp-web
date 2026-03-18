# AGENTS.md — mlp-web

**Proyecto**: Landing page institucional del Dr. Rolando Zagret Risco Valera  
**Estudio**: Media & Legal Planning Chamber  
**URL producción**: `https://mlpperu.com`  
**Stack**: Astro 6 · Tailwind CSS v4 · TypeScript · Deploy en Vercel (automático)  
**Working directory**: `/Users/sebastian/Desktop/WEBS/WEBS APPS/mlp-web/`  
**Repo git**: https://github.com/notclapxz/mlp-web (rama `main`)

---

## Cliente

- **Nombre completo**: Dr. Rolando Zagret Risco Valera
- **Relación con Sebastian**: papá (familia — NO es cliente externo, es familia)
- **Estudio**: Media & Legal Planning Chamber (MLP) · también opera como "Risco Valera Abogados & Consultores"
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

### Formación académica (completa — 7 credenciales en producción)
| # | Título | Institución | Año |
|---|--------|------------|-----|
| 01 | Título de Abogado | PUCP | 1997 |
| 02 | Maestría en Ciencias Penales | UNMSM | 2006 |
| 03 | Master en Gerencia Pública | EUCIM Business School | 2018 |
| 04 | Máster en Alta Dirección Empresarial | European Open Business School | 2021 |
| 05 | Máster en Política Criminal | Universidad de Salamanca | 2025 |
| 06 | Diploma en Compliance Corporativo | Instituto para la Calidad — PUCP | 2021 |
| 07 | Primer Puesto — Compliance y Auditoría | Instituto para la Calidad — PUCP | 2021 |

### Stats en Hero (actuales en producción)
- **20+** años de ejercicio profesional (color: blanco)
- **15+** años de MLP (color: gold `#E8B84B`)
- **5** maestrías y posgrados (color: verde claro `#5CB870`)
- **4** áreas de práctica (color: azul claro `#4A90D9`)
- ⚠️ Se eliminó el stat "116+ casos gestionados" a pedido del Doctor

---

## Logo

- Tricolor: **M** amarillo/dorado `#E8B84B` · **L** verde `#3A7D44` · **P** azul `#2B6CB0`
- En la web se usa como texto renderizado con CSS (Nav + Hero)
- SVG favicon custom implementado en `public/favicon.svg`

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
| Deploy | Vercel (automático desde GitHub `main`) |
| Node | >=22.12.0 |

### Reglas de desarrollo
- **NUNCA buildear local** — solo `commit + push`
- **Conventional commits** siempre, sin Co-Authored-By
- Tailwind v4 — variables en `@theme {}`, NO en `tailwind.config.js`
- CSS puro para animaciones — sin librerías JS
- Intersection Observer vanilla para scroll reveal
- JavaScript vanilla para carrusel e interacciones (sin librerías)

---

## Estructura de archivos actual

```
mlp-web/
├── astro.config.mjs              ← site: 'https://mlpperu.com'
├── src/
│   ├── pages/index.astro         ← Nav → Hero → Servicios → Nosotros → Contacto → Footer
│   ├── layouts/Layout.astro      ← SEO, OG, Inter, scroll reveal script, botón WhatsApp flotante
│   ├── styles/global.css         ← @theme variables, .reveal, estilos globales
│   └── components/
│       ├── Nav.astro             ← navbar fija, logo MLP tricolor CSS + links + botón Consultar
│       │                           se vuelve sólida al scroll (80px threshold), transparente sobre hero
│       ├── Footer.astro          ← logo + copyright + email + LinkedIn
│       └── sections/
│           ├── Hero.astro        ← foto oficina JPEG fondo, overlay oscuro, logo cuadrado,
│           │                       nombre estudio, tagline, CTAs, stats row (4 stats)
│           ├── Servicios.astro   ← foto biblioteca izquierda + 4 cards SVG icons
│           ├── Nosotros.astro    ← foto panorámica sala reuniones + foto Dr. Rolando circular
│           │                       + badge CAL + párrafo bio + CARRUSEL de credenciales
│           │                       + modal PDF viewer (sin toolbar, sin right-click)
│           ├── Credenciales.astro← (existente pero NO importado en index.astro — en desuso)
│           └── Contacto.astro    ← franja visual con foto despacho + cita + email + WhatsApp
│                                   + LinkedIn + formulario mailto
└── public/
    ├── dr-rolando.jpg            ← foto circular Dr. Rolando (actual — calidad mejorable)
    ├── hero-oficina.jpeg         ← foto de fondo del Hero (versión sin botellas)
    ├── oficina-biblioteca.png    ← foto para sección Servicios
    ├── oficina-despacho.png      ← foto para franja de Contacto
    ├── oficina-reuniones.png     ← foto panorámica para Nosotros
    ├── oficina-reuniones-libros.png ← foto alternativa (disponible)
    ├── favicon.svg               ← favicon SVG tricolor MLP custom
    ├── favicon.ico               ← fallback
    ├── og-image.jpg              ← OG image para redes sociales
    └── certificados/
        ├── previews/             ← 7 PNG thumbnails de cada certificado
        │   ├── 01-titulo-abogado-pucp.png
        │   ├── 02-maestria-derecho-penal.png
        │   ├── 03-master-gerencia-publica.png
        │   ├── 04-master-alta-direccion.png
        │   ├── 05-master-politica-criminal.png
        │   ├── 06-diploma-compliance.png
        │   └── 07-constancia-primer-puesto.png
        ├── Título de Abogado PUCP 31.07.2002.pdf
        ├── Constancia de Estudios de Maestría en Derecho Penal.pdf
        ├── Título Propio Master en Gerencia Pública Apostillado.pdf
        ├── Máster Alta Dirección Empresarial Universidad de Álcala.pdf
        ├── Diploma Máster en Política Criminal.pdf
        ├── Diploma Compliance Corporativo y Auditoría de Riesgos.pdf
        └── Constancia Primer Puesto Compliance Corporativo y Auditoría de Riesgos.pdf
```

---

## Estado del diseño (sesión 2026-03-18 — actualizado)

### ✅ Implementado y en producción

**Visual:**
- Hero: foto de oficina JPEG de fondo, overlay oscuro degradado, logo cuadrado translúcido, H1 estudio, tagline, dos CTAs, stats row
- Nav: transparente sobre hero, se vuelve blanca/sólida al hacer scroll (80px), logo tricolor siempre
- Servicios: foto biblioteca izquierda (5/12) + grid 2×2 de cards con SVG icons y acento de color
- Nosotros: foto panorámica sala de reuniones arriba, foto circular Dr. Rolando con badge CAL, párrafo bio, carrusel de credenciales
- Contacto: franja visual paralax con foto despacho + cita literaria + email + WhatsApp + LinkedIn + formulario mailto
- Favicon: SVG tricolor MLP custom
- OG image: para compartir en redes sociales
- Page reveal: fade-in al cargar (overlay que desaparece)
- Botón WhatsApp flotante: verde, siempre visible

**Carrusel de credenciales (en Nosotros.astro):**
- 7 tarjetas con preview PNG + info (título, institución, año)
- Autoplay cada 2200ms con loop al final
- Botón play/pause + flechas prev/next
- Pausa al hacer hover con el mouse
- Las flechas manuales pausan el autoplay
- Modal PDF al hacer click en tarjeta: sin toolbar, sin right-click, backdrop blur, cierra con Escape o click fuera

**Performance:**
- `fetchpriority="high"` en la imagen del hero
- `loading="lazy"` en imágenes debajo del fold
- Fallback: `background-color: #1A1A2E` en la sección hero por si no carga la imagen

### ⚠️ Pendiente / conocido

| Item | Detalle |
|------|---------|
| **Formulario** | Usa `action="mailto:..."` — en mobile casi no funciona. Pendiente migrar a Web3Forms o similar |
| **Foto Dr. Rolando** | La actual es recortada de LinkedIn, calidad mejorable. Pendiente foto profesional |
| **Credenciales.astro** | Archivo existente pero NO está importado en `index.astro` — fue reemplazado por el carrusel inline en Nosotros. Se puede eliminar o reusar |

### 🗑️ Eliminado / descartado
- Stat "116+ casos gestionados" — el Doctor pidió quitarlo
- Stat "28+ años" — cambiado a "20+"  
- Hero antigua con patrón de puntos (`bg-pattern`) — reemplazada por foto de oficina
- Sección Credenciales separada — integrada al carrusel dentro de Nosotros

---

## Formulario de contacto

Actualmente usa `action="mailto:..."` — abre el cliente de email del usuario. En mobile casi no funciona.

**Opciones para reemplazarlo (sin backend):**
- **Web3Forms** — gratis hasta 250 envíos/mes, solo HTML, llega al email directo ← **recomendado**
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

# Deploy = push a main (Vercel lo hace automático)
git push origin main
```
