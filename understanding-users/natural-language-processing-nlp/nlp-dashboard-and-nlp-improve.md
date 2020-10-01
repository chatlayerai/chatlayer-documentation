# NLP Dashboard & NLP Improve

The NLP dashboard & NLP improve give you an automatic overview of the quality of your NLP model. It automatically detects overlap between intents, which is especially useful if you are building a larger NLP model or if multiple team members work on it.

## **NLP Dashboard**

The NLP dashboard gives you an overall indication how well you are doing for each language. Based on how you have trained your NLP we give you an overall model score ranging from 0% to 100%. The overall model score is computed based on the amount of intents with too few expressions and the amount of intents with misclassified expressions.

![](../../.gitbook/assets/image%20%28150%29.png)

On the left of the dashboard a general summary of your model is given. Below you can find your train history which will show you how you have done in the past and whether or not you are improving over time. On the right we list all the intents with know issues. Between brackets you can see how your score has changed since the last training.

### **Too few expressions**

A first metric we measure is the amount of expressions. To optimally train your model it is advised to have at least 20 expressions per intent. Ideally you have around 50 expressions per intent.

### **Misclassified expressions**

Just like humans no AI/NLP system is perfect. And because our minds work differently than the Chatlayer.ai NLP it is hard to predict where mistakes might happen.

To guarantee the best possible outcome we do an advanced analysis on all the expressions. This determines the expressions for which the NLP might have a hard time. For example it might have difficulties differentiating between a sentences like: “I see on my bill that I have the wrong subscription” and “My bill seems wrong if I look at my subscription”.  So the second metric we take into account is the number of intents that have a risk for these misclassified expressions.

In the intent list on the right of the NLP Dashboard you can click on the wrench icon to improve your set of expressions, and thus to better discriminate between intents.

## NLP Improve

The NLP Improve module helps you out with creating better expressions where the system has detected issues. On the top of the dashboard you can select the language and the intent you want to improve. The list is automatically sorted to show you the intents with the most know issues.

![](../../.gitbook/assets/image%20%2811%29.png)

Next you can select the expression you want to improve. Once you have selected this expression you will see the confidence on the right for the top 2 or 3 intents. As you will notice the NLP model is more confident that your expression belongs to another intent than to the correct intent.

![](../../.gitbook/assets/image%20%283%29.png)



