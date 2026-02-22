# Finicium Capital — Website

Professional website for **Finicium Capital LTD**, a quantitative algorithmic trading firm.

Built with [Astro](https://astro.build) and deployed to [GitHub Pages](https://pages.github.com/) at [finiciumcapital.com](https://finiciumcapital.com).

## Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Quality Checks

```bash
# Astro type checking
npx astro check

# Spell checking
npx cspell "src/**/*.{astro,md,ts,js}"
```

## Deployment

The site deploys automatically to GitHub Pages on every push to `main` via the [deploy workflow](.github/workflows/deploy.yml).

### Custom Domain

The site is served at `finiciumcapital.com` via the [CNAME](public/CNAME) file. Ensure your DNS is configured with:

| Type  | Name | Value                              |
|-------|------|------------------------------------|
| CNAME | @    | finicium-capital.github.io         |

## Pages

| Page             | Route             |
|------------------|--------------------|
| Home             | `/`                |
| About            | `/about/`          |
| Technology       | `/technology/`     |
| Contact          | `/contact/`        |
| Privacy Policy   | `/privacy/`        |
| Terms of Service | `/terms/`          |
| Cookie Policy    | `/cookies/`        |
| Acceptable Use   | `/acceptable-use/` |

## CI/CD

- **CI** (`.github/workflows/ci.yml`): Runs on every push and PR — Astro check, build, and spell check.
- **Deploy** (`.github/workflows/deploy.yml`): Deploys to GitHub Pages on push to `main`.
