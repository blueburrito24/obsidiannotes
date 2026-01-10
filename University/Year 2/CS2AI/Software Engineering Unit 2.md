### Lecture 2 "Introduction to Artificial Intelligence" Part 1
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

