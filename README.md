LncPipe Reporter
================

A submodule for automated visualization and interactive reports.

Motivation
----------

This project is a part of LncPipe that take charge of automatically generating reports in `HTML` format with interactive plots based on pipeline output. It contains several ploting functions as well as analysis scripts to perform comparison analysis and differential expression analysis when experimental design information was available. We speculated this tools can facilitate understanding the underlining machanism of known and novel lncRNAs in their expriment.

Configuration
-------------

LncPipe Reporter currently only support **Unix-like operation system** now.

The main Rmarkdown file of LncPipe Reporter is an **R Markdown v2 document**, which need install `pandoc` first:

For Arch Linux:

``` bash
$ sudo pacman -S pandoc
```

For those runtime environment with `RStudio` (both desktop or server version is OK) installed before or more instructions, see [the rmarkdown document](https://github.com/rstudio/rmarkdown/blob/master/PANDOC.md).

To install additional R packages:

``` r
install.packages(c("curl", "httr", "data.table", "cowplot", "knitr", "heatmaply", "ggsci", "flexdashboard"))
install.packages("devtools")
devtools::install_github(c('ramnathv/htmlwidgets', "ropensci/plotly", "vqv/ggbiplot"))
source("https://bioconductor.org/biocLite.R")
biocLite("edgeR")
```

How to use
----------

### Simply run with default parameters

``` bash
$ Rscript -e "rmarkdown::render('./reporter.Rmd')"
```

Parameters with their labels and default values were listed

### Specify the parameter values with user-interface

-   With R package `knitr`: Choose "Knit" -&gt; "Knit with Parameters" in RStudio, then adjust the parameters in the message dialog box.
-   In the browser: Call `rmarkdown::render` function in R Console with its `params` set to `ask`, just like:

``` bash
$ Rscript -e "rmarkdown::render('./reporter.Rmd', params = 'ask')"
```

### Specify the parameter values in command line (Recommended)

List the paramters with values as a R `list` object:

``` bash
$ Rscript -e "rmarkdown::render('./reporter.Rmd', params = list(output = 'output.html'))"
```

### Parameters

<table style="width:57%;">
<colgroup>
<col width="16%" />
<col width="20%" />
<col width="19%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Default value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>input</td>
<td>demo_results</td>
<td>Absolute path of input directory (results of up-stream analysis)</td>
</tr>
<tr class="even">
<td>output</td>
<td>reporter.html</td>
<td>Output file name (In HTML format)</td>
</tr>
<tr class="odd">
<td>theme</td>
<td>npg</td>
<td>Journal palette applied to all plots supplied by <a href="https://cran.r-project.org/web/packages/ggsci/vignettes/ggsci.html#discrete-color-palettes">ggsci</a></td>
</tr>
<tr class="even">
<td>cdf.percent</td>
<td>10%</td>
<td>Percentage of values to display when calculating coding potential</td>
</tr>
<tr class="odd">
<td>max.lncrna.len</td>
<td>10000</td>
<td>Maximum length of lncRNAs to display when calculating distribution</td>
</tr>
<tr class="even">
<td>min.expressed.sample</td>
<td>50%</td>
<td>Minimal percentage of expressed samples</td>
</tr>
</tbody>
</table>

Gallery
-------

Later.

License
-------

This package is free and open source software, licensed under [GPL v3.0](https://github.com/bioinformatist/multiIP/blob/master/LICENSE).
