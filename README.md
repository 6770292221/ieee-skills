# IEEE Paper Skills for Claude Code

Skills for checking and reviewing IEEE academic papers — works with LaTeX, Word, and PDF.

## Install

```bash
npx skills add 6770292221/ieee-skills
```

## Skills

### `/ieee-format-checker`

Checks IEEE paper formatting compliance against the official IEEEtran_HOWTO and IEEE conference Word template. Supports both **LaTeX** and **Word/PDF** modes.

**What it checks:**

| Category | Items |
|----------|-------|
| Structure & Metadata | Title, Authors & Affiliations, Abstract, Keywords |
| Content Formatting | Sections (Roman numerals), Citations `[1]`, Equations, Figures, Tables |
| Writing & Language | Abbreviations, SI Units, Common writing mistakes |
| End Matter | Acknowledgment spelling, References list format |
| Cleanup | Template placeholder text removal before submit |

**Output per issue:**

```
## ❌ Figures

| # | Level | Location | Issue | Should be |
|---|-------|----------|-------|-----------|
| 1 | 🔴 Critical | L.42 | \label before \caption | Move \label after \caption |
| 2 | 🟡 Warning  | Fig. 3 | Axis label uses symbol only | Write full quantity name |

Found 2 issues (🔴 1 Critical, 🟡 1 Warning)
---
Fix these now? [Y] Yes  [N] Skip  [S] Stop
```

---

### `/paper-reviewer`

Evaluates a research paper like a real conference reviewer. Returns a score breakdown across 8 dimensions, a tier-based verdict, and an actionable fix plan.

**Scoring dimensions:**

| Dimension | Max |
|-----------|-----|
| Novelty | 20 |
| Technical Soundness | 20 |
| Experimental Rigor | 20 |
| Practical Relevance | 10 |
| Writing Quality | 10 |
| Organization & Presentation | 10 |
| Format Compliance | 5 |
| Acceptance Readiness | 5 |
| **Total** | **100** |

**Tier thresholds:**

| Tier | Strong Accept | Weak Accept | Borderline | Reject |
|------|--------------|-------------|------------|--------|
| T1 (NeurIPS, CVPR, ICSE) | 85–100 | 78–84 | 70–77 | <70 |
| T2 (ICSME, SANER, ISSTA) | 80–100 | 72–79 | 65–71 | <65 |
| T3 (Regional IEEE/ACM) | 75–100 | 68–74 | 60–67 | <60 |
| T4 (Workshop) | 70–100 | 60–69 | 50–59 | <50 |

**Output includes:** Executive summary · Score breakdown · Tier verdict + acceptance probability · Tier gap analysis · Top 5 major issues · Reviewer-style comments · Actionable fix plan

---

## Workflow

These two skills work together:

```
/paper-reviewer   →  overall quality + tier verdict
/ieee-format-checker  →  fix every formatting issue before submit
```

The reviewer will suggest running `/ieee-format-checker` when format issues are detected.

## Supported file types

| Format | ieee-format-checker | paper-reviewer |
|--------|-------------------|----------------|
| `.tex` | Full LaTeX checks | Content review |
| PDF | Content/structure checks | Full review |
| Word / pasted text | Word template checks | Full review |
