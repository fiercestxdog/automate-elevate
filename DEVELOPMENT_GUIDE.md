# Shopify Theme Development Guide

## Project Overview

**Goal**: Set up a local development workflow for Shopify theme customization with GitHub sync and Shopify deployment.

**Source Repository**: https://github.com/fiercestxdog/automate-elevate
**Local Path**: `C:\python\projects\shopify_theme\`
**Business**: Automate & Elevate - Web Design & AI Automation Services

---

## Phase 1: Initial Setup ✅ COMPLETE

### 1.1 Clone Repository
```powershell
cd C:\python\projects
git clone https://github.com/fiercestxdog/automate-elevate.git shopify_theme
```

### 1.2 Install Shopify CLI
```powershell
npm install -g @shopify/cli @shopify/theme
shopify version  # v3.88.1 confirmed
```

### 1.3 Analyze Existing Structure
- Original: Static HTML site with inline CSS
- Files: `index.html` (930 lines), `ai_receptionist.html` (488 lines)
- Design: Professional landing page with hero, services, process, CTA sections

---

## Phase 2: Theme Conversion ✅ COMPLETE

### 2.1 Directory Structure Created

```
shopify_theme/
├── .github/workflows/
│   └── deploy.yml              # GitHub Actions CI/CD
├── assets/
│   ├── theme.css               # Main styles (extracted from index.html)
│   └── ai-receptionist.css     # AI page styles (extracted)
├── config/
│   ├── settings_schema.json    # Theme customization options
│   └── settings_data.json      # Current theme values
├── layout/
│   └── theme.liquid            # Main layout wrapper
├── locales/
│   └── en.default.json         # English translations
├── sections/
│   ├── header.liquid           # Navigation (configurable)
│   ├── footer.liquid           # Footer with social links
│   ├── hero.liquid             # Hero + floating feature cards
│   ├── services.liquid         # 4-service grid
│   ├── process.liquid          # 4-step timeline
│   ├── cta.liquid              # Call to action
│   └── ai-receptionist.liquid  # AI Receptionist landing page
├── snippets/                   # (empty, for future reusable code)
├── templates/
│   ├── index.json              # Homepage template
│   ├── page.liquid             # Generic page template
│   ├── page.ai-receptionist.json  # AI Receptionist template
│   └── 404.liquid              # Error page
├── .gitignore                  # Shopify-specific ignores
├── README.md                   # Theme documentation
└── DEVELOPMENT_GUIDE.md        # This file
```

### 2.2 Conversion Details

| Original File | Converted To |
|---------------|--------------|
| `index.html` inline CSS | `assets/theme.css` |
| `index.html` nav | `sections/header.liquid` |
| `index.html` hero | `sections/hero.liquid` |
| `index.html` services | `sections/services.liquid` |
| `index.html` process | `sections/process.liquid` |
| `index.html` CTA | `sections/cta.liquid` |
| `index.html` footer | `sections/footer.liquid` |
| `ai_receptionist.html` | `sections/ai-receptionist.liquid` + `assets/ai-receptionist.css` |

### 2.3 Theme Features

**Customizable via Shopify Admin:**
- Brand colors (Cream, Charcoal, Sage, Clay, Slate, Gold)
- Typography (Playfair Display, DM Sans)
- Navigation menu
- Social media links
- All section content (headings, descriptions, buttons)
- Service cards with features
- Process steps with icons
- AI Receptionist benefits and steps

**Shopify Liquid Features Used:**
- `{{ content_for_layout }}` - Dynamic page content
- `{% section %}` - Modular sections
- `{% schema %}` - Theme editor configuration
- Blocks for repeatable content (services, process steps, benefits)
- Settings for customizable text, URLs, colors

---

## Phase 3: Local Development ✅ COMPLETE

### 3.1 Static Preview (No Store Required)
```powershell
cd C:\python\projects\shopify_theme
npx serve .
```
Opens at `http://localhost:3000`

Note: Liquid tags won't render in static preview - you'll see the raw template syntax. This is expected without Shopify.

### 3.2 VS Code Setup
Recommended extensions:
- **Shopify Liquid** - Syntax highlighting for .liquid files
- **Liquid** - Additional Liquid language support
- **Prettier** - Code formatting

### 3.3 Git Workflow
```powershell
# Make changes to theme files
git add .
git commit -m "Update hero section styling"
git push origin main
```

---

## Phase 4: GitHub Actions ✅ COMPLETE

### 4.1 Workflow File Created
`.github/workflows/deploy.yml` - Automatically deploys to Shopify on push to main.

### 4.2 Required GitHub Secrets (Configure Later)

