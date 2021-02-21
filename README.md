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
4. What is concept drift?
   - Concept drift in machine learning and data mining refers to the change in the relationships between input and output data in the underlying problem over time, which could degrade the performance for predictive models;
   - See [here](https://machinelearningmastery.com/gentle-introduction-concept-drift-machine-learning/)for more details.
