Generate a structured, critical paper note for a research paper in this repository.

The user provides paper content via $ARGUMENTS — this can be: raw paper text, a local file path (.pdf or .md), or a DOI/URL.

---

## Step 1 — Parse Input

- If $ARGUMENTS is a file path: read the file
- If $ARGUMENTS is a URL/DOI: fetch the page content
- If $ARGUMENTS is raw text: use it directly
- If $ARGUMENTS is empty: ask the user to paste the paper abstract + methodology + experiments

---

## Step 2 — Extract Metadata

Identify:
- Full title, year, journal/conference (+ impact factor if stated), authors, institution
- DOI / URL, source code link (or N/A)
- Technical keywords (5-8 terms)

---

## Step 3 — Classify Domain & Generate Slug

Map to this repo's taxonomy:
- `metal-processing` → `milling` | `lathe` | `grinding` | `forming`
- `heat-treatment` → `furnace` | `quenching` | `tempering`

If no existing sub-domain fits, propose a new one and note that README.md's Domain Index needs updating.

Generate a concise slug: `{MainTechnique}-{Application}` — e.g., `GPR-ToolWear`, `TransformerMPC-Furnace`, `BayesianPINN-Milling`

---

## Step 4 — Write the Paper Note

Use the template at `templates/paper-note-template.md`. Fill every section with substantive content — do not leave placeholder text.

Image path pattern for all figure references:
```
../../../images/{domain}/{Slug}_{YYYY}/{Slug}_{TypeN}_{ShortDesc}.png
```

---

## Step 5 — Critical Analysis (MANDATORY)

Every note must explicitly address each of these. Use bold **紅旗** labels for serious issues:

**Data & Sample Size**
- State the exact n. Flag if n < 500 for deep learning or n < 100 for any method.
- Identify excluded real-world variables (tool wear, downtime, material variation).

**Experimental Design**
- Cherry-picking: short eval windows, convenient conditions only, no stress tests.
- Straw-man baselines: comparison against outdated or tuned-down models instead of SOTA.

**Model & Methodology**
- Ablation honesty: quote ΔR² or ΔRMSE for each removed component. State what actually drives performance.
- Physics validity: are physics constraints physically meaningful, or just regularization in disguise?

**Deployment Feasibility**
- List 3 specific technical risks with the failure condition (not generic "may be unstable").
- Estimate computational overhead for real-time edge deployment.

---

## Step 6 — Save & Update

1. Save note to: `docs/{domain}/{sub-domain}/{YYYY}_{Slug}.md`
2. Create image folder: `images/{domain}/{Slug}_{YYYY}/` — remind the user to add paper figures there
3. Prepend a new row to the Latest Feed table in `README.md`
4. If a new sub-domain was created, add it to the Domain Index table in `README.md`

---

## Step 7 — Summary Report

Reply with:
- File saved to: `docs/...`
- Image folder to populate: `images/...`
- Top 2 red flags found: [brief description]
- Recommended alternative technique: [specific algorithm + one-line reason]
