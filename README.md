# ml-ds
Summary of the knowledge that is useful/popular in machine learning/data science, but explored less by me due to time constraint

## LSTM
1. https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21 is a very clear explanation for beginners.
2. http://colah.github.io/posts/2015-08-Understanding-LSTMs/ is another good resource, expecially for how the vector flows.
3. https://pytorch.org/tutorials/beginner/nlp/sequence_models_tutorial.html is the official explanation in Pytorch.
4. When can't we use BiLSTM?
   In any bi-directional model, we assume that we have access to the next elements of the sequence in a given “time”. This is the case for text data (i.e sentiment    analysis, translation etc.), but not the case for time-series data.

## Loss Functions
1. [torch.nn.NLLLoss()](https://pytorch.org/docs/stable/generated/torch.nn.NLLLoss.html): The negative log likelihood loss, which is useful to train a classification problem with C classes. Basically it is negative log of softmax. Here is good explanation: https://ljvmiranda921.github.io/notebook/2017/08/13/softmax-and-the-negative-log-likelihood/
2. 

## CNN
1. What are some advantages in using CNN rather than Dense Neural Network in an image classification problem?
   - Translation invariance: The convolution operator is translation invariant mathematically.
   - Hierarchical nature: learns patterns in by describing complex patterns using simpler ones.
   - Gives us a better understanding of the model: we can look at the filters’ weights and visualize what the network “learned”.
2. 

## Technique
1. What are the advantages of batch normalization?
   - It can accelarate the training process. Larger learning rate could be used.
   - It also has some regularizing effect by including some noise. So dropout may not be necessary.
2. What are hyperparameters for **transfer learning**?
   - How many layers to keep, how many layers to add, how many to freeze.
   - If the new dataset is very small, it’s better to train only the final layers of the network to avoid overfitting, keeping all other layers fixed.
   - If the new dataset is very much large, retrain the whole network with initial weights from the pretrained model.
3. What is the difference between **model.train()** and **model eval()** mode in pytorch?
   - **model.train()** tells that the model is training, so dropout and batchnorm will turn on.
   - Usually We use the with **torch.no_grad()** block to ensure no gradients are calculated within the block. In addition, dropout and batchnorm will turn off.
4. What are different types of random sampling?
   - Simple random sampling
      - Pros: Easy to implement
      - Cons: No representation guarantee: might exclude rare classes(black swan)
   - Stratified sampling
      - Pros: Minor groups are represented
      - Cons: Can not be used if data can not be devided into subgroups or one data sample could belong to multiple subgroups
   - Weighted sampling
   - Importance sampling
      - Useful when sampling from the true distribution is expensive or infeasible
   - Reservior sampling
      - Need to select k samples from a stream of N data samples with equal probability
5. Why we use epoches instead of randomly sampling with replacement from the entire dataset?
   - In a nutshell, using epoches could make the training process converge faster. See [here](https://stats.stackexchange.com/questions/235844/should-training-samples-randomly-drawn-for-mini-batch-training-neural-nets-be-dr) for more details.
6. How to deal with class imbalance?
   - Add more minority samples(SMOTE) or drop majority samples (resampling)
   - Adjust losses (weight balancing)
   - Choose algorithms robust to class imbalance (Bagging)

## General Concepts
1. What is concept drift?
   - Concept drift in machine learning and data mining refers to the change in the relationships between input and output data in the underlying problem over time, which could degrade the performance for predictive models;
   - See [here](https://machinelearningmastery.com/gentle-introduction-concept-drift-machine-learning/) for more details.
2. Online learning vs offline learning
   - There are analogies: in the domain of data processing, online learning vs offline learning is like streaming process vs batch process; in the domain of gradient descent, it is like stochastic gradient descent vs mini-batch gradient descent.
   - When to consider online learning:
      - Your data is too large to fit in the memory;
      - You expect the distribution of your data to morph or drift over time
      - Your data is a function of time (e.g. stock prices)

3. Zero-shot learning
   - Zero-short learning is a variant of transfer learning
   - In usual machine learning, the learning model classifies instances whose labels(classes) are already in the training data; while zero-shot learning tries to do the same thing but without the predicted classes in the training data
   - See [here](https://towardsdatascience.com/applications-of-zero-shot-learning-f65bb232963f) for more details 
4. Bagging, boosting and stacking
   - **bagging**, that often considers homogeneous weak learners, learns them independently from each other in parallel and combines them following some kind of deterministic averaging process. (Random Forest)
   - **boosting**, that often considers homogeneous weak learners, learns them sequentially in a very adaptative way (a base model depends on the previous ones) and combines them following a deterministic strategy. (Gradient Boosting Tree)
   - **stacking**, that often considers heterogeneous weak learners, learns them in parallel and combines them by training a meta-model to output a prediction based on the different weak models predictions
   - See [here](https://towardsdatascience.com/ensemble-methods-bagging-boosting-and-stacking-c9214a10a205) for more details.
