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
- **Teléfono**: pendiente confirmar si quiere que aparezca en la web
- **Dominio**: `mlpperu.com` — registrado en **GoDaddy** (no en Cloudflare)

### Perfil del cliente
- Minimalista — no le gusta mucha información, nada llamativo ni sombrío
- Quiere transmitir: seriedad, confianza, tranquilidad
- Audiencia: personas naturales (mayoría) y empresas

### Especialidades legales (del código de abogados-app)
- **Penal** ← principal, la mayoría de sus casos
- Civil
- Laboral  
- Administrativo

### Datos verificados desde producción (abogados-app)
- **116+ casos** gestionados en producción activa
- App LexDesk (abogados-app) corriendo en producción con esos datos reales

---

## Logo

- Tricolor: **M** amarillo/dorado · **L** verde · **P** azul institucional
- Archivo original: imagen PNG cuadrada 1024×1024 (Sebastian lo tiene)
- En la web se usa como texto renderizado con CSS (no imagen SVG todavía)

### Paleta de colores (extraída del logo)

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
| Framework | Astro 6.x (SSG — static site generation) |
| Estilos | Tailwind CSS v4 via `@tailwindcss/vite` |
| TypeScript | Sí (strict) |
| Fuente | Inter (Google Fonts) |
| Sitemap | `@astrojs/sitemap` |
| Deploy destino | Cloudflare Pages (pendiente configurar) |
| Node | >=22.12.0 |

### Reglas de desarrollo
- **NUNCA buildear local** — solo `commit + push`, Cloudflare Pages buildea automático
- **Conventional commits** siempre, sin Co-Authored-By
- Tailwind v4 — sintaxis diferente a v3: variables en `@theme {}`, no en `tailwind.config.js`
- CSS puro para animaciones — sin librerías JS de animación
- Intersection Observer vanilla para scroll reveal

---

## Estructura de archivos

```
mlp-web/
├── astro.config.mjs          ← site: 'https://mlpperu.com', Tailwind v4 + sitemap
├── package.json
├── src/
│   ├── pages/
│   │   └── index.astro       ← única página, importa todos los componentes
│   ├── layouts/
│   │   └── Layout.astro      ← HTML base, meta SEO, OG tags, Inter font, scroll reveal script
│   ├── styles/
│   │   └── global.css        ← @import tailwindcss + @theme variables + .reveal classes
│   └── components/
│       ├── Nav.astro          ← navbar fija, logo MLP + links + botón Consultar
│       ├── Footer.astro       ← logo + copyright + email
│       └── sections/
│           ├── Hero.astro     ← logo cuadrado, nombre completo, tagline, 2 CTAs
│           ├── Servicios.astro ← 4 cards: Penal, Civil, Laboral, Administrativo
│           ├── Nosotros.astro  ← stats + lista formación (con placeholders)
│           └── Contacto.astro  ← email + formulario mailto
└── public/                   ← vacío — agregar favicon cuando tengamos SVG
```

### Orden de secciones en index.astro
```
Nav → Hero → Servicios → Nosotros → Contacto → Footer
```

### Fondos alternados de secciones
| Sección | Fondo |
|---------|-------|
| Hero | `#FAFAF8` (cream) |
| Servicios | `#F3F2EF` (surface) |
| Nosotros | `#FAFAF8` (cream) |
| Contacto | `#F3F2EF` (surface) |
| Footer | `#1A1A2E` (dark) |

---

## Animaciones

- Clase `.reveal` en cada elemento — `opacity: 0` + `translateY(24px)`
- Clase `.visible` la agrega el Intersection Observer en `Layout.astro`
- Delays: `.reveal-delay-1` a `.reveal-delay-4` para escalonar elementos
- `prefers-reduced-motion: reduce` desactiva todo — accesible
- Todo en CSS puro — cero librerías JS

---

## Pendientes (info que falta del Dr. Rolando)

> Estos datos están como placeholders en el código con texto `[pendiente]` — fácil de encontrar con grep

| Dato | Archivo | Placeholder actual |
|------|---------|-------------------|
| Universidad de pregrado | `Nosotros.astro` | `Abogado — [Universidad, pendiente]` |
| Maestría/s y especialidad | `Nosotros.astro` | `Maestría en [Especialidad, pendiente]` |
| Teléfono/WhatsApp | `Contacto.astro` | No aparece — agregar si confirma |
| Años de experiencia | `Nosotros.astro` | `15+` (estimado — confirmar) |
| Foto del Dr. Rolando | — | No hay — opcional para sección Nosotros |
| Logo SVG oficial | `public/` | No hay — usar como favicon cuando lo tengan |

