# constraint-demos — Audit & Improvements

**Auditor:** Oracle1 (subagent)  
**Date:** 2026-05-18  
**Repo:** https://github.com/SuperInstance/constraint-demos  
**Clone:** /tmp/constraint-demos-audit

---

## 1. README ✅

**Status:** EXISTS and well-written (added 2026-05-17)

Good structure:
- One-line description
- Demo table with descriptions
- Quick start (open in browser)
- "What These Demos Show" explanations
- Related repos with links
- Cocapn fleet attribution

**Verdict:** README is solid. No urgent improvements needed.

---

## 2. LICENSE ❌ MISSING

**Problem:** No LICENSE file at all.

**Impact:**  
- Ambiguous legal status — contributors don't know how their code can be used
- Blocks open-source adoption in some corporate environments
- No license = default copyright (all rights reserved), which defeats the purpose of a demo/educational repo

**Recommendation:** Add MIT or Apache 2.0. MIT is standard for demo/educational repos.

---

## 3. Tests ❌ NONE

**Problem:** No test files exist.

**Context:** These are self-contained HTML files — no Python/Node runtime needed. Tests would mean browser automation (Playwright, Puppeteer, Selenium).

**What's testable:**
- HTML files open without JS errors
- Canvas renders without crashing
- Button interactions work
- Responsive layout doesn't break

**Recommendation:** Add Playwright browser tests in `.github/workflows/ci.yml`:
```yaml
- uses: actions/checkout@v4
- run: npx playwright install chromium
- run: npx playwright test
```

---

## 4. CI ⚠️ BASIC / NO-OP

**Current state (ci.yml):**
```yaml
- echo "Repository contents verified"
- ls -la
```

**What it actually does:** Nothing. Just echoes and lists.

**What it should do:**
- Validate HTML syntax
- Run browser tests (Playwright)
- Check all linked resources accessible

**Recommendation:** Expand CI to do real work. At minimum:
- `tidy -m -q` HTML validation
- Playwright browser smoke tests

---

## 5. Git Log 📊

| Date | Author | Message |
|------|--------|---------|
| 2026-05-12 | Forgemaster | 3 interactive constraint theory demos |
| 2026-05-17 | Cocapn Fleet | Add README — constraint theory HTML demos |
| 2026-05-18 | SuperInstance Bot | Add GitHub Actions CI workflow |

Active development. 3 commits, clean history.

---

## 6. Code Quality ✅

**constraint-funnel.html (236 lines):**
- Clean CSS, good visual design
- Canvas-based rendering
- Phase state machine (Approach → Narrowing → SnapImminent → Crystallized)
- Sliders for parameters
- No obvious bugs

**drift-race.html (156 lines):**
- Float32 simulation with `Math.fround()` for realistic drift
- Two racers on circular track
- Dashboard with live stats
- Trail visualization for F32 deviation

**hex-snap-playground.html (222 lines):**
- Eisenstein lattice math
- Sector coloring (6 Weyl sectors)
- Click-to-snap interaction
- Live coordinate display

**Overall:** Code is well-structured, self-contained, and visually polished. No obvious bugs.

---

## 7. What's Missing for New Developers

### Critical
1. **LICENSE** — must have before anyone can legally use/extend this code
2. **Working CI** — current CI is a no-op, gives false confidence

### Important
3. **Browser tests** — would catch rendering issues across browsers
4. **CONTRIBUTING.md** — how to add new demos, coding standards
5. **Live demo hosting info** — README mentions hosting but no actual deployment

### Nice-to-Have
6. **CHANGELOG.md** — track what's new in each version
7. **Demo screenshot/thumbnail** — for visual preview at a glance
8. **Interactive playground links** — could host these on GitHub Pages or constraint-theory.dev

---

## 8. Obvious Bugs 🔍

**None found.** The HTML demos are clean and functional. Canvas interactions work, state machines are sound, math appears correct (Eisenstein integer arithmetic, hex lattice snapping).

---

## 9. Quick Wins (Priority Order)

| Priority | Action | Effort |
|----------|--------|--------|
| 🔴 P0 | Add `LICENSE` (MIT) | 1 min |
| 🔴 P0 | Expand CI to actually validate something | 30 min |
| 🟡 P1 | Add Playwright browser smoke tests | 2 hrs |
| 🟡 P1 | Add `CONTRIBUTING.md` | 30 min |
| 🟢 P2 | Add `CHANGELOG.md` | 15 min |
| 🟢 P2 | Deploy demos to GitHub Pages | 1 hr |

---

## 10. Overall Assessment

**Good:** Clean codebase, excellent README, active development. These are genuinely useful educational demos — the constraint funneling visualization is particularly good for explaining the concept.

**Bad:** Missing LICENSE is a blocker for any open-source use. CI is a no-op. No browser tests means no regression protection.

**Verdict:** Ready for contribution but not release-ready. Fix the LICENSE + CI issues first.

---

*Part of the Cocapn fleet audit series.*