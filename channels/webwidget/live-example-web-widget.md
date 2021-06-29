# Live example web widget

We've created an example of how you can initialize and destroy the Chatlayer.ai chat widget through your own Javascript code.

```markup
<html>
  <head>
    <title>Chatlayer Events Example</title>
    <meta charset="UTF-8" />
  </head>

  <body>
    <button onclick="initChatlayer()">Initialize Chatlayer</button>
    <button onclick="destroyChatlayer()">Destroy Chatlayer</button>
    <br />
    <br />
    <button onclick="openChatlayer()">Open Chatlayer Widget</button>
    <button onclick="closeChatlayer()">Close Chatlayer Widget</button>

    <script>
      /**
       * This example showcases the destruction of a Chatlayer webwidget
       * by triggering the JSON builder plugin in the flow.
       *
       * The JSON builder action dialog was set up as follows:
       * https://minio.dev.chatlayer.ai/public/JSONBuilder.png
       *
       */

      let chatlayerInstance = null;

      const initChatlayer = () => {
        if (chatlayerInstance) return;
        console.log("Initializing the Chatlayer widget ...");
        chatlayerInstance = chatlayer({ lang: "en" });
        // Event types are "event", "open" and "close"

        chatlayerInstance.on("open", event => {
          console.log('OPENED');
        });

        chatlayerInstance.on("close", event => {
          console.log('CLOSED')
        });

        chatlayerInstance.on("event", event => {
          // Note the content of event here: the "action" key with value "destroy"
          // originates directly from the configured JSON Builder action.
          const isChatlayerDestroyEvent = event.action === "destroy";
          if (isChatlayerDestroyEvent) {
            destroyChatlayer();
          }
        });
      };

      const destroyChatlayer = () => {
        if (!chatlayerInstance) return;
        console.log("Destroying the Chatlayer widget ...");
        // To destroy the widget, it has to be opened first
        chatlayerInstance.open();
        chatlayerInstance.destroy();
        chatlayerInstance = null;
      };

      const openChatlayer = () => {
        if (!chatlayerInstance) {
          console.log("Please initialize Chatlayer first!");
          return;
        }
        chatlayerInstance.open();
      };

      const closeChatlayer = () => {
        if (!chatlayerInstance) {
          console.log("Please initialize Chatlayer first!");
          return;
        }
        chatlayerInstance.close();
      };
    </script>

    <!-- Note the absence of the onload prop on the following script tag. -->
    <!-- To automatically initialize the webwidget, you would add the prop: -->
    <!-- onload="initChatlayer()" -->
    <script
      src="https://chatbox.staging.chatlayer.ai/sdk/5ecbcf1514c3dc4942f05f96"
      async
    ></script>
  </body>
</html>
```

JSON builder plugin configuration:

![](../../.gitbook/assets/image%20%28267%29.png)

{% hint style="info" %}
View a live version of this code [here](https://codesandbox.io/s/chatlayer-destroy-webwidget-s0lnj?file=/index.html).
{% endhint %}

As you can see from the example above, you can initialize the widget, open/close it, as well as destroy it from your own code. The example shows you how to use the JSON Builder plugin to trigger a destroy event for the chat widget.

