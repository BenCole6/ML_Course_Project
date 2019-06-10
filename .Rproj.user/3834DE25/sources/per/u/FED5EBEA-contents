# Better way to normalise the data
# Dummy data where all columns are numeric
df <- mtcars

# Suppose we have some infinite values
df[1, 'mpg'] <- Inf

# Write the normalise function
normalise <- function(x){
  x[is.infinite(x)] <- NA
  (x - min(x, na.rm  = TRUE))/(max(x, na.rm = TRUE) - min(x, na.rm = TRUE))
}

# create normalised data
norm_df <- apply(df, 2, normalise)

# Rename the data
colnames(norm_df) <- paste0('norm_', colnames(norm_df))

# Concatante it to the original data
df <- cbind(df, norm_df)

