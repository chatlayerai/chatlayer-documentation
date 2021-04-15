# SaaS Regions & IP Ranges

The Chatlayer SaaS application is deployed in the following locations:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Region</th>
      <th style="text-align:left">Location</th>
      <th style="text-align:left">Status</th>
      <th style="text-align:left">CMS URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">EMEA</td>
      <td style="text-align:left">Belgium</td>
      <td style="text-align:left">Live</td>
      <td style="text-align:left">
        <p>Staging: <a href="https://cms.staging.chatlayer.ai/">https://cms.staging.chatlayer.ai/</a>
        </p>
        <p>Production: <a href="https://cms.chatlayer.ai

">https://cms.chatlayer.ai</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">NA + LATAM</td>
      <td style="text-align:left">East Coast USA</td>
      <td style="text-align:left">Live</td>
      <td style="text-align:left">
        <p>Staging: <a href="https://cms.staging.us-east4.gcp.chatlayer.ai/">https://cms.staging.us-east4.gcp.chatlayer.ai/</a>
        </p>
        <p>Production: <a href="https://cms.prod.us-east4.gcp.chatlayer.ai/">https://cms.prod.us-east4.gcp.chatlayer.ai/</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">India</td>
      <td style="text-align:left">India</td>
      <td style="text-align:left">Forthcoming</td>
      <td style="text-align:left">Planned for Q2 2021</td>
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
      <td style="text-align:left">Staging EU</td>
      <td style="text-align:left">
        <p>35.187.113.2/32</p>
        <p>51.124.69.196/31</p>
        <p>34.78.45.176/32</p>
      </td>
      <td style="text-align:left">
        <p>35.195.244.99/32</p>
        <p>51.124.69.196/31</p>
        <p>34.78.158.115/32</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Production EU</td>
      <td style="text-align:left">
        <p>35.205.75.142/32</p>
        <p>52.155.165.92/30</p>
        <p>51.124.69.116/30</p>
        <p>34.78.45.176/32</p>
      </td>
      <td style="text-align:left">
        <p>35.195.244.99/32</p>
        <p>52.155.165.92/30</p>
        <p>51.124.69.116/30</p>
        <p>34.78.158.115/32</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Staging US</td>
      <td style="text-align:left">
        <p>34.86.117.221/32</p>
        <p>35.245.65.209/32</p>
      </td>
      <td style="text-align:left">
        <p>35.236.193.49/32</p>
        <p>35.245.212.205/32</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Production US</td>
      <td style="text-align:left">
        <p>34.86.117.221/32</p>
        <p>35.245.65.209/32</p>
      </td>
      <td style="text-align:left">
        <p>35.236.193.49/32</p>
        <p>35.245.212.205/32</p>
      </td>
    </tr>
  </tbody>
</table>



