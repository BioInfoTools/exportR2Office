export version 0.2.0 Beta
=========================
export is an R package to easily export active R graphs and statistical output 
in publication quality to Microsoft Office, HTML and Latex.

Useful links: 

* Report a bug: 
[**Bug report**]
(http://github.com/tomwenseleers/export/issues "please provide a reproducible example"). 
If you report a bug, try to send a reproducible example and don't forget to send the result of 
    
        sessionInfo()
        
Features
--------
* Save active R graphs or ggplot2, lattice or base R plots in publication 
  quality to Microsoft Word, Powerpoint, HTML, Latex or various other bitmap or 
  vector formats using a single command with sensible defaults.
* Fully editable Powerpoint vector format output, enabling manual tidy-up of plot layout.
* Save the output of statistical analysis in R as tables in Word, PowerPoint, Latex or HTML documents.
* Customize formatting of R outputs.
* This is the first beta release, and some functionality may still change in
  the final release.

Installation
------------

### Dependencies

Java (it has been tested with java version >= 1.6).

export needs some R packages ; run the following script to install them if needed.

    install.packages("rJava")
    install.packages("ReporteRs")
    install.packages("ReporteRsjars")
    install.packages("ggplot2")
    install.packages("rtable")
    install.packages("xtable")
    install.packages("taRifx")
    install.packages("stargazer")
    install.packages("tikzDevice")


### Github

**Get the latest release:**  

    install.packages("devtools")
    library(devtools)
    devtools::install_github('tomwenseleers/export',local=F)

  
Getting Started
---------------

    library(export)
       
    ?graph2ppt
    ?graph2doc
    ?graph2tex
    ?graph2svg
    ?graph2png
    ?table2ppt
    ?table2tex
    ?table2doc
    ?table2html

    ## export of ggplot2 plot
    library(ggplot2)
    qplot(Sepal.Length, Petal.Length, data = iris, color = Species, 
          size = Petal.Width, alpha = I(0.7))
    # export to Powerpoint      
    graph2ppt()      
    graph2ppt(file="ggplot2_plot.pptx", aspectr=1.7)
    # add 2nd slide with same graph 9 inches wide and A4 aspect ratio
    graph2ppt(file="ggplot2_plot.pptx", width=9, aspectr=sqrt(2), append=TRUE) 
    # add 3d slide with same graph with fixed width & height
    graph2ppt(file="ggplot2_plot.pptx", width=6, height=5, append=TRUE) 
    # export to Word
    graph2doc()
    # export to Latex
    graph2tex()
    # export to bitmap or vector formats
    graph2svg()
    graph2png()
    graph2tif()
    graph2jpg()

    ## export of aov Anova output
    # export to Powerpoint
    fit=aov(yield ~ block + N * P + K, npk)
    x=summary(fit)
    table2ppt(x=x)
    table2ppt(x=x,file="table_aov.docx")
    table2ppt(x=x,file="table_aov.docx",digits=4,append=TRUE)
    table2ppt(x=x,file="table_aov.docx",digits=4,digitspvals=1,
              font="Times New Roman",pointsize=16,append=TRUE)
    # export to Latex
    x=summary(fit)
    table2tex(x=x)
    # export to Word
    table2doc(x=x)
    # export to HTML
    table2html(x=x)

  
License
-------
The export package is licensed under the GPLv2.
