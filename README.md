# Muhammad Rizki Pratama — Recruiter Portfolio

A single-page, plain/readable portfolio site (inspired by karpathy.ai), built to be
easy for a skimming recruiter *and* an AI summarizer to parse quickly.

## Files in this folder

| File | Purpose |
|---|---|
| `index.html` | The entire site. One self-contained file — all CSS is inline, the profile photo is embedded as base64. |
| `MuhammadRizkiPratama_CV.pdf` | The ATS-friendly CV, linked from the "Download CV" button. |
| `MuhammadRizkiPratama_CV.tex` | LaTeX source for the CV — open in Overleaf to edit, then re-export the PDF. |

## Deploying

`index.html` expects `MuhammadRizkiPratama_CV.pdf` to sit **next to it in the same
folder** — the Download CV button links to it with a plain relative path
(`href="MuhammadRizkiPratama_CV.pdf"`). Whatever static host you use (GitHub Pages,
Netlify, Vercel, etc.), just make sure both files are uploaded together at the same
level. No build step, no dependencies — it's plain HTML/CSS.

> Note: in a Claude-hosted preview link, only `index.html` itself is served, so the
> Download CV button won't resolve there. It works correctly once both files are
> deployed together on real hosting.

## Updating the CV

1. Edit `MuhammadRizkiPratama_CV.tex` in Overleaf (or locally with `pdflatex`).
2. Export/compile to PDF.
3. Replace `MuhammadRizkiPratama_CV.pdf` in this folder with the new PDF —
   **keep the exact filename** so the link in `index.html` doesn't break. If you do
   rename it, update the `href` on the `.cv-button` link in `index.html` to match.

## Updating the photo

The photo is embedded directly in `index.html` as a base64 data URI (inside the
`<img class="photo" src="data:image/jpeg;base64,...">` tag in the header), so there's
no separate image file to manage. To swap it:

1. Crop the new photo to a square (a headshot works best) and compress it — keep it
   small, under ~20 KB, so the page stays lightweight.
2. Base64-encode it and replace the string inside that `src="data:image/jpeg;base64,..."`
   attribute.

If you'd rather manage the photo as its own file instead of embedded base64, you can
switch the `src` to a relative path (e.g. `src="profile.jpg"`) and upload the image
file alongside `index.html` — just ask and this can be done for you.

## Section order (locked)

Identity → Quick links → Skills → Projects → Experience → Education →
Certifications & Achievements → Footer.

## Editing content

Everything is plain HTML inside `<section>` blocks with descriptive `id`s
(`#skills`, `#projects`, `#experience`, `#education`, `#certifications`). Each entry
(a project, a job, a degree) follows the same repeating structure — a title line, an
optional status/date, a stack/org line, and a description paragraph — so new entries
can be added by copying an existing block and editing the text.
