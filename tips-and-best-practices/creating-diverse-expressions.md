---
description: >-
  This tutorial will dive deeper in a methodology we use here at Chatlayer to
  create chatbots that can really understand what your users say.
---

# Creating diverse expressions

Creating a chatbot seems easy at first. Let’s look at a simple Frequently Asked Questions \(FAQ\) bot for a pizza place as an example. If a user asks “What toppings do you have?” he wants to know all the possible pizza toppings you have. We call this an **intent** in chatbot terminology.

Once you put your FAQ chatbot in production, you'll notice that real humans come up with unlimited different ways of asking the same question, for example: “What else can I put on my pizza?”. This different way of asking the same question is what we call an **expression** of an intent. Machine Learning-based chatbot platforms, like ours, will allow you to train the chatbot and its Natural Language Understanding component using expressions.

All ML-based chatbot platforms advice you to create diverse expressions. But when and how are expressions diverse? They also tell you to create enough expressions. But what is enough? A quick Google search shows that 12 to 50 to even a thousand expressions per intent are possible, how many do you need?

We want to give you a final and practical approach to this problem. If you follow these steps, you'll get diverse expressions, suitable for chatbots with a strong Natural Language Understanding like ours! 

Strong chatbot platforms look at 2 different elements of an expression:

1. Which specific words are used?
2. In which order are these words used?

But how do you keep track of these two components? How do you make sure you reach the word diversity required for a good chatbot? And how do you make sure you cover all word orders that can occur?

In the following 2 sections, we will explain how our machine learning models work and how they can distinguish sentences based on the 2 features above. In the last section, we will look at the expression creation strategy that should give you the best set of expressions.

## **Word Diversity in Machine Learning Models**

To make sure machine learning algorithms can use words as input data they are converted into a set of numbers. For those who remember bits of their math classes in school, this is comparable to x- and y-coordinates. For example, the point \(3,2\) is the point where x = 3 and y = 2. Instead of using just 2 dimensions like x and y, word vectors use hundreds, if not thousands of dimensions.

The good thing about this approach is that it makes sure that words with very similar meanings end up close to each other, because they're similar. For example, the words 'boat' and 'ship' will be closely related. 

If you use the right techniques to create these word vectors, you can add even more interesting features. Since 'cars' and 'planes' are both means of transportation, you can make sure they are closely related. But they do differ of course. Boats travel on water, cars on streets, and planes move in the air. Ships are bigger than boats, and trucks can transport more than a bike.

If we put these modes of transportation on a simple graph, it looks something like this:

![](../.gitbook/assets/image%20%28315%29.png)

So if you create a chatbot to arrange transportation over land, you will have to be very strict with the horizontal axis. You cannot transport something by boat if there is no water. The vertical axis on the other hand can be less strict, maybe you want to transport a small package in a crowded city and then a bike is enough. If it is a larger freight, you might need a truck or a train, so the word diversity you would allow in this case is shown in yellow below.

![](../.gitbook/assets/image%20%28314%29.png)

But the opposite case can also occur. Imagine you want to transport something big, and you don’t care if it is over land, water or in the air. In this case, a car and a bike won't be good options. But a boat, a train or a plane are. So in this case, you might want to allow some diversity in the horizontal axis, but not so much in the vertical axis. This can be illustrated by the blue box on the image above.

The above illustration can give you a general idea on how machine learning models handle words. To make sure your chatbot understands what is good and what is bad, you should make sure that you use words that are diverse in each direction that is relevant for the use case. But for cases that are not allowed, you should be very strict about which words to not include.

## **Word Order and Syntactic Structure in Machine Learning Models**

We all know that word order can have a specific meaning for us. “I want to take the train, not the car” does not have the same meaning as “I want to take the car, not the train” even though both sentences contain exactly the same words \(just not in the same order\).

So if you're generating expressions for your chatbot, it's very important to include any word order or syntactic structure that make sense. If you want to book a train ticket, you will have to include the 3 following options:

1. I want to take the train to Paris
2. To Paris I want to take the train
3. I want to go to Paris by train

With some imagination, you can see that each of these sentences contain more or less the same three blocks, but the order is completely different.

Native English speakers will notice that a sentence like “To Paris I want to take the train” are not syntactically correct. However, don’t expect your customers to be always syntactically \(or even grammatically\) correct. Not all your customers will be native speakers either. 

{% hint style="info" %}
As long as you as a human can understand what has been said, you should include this type of expression in your model.
{% endhint %}

## **Optimal Expression Generation Strategy**

Now that we know how important word order and word diversity are, we can use this insight to create a step-by-step guide on how to make a good set of expressions. Don’t expect a complicated algorithm here, you only need 2 steps.

### Step 1 - Word Order and Syntactic Structure

Try to come up with a list of very different sentences. In this step, the word order and syntactic structure of the sentences is **most** important. You can ignore the word diversity for now. If we look at the expressions shown above for taking the train, we can already use the sentences above and add a few more:

1. I want to take the train to Paris
2. To Paris i want to take the train
3. I want to go to Paris by train
4. By train is how I want to go to Paris
5. To Paris by train is how I want to go
6. …

Try to come up with as many weird sentences as you can that might convey your intention of taking the train. Don’t worry if you forget something, you can always come back to this step later and add other sentences.

### Step 2 - Word Diversity

In this step, you take all of the sentences listed above and try to come up with as many synonyms as possible. To make this easier for you, we've included an expression generator on our platform. You're welcome.

To illustrate how this works, let’s use the sentence: “I want to go to Paris by train”. First you strip this sentence of its components, like so:

1. I want to
2. go
3. to
4. Paris
5. by
6. train

Now for each of these components you can come up with synonyms. Here it's important to cover the highest word diversity possible for each word. Take “I want to” for example. You can replace this with:

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

And now you can repeat this process for all of the sentences from step 1. The nice thing is that for step 2, you can quite often reuse the synonyms and alternatives you created for the previous sentence.

If later you come up with an additional synonym, you can just add it to the list of alternatives. That way you don’t have to check all your expressions again to see if you missed anything.

Following this approach you can quickly generate a large amount of expressions. If you look at the example above for “I want to go to Paris by train”, all possible combinations for this sentence amounts up to 6 x 3 x 3 x 4 x 2 x 3 = 1.296 expressions! So if you repeat this for all of the 5 sentences above, you'll end up with almost 10.000 expressions and you only had to come up with 5 or 6 sentences. Easy does it.

Since our NLU doesn’t need such a high number of expressions to do its job well, our system selects the 50 most diverse sentences to train on. So per sentence you will only see up to 50 expressions show up in our platform.

## **Conclusion**

If you follow this guide, you can make sure that you have covered all possible word orders that you can come up with, and that you have a diverse set of words included. No more going through all of your expressions to check whether you haven’t missed anything. And if a real human comes up with a new word order, you can simply add this sentence to the set, include all the synonyms and alternatives, and retrain your model. Now you have an even better chatbot.