Para encontrar todos los pendientes:
```bash
grep -r "pendiente" src/
```

---

## Formulario de contacto

Actualmente usa `action="mailto:..."` — **abre el cliente de email del usuario**.  
Es funcional pero básico. Si en el futuro se quiere un formulario que envíe directo al email:
- Opción A: **Resend** con Astro API endpoint (`src/pages/api/contact.ts`)
- Opción B: **Formspree** (sin backend, solo HTML)
- Opción C: **Web3Forms** (gratis, sin backend)

Por ahora el mailto está bien para empezar.

---

## Deploy (pendiente — configurar al final)

### Situación actual del dominio
- `mlpperu.com` está en **GoDaddy** (no en Cloudflare)
- Sin SSL activo — aparece como "no seguro" en el browser
- Actualmente apunta a una web vieja con solo fondo + email

### Plan de deploy
1. Crear repo en GitHub: `github.com/notclapxz/mlp-web`
2. Conectar a **Cloudflare Pages** (igual que clapxz-landing)
3. En GoDaddy: cambiar nameservers a Cloudflare **O** agregar CNAME a Cloudflare Pages
4. SSL se resuelve automático con Cloudflare

### Alternativa si no quieren mover a Cloudflare
- Deploy en Vercel y apuntar DNS de GoDaddy al dominio de Vercel con CNAME
- Sebastian ya tiene cuenta Vercel activa (`notclapxz`) — plan free: 3 proyectos

---

## Decisiones técnicas tomadas

| Decisión | Razón |
|----------|-------|
| Astro SSG (sin framework JS) | Landing estática, carga instantánea, cero mantenimiento |
| Una sola página (single page) | El Dr. Rolando es minimalista — no quiere mucho contenido |
| Sin foto hero | No se tiene foto todavía — diseño funciona sin ella |
| Logo como texto CSS | No se tiene SVG todavía — se puede reemplazar con `<img>` cuando lo haya |
| Formulario mailto | Sin backend por ahora — funcional y cero infraestructura |
| Fuente Inter (Google Fonts) | Limpia, legible, institucional — ni demasiado formal ni informal |
| Paleta basada en el logo | El logo ya define los colores — mantener coherencia de marca |
| CSS puro para animaciones | Cero JS extra, respeta prefers-reduced-motion |

---

## Comandos útiles

```bash
# Dev server (puerto 4322 para no chocar con clapxz-landing en 4321)
npm run dev -- --port 4322

# Buscar placeholders pendientes
grep -r "pendiente" src/

# Ver estado git
git status
git log --oneline
```

---

## Relación con otros proyectos de Sebastian

| Proyecto | Relación |
|----------|----------|
| `agenda-legal` (Vercel) | Agendai del Dr. Rolando — `agenda.mlpperu.com` — **INTOCABLE sin orden explícita** |
| `abogados-app/despacho-web` | LexDesk (CRM legal) — también del Dr. Rolando — **INTOCABLE** |
| `clapxz-landing` | Landing de Sebastian — menciona "Despacho Legal" como producto |

> ⚠️ NUNCA tocar `agenda-legal` ni `abogados-app` trabajando en este repo.

---

## Estado actual (sesión 2026-03-14)

### ✅ Hecho
- Proyecto Astro 6 scaffoldeado con Tailwind v4 + sitemap
- Layout base con SEO, OG, Inter font, scroll reveal
- Nav fija con logo tricolor
- Hero: logo cuadrado, nombre completo, tagline, 2 CTAs
- Servicios: 4 cards con acentos de color del logo
- Nosotros: stats (116+ casos, 15+ años) + formación con placeholders
- Contacto: email + formulario mailto
- Footer oscuro con logo + email
- Git init, rama `main`, primer commit

### 🔴 Pendiente para próxima sesión
1. Conseguir info del Dr. Rolando: universidad, maestría/s, teléfono (opcional)
2. Crear repo en GitHub y conectar a Cloudflare Pages
3. Configurar DNS en GoDaddy para apuntar a Cloudflare Pages
4. Agregar favicon (cuando haya SVG del logo)
5. Reemplazar logo CSS por imagen SVG real cuando esté disponible
6. Decidir si agregar foto del Dr. Rolando en sección Nosotros
