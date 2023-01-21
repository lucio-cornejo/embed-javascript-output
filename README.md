- The purpose of this project is to include
the output of **JavaScript chunks** into the
generated HTML document.

- This implementation works for:
    - Quarto's `format: html` documents.
    - R Markdown's Xaringan presentations. 

- Such **embedded JavaScript output** looks mostly
similar to how it works by default with
R, Python and Julia.

- This project was partly inspired by the
[js4shiny](https://github.com/gadenbuie/js4shiny) 
`R` package, and, was created due to the need
of taking reproducible notes of the 
book [JavaScriot for Data Science](https://third-bit.com/js4ds/).

## Installation

Only the file `./src/embed-js-output.html` is required for
this JavaScriot output embedding to work in your project.

Simply include such file in the header of your HTML document.

For example:

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
