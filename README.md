# 🚢 Titanic EDA — Analisi Esplorativa in R

Analisi esplorativa del naufragio del RMS Titanic (1912) su 1.305 passeggeri,
realizzata in R Markdown e compilata in PDF.

## Contenuto
- Pulizia e feature engineering
- Analisi di sopravvivenza per sesso, classe, età, tariffa, famiglia e cabina
- Matrice di correlazione e analisi dei valori mancanti

## Stack
`R 4.4` · `tidyverse` · `ggplot2` · `patchwork`

## Riproduzione
```r
install.packages(c("tidyverse", "patchwork", "scales"))
rmarkdown::render("titanic_eda.Rmd")
```

## Riferimenti
- [Encyclopedia Titanica](https://www.encyclopedia-titanica.org/class-gender-titanic-disaster-1912~part-2.html)
- [Kaggle Titanic Dataset](https://www.kaggle.com/competitions/titanic)



**Colombini Francesco**
