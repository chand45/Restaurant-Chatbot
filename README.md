# Restaurant-Chatbot

During the pandemic situation where human contact was considered risky, chatbots helped us in serving the customers efficiently. This was our inspiration in building a chatbot. The aim of our chatbot is to reduce the communication gap between restaurant management and customers, without the involvement of any physical contact.

Coming to the data format of our chatbot: 
We are going to classify any given input sentence into one of our 7 predefined tags like greetings, payments, thank you. Each tag has some predefined patterns and responses. We train our model with theese patterns. Customer is served with one of the responses randomly taken from our predefined set.

# How does chatbot understand human language?
Using Natural Language Processing techniques, we are going to convert the input sentence into a vector of 0s and 1s as computer only understands 0 and 1. This conversion process contains steps like tokenizing,stemming and bag of words.

Tokenization is splitting a string into meaningful units.
 
Each unit is then trimmed to it's base word by stemming. Stemming is helpful in reducing the number of words in our dictionary. Since words like organize, organizes, organized have the same meaning, we can reduce the complexity of our model by considering the root form of each word.

Bag of words is the Process of converting the given input sentence into a word vector i.e. a sequence of 0’s and 1’s. For every word in our dictionary, we check if it is present in our input sentence. If present, the corresponding index in our word vector is made 1, else 0. 

The functions are implemented using nltk, which is an open source python module.

# Neural network model of chatbot.
Our model has 1 input layer, 2 hidden layers and 1 output layer. Input layer has 54 nodes as there are 54 words in our dictionary. Hidden layer as 8 nodes and output layer has 7 nodes. 7 nodes in our output layer correspond to 7 different tags in our input data. The values of nodes in hidden layer are calculated using innerproduct i.e. 
Hidden Node Value = x1w1 + x2w2 + x3w3 + x4w4 .......xnwn
After each hidden layer, we use ReLU as our activation function. Since the final output represents probability which is always positive, we ignore negative values using ReLU. Softmax is used after the output layer to find the probability that the given input sentence corresponds to the specific tag. 

# How the model actually Learns?
When we train the model, we compare the output produced by our model with actual output using which we define a loss function. Using the technique of back propogation i.e. adjusting weights by finding gradient (slope) our model optimizes itself in every iteration. 

# Implementation of chatbot.
We first import the neural network parameters (weights) of our previously trained model. The input senctence from the user is tokenized, stemmed and converted into a bag of words before sending it the model. Our model then classifies the sentence into an appropriate tag and responds with a predefined response.
