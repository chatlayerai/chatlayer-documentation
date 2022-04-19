# Template: Find nearest location

With this template, users can easily find your organisation’s nearest branch by simply asking your chatbot! After the bot asked the user for their address, it will look through an external database (in this case, Airtable) which contains the data for all your organisation's locations. Then it will calculate which location is closest to the user’s address by using the Google Maps API. Finally, the bot will show the result on Google Maps, within an iFrame.&#x20;

Keep reading to learn how you can customise this template for your own organisation.&#x20;

### Flow Overview&#x20;

Below is a brief overview of what happens in which bot dialogs in this flow:

1. Ask address: In this dialog, the bot asks the user for their address and saves the response as a variable named `user_address`. &#x20;
2. Thanks: Here, the bot thanks the user for providing their address and automatically goes to the next dialog, named `Locator`. &#x20;
3. Locator: This dialog uses a Code Action to call the Airtable API and the Google Maps API &#x20;
4. Give address: In this dialog, the bot shows the name and address of the closest location found in the database. The name is shown as the variable `closestLocation.Name` and the address is shown as `closestLocation.Address`.&#x20;
5. Show location on map: Next, the bot shows the closest branch location on a map, within an iFrame&#x20;
6. Clear user address: Finally, the bot clears the variable user\_address so if needed, the user can use another address to find another closest branch. &#x20;

### How to customise this template for your business&#x20;

To customise this flow, you will need two things:&#x20;

1. An Airtable account, a table containing the data of your organisation's locations, and the Airtable API key &#x20;
2. A Google Maps API key&#x20;

#### Technical customization&#x20;

To make the branch finder work, your bot needs to be able to access the location data of your branch locations (using the Airtable API) and look up the user’s address (using the Google Maps API).&#x20;

Your bot can make these API calls within an Action dialog, named `Locator`, which contains a piece of custom code shown below. This code may look a bit intimidating, but don’t worry, you only have to change a few pieces of information!

Here's the code written within the `Locator` dialog:&#x20;

```
const allStations = await fetch(`https://api.airtable.com/v0/(YOUR_BASE_ID)/(YOUR_TABLE_NAME)`, { 
headers: {
Authorization: `Bearer (YOUR_AIRTABLE_API_KEY)`
}
}).then(r => r.json());
let re = / /g; 

const currLoc = args.user_address.replace(re, '+');
let minDistance = Number.MAX_SAFE_INTEGER; 
let nearestShop;
const chatlayer = ChatlayerResponseBuilder(); chatlayer.addSessionVariable('currLoc', currLoc); 
const addressFromMaps = await fetch(`https://maps.googleapis.com/maps/api/place/findplacefromtext/json?input=${currLoc}&inputtype=textquery&fields=geometry&key=(INSERT_YOUR_GOOGLEMAPS_API_KEY)`).then(r=> r.json()); 
const geoLocation2 = { 
Latitude: addressFromMaps.candidates[0].geometry.location.lat, 
Longitude: addressFromMaps.candidates[0].geometry.location.lng, 
} 
//const geoLocation2 = {Latitude : "52.5001278", Longitude : "13.3121555"}; allStations.records.forEach(station=>{ 
const geoLocation1 = station.fields;
const lat = geoLocation1.Latitude - geoLocation2.Latitude; 
const lon = geoLocation1.Longitude - geoLocation2.Longitude; 
 
const val = Math.sqrt(Math.pow(lat, 2) + Math.pow(lon, 2)); if(minDistance>val){ 
minDistance = val; 
closestLocation = geoLocation1;
}
});

closestLocation.Address = closestLocation.Address.replace(/ /g, ' ');
chatlayer.addSessionVariable('closestLocation', closestLocation);
chatlayer.addSessionVariable('addressFromMaps', addressFromMaps); chatlayer.send();----------------------------------
```

In this piece of code, you should customise the following three things: &#x20;

1. The Airtable link
2. The Airtable API key &#x20;
3. The Google Maps API key &#x20;

#### 1 – Setting up your own Airtable base

For each of your organisation's locations, your Airtable will need to contain fields with the following information:&#x20;

1. Name of the branch&#x20;
2. Address&#x20;
3. Latitude&#x20;
4. Longitude&#x20;

When you’ve newly imported the 'Nearest Location' template, it will automatically link to [this Airtable](https://airtable.com/invite/l?inviteId=invF76GY9tGp3hGyz\&inviteToken=224dcd7cbf041e3e39f7caefbbe6798f4dc4f5ef1643586d2a1a5cbcb286f1f3). Feel free to use it for testing, or as an example of what the data in your own Airtable should look like, but make sure to replace it once you start using the bot for your own organisation.&#x20;

For more information on how to integrate Airtable into your bot, check out [this tutorial](https://docs.chatlayer.ai/integrations/code-action/airtable).&#x20;

{% hint style="info" %}
You can link any sort of database to this bot, as long as it has an API. Read more about integrations [here](https://docs.chatlayer.ai/integrations/integrations-101).
{% endhint %}

#### 2 – Adding your own Airtable link to the Action dialog

In the piece of code within the 'Locator' dialog, in the url on line 1, replace `(YOUR_BASE_ID)` with the ID of your own Airtable base and `(YOUR_TABLE_NAME)` with the name of the table that contains your location data. On line 3, replace `(YOUR_AIRTABLE_API_KEY)` with your own Airtable API key. You can find your Airtable's base ID and API key [here](https://airtable.com/api). Make sure to select the right one!

#### 3 – Adding your own Google Maps API to the Action dialog

In the piece of code within the 'Locator' dialog, on line 13, replace `(YOUR_GOOGLEMAPS_API_KEY)` with your own Google API key. Learn how to create a Google Maps API key (or find an existing one) [here.](https://developers.google.com/maps/documentation/embed/get-api-key)&#x20;

In the Show Location on map Action dialog, in the Source Field of the iFrame action, you should also replace `(YOUR_GOOGLEMAPS_API_KEY)` with your own Google API key.

#### 4 – Edit the text in the dialogs

In the ‘Ask address’, ‘Thanks’ and ‘Give address' dialogs, make sure to change the default text to add your organisation's name and other data needed for the bot to match the style and tone of your organisation.&#x20;

#### 5 – Connect the flow to other flows

Now that you've added this new flow, make sure it connects to other flows. For example, if this is an important use case for your bot, make sure to mention it in the introduction.

#### 6 – Update the NLP

As always, when you add, change, or remove something from the NLP section, you'll need to train it again. Click on the right top button called 'NLP'.&#x20;

That's it, now your bot can find locations nearest to the user's address! 👏
