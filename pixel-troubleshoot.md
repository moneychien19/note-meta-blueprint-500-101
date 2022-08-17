# Optimize and Troubleshoot the Pixel

# Custom Conversions
## Custom Conversions Using URL Rules
You can set up a URL rule that contains a specific keyword.

For example, if the keyword is "flashsale", then you can track when people land on `https://windandwool.com/flashsale` or `https://windandwool.com/flashsale/shirts` since they both contain keyword "flashsale".

### Implementation
1. Go to `Event Manager(事件管理工具)` > `Custom Conversion(自訂轉換)` > `Create(建立)`.
2. Choose data source.
3. Choose `conversion event(事件)` to **All Traffic (所有流量)**.
4. Also you can choose event if you want, otherwise Facebook will choose it for you.
5. In the `Rules(規則)` section, you can either choose `URL equals` a specific URL or `URL contains` a keyword.

## Custom Conversions Using Event Rules
There are some reasons why you may use custom conversions:
- Filter events.
- Optimize ad delivery.
- You can choose to share one specific custom conversion instead of entire data source.

Note that **dynamic ads can only use standard events**.

### Implementation
1. Go to `Event Manager(事件管理工具)` > `Custom Conversion(自訂轉換)` > `Create(建立)`.
2. Choose data source.
3. Choose `conversion event(事件)` to a **specific event**.
4. Also you can choose event if you want, otherwise Facebook will choose it for you.
5. In the `Rules(規則)` section, you can set parameters and their values.

The effect of the setup in Event Manager is the same as using code such as
```js
fbq('track', 'Purchase', { value: 40.00 });
```

# Troubleshoot the Pixel
## Troubleshoot Tools
### Pixel Helper
The Facebook pixel helper is one of the most effective and fastest ways to get **immediate feedback** on your pixel implementation.

### Event Manager
Events Manager enables you to see what events and parameters are currently passing in from your pixel, but there's often a **lag of up to 20 minutes** for our system to receive data.
- In the **diagnostics (問題診斷) tab**, we can review diagnostic messages and the solution section of each message.
- Common Pixel Errors
	- invalid currency code
		- error message
		```
		Error (“British Pound”)”: fbq('track', 'Purchase', {'value': 4, 'currency': 'British Pound' });
		```
		- troubleshoot: the currency code for an event is formatted incorrectly
		- solution
		```js
		fbq('track', 'Purchase', { 'value': 4, 'currency': 'GBP' });
		```
	- event name mismatch
		- error message
		```
		Error (“purchase”): fbq('track', 'purchase', { 'value': 4, 'currency': 'USD' });
		```
		- troubleshoot: your standard events is not identical to one of the standard events
		- solution
		```js
		fbq('track', 'Purchase', { 'value': 4, 'currency': 'USD' });
		```
	- invalid value parameter/missing value parameter or missing currency parameter
		- error message
		```
		Error (blank value): fbq('track', 'purchase', { 'value': '', 'currency': 'USD' });
		```
		- troubleshoot: a value or currency parameter is empty or missing for an event, or the value or currency parameter is formatted incorrectly
		- solution
		```js
		fbq('track', 'Purchase', { 'value': 4, 'currency': 'USD' });
		```

### Chrome DevTools
In the **Network tab**, type `facebook.com/tr` or your pixel ID in the filter box to examine all tracking calls sent to Facebook servers.

For example, if you find that the events on their page fire more than once, you can go and check the **Initiator** of those requests. 

## GTM Pixel Implementation
**Google Tag Manaer (GTM)** is a tool for integrating campaigns. However, it can only verify if an event code executes based on the specific trigger. It doesn't verify the existence of a corresponding outgoing HTTP call or even whether the code fully executes to make the resulting call.

## Key Knowledge
- Check parameters of pixel code to troubleshoot.