# Making SOAP requests

You can use the [API Action](../custom-back-end-integrations/#api-plugin) to make REST-based API calls. If the API you're integrating with is SOAP-based, the[ Code Editor](./) is the tool for you. 

### Example

The following is an example of how you can leverage the [fetch ](./#fetch)library embedded in the Code Editor runtime to perform SOAP requests. The example uses an open API that 

The `input`  variable should contain any stringified number, like "500". We build the XML body through a [template literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals?retiredLocale=nl) and substitute the input value. We then extract the response value through Regex. The output message in the chat will then contain the number as words, "five hundred" in the case of our example.

```javascript
// We make use of the following public API
// https://documenter.getpostman.com/view/8854915/Szf26WHn

const { input } = args;

const url = "https://www.dataaccess.com/webservicesserver/NumberConversion.wso";

// The request body
const body = `<?xml version="1.0" encoding="utf-8"?>
  <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
      <NumberToWords xmlns="http://www.dataaccess.com/webservicesserver/">
        <ubiNum>${input}</ubiNum>
      </NumberToWords>
    </soap:Body>
  </soap:Envelope>
`;

const headers = {
  // Additional headers may be required
  // dpending on your server implementation
  "Content-Type": "text/xml; charset=utf-8",
};

const options = { method: "POST", headers, body };

const chatlayer = ChatlayerResponseBuilder();

try {
  // Perform the request to the SOAP api
  const response = await fetch(url, options);
  
  // Extract the text value from the response
  const xmlResponse = await response.text();
  
  // Build and match the RegExp to extract data from the response
  const regExp = new RegExp(
    "<m:NumberToWordsResult>(.*?)</m:NumberToWordsResult>"
  );
  const match = xmlResponse.match(regExp);
  if (!match) {
    throw new Error("Could not find the given number");
  }
  const result = match[1];
  chatlayer.addMessage(result);
} catch (ex) {
  chatlayer.addMessage(ex.toString());
} finally {
  chatlayer.send();
}
```







