# AI — دروس الأتمتة (Abdullah Alawadhi)

Static site on GitHub Pages, served at https://eng-abdullah-alawadhi.github.io/AI/ from the `main` branch root.
No build step, no framework. Pure HTML/CSS/JS, one `index.html` per folder. Keep `.nojekyll` in the root.

The site is the bio link of Instagram @eng.abdullah.ai. Every Instagram reel/post points people here.
Owner: م. عبدالله العوضي, IT Manager at Cash Clinic Kuwait. Services are sold through Cash Clinic ("الشريك التقني لكاش كلينك").

## Structure

- `index.html` — hub
  - header: `>_` logo lockup, nav (الدروس · الخدمات)
  - hero: mono label `automation / lessons`, Cash Clinic badge, headline, owner card
  - `#lessons` — lesson cards 01–07, each with **الشرح** (guide) and **جرّب** (demo) buttons
  - `#tricks` — «حيل ٥ دقايق»: one card per quick trick (numbered 01…), **الشرح** + **جرّب** both point at the trick page (جرّب → `#make`)
  - `#services` — 8 service cards + «كيف نشتغل» strip
  - `#build` — dark CTA «ما عندك وقت تبنيه؟ نسويلك اياه» → Instagram DMs
  - footer with badge and `@eng.abdullah.ai`
- `demo/index.html` — interactive demos, one tab per lesson, hash routed (`#instagram #whatsapp #bookings #accounting #clinic #store`). Each demo is a simulation that logs to a `.log` box; no network calls.
- Lesson guides (same template everywhere):
  `instagram/` `whatsapp/` `bookings/` `accounting/` `clinic-website/` `store/`
  Layout: header → hero → personalize box (inputs that rewrite the message scripts) → 3 level tabs (المستوى ١ مجاني/جاهز · ٢ بدون برمجة · ٣ نظامك الخاص) → steps as `<details class="step">` with a checkbox (progress saved in localStorage) → copyable `.script` blocks → finish block → footer
- Quick-trick pages (one per reel in the «5-minute trick» format, like nadr.ai's free guides):
  `wa-link/` — WhatsApp link with a pre-filled message per source + counter QR.
  `post-prompt/` — a ready prompt (shop name, what you sell, tone, how to order) that turns a product photo into a Kuwaiti caption, story line, hashtags and comment replies in ChatGPT/Claude. Mono label `5-minute trick / 02`, localStorage prefix `pp-guide-`.
  Same template as the guides but a single route (no level tabs, no demo tab); the personalize box is `#make` and doubles as the live tool. Mono label `5-minute trick / 01`.
  Adding one: copy `wa-link/`, give its localStorage keys a new prefix, add a card to `#tricks`, update this file.
- `cv-skill/` — «سكيلات Claude» card 01 (`#skills` on the hub): the `ats-cv` Claude skill (score a CV against a job ad, tailor it truthfully, ATS-safe Word file, cover letter, LinkedIn). Source `cv-skill/skills/ats-cv/SKILL.md`, zip `cv-skill/zips/ats-cv.zip` (folder `ats-cv/SKILL.md` inside) — rebuild the zip after editing. localStorage prefix `cv-guide-`. Adding a skill page: copy `cv-skill/`, new prefix, new card in `#skills`.
- `excel-report/` — «سكيلات Claude» card 02: the `excel-report` skill (messy Excel/CSV → cleaned data with a cleaning log, key numbers that reconcile, charts, clean .xlsx with Summary sheet, Word/PDF/PowerPoint report, ready message to the manager). Source `excel-report/skills/excel-report/SKILL.md`, zip `excel-report/zips/excel-report.zip`. localStorage prefix `xl-guide-`.
- `cash-mark.png` — Cash Clinic knot mark, transparent. Use as-is. Never redraw, recolor, or stretch it.

## Brand — do not change without being asked

Colors (CSS vars in each page):
- ground `#F6F1E7` · panel `#FFFFFF` · ink `#10251B` · dark panel `#17382A` · dark line `#2E5A44`
- green `#007A3D` · deep green `#005C2E` · soft green `#E3F2EA` · line `#DCD5C6` · mute `#5C6B62`
- red `#CE1126` — one dot or one word only, never a fill or a paragraph
- The only purple on the page is inside `cash-mark.png`.

Type: IBM Plex Sans Arabic (all text), Space Grotesk (Latin lockup "Abdullah / Alawadhi"), IBM Plex Mono (labels like `automation / 01`, card numbers). Loaded from Google Fonts via `<link>`.

Marks:
- Logo: green rounded square with the `>_` prompt (inline SVG, already in every header).
- Badge: cream pill «الشريك التقني لكاش كلينك» with `cash-mark.png` at 24px.
- Dot-grid texture on the ground and on dark sections (radial-gradient background).

Tone of the design: calm, lots of air, big Arabic headlines, green as the single accent. No gradients, no shadows beyond the hover lift, no stock photos.

## Language rules

- Arabic is the default language and the page is RTL (`<html lang="ar" dir="rtl">`).
- Dialect is **Kuwaiti**. Never Egyptian, Levantine, Iraqi or MSA-heavy. Use:
  «منو» not «مين» · «شنو» not «وش/ايش» · «شلون» · «الحين» · «محد» · «حق» (ownership) · «بروحه» · «عقب» not «بعد» where natural · «وياه» · «إحنا» · «يبي» · «قاعد» · «وايد».
- Guides have an EN toggle: Arabic lives in the markup, English in `data-en="…"` attributes (HTML-escape quotes inside). When editing text, update both.
- Never write prices, income, or “$X per year”. The only calls to action are: learn how (الشرح), try it (جرّب), or «ولو ما تقدر تسويه… إحنا نسويلك اياه».
- Numbers in Arabic text use Arabic-Indic digits (١٢٣); code, URLs and money in Latin digits.

## Conventions

- Mobile first. Test at 430px width; the Instagram in-app browser is the main viewer.
- Inputs: `width:100%; min-width:0`. Grids: `minmax(0,1fr)` so nothing overflows the card.
- Header toggle (`.lang`) must never shrink: `flex:none; white-space:nowrap`.
- Lesson numbers are two-digit mono (`01`…). Adding a lesson means: new folder from the `bookings/` template, a hub card, a demo tab (`.tabs button[data-t]` + `section.panel#p-<name>` + JS block), and an update to this file.
- Keep each page self-contained (inline CSS/JS). No external JS libraries.
- Before committing: `node --check` any JS you extract, confirm HTML tags balance, open `index.html` and `demo/index.html` locally and click every tab/button once.

## Deploy

```
git add -A
git commit -m "<what changed>"
git push origin main
```

GitHub Pages updates within about a minute. Verify:
- https://eng-abdullah-alawadhi.github.io/AI/
- https://eng-abdullah-alawadhi.github.io/AI/demo/#store
- one guide, e.g. https://eng-abdullah-alawadhi.github.io/AI/store/

## Things not to do

- Don't add analytics, trackers, cookie banners or forms that send data anywhere.
- Don't rename folders — ManyChat automations and old posts link to them.
- Don't translate the Arabic to MSA "to be safe". Kuwaiti is the brand.
- Don't touch `cash-mark.png` or the Cash Clinic badge wording.
