# Entities

Entities are important pieces of information that are extracted from an expression. You want to store these entities in a variable so you can re-use them later on.

## Types of entities

There are four types of entities:

* **Match entity:** if the user says a word that is in a list or matches a certain pattern, the entity is detected
  * For example: I want to know more about the **Premium** pack: _@product:_ Premium
* **Contextual entity:** train your NLP to recognize entities that depend on the context of the sentence
  * For example: Book a train ticket from **Brussels** to **Amsterdam**: _@origin:_ Brussels, _@destination:_ Amsterdam
* **System entity:** pre-built entities for common use cases that are extracted automatically
  * For example: My e-mail address is **ilovebots@chatlayer.ai**: _@sys.email_: ilovebots@chatlayer.ai
* **Composite entity:** a set of different but related entities combined into one
  * For example: **Two** **fries** please: _@order_ consists of _@sys.number:_ 2 and _@foodItem_: fries

### When to use which entity type

Use the following flowchart to find out which type of entity best fits your use case:

![](../../.gitbook/assets/image%20%28347%29.png)

{% hint style="warning" %}
Entities of all types are only detected after you have pressed the "Update NLP" at least once.
{% endhint %}

## Match entities

Match entities is an entity type that is detected when the user says a word that is in a list or matches a certain pattern.

### Match text

Add a list of possible entity values for an entity. If a user mentions one of these words during their conversation with the bot, that word will be saved as an entity.

For example: you have defined @product as a match entity, and have provided 4 possible values. When a user says "I want to know more about the **Premium** pack", the entity @product will be saved, with the value "Premium".

#### Synonyms

For each value, you can add a synonym that will be converted to the original value

Synonyms allow you to add alternatives to entities that are assigned to the same value.   
For example:

`I want to go to Brussels`

`I want to go to Bruxelles`

The meaning of these two expressions is exactly the same, but you want to convert `Bruxelles` to `Brussels` so your bot can work with one and the same value.

![](../../.gitbook/assets/image%20%28348%29.png)

### Match pattern

Use a pattern to extract some data out of the user's expression if it matches a particular format. Patterns are formed as regular expressions \(Python style\). You can learn about how to create a regular expression and test your regular expressions [here](https://regex101.com/).

For example: you have defined @customerID as a match entity, and have provided the following regex pattern: \[a-z\]{5}\[0-9\]{2}. This means that when a users says "My customer ID is **terwf33**", which consists of 5 letters and 2 numbers, it is saved as @customerID with value "terwf33".

## Contextual entities

Contextual entities use machine learning to identify entities in your sentence by learning which type of word your entity is, where in the sentence it's placed and what the specific context is.

[Synonyms](synonym-entities.md#synonyms) can also be added for contextual entities.

### Fuzzy matching for contextual entities

Fuzzy matching allows you to recognize a slight variation of a synonym or entity value as the original value. For example "Brusselt" will be corrected to "Brussels".

![](../../.gitbook/assets/image%20%28346%29.png)

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

## Composite entities



