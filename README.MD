# Menopause Cardiometabolic Trend Prototype (Clinician-Facing)

Prototype web app to help clinicians **capture key cardiometabolic measures**, store them **locally in the browser**, visualize **trends over time**, and highlight **missed care opportunities** and **pattern-level risk signals** that may be overlooked when metrics are reviewed in isolation.

**Prototype created by Dr. Vinaya Gogineni and Dr. Nihit N. Mehta.**

> Focus (clinical need): In postmenopausal women with overweight/obesity, cardiometabolic risk assessment clusters around BP, lipids, glucose/diabetes, and adiposity (BMI + waist circumference), integrated with global ASCVD risk estimation, metabolic syndrome identification, female-specific risk enhancers, and—when appropriate—CAC/Lp(a)/hs-CRP plus kidney function (eGFR, urine ACR).

---

## What this prototype does

### Core features (in this repo)
- **Clinician data entry** for key cardiometabolic measures
- **Local storage only** (browser `localStorage`) to persist longitudinal values without a backend
- **Automatic graphs** for:
  - Waist circumference
  - Systolic/diastolic BP
  - A1C
  - Triglycerides, LDL-C, HDL-C
  - eGFR and urine ACR
- **Pattern flags** for:
  - Metabolic syndrome criteria count (0–5)
  - Missing/overdue domains (e.g., waist circumference not recorded)
  - Rising trajectories (e.g., waist ↑ + TG ↑ + A1C ↑)
- **Export/Import JSON** so a clinician can move data between machines (still prototype-level workflow)

### Planned (not implemented here)
- **EHR pull** via FHIR (SMART on FHIR) or health-system integration
- Multi-patient storage and authentication
- Audit logging, role-based access, HIPAA-grade hosting

---

## Important notes / clinical boundaries

- This is a **prototype** and **not** a medical device.
- Educational + workflow support tool only; does not provide diagnosis or treatment recommendations.
- Data are stored locally in the user’s browser. Do **not** enter identifiers if you are not allowed to store them on the device.
- For production use, a security review, threat model, and approved hosting environment would be required.

---

## Data model (high level)

Each entry is a dated visit with optional fields:
- Anthropometrics: weight, BMI, waist circumference
- BP: systolic, diastolic
- Lipids: total cholesterol, LDL-C, HDL-C, triglycerides, ApoB (optional)
- Glycemia: A1C, fasting glucose (optional)
- Kidney: eGFR, urine ACR
- Risk enhancers: early menopause/POI, adverse pregnancy outcomes, PCOS, inflammatory disease, depression
- Notes

---

## How the flags work (prototype heuristics)

- **Metabolic syndrome**: counts criteria based on available fields:
  - Waist circumference ≥88 cm
  - TG ≥150 mg/dL
  - HDL-C ≤50 mg/dL
  - BP ≥130/85 (or flagged if SBP/DBP entered above threshold)
  - A1C ≥5.7% (used as proxy for dysglycemia when fasting glucose not entered)
- **Trend flags** (simple): compares the most recent value vs. prior value(s) and flags directional changes.

Heuristics are intentionally simple for prototype clarity and should be validated before clinical deployment.

---

## Run locally

Just open `index.html` in a browser.

---

## GitHub Pages deploy

1. Push repo to GitHub
2. Settings → Pages → Deploy from branch
3. Choose `main` and `/ (root)`

---

## Recommended repo name

Examples:
- `menopause-cardiometabolic-trends-prototype`
- `ckm-menopause-clinician-prototype`

---

## License

Add a license if sharing externally (e.g., MIT). For internal clinical prototyping, follow your institution’s policies.
