# Zahrada moudré sovy
Educational browser game in Czech for a 9-year-old girl (3rd grade):
multiplication tables 1-10 + vyjmenovaná slova (all rows b,l,m,p,s,v,z).

## Hard rules
- Single self-contained index.html (inline CSS/JS), no build tools, no dependencies.
- Touch-first for Samsung tablet, tap targets ≥48px, portrait + landscape.
- ANTI-RUSHING design: no timers, no speed rewards, 3s wait-lock on every
  question, sessions capped at 12 flowers. Calm visuals, no urgency cues.
- All UI text in Czech with correct diacritics.
- Progress persists in localStorage.

## Workflow
- Test locally: python3 -m http.server 8080
- Deploy: git push to main → GitHub Pages
- Bump the version string in the corner on every deploy.
- Claude preview tools: the preview server can't read ~/Documents (macOS
  privacy), so .claude/launch.json serves /private/tmp/sova-zahrada-preview.
  Copy index.html there before verifying: cp index.html /private/tmp/sova-zahrada-preview/
- Word data for "Stavba slova": data/rozbor-slova.xlsx is the source of truth;
  the ROZBOR_BANK block in index.html is generated from it (see markers).
  Picture for spojovačka: "svg" column (key into PIC_SVG registry in index.html)
  wins over "emoji" column; a word needs one of them to appear there.
  Spojovačka = ONE word-family per round (its 2-3 depictable related members),
  rotating with family-level recent-exclusion (DB.spojRecent = family names).
  Rozbor + skládačka use the whole bank with error-weighting + recent-exclusion
  (DB.rozstats/rozRecent). To add a spojovačka family: give ≥2 members of one
  rodina an svg key + draw the SVGs in PIC_SVG.
