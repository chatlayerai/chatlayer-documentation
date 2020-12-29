# 'Not understood' Google search

Users can ask many different questions and it is nearly impossible to put all these questions in your bot. That's why Chatlayer offers the 'not understood' bot dialog message for when the bot cannot understand user input. This usually leads to an offloading action. However, there is a way to make this 'not understood' bot message more user-friendly and help them search for the correct answer without offloading. This tutorial will show you how to create a search engine lookup on your own website using the user input from your chatbot!

This tutorial will walk you through the steps of creating a lookup search on your website, using Google's 'Programmable Search'. For example, the user asks 'opening hours' in the chatbot. However, this is not recognized because there isn't such an intent in the bot. So, the bot will go to 'not understood'. Then, a search will be done on your website using the input. Google will search for '{your website} + opening hours' and show the first five results in a carousel in the chatbot.

![An example of the &apos;Not understood&apos; lookup functionality with of docs.chatlayer.ai](../.gitbook/assets/image%20%28359%29.png)

## Google Programmable Search

With Google Programmable Search you can include a search engine on a website you specified. We will use this \(free\) feature of Google for this tutorial. First, create a new search engine [here ](https://programmablesearchengine.google.com/cse/create/new)for your website. Simply add your website where you want to search and save.

For this tutorial you need the [GoogleAPI key ](https://developers.google.com/custom-search/v1/introduction)and your search engine ID.

![](../.gitbook/assets/image%20%28358%29.png)

## Action dialog Expression Lookup

Now we can put the Lookup with the information of the Google Engine in an Action dialog in the chatbot:

Add the following arguments in your action dialog:

* NLP: this is the variable what we are looking for, so the input the user has given and resulted in a 'not understood'
* googleAPIKey: To be retrieved with the link mentioned above
* googleEngine: The 'Search engine ID' on the search engine page above 

![](../.gitbook/assets/image%20%28361%29.png)

Then, add the following code in the same action dialog. In line 15, paste a fallback image there, for example the company logo. This will be the image shown in the carousel if the search does not retrieve an image. 

```javascript
const { nlp, googleEngine, googleAPIKey } = args;

const { expression } = nlp;

const url = `https://www.googleapis.com/customsearch/v1?key=${googleAPIKey}&cx=${googleEngine}&q=${expression}`;

const searchResult = await fetch(url).then(res => res.json());

const elements = _.get(searchResult, 'items', [])
  .slice(0, 5)
  .map(result => {
    const imageUrl = _.get(
      result,
      'pagemap.cse_thumbnail[0].src',
      'https:// {your image here} .png'
    );
    return {
      title: result.title,
      subTitle: result.snippet,
      ...(imageUrl ? { imageUrl } : {}),
      buttons: [
        {
          title: result.title,
          type: 'web_url',
          url: result.link,
          payload: {},
        },
      ],
    };
  });

const builder = ChatlayerResponseBuilder();

if (elements.length) {
  builder.addCarousel(elements);
} else {
  builder.addMessage('Nothing found!');
}

builder.send();


```

This code block already takes care of the carousel so no need to add an extra bot message dialog. The last thing we have to do is link this to the 'Not understood' bot message:

* Change the text message with {internal.nlp.expression}, so the user input is reflected in the 'not understood' message
* Add a 'Go to' to link the Lookup action dialog to 'Not understood'

![](../.gitbook/assets/image%20%28363%29.png)

You can also add the offloading message after the lookup, to make sure the user can get the answer from a human agent if the answer is not sufficient. 

And that's it! A more user-friendly 'not understood' message!



