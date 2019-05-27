# box_grobs <- list()

# for (i in seq(-5, 5, 1)) {
#   
#   
#   boxcox_pos_price <- mutate(advertising_train,
#                              "bc_price1" = boxcox_pos(x = price1,
#                                                       lambda = i),
#                              "bc_price2" = boxcox_pos(x = price2,
#                                                       lambda = i),
#                              "bc_price3" = boxcox_pos(x = price3,
#                                                       lambda = i))
#   box_grobs[i] <- grob(
#     ggplot(boxcox_pos_price) +
#       geom_density(aes(x = bc_price1, fill = deviceType),
#                    alpha = 1/3) +
#       ggtitle(paste("Lambda = ", i)) +
#       theme_minimal() +
#       theme(panel.grid.major.x = element_blank(),
#             panel.grid.minor.x = element_blank())
#   )
#   
# }
# 
# do.call(grid.arrange, box_grobs)

for (i in -5:5) {
  
  boxcox_pos_price <- mutate(advertising_train,
                             "bc_price1" = boxcox_pos(x = price1,
                                                      lambda = i),
                             "bc_price2" = boxcox_pos(x = price2,
                                                      lambda = i),
                             "bc_price3" = boxcox_pos(x = price3,
                                                      lambda = i))
  print(
    ggplot(boxcox_pos_price) +
      geom_density(aes(x = bc_price1, fill = deviceType),
                   alpha = 1/3) +
      ggtitle(paste("Lambda = ", i)) +
      theme_minimal() +
      theme(panel.grid.major.x = element_blank(),
            panel.grid.minor.x = element_blank())
  )
  
}


for (i in seq(-2, 2, 0.1)[-21]) {
  
  boxcox_pos_price <- mutate(advertising_train,
                             "bc_price1" = boxcox_pos(x = price1,
                                                      lambda = i),
                             "bc_price2" = boxcox_pos(x = price2,
                                                      lambda = i),
                             "bc_price3" = boxcox_pos(x = price3,
                                                      lambda = i))
  print(
    ggplot(boxcox_pos_price) +
      geom_density(aes(x = bc_price1, fill = deviceType),
                   alpha = 1/3) +
      ggtitle(paste("Lambda = ", i)) +
      theme_minimal() +
      theme(panel.grid.major.x = element_blank(),
            panel.grid.minor.x = element_blank())
  )
  
}
