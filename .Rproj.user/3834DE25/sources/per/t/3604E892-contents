classif.task.rpart <- makeClassifTask(id = "revenue",
                                      data = advertising_train_transformed,
                                      target = "norm_ln_y_binned")

rpart.lrn <- makeLearner("classif.rpart", predict.type = 'response',
                         fix.factors.prediction = TRUE)

wrapped.lrn.rpart <- makeBaggingWrapper(rpart.lrn,
                                        bw.iters = 10,
                                        bw.feats = 0.2)

wrappedRpart.mod <- train(wrapped.lrn.rpart, classif.task)

wrappedRpart.mod


rf.lrn <- makeLearner("classif.randomForest",
                      predict.type = "response",
                      fix.factors.prediction = T)

wrapped.lrn.rf <- makeBaggingWrapper(rf.lrn,
                                     bw.iters = 10,
                                     bw.feats = 0.2)

wrappedRf.mod <- train(wrapped.lrn.rf, classif_task)

wrappedRf.mod

predict(wrappedRf.mod, classif_task)

lapply(advertising_train_transformed, class)
