# 'Not understood' Google search

What if a user asks a question that is outside of the bot's scope? Or what if your bot can't understand the user input? One of the things you can do is show a 'not understood' bot dialog message, which usually leads to an offloading action. It works well, but what if there's a more user-friendly way for the user to still get the answer to their question without offloading or leaving the bot?  

This tutorial will show you how to create a **search engine lookup** on your own website using the user input from your chatbot! We will walk you through the steps of creating a lookup search on your website, using Google's 'Programmable Search'. 

For example, the user asks about 'opening hours' in the chatbot. However, this is not recognized because there isn't such an intent in the bot. So, the bot will go to 'not understood'. Then, a search will be done on your website using the input. Google will search for '{your website} + opening hours' and show the first five results in a carousel in the chatbot.

![An example of the &apos;Not understood&apos; lookup functionality using the Chatlayer docs.](../.gitbook/assets/image%20%28359%29.png)



## Google Programmable Search

With Google Programmable Search you can include a search engine on a website you specified. We will use this \(free\) feature of Google for this tutorial. First, create a new search engine [here ](https://programmablesearchengine.google.com/cse/create/new)for your website. Simply add your website or the webpages where you want to search and click save.

For this tutorial, you need the [GoogleAPI key ](https://developers.google.com/custom-search/v1/introduction)and your search engine ID.

![](../.gitbook/assets/image%20%28358%29.png)

## Action dialog Expression Lookup

Now we can put the _Lookup_ with the information of the Google Engine in an _Action dialog_ in the chatbot:

Add the following arguments to your action dialog:

* NLP: this is the variable what we are looking for, so the input the user has given and resulted in a 'not understood'
* googleAPIKey: this you retrieved using the link mentioned above
* googleEngine: The 'Search engine ID' on the search engine page above 

![](../.gitbook/assets/image%20%28361%29.png)

Once that's done, add the following code in the same action dialog. In line 15, paste a fallback image there, for example the company logo. This will be the image shown in the carousel if the search does not retrieve an image. 

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



