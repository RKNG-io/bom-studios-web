# BOM Studios — AI-Accelerated Video Ads

A modern, bilingual landing page for BOM Studios. **AI-accelerated. Human-crafted.**

## Stack

- **Framework**: Nuxt 3 + TypeScript
- **Styling**: Custom CSS with CSS variables
- **Deployment**: Vercel
- **Languages**: English (EN) + Dutch (NL)

## Features

- Fully responsive landing page
- Language switching (EN/NL) with persistent state
- Brand-consistent design system (Deep Navy, Electric Blue, Aqua Beam)
- 10 optimised sections: Hero, Why Video, Quality, How It Works, Styles, Durations, Pricing, FAQ, Final CTA
- Semantic HTML structure
- Optimised for conversion
- Mobile-first responsive design

## Getting Started

### Local Development

```bash
# Install dependencies
npm install

# Run dev server (http://localhost:3000)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

### Environment

- Node.js 18+ (via Homebrew)
- No version manager required

## Deployment to Vercel

### Option 1: Via Vercel CLI

```bash
# Install Vercel CLI if you haven't already
npm install -g vercel

# Deploy
vercel
```

### Option 2: Via GitHub

1. Push this project to a GitHub repository
2. Go to [vercel.com](https://vercel.com)
3. Create a new project and import your GitHub repo
4. Vercel will auto-detect Nuxt 3 and deploy

### Option 3: Manual (Recommended)

1. Visit [vercel.com](https://vercel.com/dashboard)
2. Click "New Project"
3. Select "Import Git Repository"
4. Connect your GitHub account and select this repo
5. Click "Import"
6. Vercel will automatically:
   - Detect Nuxt 3
   - Install dependencies
   - Run `npm run build`
   - Deploy to production

**Vercel configuration** is already in place in `vercel.json`.

## Project Structure

```
/Users/liz/BOM Studios/
├── app.vue                  # Root component
├── nuxt.config.ts          # Nuxt configuration
├── tsconfig.json           # TypeScript config
├── vercel.json             # Vercel deployment config
├── package.json            # Dependencies
│
├── layouts/
│   └── default.vue         # Header, footer, navigation
│
├── pages/
│   └── index.vue           # Landing page (bilingual)
│
├── assets/
│   ├── css/
│   │   └── main.css        # Global styles + brand colours
│   └── images/
│       └── BOM.png         # Logo
│
└── public/                 # Static assets
```

## Customisation

### Brand Colours

Edit `/assets/css/main.css` CSS variables:

```css
:root {
  --color-deep-navy: #0F1638;
  --color-electric-blue: #394D9B;
  --color-aqua-beam: #7DD1E7;
  --color-mint-lime: #A8D897;
}
```

### Copy / Content

All copy is in `/pages/index.vue` in the `copyData` object. Supports EN and NL:

```typescript
const copyData = {
  en: { /* English copy */ },
  nl: { /* Dutch copy */ },
}
```

### Add New Sections

1. Add section to the template
2. Add corresponding data to `copyData`
3. Add styles in the `<style scoped>` block

## Language Switching

Users can switch languages using the fixed button in the top-right corner. The switch is instant and does not require a page reload.

## Performance

- **Build size**: ~1.9 MB total (464 kB gzip)
- **Client bundle**: ~164 KB uncompressed (~62 kB gzip)
- **Lighthouse optimised**: CLS, LCP, FID friendly
- **Mobile-first design**: 375px baseline

## Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+

## Git & Version Control

```bash
# Initialise git (if not already done)
git init
git add .
git commit -m "Initial commit: BOM Studios landing page"

# Push to GitHub
git remote add origin <your-repo-url>
git push -u origin main
```

## Troubleshooting

### Build fails

```bash
# Clear cache and rebuild
rm -rf .nuxt .output node_modules/.cache
npm run build
```

### Vercel deployment fails

1. Check `vercel.json` is present
2. Ensure `package.json` has `"type": "module"`
3. Check Node.js version compatibility
4. Review Vercel logs in dashboard

### Logo not loading locally

```bash
# Ensure logo is in the right place
ls assets/images/BOM.png

# If missing, copy it
cp web\ design/BOM.png assets/images/BOM.png
```

## Next Steps

- [ ] Set up analytics (Plausible, Fathom, etc.)
- [ ] Add email capture form
- [ ] Integrate payment gateway (Stripe, Paddle, etc.)
- [ ] Add success/error pages
- [ ] SEO optimisation (schema, OG tags)
- [ ] Accessibility audit (WCAG 2.1 AA)
- [ ] Performance testing (Core Web Vitals)

## Support

For issues, check:

1. `/Users/liz/.claude/CLAUDE.md` (local configuration)
2. Official Nuxt 3 docs: https://nuxt.com
3. Vercel docs: https://vercel.com/docs

---

**Built with ❤️ for BOM Studios**
