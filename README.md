# Livets_Diversitet_fylogeni
Fylogenetisk øvelse 1. semester "Livets Diversitet" uge 37

```R
install.packages("phangorn")
library(phangorn)
```

```R
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))
```

```R
data <- read.phyDat("dummy1.phy", type="USER", levels=c(1,0))
```

```R
tree <- pratchet(data = data)
```

```R
tree <- root.phylo(tree, "outgroup", resolve.root = TRUE)
```

```
plot(tree, root.edge = TRUE)
```