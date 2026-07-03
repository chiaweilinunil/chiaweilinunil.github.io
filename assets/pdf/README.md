# cv.pdf

Place your compiled CV here as `cv.pdf` so the `/cv/` page can embed and link to it.

To compile the CV from `Prompt and materials/CV_Academia_20260127/`:

```bash
cd "Prompt and materials/CV_Academia_20260127"
xelatex Main.tex
biber Main
xelatex Main.tex
xelatex Main.tex
cp Main.pdf "../../chiaweilinunil.github.io/assets/pdf/cv.pdf"
```

(`xelatex` is required because the CV uses non-Latin scripts via fontspec/polyglossia.)

Until `cv.pdf` exists in this folder, the `/cv/` page will show its fallback link only.
