---
title: "Generating summary statistics and box/violin plots in R"
subtitle: Student resources
summary: "Start a basic data analysis with real data in R."
date: "2012-05-22"
url: blog/2012/05/22/generating-summary-statistics-in-r/
tags:
- data
- visualization
- R
- teaching
- statistics
categories:
- resources
keywords:
- summary statistics in R
- box plots in R
- violin plots in R
- descriptive inference
- r tutorial
- r walkthrough
---

Here is a script (with highly detailed comments) to get you up and running in R, analyzing a real social science dataset. Data come from the 1970-2010 General Social Survey dataset. When you download the original master file from the web, the whole dataset has more than 5,000 variables and more than 55,000 respondents, which is too large for most computers to handle efficiently. So I've limited the original file to 613 of some of the most commonly used and generally valuable variables–still large and comprehensive enough to be useful for a wide-range of research interests, but a little more manageable.

All you have to do is [download this dataset, the 1970-2010 General Social Survey.](https://www.dropbox.com/s/29s8ivlo0xagpv3/GSS.csv?dl=0) Then in RStudio set the working directory to wherever the GSS.csv file is located on your computer.

You can then work through this script to get started on your own research project.

If you are absolutely new to using R and RStudio, I have also made a corresponding [video walkthrough on Youtube, "Intro to R Studio and Basic Descriptive Statistics."](https://www.youtube.com/watch?v=uwlwNRbaKMI)

If you are looking for a text, my favorite book for learning basic statistics in R is [Andy Field's *Discovering Statistics Using R*](http://amzn.to/2EPIpr7).

{% highlight R %}

##################################################
### Read data from your working directory
### You need to set that from the file menu.
##################################################

# read GSS.csv as a table (with values separated by a comma and with the first row reserved as names).

gss<-read.table("GSS.csv", sep=",", header=TRUE)

##################################################
### summary statistics
##################################################

# Install package "pastecs," which has a nice little summary.statistics() function
install.packages("pastecs")           		
                           
# Load it into working memory
library(pastecs) 

# Generate summary stats for importance attributed to work, relaxation, and politics	
stat.desc(gss$impwork, basic=FALSE)   		
stat.desc(gss$imprelax, basic=FALSE)
stat.desc(gss$imppol, basic=FALSE)

##################################################
#### Generate some boxplots to compare the distributions
##################################################

par(mfrow=c(1,3))       # Set up a graph with 1 row and 3 columns.
                        # We do this because we plan to compare
                        # 3 distributions.
                        # R will just place the next three graphs
                        # in these slots.

boxplot(gss$impwork, col="magenta")     # Make boxplot for the variable
                                        # "impwork" in the dataframe "gss"
                                        # and color it magenta.

boxplot(gss$imprelax, col="green")      # Make boxplot for the variable "imprelax" in the
                                        # dataframe "gss" and color it green.

boxplot(gss$imppol, col="cyan")         # Make boxplot for the variable "imppol" in the
                                        # dataframe "gss" and make it magenta.

##################################################
### Box plots are good but not great. violin plots are similar
### but better because they represent the distribution directly.
##################################################

install.packages("wvioplot")             # install the package called "wvioplot" for making
                                         # violin plots
library(wvioplot)                        # load the library of the package "wvioplot"

par(mfrow=c(1,3))                                        #  Set up a graph with 1 row and 3
                                                         #  columns. We do this because we
                                                         #  plan to compare 3 distributions.

wvioplot(gss$impwork, col="magenta", names="Work")       #  Make violin plot for the variable
                                                         #  "impwork" in the dataframe "gss",
                                                         #  color it magenta, label it "Work".

wvioplot(gss$imprelax, col="green", names="Relaxation")  #  Make violin plot for the variable
                                                         # "imprelax" in the dataframe "gss",
                                                         # color it green, label it "Relaxation."

wvioplot(gss$imppol, col="cyan", names="Politics")       # Make violin plot for the variable
                                                         # imppol in the dataframe gss,
                                                         # color it cyan, label it Politics

{% endhighlight %}