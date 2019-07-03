Automatic tools and information for creating and improving R packages
================

This document includes some automatic tools, resources about my workflow
when I create or improve an R package. screenshots of my preferred
RStudio configuration. It heavily relies on this
[post](https://drdoane.com/my-rstudio-configuration/) by William Diane.
Details about the different options can be found
[here](https://support.rstudio.com/hc/en-us/articles/200549016-Customizing-RStudio).

## Creating R package

  - [R-packages](http://r-pkgs.had.co.nz/) book by Hadley Wickham.
  - [MIT Step by Step Instructions for Creating Your Own R
    Package](http://web.mit.edu/insong/www/pdf/rpackage_instructions.pdf)
    by Kim, Martin, McMurry and Halterman.
  - R package
    [usethis](https://www.tidyverse.org/articles/2017/11/usethis-1.0.0/)
    automates several steps described in
    [R-packages](http://r-pkgs.had.co.nz/).
  - [rOpenSci Packaging
    Guide](https://devguide.ropensci.org/building.html) by rOpenSci
    community.

## Styling Code

  - R package [lintr](https://github.com/jimhester/lintr) for static
    code analysis.
  - R package [style](https://github.com/r-lib/styler) or the R function
    `usethis::use_tidy_style()` to prettify code.

Workflow:

``` r
usethis::use_tidy_style()
lintr::lint_package()
```

## Continuous Intergration

  - [Travis CI
    guide](https://docs.travis-ci.com/user/languages/r/#configuration-options)
    by Travis-CI.
  - [Advanced
    guide](https://towardsdatascience.com/travis-ci-for-r-advanced-guide-719cb2d9e0e5)
    by Sebastian Wolf.

Personal configuration for `.travis.yml` file:

    language: r
    r:
      - oldrel
      - release
      - devel
    
    r_github_packages:
      - jimhester/lintr
      
    after_success:
      - R CMD INSTALL $PKG_TARBALL
      - Rscript -e 'covr::codecov()'
      - Rscript -e 'lintr::lint_package()'

## Spelling

  - `devtools::spell_check`
  - `spelling::spell_check_package`

Workflow:

``` r
devtools::spell_check(".")
spelling::spell_check_package(".")
```

## Other Resources

  - <https://www.r-bloggers.com/automatic-tools-for-improving-r-packages/>
  - <https://www.r-bloggers.com/some-ideas-for-your-internal-r-package/>
  - <https://www.r-bloggers.com/dealing-with-s3-methods-in-r-with-a-simple-example/>
  - <https://www.r-bloggers.com/mit-step-by-step-instructions-for-creating-your-own-r-package/>
  - <https://www.r-bloggers.com/seeking-guidance-in-choosing-and-evaluating-r-packages/>
  - <https://www.r-bloggers.com/how-to-develop-good-r-packages-for-open-science/>
  - <https://github.com/ropensci/software-review>