| Secret | Description | Where to Get |
|--------|-------------|--------------|
| `SHOPIFY_ACCESS_TOKEN` | Theme API token | Shopify Admin → Settings → Apps → Develop apps |
| `SHOPIFY_STORE_URL` | Store URL | `your-store.myshopify.com` |
| `SHOPIFY_THEME_ID` | Target theme ID | Optional - uses unpublished if not set |

---

## Phase 5: Shopify Store Integration 🔜 PENDING

*Deferred until local development workflow is established*

### 5.1 Authenticate with Shopify
```powershell
shopify auth login --store YOUR-STORE.myshopify.com
```

### 5.2 Push Theme to Store

**Option A: As Unpublished Theme (Safe)**
```powershell
shopify theme push --unpublished
```
Creates a new theme in your store without affecting live site.

**Option B: To Existing Theme**
```powershell
shopify theme push --theme THEME_ID
```

**Option C: Shopify GitHub Integration**
1. Shopify Admin → Online Store → Themes
2. Add theme → Connect from GitHub
3. Select `fiercestxdog/automate-elevate`
4. Shopify auto-deploys on every push

### 5.3 Live Development Server
```powershell
shopify theme dev --store YOUR-STORE.myshopify.com
```
- Hot reload on file changes
- Preview at localhost with real Shopify data
- Changes sync to development theme

### 5.4 Configure GitHub Secrets

1. **Create Theme Access App:**
   - Shopify Admin → Settings → Apps and sales channels
   - Develop apps → Create an app
   - Configure Admin API scopes: `write_themes`
   - Install app and copy access token

2. **Add Secrets to GitHub:**
   - Repository → Settings → Secrets and variables → Actions
   - Add `SHOPIFY_ACCESS_TOKEN`, `SHOPIFY_STORE_URL`, `SHOPIFY_THEME_ID`

---

## Accomplishments Summary

| Task | Status |
|------|--------|
| Clone automate-elevate repo | ✅ Complete |
| Install Shopify CLI (v3.88.1) | ✅ Complete |
| Create Shopify directory structure | ✅ Complete |
| Extract CSS to asset files | ✅ Complete |
| Create layout/theme.liquid | ✅ Complete |
| Create header section | ✅ Complete |
| Create footer section | ✅ Complete |
| Create hero section | ✅ Complete |
| Create services section | ✅ Complete |
| Create process section | ✅ Complete |
| Create CTA section | ✅ Complete |
| Create AI Receptionist page | ✅ Complete |
| Create templates (index, page, 404) | ✅ Complete |
| Create settings schema | ✅ Complete |
| Create locales file | ✅ Complete |
| Create GitHub Actions workflow | ✅ Complete |
| Create .gitignore | ✅ Complete |
| Create README.md | ✅ Complete |
| Connect to Shopify store | 🔜 Pending |
| Configure GitHub secrets | 🔜 Pending |
| Test live deployment | 🔜 Pending |

**Files Created:** 17 total
- 7 Liquid sections
- 3 Liquid templates
- 4 JSON config files
- 2 CSS assets
- 1 GitHub workflow

---

## Next Steps

### Immediate (When Ready for Store)
1. [ ] Get Shopify store URL
2. [ ] Run `shopify auth login`
3. [ ] Push theme with `shopify theme push --unpublished`
4. [ ] Preview in Shopify Admin
5. [ ] Create "AI Receptionist" page with `ai-receptionist` URL handle

### GitHub Integration
1. [ ] Create Shopify theme access app
2. [ ] Add secrets to GitHub repository
3. [ ] Test automated deployment
4. [ ] Consider direct GitHub integration in Shopify

### Future Enhancements
- [ ] Add contact form integration
- [ ] Add more page templates (blog, portfolio)
- [ ] Add product templates (if selling services as products)
- [ ] Add newsletter signup section
- [ ] Optimize images with Shopify CDN
- [ ] Add structured data for SEO

---

## Quick Reference

### Common Commands
```powershell
# Local static preview
npx serve C:\python\projects\shopify_theme

# Check Shopify CLI version
shopify version

# Login to store
shopify auth login --store YOUR-STORE.myshopify.com

# Start dev server (requires store auth)
shopify theme dev

# Push to store
shopify theme push --unpublished

# List themes
shopify theme list

# Pull theme from store
shopify theme pull --theme THEME_ID
```

### File Locations
- **Theme Root**: `C:\python\projects\shopify_theme\`
- **Main Styles**: `assets/theme.css`
- **Layout**: `layout/theme.liquid`
- **Homepage**: `templates/index.json`
- **Settings**: `config/settings_schema.json`

### Design Tokens
```css
--cream: #FAF8F3      /* Background */
--charcoal: #1A1A1A   /* Primary text */
--sage: #8B9D83       /* Accent 1 */
--clay: #C88B65       /* Accent 2 / CTA */
--slate: #4A5568      /* Secondary text */
--gold: #D4AF37       /* Highlights */
```

---

*Last Updated: January 17, 2026*
