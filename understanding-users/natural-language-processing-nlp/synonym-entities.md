# Entities

Entities are important pieces of information that are extracted from an expression. You want to store these entities in a separate variable so you can re-use them later on.

## Contextual entities

Contextual entities use machine learning to identify entities in your sentence by learning which type of word your entity is, where in the sentence it's placed and what the specific context is.

### Adding synonyms for entities

Synonym entities allow you to add alternatives to entities that are assigned to the same value.   
For example:

`I want to go to Brussels`

`I want to go to Bruxelles`

The meaning of these two expressions is exactly the same, but you want to convert `Bruxelles` to `Brussels` so that your bot understands the destination your user wants to go to.

To do this, go to the Entities tab and click on the entity you want to create synonyms for to add them.

![](../../.gitbook/assets/image%20%28201%29.png)

### Fuzzy matching for contextual entities

Fuzzy matching allows you to recognize a slight variation of a synonym or entity value as the original value. For example "Brusselt" will be corrected to "Brussels".

The fuzzy matching is quite strict. Less than 20% of the characters can be different in order to map it to another entity. This is to avoid that the value is mapped to another entity which also has overlap. 

## System entities

System entities are entities that are automatically extracted from the messages of users. You can use these to enrich your conversations and data integrations without having to configure custom entities yourself.

{% hint style="warning" %}
You should not overwrite System Entities yourself – they will automatically be overwritten with the last detected value if any are available. Instead, copy the System Entity variable to a variable of your own choosing outside the **sys** or **internal** namespaces.
{% endhint %}

### Supported system entities

We support the following system entity types:

| Variable name | Example input by user | Example result in session |
| :--- | :--- | :--- |
| `sys.email` | "ilovebots@chatlayer.ai" | `sys: {email: 'ilovebots@chatlayer.ai'}` |
| `sys.phone_number` | "+32 487 23 02 03" | `sys: {phone_number: '(+32) 487230203'}` |
| `sys.ordinal` | "5th" | `sys: {ordinal: '5'}` |
| `sys.amount_of_money` | "5 euro" | `sys: {amount_of money: '5', amount_of_money_currency: 'EUR'}` |
| `sys.distance` | "5 kilometers" | `sys: {distance: '5', distance_unit: 'kilometre'}` |
| `sys.number` | "eighty eight" | `sys: {number: '88'}` |
| `sys.quantity` | "3 liters" | `sys: {volume: '3', volume_unit: 'litre'}` |
| `sys.temperature` | "80C" | `sys: {temperature '80', temperature_unit: 'celsius'` |
| `sys.time` | "3 pm tomorrow" | `sys: {time: '2020-12-25T15:00:00.000+00:00', time_grain: 'hour'}` |
| `sys.url` | "[www.chatlayer.ai/jobs](https://www.chatlayer.ai/jobs)" | `sys: {url: 'www.chatlayer.ai/jobs', url_domain: 'chatlayer.ai'}` |
| `sys.duration` | "3 hours" | `sys: {duration: '3', duration_unit: 'hour', duration_normalized: '10800', duration_normalized_unit: 'second'}` |

