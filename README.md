# CS4783_HW03
1.)
The notes that my conclusions are derived from can be found inside the colab notebook.
For training the first model, I started by evaluating the effect of batch size. I found
that decreasing batch size increased both the time to train and the general accuracy of 
the model. I settled on a batch size of 32 for my final implementation because it struck
a nice balance of computation time and general performance, seeing only marginal gains in
average accuracy if I decreased it further, but much larger increases in computation time.
To evaluate the other hyper parameters I tuned, I did further testing at a batch size of 128
in order to reduce computation time. Throughout my testing, I had more luck with the Adam 
optimizer and eventually settled on a learning rate, alpha, of .0001 instead of the default
.001. The second model has significantly more parameters. I first tried a batch size of 128 but
still required an hour of testing to complete 1 epoch so I switched to 256 and the runtime crashed.
For the third model, I was able to make use of the accuracy benefits gained from smaller batch
size without suffering the penalties for computation time as it has the least parameters and
trains faster on average anyway. I settled on a batch size of 16 and used the SGD optimizer with
a learning rate of .03.

Model evaluations:
Model 1: average training time = 433.6s; average training accuracy = 98.418%; average testing accuracy = 96.668%
Model 2: N/A
Model 3: average training time = 277.33s; average training accuracy = 98.50%; average testing accuracy = 98.39%

2.1) I  tried a variety of different learning rates ranging from the default value to orders of magnitude smaller
and larger. I found no reason to prefer a value other than the default value as oscilating in either direction
lead to reductions in accuracy on the test set.
2.2) One way that batch size affects the training process is the computation time. Small batch size leads to 
slower training and large batch size leads to faster training. Unlike question 1, this model did not increase
in test accuracy with smaller batch sizes. Training set accuracy increased as batch size increased but that did
not correlate to an increase in test set accuracy. This leads me to conclude that increasing batch size can
run the risk of overfitting to the training set. 
2.3) The best performance I achieved was 56.70% accuracy on the test set. The hyperparameters were:
batch size = 64; epochs = 25; optimizer = adam; learning rate = .0001
2.4) The performance for the feed forward network was not possible to evaluate, the structure 
created an out of bound exception with the memory.
