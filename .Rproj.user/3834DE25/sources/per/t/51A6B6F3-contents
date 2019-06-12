classif.task.kknn <- makeClassifTask(id = "revenue",
                                data = advertising_train_transformed,
                                target = "norm_ln_y_binned")

kknn.lrn    <- makeLearner("classif.kknn", predict.type = 'response', 
                           fix.factors.prediction = TRUE)

wrapped.lrn <- makeBaggingWrapper(kknn.lrn,
                                  bw.iters = 10,
                                  bw.feats = 0.2)

wrappedkknn.mod <- train(wrapped.lrn, classif.task.kknn)

wrappedkknn.mod

beep(8)
stop()


prediction <- predict(wrappedkknn.mod,
                      newdata = advertising_train_transformed)


##### Tuning Hyperparameters

getParamSet(wrapped.lrn)

rdesc <- makeResampleDesc("CV",
                          iters = 2)

par.set <- makeParamSet(makeIntegerParam("bw.iters", lower = 2, upper = 5),
                        makeNumericParam("bw.feats", lower = 0.35, upper = 0.9))

ctrl  <- makeTuneControlRandom(maxit = 2)

tuned.lrn <- makeTuneWrapper(wrapped.lrn, rdesc, mmce, par.set, ctrl)
tunedBaggedTreeMod <- train(tuned.lrn, task = classif.task)

pred <- predict(tunedBaggedTreeMod, newdata = advertising_train_transformed)

performance(pred)

lrnCurve <- generateLearningCurveData(task =  classif.task, 
                                      learners = list(rf.lrn, rpart.lrn, kknn.lrn))

ggplot(lrnCurve$data, aes(x = percentage, y = mmce, color = learner)) + 
  geom_point() + geom_line() + 
  labs(x = 'Percentage of data used %', 
       y = 'MMCE')
