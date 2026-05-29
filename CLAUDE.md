# CLAUDE.md

## How I expect you to write code

**No shortcuts. "Simple" never means "sloppy."** A small diff that hardcodes,
duplicates, or skips a test isn't simpler — it's deferred cost.

1. **Fix causes, not symptoms.** Find the root cause before fixing. If you're
   applying a workaround, say so explicitly and explain why. Never swallow an
   exception or silence an error to make a problem disappear.

2. **Think about consequences.** Before changing shared or widely-used code,
   trace its callers and the invariants they rely on. A fix that's locally
   correct but breaks something elsewhere — now or later — is not a fix.

3. **SOLID, sensibly.** One responsibility per class/widget/function. Separate
   pure logic from I/O so it can be tested. Inject dependencies that cross a
   boundary so they're mockable. Don't add abstractions for things that don't
   cross a boundary.

4. **DRY about knowledge, not appearance.** Don't duplicate a rule or decision.
   Code that merely looks similar but changes for different reasons stays
   separate. When unsure, prefer duplication over a premature/wrong abstraction.

5. **No hardcoded values.** No magic numbers or strings inline — give them
   names. Environment/tenant/feature-specific values go in typed config in
   application code, never scattered literals, never the database.

6. **Readable & maintainable.** Clear names, short flat functions, early
   returns over deep nesting. Comments explain *why*, not *what*. Match the
   existing style of the file you're editing.

7. **Testable, and prove it.** Ship a test for behavior you add or change. If
   something is hard to test, that's a design smell — restructure until it
   isn't. "Works but can't be tested" means it isn't done.

A change is done only when: the cause (not a symptom) is fixed, no new hardcoded
values, a test covers it, and the analyzer/formatter are clean.

## Project facts

> Keep these current as the repo evolves; only write what you've confirmed.

- **Setup command:** `npm install` (CI uses `npm ci`)
- **Analyze/lint command:** `npx astro check` (type-check) and `npx cspell "src/**/*.{astro,md,ts,js}"` (spell check)
- **Test command (all):** _TBD_ (no test runner configured; CI gates via `npx astro check` + `npm run build`)
- **Test command (single file/test):** _TBD_ (no test runner configured)
- **Format command:** _TBD_ (no formatter configured)
- **Run an app:** `npm run dev` (dev server); `npm run build` then `npm run preview` (preview production build)
- **Repo layout:** `src/` (Astro site: `pages/` routes, `components/`, `layouts/`, `styles/`); `public/` (static assets, `CNAME`, `robots.txt`); `astro.config.mjs`, `tsconfig.json`, `cspell.json`; `.github/workflows/` (CI + GitHub Pages deploy)
- **State management / data layer conventions:** None — static Astro site (`output: 'static'`), no client state or data layer
- **Generated files NOT to hand-edit:** `dist/` (build output), `.astro/` (generated types), `package-lock.json`
- **Other gotchas worth recording:** Deploys to GitHub Pages on push to `main` (`.github/workflows/deploy.yml`); custom domain `finiciumcapital.com` via `public/CNAME`; spelling is en-GB and enforced by `cspell` (add new terms to `cspell.json` `words`); Astro is configured with the `strict` tsconfig preset
