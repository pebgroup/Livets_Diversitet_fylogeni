# LØ5: Karakteranalyse og fylogenetisk rekonstruktion

Linjer der er markeret `med grå baggrund` skal kopieres i R-studio og køres derfra. Det bliver demonstreret under øvelsen hvordan man kører funktioner i R-studio. 

1. Installer R-pakken "phangorn". "Pakker" er samlinger af små funktioner til forskellige formål; Phangorn indeholder funktioner til fylogenetisk rekonstruktion (læs mere [her](https://cran.r-project.org/web/packages/phangorn/index.html)).

```R
install.packages("phangorn")
library(phangorn)
```

2. Sørg for, at R-studio leder efter dit dataset i den samme folder, hvor R-skriptet ligger: 

```R
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))
```

3. Indlæs datasættet: 

```R
data <- read.phyDat("dummy1.phy", type="USER", levels=c(1,0))
```

4. Find det korteste træ vha. "parsimony ratchet" ([Nixon, 1999](https://cran.r-project.org/web/packages/phangorn/index.html)), en effektiv søgestrategi:

```R
tree <- pratchet(data = data)
```

5. Definer outgroup og dermed træets rod: 

```R
tree <- root.phylo(tree, "outgroup", resolve.root = TRUE)
```

6. Tegn træet: 

```
plot(tree, root.edge = TRUE)
```