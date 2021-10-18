# Create a web widget demo page

This guide will explain to you how to set up a custom demo page to showcase your chatbot as seen in this example: [https://banking-bot-demo.glitch.me/](https://banking-bot-demo.glitch.me). This can be done using Glitch, where you can create apps in your browser for free.

## 1. Create a web widget in Chatlayer

Create a web widget with the configuration of your liking via Channels. Read more about that [here](https://docs.chatlayer.ai/channels/webwidget#creating-your-web-chat-widget).

## 2. Create account on Glitch

Create an account on [glitch.com](http://www.glitch.com). 

Create a new project and name it the way you want your link to be shown: 

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LLTwFwbOqJj4dDhg8Ju%2Fuploads%2FpoCWsn3ZrKa5HTTK9GAL%2Ffile.png?alt=media)

## 3. Create html page

Now click on the Index.html page in the left column. There, paste the following block of code between the two lines. 

Pay close attention to:

* Line 97: Use the link of the web widget in Chatlayer there

![](<../.gitbook/assets/image (410).png>)

* Replace 'onload='chatlayer()'' with 'onload="initChatlayer()'
* Line 92: Please enter the name of your glitch web page here
* Line 81: If you want to change the background colour of the web page, you can do so by entering the [HEX colour code](https://www.color-hex.com) 

```markup
 <!DOCTYPE html> 
<html lang="en"> 
  <head> 
    <title>Chatlayer x Sinch</title> 
    <meta charset="utf-8" /> 
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <meta name="viewport" content="width=device-width, initial-scale=1" /> 

    <style> 
      #chatlayer-iframe-wrapper { 
        margin-top: 40px; 
        flex: 1; 
        display: flex; 
        flex-direction: column; 
        min-width: 100%; 
        margin-bottom: 40px; 

      } 

       
      #chatlayer-iframe-wrapper .chatlayer-iframe { 
        flex: 1; 
        border: 1px solid #F0F0F0 !important; 
        box-shadow: 0px 20px 20px -15px rgba(20,20,20,0.1) !important; 
      } 
       
      iframe .chatBalloon-bot { 
        border-radius: 5px 5px 5px 0px!important; 
      } 

  
      #chatlayer-wrapper { 
        flex: 1; 
        padding: 40px; 
        display: flex; 
        flex-direction: column; 
        position: relative; 
        justify-content: center; 
        align-items: center; 
        margin: 0 auto; 
        width: 50%; 
        max-width: 600px; 
      } 

      .sinch-logo svg { 
        fill: white; 
        height: 40px; 
      } 

  

      .chatlayer-chatbox-wrapper { 
        box-sizing: border-box; 
        position: fixed; 
        top: 0px; 
        left: 0px; 
        min-width: 100vh; 
        min-height: 100vh; 
      } 

      iframe.chatlayer-iframe { 
        width: 100%; 
        font-family: arial!important 
      } 

       

      iframe.chatlayer-iframe html * { 
        font-family: Helvetica !important; 
      } 

      html { 
        height: 100vh; 
        width: 100vw; 
      } 

      body { 
        min-height: 100vh; 
        display: flex; 
        flex-direction: column; 
        background: #f8f8f8; 

      } 

    </style> 
    
    <script> 

    function initChatlayer() { 
      var time = (new Date()).getTime(); 
      console.log(time) 
      var cl = chatlayer({ "autoOpen": "true", "lang":"en", wrapper: document.querySelector("#chatlayer-iframe-wrapper"), sessionId: `YOUR NAME-demo.glitch.me.${time}` }) 
      cl.open(); 
    } 

    </script> 
    <script src="Please enter the SDK link you’ve copied from the chat widget on the Chatlayer platform here " onload="chatlayer()" async></script> 
  </head> 

  <body> 

    <div id="chatlayer-wrapper"> 
      <div id="chatlayer-iframe-wrapper"> 
               </div> 
    </div> 
    <div style="display:flex;flex-direction:colum;justify-content: center;"> 
   </div> 

  </body> 

</html> 

-------------------
```

Now check your website by clicking on ‘Show’ and then ‘In a New Window’ (see left top corner) 

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LLTwFwbOqJj4dDhg8Ju%2Fuploads%2F7D542SghUCqAwxvo3GRJ%2Ffile.png?alt=media)

And there you go! A quick and easy page to show off your amazing bot!
