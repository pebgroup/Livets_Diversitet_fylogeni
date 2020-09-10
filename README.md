# LØ5: Karakteranalyse og fylogenetisk rekonstruktion
Wolf Eiserhardt ([wolf.eiserhardt@bio.au.dk](wolf.eiserhardt@bio.au.dk)) og Lars Emil S. Feldager Hansen ([feldager@bio.au.dk](wolf.eiserhardt@bio.au.dk)), 10.-11.9.2020

Linjer der er markeret `med grå baggrund` skal kopieres i R-studio og køres derfra. Det bliver demonstreret under øvelsen hvordan man kører funktioner i R-studio. 

1. Lav en mappe (f.eks. på desktop). Folderens navn er uden betydning. 

2. Gem datasettet i mappe som *data.phy*. 

3. Lav et nyt R-skript i R-studio (det bliver demonstreret under øvelsen hvordan man gør) og gem det i din mappe. 

4. Installer R-pakken "phangorn". "Pakker" er samlinger af små funktioner til forskellige formål; Phangorn indeholder funktioner til fylogenetisk rekonstruktion (læs mere [her](https://cran.r-project.org/web/packages/phangorn/index.html)).

```R
install.packages("phangorn")
library(phangorn)
```

5. Sørg for, at R-studio leder efter dit dataset i den samme folder, hvor R-skriptet ligger: 

```R
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))
```

6. Indlæs datasættet: 

```R
data <- read.phyDat("data.phy", type="USER", levels=c(1,0))
```

7. Find det korteste træ vha. "parsimony ratchet" ([Nixon, 1999](https://cran.r-project.org/web/packages/phangorn/index.html)), en effektiv søgestrategi:

```R
tree <- pratchet(data = data)
```

8. Definer outgroup og dermed træets rod: 

```R
tree <- root.phylo(tree, "outgroup", resolve.root = TRUE)
```

9. Tegn træet: 

```
plot(tree, root.edge = TRUE)
```