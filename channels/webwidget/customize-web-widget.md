# Customize web widget

There are several options to customize the web widget on your website. Some changes need to be done within the chat widget, and some of them in de code of your website. Check out the examples below for some inspiration how to customize the web widget to your brand.

## Change width / height of chat window

You can change the width / height of your widget in the wrapper on your website:

```css
body .chatlayer-chatbox-wrapper{
 width: 350px;
 max-width: 100%;
 max-height: 560px;
}
```

## Web widget overlay

If you are experiencing that your website is on top of the web widget, and the web widget is not correctly visible, you can change this with the z-index:

* If you remove the 'z-index' css property for that HTML element which is overlapping the widget, the widget should not be hidden behind that element anymore.
* Alternatively, you could pass an HTML element as an option to our SDK, that HTML element will then be used as a container to show the chat widget in. An example for using a wrapper element, assuming your webpage contains an HTML element with id 'chatlayer-sdk-wrapper': 

```markup
<script src=“YOUR_CHATBOX_URL" onload=‘chatlayer({ wrapper: document.querySelector('#chatlayer-sdk-wrapper') })’ async></script>
```

This will allow you to apply css to the '\#chatlayer-sdk-wrapper' directly for positioning it on your page, instead of using our default wrapper.

## Border chat balloon

You can style the balloon with an extra border in the colour of your choice by using the following in the custom CSS \(only available for Enterprise and Corporate customers\) in your chat widget:

```css
.chatBalloon-user{
 border: 1px solid red;
}
```

## Center send button

In your custom CSS you can upload the following code to center the send button:

```css
.ChatInputContainer{
 display: flex;
 align-items: center;
}
```

## Open widget automatically

The web widget is opened when clicked on, but can also open automatically. This can be changed in the HTML of your webpage. In the example below, the chatbot opens every 10 seconds:

```markup
<script>
 const initChatlayer = () => {
 const chatlayerInstance = chatlayer();
 chatlayerInstance.open();

 setInterval(()=>{
      chatlayerInstance.open();
 }, 10000)
  }

</script>
<script src="<YOUR_SDK_URL>" referrerpolicy="no-referrer-when-downgrade" onload='initChatlayer()' async></script>
```

Change `YOUR SDK URL` with the SDK URL, as described [here](https://docs.chatlayer.ai/channels/webwidget#embedding-the-web-widget-on-your-website). 

## Custom CSS

To make your Chat Widget look customized as per your needs, our Enterprise and Corporate clients can upload their own CSS. Please see the following list of CSS classes that you can use to customize your Web Widget:

* ChatTitle
* ChatTitleBar
* ChatTitleImage
* wrapper
* BotImage
* userImage
* container
* chatBalloon-default
* chatBalloon-user
* chatBalloon-bot
* chatBalloon-agent
* ChatInputContainer
* ChatInputText-container
* ChatInputText-textarea
* chatQuickReplies-container
* buttons-image
* buttons-textimage
* buttons-default
* chatTemplate-buttonTemplate-container
* chatTemplate-buttonTemplate-buttons-default
* chatTemplate-buttonTemplate-buttons-unknown
* chatTemplate-buttonTemplate-buttons-header
* chatTemplate-listTemplate-button
* chatTemplate-listTemplate-container
* chatTemplate-element-container
* chatTemplate-element-column
* chatTemplate-element-image
* chatTemplate-element-title
* chatTemplate-element-subtitle
* chatTemplate-element-button
* chatTemplate-chatImage-container
* chatTemplate-chatVideo-container
* chatTemplate-chatAudio-container
* chatTemplate-chatClarousel-element-container
* chatTemplate-chatCarousel-element-image
* chatTemplate-chatCarousel-element-title
* chatTemplate-chatCarousel-element-subtitle
* chatTemplate-chatCarousel-element-button
* chatTemplate-chatCarousel-element-prevButton
* chatTemplate-chatCarousel-element-prevButtonIcon
* chatTemplate-chatCarousel-element-nextButton
* chatTemplate-chatCarousel-element-nextButtonIcon



