# Statistical Analysis Using Python — bookdown project

This folder contains the source for the **Statistical Analysis Using Python** textbook,
built with **bookdown** (the same way as the Official Statistics book).

## Files in this project

| File | What it is |
| ---- | ---------- |
| `index.Rmd` | Title page, preface, course information, syllabus, dataset description |
| `01-module1.Rmd` | Chapter 1 — Introduction to Python Programming |
| `02-module2.Rmd` | Chapter 2 — Data Manipulation with Pandas *(in preparation)* |
| `03-module3.Rmd` | Chapter 3 — Data Visualization *(in preparation)* |
| `98-glossary.Rmd` | Glossary *(in preparation)* |
| `99-references.Rmd` | References *(in preparation)* |
| `_bookdown.yml` | Lists the files, in order, and the output file name |
| `_output.yml` | Sets the GitBook web style |
| `style.css` | Small custom styling (objective / worked-example / practice boxes) |
| `College_Data.csv` | The dataset used in Chapters 2 and 3 |

## How to render on Posit Cloud (same workflow as your Official Statistics book)

1. Upload this whole folder to your Posit Cloud project (or create a new project from your GitHub repo).
2. Make sure the **bookdown** package is installed. If not, run once in the R console:
   ```r
   install.packages("bookdown")
   ```
3. In the R console, run:
   ```r
   bookdown::render_book("index.Rmd")
   ```
4. The rendered website appears in a new folder called `_book/`. Open `_book/index.html` to preview.

## How to also produce a PDF version

The PDF is built through LaTeX. You need to install a LaTeX engine **once** in your Posit Cloud project:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

The second line takes a few minutes. After that, build both the website and the PDF with:

```r
# Web version (GitBook)
bookdown::render_book("index.Rmd", output_format = "bookdown::gitbook")

# PDF version
bookdown::render_book("index.Rmd", output_format = "bookdown::pdf_book")
```

The PDF appears inside the `_book/` folder as
`statistical-analysis-using-python.pdf`.

Tip: to build **both** formats at once, run:

```r
bookdown::render_book("index.Rmd", output_format = "all")
```

When you push the project to GitHub, include the PDF (it is inside `_book/`,
or inside `docs/` if you set `output_dir: "docs"`). The GitBook web version
already shows a **PDF download button** in the top toolbar, and that button
links to this PDF file, so your students can download it directly from the
published website.

## How to publish on GitHub Pages

1. Commit and push all files **including the `_book/` folder** to your GitHub repository.
2. In the repository settings, under **Pages**, set the source to the `docs/` folder or the
   `_book/` folder (whichever you used for the Official Statistics book).
   - Tip: if your Official Statistics book publishes from a `docs/` folder, add this line to
     `_bookdown.yml` so the site is built straight into `docs/`:
     ```yaml
     output_dir: "docs"
     ```
3. GitHub Pages will then serve the book at your usual `https://<username>.github.io/<repo>/` address.

## Note on the code examples

All Python code in this book is shown as **static listings with their expected output**.
The code is **not executed** during rendering, so you do **not** need Python configured on
Posit Cloud. This keeps the build simple and identical in spirit to your text-only
Official Statistics book. Students run the code themselves in Google Colab.
