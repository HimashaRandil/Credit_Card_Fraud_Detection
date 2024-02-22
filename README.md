# Credit_Card_Fraud_Detection

## Introduction of the Dataset

The dataset contains credit card transactions made by European cardholders in September
2013. It spans two days and comprises 284,807 transactions, of which 492 are identified as
fraudulent. This imbalance results in frauds accounting for only 0.172% of all transactions.
The dataset predominantly consists of numerical input variables resulting from a Principal
Component Analysis (PCA) transformation. While features V1 through V28 represent
principal components obtained from PCA, the 'Time' and 'Amount' features remain
untransformed. Specifically, 'Time' denotes the elapsed seconds between each transaction and
the first transaction recorded, while 'Amount' signifies the transaction amount.
The 'Class' feature serves as the response variable, taking a value of 1 for fraud and 0
otherwise.


## Custom Neural Network Architecture

The custom neural network class named "Perceptron" using the PyTorch library. The
network architecture consists of four fully connected layers (fc1 to fc4) with input features,
and each hidden layer is followed by a Rectified Linear Unit (ReLU) activation function and
a dropout layer with a specified dropout probability. The last layer uses a sigmoid activation
function, indicating that the network is designed for binary classification tasks, as it outputs
values between 0 and 1. The number of neurons in the hidden layers decreases from 5 to 4
and then to 3, and finally, the output layer has a single neuron. The dropout layer is employed
to regularize the network by randomly setting a fraction of input units to zero during training,
preventing overfitting. The architecture aims to map input features to a binary output,
potentially for binary classification problems.

## Parameters

The parameters utilized in building a credit card fraud detection model using MLP include
preprocessing techniques such as RobustScaler and StandardScaler for the robust scaling of
'Amount' and 'Time' features. Numpy arrays are employed to activate the feature called
numpy bridge, and the unsqueeze operation is applied to transform the target variable into a
2D tensor, aligning it with the requirements of the neural network architecture. Imbalanced
data is addressed through SMOTE oversampling. In dataset creation, the minibatch gradient
descent method is used to feed data samples into the model. The neural network architecture,
defined in the Perceptron class, comprises four fully connected layers with ReLU activations
and a final sigmoid activation for binary classification. Training is organized over a specified
number of epochs (config.epochs), with a designated batch size (config.batch_size) and
learning rate (config.lr). The Binary Cross-Entropy Loss (BCELoss) acts as the loss function,
and the Stochastic Gradient Descent (SGD) optimizer is employed for updating neural
network weights during training. These parameters ensure the smooth execution of the entire
process.


## The graph results generated by weights & biases

![W B Chart 2_22_2024, 10_12_33 PM](https://github.com/HimashaRandil/Credit_Card_Fraud_Detection/assets/101445238/f382b334-33fd-4ec3-a03d-9e5ad734f12f)

Figure 1:Models’ loss trend


The graph presents a loss function trajectory using binary cross-entropy over training
iterations, with the x-axis indicating the training steps and the y-axis displaying the loss
values. The x-axis extends from 0 to beyond 40 steps, while the y-axis loss values range
approximately between 0.2 and 0.5. The curve is jagged, showing significant variance at each
step, which suggests fluctuations in model performance during training. At the start, the loss
seems to start at about 0.35, peak around 0.5 near the 5th step, and exhibit its lowest visible
point close to 0.2 near the 30th step. This indicates that the model's predictions are becoming
more or less aligned with the actual targets at different stages of training. Despite these
fluctuations, there isn't a clear downward or upward trend observable, implying that the
model may not be consistently improving or deteriorating over the range of steps.

![W B Chart 2_22_2024, 10_12_19 PM](https://github.com/HimashaRandil/Credit_Card_Fraud_Detection/assets/101445238/679a1695-cde3-486f-8a83-27a51dc4c370)

Figure 3:Model Accuracy graph


This graph's line fluctuates significantly, indicating variability in the model's performance
from step to step. The accuracy peaks at several points, nearing 0.95, which indicate moments
where the model was highly accurate in its predictions. Conversely, there are troughs where
the accuracy dips close to 0.75, showing instances of poorer performance.Notably, there is no
clear upward or downward trend over the span of the graph, which suggests that the model's
accuracy is not consistently improving or degrading over these iterations.

## Challenges and Limitations


Several challenges arise and are effectively addressed when developing a neural network for
detecting fraudulent or non-fraudulent transactions. One issue is dataset imbalance, where the
number of fraudulent transactions is significantly lower than non-fraudulent ones. This can
lead to biased models that perform poorly on detecting fraud. To mitigate this, techniques like
Synthetic Minority Over-sampling Technique (SMOTE) are employed to balance the dataset
by generating synthetic examples of the minority class. Additionally, the architecture of the
neural network becomes overly complex, leading to overfitting and poor generalization. This
complexity is managed with dropout layers, where a fraction of neurons is randomly dropped
out during training, effectively regularizing the model, and preventing overfitting.
Furthermore, to ensure the model's performance, validation on a separate dataset is crucial.
However, neglecting validation and training solely on the training data can lead to inaccurate
assessments of the model's performance and potential overfitting. Therefore, incorporating
validation procedures is essential for developing a robust and reliable fraud detection system
