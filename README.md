<!-- README.md is generated from README.Rmd. Please edit that file -->
[![Travis-CI Build Status](https://travis-ci.org/coatless/searcher.svg?branch=master)](https://travis-ci.org/coatless/searcher)[![CRAN RStudio mirror downloads](http://cranlogs.r-pkg.org/badges/searcher)](http://www.r-pkg.org/pkg/searcher)[![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/searcher)](https://cran.r-project.org/package=searcher)

searcher
========

The goal of searcher is to provide a search interface for *R* errors among the search portals. As an added bonus, the functions can also be used to directly search other terms such as `UIUC` or `mcmc rcpp`.

![](https://media.giphy.com/media/l378bwNTMR8DejX0I/giphy.gif)

Installation
------------

The `searcher` package is only available on GitHub for the moment. You can install the `searcher` package with:

``` r
devtools::install_github("coatless/searcher")
```

Usage
-----

``` r
library(searcher)
```

Search Errors
-------------

### Automatically

Searching the last error automatically is possible by registering either `search_error(site="")` or one of the `search_` functions as the error handler. Thus, when an error occurs, this function will automatically be called. This triggers a new browser window to open with the error term listed in verbatim.

``` r
# Using the generic search error handler
options(error = search_error("google"))

# Directly specify the search function
options(error = search_github)
options(error = search_google)
```

### Manually

Alternatively, these functions can also be used manually so that the default error dispatch is preserved. In the manual case, you will have to explicitly call the search function. After that, a browser window will open with the last error message as the search query on the desired search portal.

``` r
search_google()
search_bing()
search_duckduckgo()    # or search_ddg()
search_stackoverflow() # or search_so()
search_github()        # or search_gh()
search_bitbucket()     # or search_bb()
```

Search Terms
------------

As an added bonus, the search functions can be used to trigger a search directly from *R* on major search engines. In particular, you can supply your own query directly.

``` r
# Searching R project on major search engines
search_google("R project")
search_bing("R project")
search_duckduckgo("R project")

# Searching for linear regression questions for R and in general
search_stackoverflow("linear regression")
search_stackoverflow("linear regression", rlang = FALSE)

# Searching GitHub Issues for maps in R and other languages
search_github("maps")
search_github("maps", rlang = FALSE)

# Searching BitBucket for assertions in R and other languages
search_bitbucket("assertions")
search_bitbucket("assertions", rlang = FALSE)
```

Motivation
==========

The idea for `searcher` came from a conversation among [Dirk Eddelbuettel](http://dirk.eddelbuettel.com), [Barry Rowlingson](http://barry.rowlingson.com), and myself musing about the having compilers provide a link explaining what the error meant and how to solve it. This conversation was sprouted due to the mouse overtext of [XKCD Comic 1185: Ineffective Sorts](https://xkcd.com/1185/).

> StackSort connects to StackOverflow, searches for 'sort a list', and downloads and runs code snippets until the list is sorted.

This type of code search was implemented by:

<https://gkoberger.github.io/stacksort/>

The idea morphed from evaluating random code chunks to providing search support for errors that occurred at runtime.

License
=======

GPL (&gt;= 2)
