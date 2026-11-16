# Karoseri static export codebase

Static WordPress export, hosted on Cloudflare Pages from main. HTML content is preserved; there is no PHP/backend in this repository.

- `index.html` and nested `*/index.html`: exported pages, inline Astra tokens and generated Elementor CSS.
- `wp-content/uploads/`: existing media and generated UAG styles.
- `wp-content/themes/astra/assets/`: restored Astra layout, gallery CSS and frontend navigation script. `main.min.css` ends with a documented compatibility rule using horizontal clip and dark mobile menu icon on the light header.
- `wp-content/plugins/elementor/assets/`: restored frontend/widget styles, icon fonts, Swiper and runtime JS including browser-discovered widget chunks.
- `wp-content/plugins/header-footer-elementor/`: restored shared header/footer styles.
- `wp-content/plugins/codev-starter-templates-companion/assets/planner-sections.css`: restored exported planner styling only.
- `wp-content/plugins/sureforms/assets/`: restored form display dependencies; availability of a static asset does not establish a form backend.
- `wp-includes/`: restored frontend JavaScript and block CSS dependencies. No server code.
- `404.html`: real static missing-page response, prevents Cloudflare Pages returning homepage HTML for absent assets.

No application function signatures changed. Original assets were retrieved from the matching original WordPress host, checked for non-HTML content and bundled locally. Existing page/contact/metadata bytes remain unchanged. Root cause: required directories omitted from both original and revised uploads. Git cannot identify the upstream export setting. Restoration includes CSS font/image dependencies and runtime chunks; a homepage-only HTTP check is insufficient.

Operational evidence and the complete UI contract live in the canonical OneDrive MD hub under `OPERATIONS/PROJECTS/KAROSERI_CSS_REPAIR_2026-11-16/`. Reusable procedure: `SKILLS/static-site-css-repair/SKILL.md`. Validate asset MIME/body, render desktop/mobile, test menu, and verify deployment before claiming done. Do not add CI suppression to website commits.
