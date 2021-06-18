# NLP Dashboard & NLP Improve

{% hint style="info" %}
The NLP Dashboard & NLP Improve is only available on the Enterprise plan or higher. Want to upgrade? [Get in touch](../../support/get-in-touch.md).
{% endhint %}

The NLP dashboard \(and the tab 'improve'\) give you an overview of the quality of your NLP model. It automatically detects any overlap between intents, which is especially useful if you are building a larger NLP model, or if multiple team members work on it.

## **NLP Dashboard**

The NLP dashboard lets you know how well you are doing for each language. Based on how you have trained your NLP, it gives you an overall model score, ranging from 0% to 100%. The overall model score is calculated based on the amount of intents with too few expressions and the amount of intents with misclassified expressions.

![](../../.gitbook/assets/image%20%28150%29.png)

* On the left side of the dashboard you will find a general summary of your model
* Below you can see your training history which shows how you're doing so far and whether or not you are improving over time
* On the right side, you find an overview of all the intents with know issues. The blue number between brackets indicates how your score has changed since your last training

### **Not enough expressions**

A first metric our platform measures is the amount of **expressions**. To train your model as best as possible, we advise to create at least 20 expressions per intent. Ideally you'd have around 50 expressions per intent. The more, the better, and the more accurate your bot will be able to interact with the user.

### **Misclassified expressions**

Just like us humans, no AI or NLP system is absolutely perfect. And because our brain works different from the Chatlayer.ai NLP, it is hard to predict where mistakes can and might happen.

To guarantee the best possible outcome for your bot, we do an advanced analysis of all the expressions. This recognizes the expressions that the NLP might have a hard time with. For example, it might have difficulties differentiating between sentences like: “I see on my bill that I have the wrong subscription” and “My bill seems wrong if I look at my subscription”.  Both sentences mean a different thing. So the second metric we take into account is the number of intents that have a risk for misclassified expressions like these.

In the intent list on the right side of the NLP Dashboard, you can click on the wrench icon to improve your set of expressions and thus to better differentiate between intents.

## NLP Improve

The 'NLP Improve' module helps you create better expressions for where the system has detected issues. At the top of the dashboard, you can select the language and the intent you wish to improve. Quick tip: the list is automatically sorted to show you the intents with the most known issues.

![](../../.gitbook/assets/image%20%2811%29.png)

Next you can select the expression you wish to improve. Once you have selected this expression, you will see the confidence score on the right for the top two or three intents. As you may notice, the NLP model is more confident that your expression belongs to another intent than to this intent.

![](../../.gitbook/assets/image%20%283%29.png)



