library(tidyverse)
library(profvis)

Skater_Stats <- read_csv(file.path(getwd(),
                                   "skater_stats.csv"))

Skater_Stats <- select(Skater_Stats,
                       -X1)

Skater_Stats <- rename(Skater_Stats,
                       "PM" = `+/-`,
                       "S_Pc" = `S%`,
                       "FO_Pc" = `FO%`)

Skater_Stats[, c(7:length(colnames(Skater_Stats)))] <- mutate_all(Skater_Stats[, c(7:length(colnames(Skater_Stats)))],
                                                                  as.double)

Skater_double <- Skater_Stats[, c(3, 6:length(colnames(Skater_Stats)))]

for (i in colnames(Skater_double)) {
  
  print(acf(Skater_double[ , i],
            na.action = na.pass,
            lag.max = nrow(Skater_double),
            main = colnames(Skater_double[, i]),
            ylab = "Autocorrelation",
            xlab = "Lag Position"))
  
  pause(3)
  
}

