# LØ5: Karakteranalyse og fylogenetisk rekonstruktion
Wolf Eiserhardt ([wolf.eiserhardt@bio.au.dk](wolf.eiserhardt@bio.au.dk)) og Paola de Lima Ferreira ([paolaferreira@bio.au.dk](paolaferreira@bio.au.dk)), 11.-12. 9. 2023

Linjer der er markeret `med grå baggrund` skal kopieres og køres i R-studio. Det bliver demonstreret under øvelsen hvordan man kører funktioner i R-studio. 

1. Lav en mappe (f.eks. på desktop). Folderens navn er uden betydning. 

2. Gem datasettet i mappen som *data.phy*. 

3. Lav et nyt R-skript i R-studio (det bliver demonstreret under øvelsen hvordan man gør) og gem det i din mappe. Kald den *analyse.R*.

4. Installer R-pakken "phangorn". "Pakker" er samlinger af små funktioner til forskellige formål; Phangorn indeholder funktioner til fylogenetisk rekonstruktion (læs mere [her](https://cran.r-project.org/web/packages/phangorn/index.html)).

```R
install.packages("phangorn")
library(phangorn)
```

5. Sørg for, at R-studio leder efter dit dataset i den samme mappe, hvor R-skriptet ligger: vælg "Session", "Set Working Directory", "To Source File Location" I menuen. 

6. Tjek, om den rigtige mappe er valgt: 

```R
getwd()
```

7. Indlæs datasættet: 

```R
data <- read.phyDat("data.phy", type="USER", levels=c(1,0))
```

8. Find det korteste træ vha. "parsimony ratchet" ([Nixon, 1999](https://www.sciencedirect.com/science/article/pii/S0748300799901214)), en effektiv søgestrategi:

```R
tree <- pratchet(data = data)
```

9. Definer outgroup og dermed træets rod: 

```R
tree <- root.phylo(tree, "outgroup", resolve.root = TRUE)
```

10. Tegn træet: 

```
plot(tree, root.edge = TRUE)
```