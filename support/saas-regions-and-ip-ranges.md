# SaaS Regions & IP Ranges

![](../.gitbook/assets/worldmap-datacenters-updated.png)

The Chatlayer SaaS application has environments deployed in the following locations:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Region</th>
      <th style="text-align:left">Location</th>
      <th style="text-align:left">Cloud Provider</th>
      <th style="text-align:left">Status</th>
      <th style="text-align:left">App URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">EU</td>
      <td style="text-align:left">
        <p></p>
        <p>St. Ghislain, Belgium, Europe</p>
      </td>
      <td style="text-align:left">
        <p>GCP</p>
        <p>(eu-west1)</p>
      </td>
      <td style="text-align:left">Live</td>
      <td style="text-align:left"><a href="https://app.chatlayer.ai/">https://app.chatlayer.ai/</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">US</td>
      <td style="text-align:left">Ashburn, Virginia, North America</td>
      <td style="text-align:left">
        <p>GCP</p>
        <p>(us-east4-a)</p>
      </td>
      <td style="text-align:left">Live</td>
      <td style="text-align:left"><a href="https://app.us-east4.gcp.chatlayer.ai">https://app.us-east4.gcp.chatlayer.ai/</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">India</td>
      <td style="text-align:left">Mumbai, India APAC</td>
      <td style="text-align:left">
        <p>GCP
          <br />(asia-south1)</p>
        <p></p>
      </td>
      <td style="text-align:left">Live</td>
      <td style="text-align:left"><a href="https://app.asia-south1.gcp.chatlayer.ai/">https://app.asia-south1.gcp.chatlayer.ai/</a>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
If you would like to switch your bots from one location to another, please [Get in Touch](get-in-touch.md) with us.
{% endhint %}

### IP's to be whitelisted <a id="To-be-whitelisted-by-customers"></a>

If you're connecting your bot to internal systems that require whitelisting, please whitelist the following IP addresses.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Environment</th>
      <th style="text-align:left">ingress</th>
      <th style="text-align:left">egress</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">EU</td>
      <td style="text-align:left">34.78.45.176/32</td>
      <td style="text-align:left">
        <p>34.78.158.115/32</p>
        <p>23.251.136.162/32</p>
        <p>34.140.169.192/32</p>
        <p>34.76.255.244/32</p>
        <p>34.140.104.91/32</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">US</td>
      <td style="text-align:left">
        <p>34.86.117.221/32</p>
        <p>35.245.65.209/32</p>
      </td>
      <td style="text-align:left">
        <p>35.236.193.49/32</p>
        <p>35.245.212.205/32</p>
        <p>34.145.223.151/32</p>
        <p>34.85.204.75/32</p>
        <p>35.245.164.149/32</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">India</td>
      <td style="text-align:left">
        <p>35.200.129.64/32</p>
        <p>35.200.132.180/32</p>
      </td>
      <td style="text-align:left">
        <p>35.244.41.108/32</p>
        <p>34.93.181.152/32</p>
        <p>34.93.184.224/32</p>
        <p>35.244.23.10/32</p>
        <p>34.93.140.182/32</p>
      </td>
    </tr>
  </tbody>
</table>

### Security & certification

Chatlayer is ISO 27001 certified. You can read more about our security policies on [this page](https://chatlayer.ai/security/).

![](../.gitbook/assets/image%20%28572%29.png)

