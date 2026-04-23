# BSD XR Readiness Assessment

Single-page readiness assessment tool for evaluating whether an organization is a strong candidate for XR deployment.

This project is intentionally lightweight:

- Single-file application in `index.html`
- No build step
- No framework or package manager required
- Rooted in the BSD XR branding system found in `branding/`
- Includes browser-based PDF export via print styles

## What The Tool Does

The app walks a user through a short operational questionnaire and calculates an XR readiness score.

Questions cover:

- Repeatable training processes
- High turnover roles
- Safety-sensitive work
- Multi-site teams
- Existing SOPs or documentation
- Hardware budget
- LMS integration needs

Based on the total score, the tool classifies the organization as:

- `EMERGING`
- `READY NOW`
- `HIGH IMPACT CANDIDATE`

The interface is designed to support:

- Self-guided exploration
- Live qualification on calls
- Internal discovery workshops
- Lead capture follow-up
- Quick PDF export for handoff or review

## Project Structure

```text
xr readiness/
├── index.html        # Self-contained SPA (HTML + CSS + JS)
├── README.md         # Project documentation
└── branding/
    ├── branding.md   # Source-of-truth brand guidance
    ├── README.md     # Brand system overview
    ├── index.html    # Brand reference SPA
    ├── theme.json    # Design tokens
    ├── logo-dark.png
    ├── logo-light.png
    ├── dark.png
    ├── light.png
    └── vercel.json
```

## Design Direction

This tool follows the BSD XR visual system:

- Space Mono everywhere
- Uppercase interface text
- Wide tracking
- Hard 90-degree corners
- 1px borders only
- No shadows
- No decorative UI gradients
- Sparse, utilitarian layout

The only brand gradient remains the XR logo mark.

## Current UX Model

The app is structured more like a tool than a sales page:

- Compact utility header
- Focused assessment workspace
- Question stack on the left
- Live score and interpretation on the right
- Contained follow-up CTA instead of a hero-led landing page flow

This keeps the primary task clear: answer questions, evaluate readiness, export or follow up.

## Scoring Model

Each question has three answers:

- `NO` = `0`
- `SOMEWHAT` = `1`
- `YES` = `2`

Seven questions produce a maximum score of `14`.

Bands:

- `0-5` → `EMERGING`
- `6-10` → `READY NOW`
- `11-14` → `HIGH IMPACT CANDIDATE`

The UI also surfaces:

- Current readiness band
- A qualitative readiness signal
- Top insight callouts based on strongest answers

## PDF Export

The app supports PDF export with no external dependency.

How it works:

- `EXPORT PDF` and `SAVE REPORT AS PDF` trigger `window.print()`
- Print-specific CSS hides non-essential UI
- The layout is reformatted into a cleaner report view for printing
- Users can choose `Save as PDF` in the browser print dialog

Why this approach was used:

- Keeps the app dependency-free
- Works in a single static HTML file
- Easy to host anywhere
- Good enough for lightweight reporting and internal sharing

If needed later, this can be upgraded to a fully custom generated PDF workflow.

## Lead Capture Behavior

The follow-up form captures:

- Name
- Work email
- Company

In the current demo implementation:

- Submission is stored in `localStorage`
- No backend is connected
- No real email or CRM submission occurs

This makes the tool easy to demo without server infrastructure.

## Theme Behavior

The tool supports dark and light themes.

- Default theme is dark
- Light mode is restored from `localStorage`
- The header logo swaps to the correct brand asset per theme

Theme preference key:

- `bsdxr-theme`

Demo assessment payload key:

- `bsdxr-xr-readiness-demo`

## Running Locally

Because this is a static app, you can open it directly in a browser or serve it with any simple static server.

Examples:

```bash
open index.html
```

Or:

```bash
python3 -m http.server
```

Then open:

```text
http://localhost:8000
```

## Editing Guidance

When making changes:

- Preserve BSD XR branding rules from `branding/branding.md`
- Keep the app dependency-free unless there is a strong reason not to
- Prefer simple, readable vanilla HTML/CSS/JS
- Maintain print/PDF compatibility when changing layout
- Avoid turning the tool back into a marketing-heavy landing page

## Deployment

This project can be deployed as a static site to any host that serves plain files.

Examples:

- GitHub Pages
- Vercel
- Netlify
- S3/static hosting

No build pipeline is required.

## Future Improvements

Potential next steps:

- Connect form submission to a CRM or email workflow
- Add custom generated PDF reports
- Pre-fill reports with respondent details
- Add weighted scoring instead of equal scoring
- Save/load assessment sessions
- Add analytics for drop-off and completion rate
- Export structured JSON or CSV

## Source References

Brand references used for this tool live in:

- `branding/branding.md`
- `branding/README.md`
- `branding/theme.json`
- `branding/index.html`
- `branding/dark.png`
- `branding/light.png`

## License / Ownership

Brand assets and the tool implementation are intended for BSD XR use.
