---
title: "Inequality and the Pacification of Militant Protest in the United States, 1919-2012"
summary: "Code for reproducing the graph in our 2018 ISQ article on Liberal Pacification."
url: /blog/inequality-and-pacification-of-protest
date: "2018-06-01"
tags:
  - academic research
  - data
  - R
  - social science
categories:
  - theory & empirics
---

To generate the graph below, you need two data files. The first is yearly income decile data from [Piketty (2014)](https://amzn.to/2JhLrGT), which should be named "Inequality_USA.csv." The second is the Cross-National Time-Series data from [Banks and Wilson (2017)](https://www.cntsdata.com/), which should be called "2017 Edition CNTSDATA.csv." Finally, the code snippet below should be in a file called "Baron_et_al-ISQ.R" — that will be an R script that compiles the two datasets before producing the figure from our article. To reproduce the Figure, open the R script on your computer, ensure each dataset is in the same directory as the R script, set your R working directory to that directory, and run the script.

Please note that while Piketty's data is freely available and included in our replication archive on the ISQ website, the CNTS data is proprietary and cannoot be made public.

Issues or questions about replicating our analysis can be directed to me at j [dot] murphy [at] soton [dot] ac [dot] uk.

For legibility, event counts from Banks and Wilson (2017) were transformed into 10-year moving averages. These and the inequality measure from Piketty (2014) were then scaled to ease comparison. Scaling was done by subtracting the mean from each variable and dividing by one standard deviation; the lines reflect standard deviations from historical means (0).

```r

# Check for packages ————————————
x<-c("Zelig",
     "ggplot2",
     "reshape2",
     "zoo",
     "countrycode",
     "arm",
     "dplyr",
     "stringr",
     "foreign",
     "lubridate")

# Install any not already installed ——————————
new.p <- x[!(x %in% installed.packages()[,"Package"])]
if(length(new.p)) install.packages(new.p)

# Load packages ——————————————————
lapply(x, require, character.only = TRUE)
rm(x, new.p)

# Load data and wrangle dates
ineq<-read.csv("inequality_USA.csv")
ineq$year<-mdy(ineq$year)
ineq$year<-year(ineq$year)
ineq$year<-ifelse(ineq$year>=2019, ineq$year-100, ineq$year)

df<-read.csv("2017_Edition_CNTSDATA.csv")
df$country<-df$Country
df$year<-as.numeric(as.character(df$Year))

# Wrangle the CNTS data
df$Assassinations<-as.numeric(as.character(df$Assassinations))
df$Riots<-as.numeric(as.character(df$Riots))
df$Guerrilla.Warfare<-as.numeric(as.character(df$Guerrilla.Warfare))
usriots<-subset(df, country=="United States" & year>=1919 & year<=2016, select=c("Assassinations", "Riots", "Guerrilla.Warfare", "year"))

# Merge the two datasets
df2<-merge(usriots, ineq, by=c("year"), all.x=T)

# Create rolling averages
df2$Riots<-rollmean(df2$Riots, k=10,fill = NA)
df2$Assassinations<-rollmean(df2$Assassinations, k=10,fill = NA)
df2$Guerrilla.Warfare<-rollmean(df2$Guerrilla.Warfare, k=10,fill = NA)

# Standardize for comparability
df2$Inequality<-scale(df2$top_decile)
df2$Riots<-scale(df2$Riots)
df2$Guerrillas<-scale(df2$Guerrilla.Warfare)
df2$Assassinations<-scale(df2$Assassinations)

# Reshape for plotting
molt<-melt(df2[c("year", "Inequality", "Riots", "Guerrillas", "Assassinations")], id.vars="year")
molt<-filter(molt, year<2012)

ggplot(molt, aes(x=year, y=value, colour=variable, linetype=variable)) +
  geom_line(size=.8) +
  theme_bw(base_size = 12) +
  ggtitle("Inequality and the Pacification of Militant Contention in the U.S.") +
  xlab("Year") +
  ylab("Standardized values (z-scores)") +
  scale_x_continuous(breaks = seq(1919, 2011, by = 5)) +
  theme(axis.text.x = element_text(angle = 45, hjust = 1)) +
  theme(legend.title=element_blank())

```

![Inequality and protest data](https://i.imgur.com/OFF5kr8.png "Inequality and protest data")

## References

Banks, A.A., Wilson, K.A., 2017. "Cross-National Time-Series Data Archive." Databanks International, Jerusalem, Israel.

Piketty, T., 2014. "The top decile income share in the United States (including capital gains), 1910-2010," in [*Capital in the Twenty-First Century.*](https://amzn.to/2JhLrGT) Harvard University Press, Cambridge, Massachusetts.

