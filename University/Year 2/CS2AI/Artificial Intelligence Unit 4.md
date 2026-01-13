### Lecture 4 "Introduction to Artificial Intelligence" Part 2
"Data Cleaning" is a critical pre-processing step for Machine Learning.
![[{6C83CAE0-ED1E-49DA-91F3-7F13078EA485}.png]]
Also known as "data wrangling", data cleaning involves handling missing data, detecting and treating outlier data, scaling and normalising data so that we have a consistent range to operate within, and handling categorical data with encoding techniques like "one-hot encoding" and "label encoding". Data cleaning is often done using various libraries and frameworks like Python's "pandas" and scikit-learn, alongside automated tools for efficient data cleaning like open-source libraries and custom scripts.

![[Pasted image 20260112202029.png]]
We have to consider what data features we want to focus on, through the process of "Feature Selection" we can reduce the amount of data used by an ML model to narrow that scope on what features are most important.
![[Pasted image 20260112202225.png]]
If we were to include unimportant features in the data, it could worsen the accuracy of our ML model.

![[Pasted image 20260110223323.png]]
We looked at this diagram previously in [[Remote-Folder/University/Year 2/CS2SE/Software Engineering Unit 2|Software Engineering Unit 2]], it's important we note that the training data set builds a classification model while test data set evaluates the model quality. This classification model is applied to data unseen to the model previously.

When it comes to choosing and training a model, we have to determine a new set of classifiers. Below is an elaboration on some of the models mentioned in [[Artificial Intelligence Unit 3]].

"Decision Trees"
![[Pasted image 20260112203442.png]]
Decision trees handle "nominal" or qualitative data like gender, height, age, ethnicity. These trees are a non-metric method for categorical data, not measuring the data in any way.
The data is classified with a sequence of parameters or questions.
We use these data (input) comparisons and trees to create classes (output) like tall or short to define height.
Decision trees are an example of a Supervised ML Algorithm, it uses a set of rules to make decisions like how we make decisions. It's a simple algorithm that we can understand and implement.
For example, if we were to plan a vacation trip we would use such a rule-based approach.
![[{2BFFCA5A-8349-4F86-BDFC-2D8644D829B3}.png]]
We can also see an example of this algorithm in Machine Learning below:
![[{CB7F4E1F-05F3-4AB7-AE57-1578CA490B5F}.png]]
![[{C52D2F70-A4EB-48BA-BF5D-8D86012BFC47}.png]]
Decisions/rules separate the data into what works and what doesn't, 
the "leaves" or terminal nodes of the tree indicate what class the items are categorised into,
the tree partitions samples into mutually exclusive categories,
each terminal node is in one group (as all paths start at the root and end at leaves),
each path aligns with a decision rule including all the tests on the path (AND),
the separate paths that result in the same class are disjunctions (ORs),
in any case only one path can be followed - false decisions go on the left branch and true decisions go on the right path.

To simplify it:
- Pick the best feature, the one which splits the data between false and true decisions for the model.
- Ask the relevant question.
- Follow the answer path.
- Cycle back to the first step until we get definitive answers.

Here is an example of training data and decision trees in use:
![[Pasted image 20260112204955.png]]
![[Pasted image 20260112205006.png]]
![[Pasted image 20260112205041.png]]
Here we can see that if it's sunny or humid then the player of interest will not play tennis.

Our goal with a decision tree is to have it be as small as possible, shaving away any unnecessary decisions or information.
We want features that split the data sets by given labels, so we have distinct leaf nodes.
Our most favourable rules are based on how well a feature separates the training data into our desired classes. We do this to select among the features while still growing the tree.
The information "gain" in this process is a measure of how much we can reduce uncertainty (typically a value lying between 0 and 1).

A "goodness function" is used to select which features we use to make this decision tree. An example of a typical goodness function is the "Gini Impurity" which measures the variance of features across different classes.

"Nearest neighbour classifier"

Another classifier we can use is a Nearest Neighbour Classifier.
This stores all the training data, $(x_1, y_1)...,(x_n, y_n)$ and given a new test vector $x^{(test)}$ finds the nearest similar training vector $x^{(NN)}$ and outputs a class label to boot, $y^{(NN)}$.
![[{E8FF0EE4-9956-43BD-BCD6-4CA0CCE3D0C2}.png]]
We have to use a good distance measure for the training vector and test vector, known as Euclidean Distance.
![[Pasted image 20260112211040.png]]
The Euclidean Distance is a straight line distance between two points in space, it measures the distance between the two points, or vectors, of interest.

The "K-Nearest Neighbour Classifier" similar to the "NN" classifier but it takes "K" nearest points instead of just one, with a smaller distance meaning the test and training vector are more similar.
It chooses the majority label among them as the predicted label.
![[{1816EE2D-38BB-4DAF-B125-8758EAC320F5}.png]]

The methods previously discussed fall into the category of "Supervised Learning" in ML algorithms.
Unsupervised learning in ML algorithms is performed to attempt to identify a structure or pattern in the input data, forming classes/groups out of these input data. 
However these classes are called "clusters", there are as many similar and as few dissimilar items in the cluster.
Clustering reduces the complexity of the data by creating a reduced representation from it, and helps us look for new insights into the structure of the data.
![[Pasted image 20260112211919.png]]
We can see examples of clustering with documents- often times clustering is used with documents when looking for groups of documents with similar and important terms amongst them.

Unsupervised Learning- only requires an input, there is no underlying model structure, there are no correct answers or a "teacher" for the model to follow, the model can find its own interesting structures.
Supervised Learning- requires an input and output to map out a process to predict outputs from new inputs, alike a teacher-supervised learning processed.