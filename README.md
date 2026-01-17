# Automate & Elevate - Shopify Theme

A custom Shopify theme for the Automate & Elevate web design and AI automation business.

## Theme Structure

```
shopify_theme/
├── assets/                    # CSS, JS, images
│   ├── theme.css              # Main theme styles
│   └── ai-receptionist.css    # AI Receptionist page styles
├── config/
│   ├── settings_schema.json   # Theme customization settings
│   └── settings_data.json     # Current theme settings
├── layout/
│   └── theme.liquid           # Main layout wrapper
├── locales/
│   └── en.default.json        # English translations
├── sections/                  # Modular page sections
│   ├── header.liquid          # Navigation header
│   ├── footer.liquid          # Site footer
│   ├── hero.liquid            # Hero section
│   ├── services.liquid        # Services grid
│   ├── process.liquid         # Process timeline
│   ├── cta.liquid             # Call to action
│   └── ai-receptionist.liquid # AI Receptionist page section
├── snippets/                  # Reusable code fragments
└── templates/
    ├── index.json             # Homepage template
    ├── page.liquid            # Generic page template
    ├── page.ai-receptionist.json  # AI Receptionist page
    └── 404.liquid             # Error page
```

## Local Development

### Prerequisites
- Node.js 20+
- Shopify CLI: `npm install -g @shopify/cli @shopify/theme`

### Development Workflow

**Option 1: Without Shopify Store (Static Preview)**
```powershell
# Simple local preview using any static server
npx serve .
# Or use VS Code Live Server extension
```

**Option 2: With Shopify Store (Full Preview)**
```powershell
# Authenticate with Shopify
shopify auth login --store YOUR-STORE.myshopify.com

# Start development server with hot reload
shopify theme dev
```

### Git Workflow
```powershell
git add .
git commit -m "Description of changes"
git push origin main
```

## Deployment

### Automatic (GitHub Actions)
Push to `main` branch triggers automatic deployment.

**Required Secrets** (GitHub → Settings → Secrets):
- `SHOPIFY_ACCESS_TOKEN` - Theme access token from Shopify app
- `SHOPIFY_STORE_URL` - your-store.myshopify.com
- `SHOPIFY_THEME_ID` - (Optional) Target theme ID

### Manual Deployment
```powershell
# Push as new unpublished theme
shopify theme push --unpublished

# Push to specific theme
shopify theme push --theme THEME_ID
```

## Theme Customization

The theme supports customization through Shopify's theme editor:

### Colors
- Cream (Background)
- Charcoal (Text)
- Sage (Accent 1)
- Clay (Accent 2)
- Slate (Secondary Text)
- Gold (Highlight)

### Sections
All sections are fully customizable:
- **Hero**: Heading, description, buttons, feature cards
- **Services**: Service cards with features list
- **Process**: Timeline steps with icons
- **CTA**: Call to action with button
- **AI Receptionist**: Benefits grid and how-it-works steps

## Pages

### Homepage (index)
- Hero section with animated feature cards
- Services grid (4 services)
- Process timeline (4 steps)
- Call to action

### AI Receptionist (/pages/ai-receptionist)
- Dedicated landing page for AI receptionist service
- Benefits grid
- How it works section
- Custom styling

## Creating New Pages

1. Create a page in Shopify Admin → Online Store → Pages
2. In the page settings, select the appropriate template
3. Use "AI Receptionist" template for `/pages/ai-receptionist` URL handle

## Source Repository

- **GitHub**: https://github.com/fiercestxdog/automate-elevate
- **Live Site**: https://fiercestxdog.github.io/automate-elevate/ (static version)
