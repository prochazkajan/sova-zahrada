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
