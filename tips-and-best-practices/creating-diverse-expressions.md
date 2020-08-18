---
description: >-
  This tutorial will dive deeper in to a methodology we use at Chatlayer to
  create chatbots that can really understand what your users say.
---

# Creating diverse expressions

Creating a chatbot seems easy at first. Let’s take a simple Frequently Asked Questions \(FAQ\) bot for a pizza place as an example. If a user asks “Which toppings do you have?” we recognise this as an intention by the user to know all possible toppings. We call this an intent in chatbot speak.

Once you put your FAQ chatbot in production you notice that real humans come up with unlimited different ways of asking a question, for example: “What else can you put on my pizza?”. This question we call an expression of an intent. Machine Learning based chatbot platforms like Chatlayer will allow you to train the chatbot and its Natural Language Understanding component with expressions.

All ML-based chatbot platforms tell you you should create a diverse set of expressions. But when can you consider expressions diverse? They also tell you should create enough expressions. But what is enough? If you google it, you find ranges from 12 to 50 to even a thousand expressions per intent. This blogpost will give you a practical way to approach this problem. It will guarantee that you get a set of diverse expressions suitable for chatbots with a strong Natural Language Understanding like Chatlayer \[link to blogpost on our NLU performance\]. So this won’t work for keyword based chatbot platforms.

Strong chatbot platforms look at 2 discriminating features in an expression:

1. Which specific words are used?
2. In which order are these words used?

But how do you keep track of these two components? How do you make sure you use the word diversity required for a good chatbot? And how do you make sure you have covered all word orders that can occur?

In the following 2 sections I will go deeper into how machine learning models work and how they can distinguish sentences based on these 2 features. In the last section I will dive deeper into the expression creation strategy that should give you the optimal set of expressions.

**Word Diversity in Machine Learning Models**

To make sure machine learning algorithms can work with words as input data they are converted into a set of numbers. For those who remember something of their math education in secondary school, this is comparable to x and y coordinates. For example the point \(3,2\) is the point where x = 3 and y = 2. Instead of using just 2 dimensions like x and y, word vectors use hundreds if not thousands of dimensions.

The nice thing about this approach is that you can make sure that words with very similar meanings end up close to each other. For example boat and ship will be closely related. And if you use the right techniques to create these word vectors you can add even more interesting features. Since cars and planes are also modes of transportation, you can make sure they are also closely related. But they do differ in some small ways. Boats travel on water, cars on streets and planes in the air. Ships are bigger than boats and trucks can transport more load than a bike.

If we map only the way these modes of transportation to a simplified graph you might get something like this:

![](../.gitbook/assets/image%20%28315%29.png)

So if you create a chatbot that you can use to arrange transportation over land you will have to be very strict about the horizontal axis. You will not transport something by boat if there is no water. For the vertical axis on the other hand you can be less strict. Maybe you want to transport a small package in a crowded city and then a bike might be sufficient. If it is a larger freight you might need a truck or a train. So the word diversity you would want to allow in this case is illustrated in red below.

![](../.gitbook/assets/image%20%28314%29.png)

But the opposite case can also occur. Imagine you want to transport something big, and you don’t care if it is over land, over water or through the air. In this case, a car and a bike will not be an option. But a boat, a train or a plane is. For this case you might want to allow some diversity in the horizontal axis but not so much in the vertical axis. This can be illustrated by the green box on the image above.

The above illustration can give you a general idea on how machine learning models handle words. To make sure your chatbot understands what is good and what is bad, you should make sure that you use words that are diverse in each direction that is relevant for the use case. But for cases that are not allowed you should be very specific about which words not to include.

**Word Order and Syntactic Structure in Machine Learning Models**

We all know that word order can have a specific meaning for us. “I want to take the train not the car” does not have the same meaning as “I want to take the car not the train” even though both sentences contain the same words.

So if you generate expressions for a chatbot it is very important to include any word order or syntactic structure that makes sense. If you want to book a train ticket you will have to include the 3 following options:

1. I want to take the train to Paris
2. To Paris I want to take the train
3. I want to go to Paris by train

With some imagination you can see that each of these sentences contain more or less the 3 same blocks, but they are ordered completely differently.

Native English speakers will notice that sentence like “To Paris I want to take the train” are not syntactically correct in this context. However, don’t expect your customers to be always syntactically or even grammatically correct. And not all your customers will be native speakers. As long as you as a human can understand what has been said, you should include this type of expression in your model.

**Optimal Expression Generation Strategy**

Now that we know that word order and word diversity is important and why, how can we use this insight to create a step by step guide to make a good set of expressions. Don’t expect a complicated algorithm here. It is actually quite simple. You only need 2 steps.

**Step 1 - Word Order and Syntactic Structure**

Try to come up with a range of very different sentences. In this step the word order and syntactic structure of the sentences is most important. You can ignore the word diversity for now. If we look at the expressions shown above for taking the train we can already use the sentences above and add a few more:

1. I want to take the train to Paris
2. To Paris i want to take the train
3. I want to go to Paris by train
4. By train is how I want to go to Paris
5. To Paris by train is how I want to go
6. …

Try to come up with as many weird sentences as you can that might convey your intention to take the train. But don’t worry if you forget something. You can always come back to this step later in the process and add another sentence.

Now that you have these sentences with very diverse word orders you are ready to go to step 2.

**Step 2 - Word Diversity**

In this step you take all of these sentences above and try to come up with as many synonyms as possible. To make your life easy we have included an expression generator in our platform.

To illustrate how it works, let’s take the sentence: “I want to go to Paris by train”. First you cut this sentence up in its components like so:

1. I want to
2. go
3. to
4. Paris
5. by
6. train

Now for each of these components you can come up with alternatives. Here it is important to cover the highest word diversity for each word as possible. Take “I want to” for example. You can replace this with:

* I would like to
* I must
* I should
* I prefer to
* Let me
* …

Repeat this for every word or set of words. In our Expression Generator tool this will look something like this:

| I want to  | go  | to  | Paris  | by  | train  |
| :--- | :--- | :--- | :--- | :--- | :--- |
| I would like to  | travel  | in the direction of  | London  | with the  | rail  |
| I must  | transport  | with as destination  | Brussels  |  | railway  |
| I should  |  |  | Berlin  |  |  |
| I prefer to  |  |  |  |  |  |
| Let me  |  |  |  |  |  |

And now you repeat this process for all of the sentences from step 1. The nice thing is that for step 2 you can quite often reuse the synonyms and alternatives you created for the previous sentence.

If trough time you come up with an additional synonym, you can just add it to the list of alternatives. That way you don’t have to check all your expressions again to see if you haven’t missed anything.

Following this approach you quickly generate a large amount of expressions. If you look at the example above for “I want to go to Paris by train”, all possible combinations for this sentence amounts up to 6x3x3x4x2x3 = 1296 expressions. So if you repeat this for all 5 sentences above you will end up with close to 10000 expressions and you only had to come up with 5 or 6 sentences.

Since the Chatlayer NLU doesn’t need such a high number of expressions to work well, our system selects the 50 most diverse sentences to train on. So per sentence you will only see up to 50 expressions show up in our platform.

**Conclusion**

If you follow this 2-step guide you are sure that you have covered all possible word orders that you can come up with and that you have a diverse set of words included. No more going through all of your expressions to check whether you haven’t missed anything. And if a real human comes up with a new word order you can simply add this sentence to the set, include all the synonyms and alternatives and retrain your model. And now you will have an even stronger chatbot.

