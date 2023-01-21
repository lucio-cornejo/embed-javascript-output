- The purpose of this project is to include
the output of **JavaScript chunks** into the
generated HTML document.

- This implementation works for:
    - Quarto's `format: html` documents.
    - R Markdown's Xaringan presentations and `output: html_document`.

- Such **embedded JavaScript output** looks mostly
similar to how it works by default with
R, Python and Julia.

- This project was partly inspired by the
[js4shiny](https://github.com/gadenbuie/js4shiny) 
`R` package, and, was created due to the need
of taking reproducible notes of the 
book [JavaScript for Data Science](https://third-bit.com/js4ds/).

## Installation

Only the file `./src/embed-js-output.html` is required for
this JavaScript output embedding to work in your project.

**Simply include** such file in the header of your HTML document, like in the **examples** folder.

- **R Markdown**
    ```yaml
    output:
      # ...
      includes:
        in_header: "../src/embed-js-outputs.html"
    ```
- **Quarto**
    ```yaml
    format:
      # ...
      include-in-header: "../src/embed-js-outputs.html"
    ```

## Important caveats

- The JavaScript code in each chunk **must use semicolon**
to denote the end of a statement. If not, such code
will not be evaluated properly.

- It's higly recommended that the JavaScript chunks whose
output you don't want to be embedded in the page have
`eval: false`, that is, that their code doesn't get executed.
This due to a possible duplicate execution of JavaScript
code chunks if `eval` is set to true, which can cause
issues, for example, when *event listeners* are used,
as they'd get registered twice.

- Due to having **rewritten** the `console.log` function,
sometimes it does not work the same way as if it had been
executed directly in the browser console. For example,
`console.log(1, 2)` and *console.logging* a JavaScript
object (to skim its entries perhaps) behave different
to the standard.

- In Quarto, if `echo: fenced` is used, the JavaScript code
output will not be inserted properly into the webpage.
This happens due to the HTML container of the chunk's
code (specifically some `<pre>` tag) no longer having `js`
as one of it classes, but `markdown` instead.

- If you open any of the html files in the `examples` folder,
they all work as intended when seen on a browser, but, 
none of them include their JavaScript chunks outputs when
seen on a *Viewer* window from RStudio or VS Code.
