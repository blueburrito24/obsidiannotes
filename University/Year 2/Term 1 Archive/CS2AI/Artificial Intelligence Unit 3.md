### Lecture 3 "Introduction to Artificial Intelligence" Part 1
Machine Learning is a subset of AI, using advanced techniques from data without explicit programming. Deep Learning is also a subset of Machine Learning, involving multi-layered neural networks for high accuracy.

An example of machine learning is how mobile phone keyboards pick up text patterns from users and predicts the type of language they will use.
We can follow the definition from Arthur Samuel (1959) - "Learning from data without explicit programming" and Tom Mitchell (1998) - "Improving performance P on Task T through experience E".
Here's a diagram on the differences between Traditional Programming and Machine Learning.
![[{E3D9296E-6C0F-4784-9519-BA5AB496390D}.png]]
Also when it comes to machine learning, for example in the scenario of reading a number from a handwritten image, we can't rely on few simple rules to complete such a task - so we need to combine a large number of weak but relevant rules.
Instead of writing the program by hand for each task needed, we collect lots of examples of correct outputs and the machine learning algorithm takes these examples and produces a program that does the same thing.

So, we can categorise it like this;

"Traditional Programming" input + program -> output
"Machine Learning" input + output -> program/model via learner algorithm
So, traditional programming is less flexible and uses fixed rules and structured data whereas machine learning is adaptable, handles dynamic/unstructured data and continuous adaptation.

Examples of Machine Learning in practice:
- Self-driving cars
- automated game playing
- facial and fingerprint recognition, which rely on the common structural components of the items of interest
- spam filtering
- speech recognition like Alexa and Siri
- medical diagnosis
- trading
- fraud prevention i.e., anomaly detection, historical purchase data mining, personalised analysis relating to a person's information
And note that in many of these examples, the results aren't perfect but are much easier to reach compared to what we could try using purely traditional programming.

There are also different forms of Machine Learning, in three branches; "Supervised" "Unsupervised" and "Reinforcement".
- Supervised machine learning involves a process of input (X) + output (Y) and learn mapping -> Y=f(X).
The goal is to figure out the mapping function and create new input data (X) from it, from which we can predict output variables (Y).
This algorithm gets its name from how the algorithm learning from a dataset is similar to a teacher supervising a learning process.
The model has to attempt to map its output (Y) against sets of features from the given input (X).
- Unsupervised machine learning involves only an input (X), with an underlying model structure and no examples of a correct output.
Unsupervised machine learning is often used to model that underlying structure seen in the data provided to learn more about it.

With the example of spam detection, we can identify its learning task and training data - classifying emails as spam or ham (non-spam) and learning from labelled email examples respectively.
Here's two examples of spam and ham emails:
![[Pasted image 20260110222425.png]]
![[{5B8C53FA-A696-4FE7-A5DB-25E4EF3FCE6C}.png]]
We can identify that spam emails often be characterised by the following:
- special characters like $ and %
- mentioning awards, cash and "free"
- generic or even specific greetings
- bad grammar and misspelled words like m0ney, c1ick here
- excessive excitement like an abundance of capitalisation or !!!
- senders being on the contact list
- the email length
- the receiver and sender having interacted previously
![[Pasted image 20260110222639.png]]
We can map these characteristics on a "feature vector" showing how often these characteristics appear.

We can attribute a mathematical function to the supervised learning problem:
$$ Feature\ space = R^d $$
Where "d" is the number of features.
- Label space (a class or target label): Y = {0, 1} = {ham, spam}
- a classifier (hypothesis): "h" (family of classifiers)
- Data: (x$_1$, y$_1$)...(x$_n$, y$_n$)
- The task of Machine Learning is a selection problem to find "h" that works well on this problem.
![[Pasted image 20260110223323.png]]
Diverse Machine Learning Terminology:
- Training Data - a data set used to find predictive relationships for the model.
- Test Data - separate data set used to measure the performance of a model.
- Model - mathematical representation of a real world process; a predictive model forecasts an outcome based on past behaviours.
- Training process - the process of creating a model from the training data, which is fed into the training algorithm to learn a representation of the problem. AKA "learning".
- Predicative/data features - independent variables or predictor variables are observable quantities that a prediction model records and uses. We can engineer features by combining or adding new information to them.
- Target - a dependent variable, the output of the model or the variables we want to predict.
- Classification - predicting a category label, like spam and ham.
- Regression - predicting a numerous or continuous label like a price.

"Inductive Learning" 
The simplest form of inductive learning is learning a function from examples.
"f" is the target function e.g., a pair of x and f(x).
Using a hypothesis "h" we can approximate function "f".
![[{BF357DD7-333A-4490-B796-CB1D4BEEC6AE}.png]]
We adjust or construct "h" to consist with "f" on the training data set.
![[{69988A79-3A4B-4924-A80A-2D1D4C3D141D}.png]]
![[{0C80C5D6-F7F7-4A99-A7FB-C512C5F28DEE}.png]]
We can see here how red, green and blue are iterations of adjusting "h" to fit with "f" by fitting along a curve.
![[{D16DE902-427D-404C-887D-CC0D7D5534DD}.png]]
Overfitting against the training data set is a machine learning behaviour (that we DON'T WANT) that occurs when the machine learning model gives accurate predictions for training data but not for new data.

We also have an identified workflow in machine learning:
- Define an ML problem and propose a solution
Choose an unsolved or interesting problem, identify patterns or classifications we can give the model.
- Provide a data set
Gather reliable and labelled data with relevant parameters.
We need to split the data by what data will be used for training and testing (typically falls into a ratio of 66:33). Testing data should never be seen during training. Also note that we should provide a minimum of 1000 examples and 10,000 - 100,000 typical problems + 100,000 - 1,000,000 extreme problems.
- Prepare the data set and select features
We need to remove repeated data, fill in missing values, fix outliers in the data set and reformat the data for the model to process. We should remove data that is irrelevant to the problem at hand.
- Choose and train a model
Common models for machine learning can involve Decision Trees, Artificial Neural Networks, Hidden Markov Models, Support Vector Machines, Genetic Algorithms and Bayesian Networks. We will likely have to attempt using various models to determine what our best option is.
- Test and validate your model
We have to determine how accurate our classifications are, which can be plotted on a "Confusion Matrix".
![[{827B0BB8-F45C-4CFA-9FF7-F4610B76C8FD}.png]]
- Use the model to make predictions
We can now apply the model to new examples that aren't in the training or test data.