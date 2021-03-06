
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Analyzing **scRNA-seq** data with **Bioconductor** for **LCG-EJ-UNAM** March 2020 <a href="https://bioconductor.org/"><img src="https://osca.bioconductor.org/cover.png" width="20%"/></a>

<!-- badges: start -->

<!-- badges: end -->

Here you can find the files for the March 2020 single cell
RNA-sequencing (scRNA-seq) course for
[LCG-EJ-UNAM](https://lcgej.unam.mx/) at
[LIIGH-UNAM](https://liigh.unam.mx/) based on the book [**Orchestrating
Single Cell Analysis with
Bioconductor**](https://osca.bioconductor.org/) by [Aaron
Lun](https://www.linkedin.com/in/aaron-lun-869b5894/), [Robert
Amezquita](https://robertamezquita.github.io/), [Stephanie
Hicks](https://www.stephaniehicks.com/) and [Raphael
Gottardo](http://rglab.org), plus [**WEHI’s scRNA-seq
course**](https://drive.google.com/drive/folders/1cn5d-Ey7-kkMiex8-74qxvxtCQT6o72h)
by [Peter Hickey](https://www.peterhickey.org/).

Instructor: [**Leonardo
Collado-Torres**](http://lcolladotor.github.io/).

## Course Prerequisites

Install R 3.6.x from [CRAN](https://cran.r-project.org/) then install
the following R packages:

``` r
## For installing Bioconductor packages
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

## Install required packages
BiocManager::install(
    c(
        'SingleCellExperiment',
        'usethis',
        'here',
        'scran',
        'scater',
        'scRNAseq',
        'org.Mm.eg.db',
        'AnnotationHub',
        'ExperimentHub',
        'BiocFileCache',
        'DropletUtils',
        'EnsDb.Hsapiens.v86',
        'TENxPBMCData',
        'BiocSingular',
        'batchelor',
        'uwot',
        'Rtsne',
        'pheatmap',
        'fossil',
        'ggplot2',
        'cowplot',
        'RColorBrewer',
        'plotly',
        'iSEE',
        'pryr',
        'LieberInstitute/spatialLIBD',
        'sessioninfo'
    )
)
```

You will also need to install
[RStudio](https://rstudio.com/products/rstudio/download/#download)
version 1.2.5 or newer.

## Course files

1.  [Introduction](01-introduction.html)
2.  [Data Infrastructure and
    Import](02-data-infrastructure-and-import.html)
3.  [Quality Control](03-quality-control.html)
4.  [Normalization](04-normalization.html)
5.  [Feature Selection](05-feature-selection.html)
6.  [Dimensionality Reduction](06-dimensionality-reduction.html)
7.  [Clustering](07-clustering.html)
8.  [Marker gene detection](08-marker-gene-detection.html)
9.  [Cell Annotation](09-cell-annotation.html)
10. [Data Integration](10-data-integration.html)
11. [Multi-Sample Comparisons](11-multi-sample-comparisons.html)
12. [Spatial Transcriptomics](12-spatial-transcriptomics.html)

## OSCA Workflow

<a href="https://osca.bioconductor.org/"><img src="https://raw.githubusercontent.com/Bioconductor/OrchestratingSingleCellAnalysis/master/images/Workflow.png" /></a>

## LIIGH Cluster DNA setup

If you add the following code to your `~/.Rprofile` at the DNA
LIIGH-UNAM cluster, you’ll be able to use the same R packages I
installed.

``` bash
## Log into the cluster

## Load the R 3.6.1 module
module load r/3.6.1

## Edit your ~/.Rprofile
vi ~/.Rprofile
```

``` r
## Add this to your ~/.Rprofile file
if(R.home() == '/cm/shared/apps/r/3.6.1-studio/lib64/R') {
    if (interactive())
        message("Using the following library: /mnt/Genoma/amedina/lcollado/R/3.6.1")
    .libPaths(
        c(
            '/mnt/Genoma/amedina/lcollado/R/3.6.1',
            '/cm/shared/apps/r/3.6.1-studio/lib64/R/library'
        )
    )
}
```

If you are using RStudio through Cyberduck or something like that, you
could use `usethis::edit_r_profile()`.

Now, to avoid having to download the data many times, you can use the
data I downloaded by editing/creating a `~/.Renviron` file with the
following contents:

``` bash
## Note that it has to have an empty line at the end

## For using Leo's Bioconductor cached' files
EXPERIMENT_HUB_CACHE="/mnt/Genoma/amedina/lcollado/BiocHubCache"
ANNOTATION_HUB_CACHE="/mnt/Genoma/amedina/lcollado/BiocHubCache"
XDG_CACHE_HOME="/mnt/Genoma/amedina/lcollado/BiocHubCache"
```

To test that it works, run:

``` bash
qrsh
module load r/3.6.1
Rscript -e "packageVersion('spatialLIBD')"
```

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This
work is licensed under a
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative
Commons Attribution-NonCommercial-ShareAlike 4.0 International
License</a>.

Download the materials for this course with
`usethis::use_course('lcolladotor/osca_LIIGH_UNAM_2020')` or view online
at
[**lcolladotor.github.io/osca\_LIIGH\_UNAM\_2020**](http://lcolladotor.github.io/osca_LIIGH_UNAM_2020).

<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=ffffff&w=300&t=n&d=tq5q8216epOrQBSllNIKhXOHUHi-i38brzUURkQEiXw'></script>

<!-- Global site tag (gtag.js) - Google Analytics -->

<script async src="https://www.googletagmanager.com/gtag/js?id=UA-161558379-1"></script>

<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-161558379-1');
</script>
