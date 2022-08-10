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

Note that **dynamic ads can only you standard events**.

### Implementation
1. Go to `Event Manager(事件管理工具)` > `Custom Conversion(自訂轉換)` > `Create(建立)`
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
- **Diagnostics (問題診斷) tab**

### Developer Tools