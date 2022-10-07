# Technical Pixel Implementation

# Introduction
The Facebook pixel is a small piece of code on your website that functions as an analytics tool. It **measures the actions** people take on your website and **determine the effectiveness** of your advertising. It works across mobile and desktop web-based environments.
>Pixel can't work on apps.

When a customer visits your website, they leave clues based on their behavior. If you have the pixel installed, you can turn those key behaviors, also called signals of intent, into **conversions**.

## Privacy Machanisms
### General Data Protection Regulation (GDPR)
Creates consistent data protection rules across **Europe**. It applies to companies who process personal data about individuals in the EU regardless of where they're based.
### California Consumer Privacy Act (CCPA)
Enhances privacy rights and consumer protection for California residents. It applies to companies who process personal data about individuals in the state of **California**, regardless of where the company is based. 

## Tools and Solutions of Pixels
- Dynamic ads: capture customer activities.
- Value optimization: predict purchase value.
- Custom audiences: reach specific audiences.
- Conversions tracking: identify the devices your audiences use.
- Conversion optimization: reach people likely to convert.
- Conversion lift: test the effectiveness of your advertising.

## Key Knowledge
- Use cases that the Facebook pixel covers.
- Tools of pixels.

# Pixel Implementation
## Implementation
1. Create a pixel in Business Manager
	1. Go to Events Manager.
	2. Select **Connect Data sources (連結資料來源)** and choose **Web (網站)**.
	3. Add your pixel name.
	4. Add your website URL.
	5. Choose **僅使用 Meta 像素**.
	6. Select **Install Code Manually (手動設定)**, then the pixel code will be copied to your clipboard.
2. Copy the piece of code and paste between the `<head></head>` tag.
3. Verify that pixel works correctly (usually wait up to 20 minutes).

## About the Pixel Code
The code will be like:
```html
<!-- Meta Pixel Code --> 
<script> 
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod? n.callMethod.apply(n,arguments):n.queue.push(arguments)}; 
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0'; 
  n.queue=[];t=b.createElement(e);t.async=!0; 
  t.src=v;s=b.getElementsByTagName(e)[0]; 
  s.parentNode.insertBefore(t,s)}(window, document,'script', 'https://connect.facebook.net/en_US/fbevents.js');

  // Be careful to check that pixel code is wrapped in <script> tags.
  fbq('init', '1218369535643821'); 
  fbq('track', 'PageView'); 
  
</script> 
<noscript><img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=1218369535643821&ev=PageView&noscript=1" /></noscript>
<!-- End Meta Pixel Code -->
```
- `1218369535643821`: pixel ID
- `PageView`: the default event that the pixel base code fires. This default event is particularly important if you'd like to create custom conversions. When you filter or segment upon “Traffic URLs”,  it uses the URL value that it receives from this default event.
- It can take up to 20 minutes for your pixel to become active and start working.

> Note that if you use **Shopify** for your ecommerce business, you will never need to insert pixel code in your website. Shopify has a native integration with Meta pixel.  If the pixel is also coded, the pixel will fire twice almost every time a page is loaded.

## Pixel Helper
[Facebook Pixel Helper](https://developers.facebook.com/docs/meta-pixel/support/pixel-helper), which is a Chrome extension, can help you verify that everything functions properly. Once you install this Chrome plugin, you're able to
- verify the pixel is installed on a website.
- examine events and parameters that your pixel receives.
- troubleshoot errors.

For deeper investigation, you can use DevTools (Network panel) to examine HTTP requests that pass the relevant event and parameter information to Facebook.

## Key Knowledge
- Able to generate default pixel code within Business Manager and implement it.
- Ensure the Pixel Helper can operate.

# Conversion Tracking
## Ways to Track Conversions
### Standard Event
- use to measure typical and predefined activities.
- include [predefined actions](https://developers.facebook.com/docs/facebook-pixel/reference) that Facebook recognize and support across ad products.
- common behaviors include `Search`, `ViewContent`, `AddToCart`, `Purchase`.

### Custom Event
- are actions that the list of standard events doesn't include. You can give them a unique name to represent the measured action.
- can also be used to build audiences.
- You can't use custom events for optimization or attribution unless they're **mapped to a custom conversion**.
- For example, following code create a custom event which means viewing video.
	```js
	fbq('trackCustom', 'ViewVideo');
	```

### Custom Conversions
- use to measure very specific customer activity.
- two ways to create custom conversions:
    - **URL-based custom conversions**: create the conversion based on the **URL referrer** values you've captured with your PageView events.
	    - For example, create a custom conversion based on the term "shirts" such as `https://shop.com/shirts/red`.
    - **event-based custom conversions**: create the conversion based on events that fire your pixel.
	    - For example, create a custom conversion against the `Purchase` event with price greater than 50 dollars.

> Scenario: A client wants to measure the customers that reach their order confirmation page. 
> Then there are two ways to build custom conversions:
> 1. Implement custom conversions against the order confirmation page URL.
> 2. Add Purchase tag, if they want more accurate report, they can add parameters.

### Determine Conversion Tracking Method
| | Definition | Optimization | Attribution |
|-|-|-|-|
| Standard Events | Predefined actions that products across Facebook recognize | O | X |
| Custom Events | User-defined events beyond the predefined standard events | X | X |
| Custom Conversions | User-defined conversion based on recorded URLs or events from the pixel | O | O |
- Optimization: You can tell Facebook to optimize standard events or custom conversions. For example, optimize against `Purchase` standard event, then Facebook will find people most likely to do the purchase.
- Attribution: You can see statistics for this event directly in Ads Manager when they run campaigns.

## Event Configurations
With the impact of iOS 14.5+, you can only use **eight conversion events for campaign optimization**.
- impacted
    - standard events
    - custom conversions created from the same standard event with different parameters
    - custom conversions formed using custom event
- not impacted
    - page views
    - link clicks
    - landing page views
    - events not configured in the top eight events

## Domain Verification
[Verification](https://developers.facebook.com/docs/sharing/domain-verification) enables you to establish authority over that domain above other organizations that placed their pixel on your domain.

## Aggregated Event Measurement
In the event manager > pixel, there is a tab `Aggregated Event Measurement(彙總事件成效衡量)`, contains a list of the top eight events that Facebook automatically configures based on your previous activity.

Click `Configure Web Event(設定網站事件)` will lead to a list of domains that you own and events that are automatically configured for each domain.

If you want to change the events automatically configured for you by Facebook, you can select `Edit Events(管理事件)` to update, add or rank the prioritization of your events for optimization.

## Key Knowledge
- Apply each event or conversion type based on the needs of your business.

# Events and Parameters

While implementing events, those functions should be placed between `<body></body>` tags of your website. They can be called either when the page loads or when a visitor completes an **action**, such as the click or tap of a button or visits to key pages along the marketing funnel.

> For example, an ecommerce advertiser wants to start firing a pixel event when the user clicks `Add To Cart` button. The advertiser has already initialized the pixel code in this page and has been sending the PageView event. 
>
> Then the developer can write function as button's onClick event like this to start sending the `Add To Cart` pixel event.
> ```
> <button 
>   id="addToCartButton"
>   onClick="fbq('track', 'AddToCart', {currency: "USD", value: 30})">
>   Add To Cart
> </button>
> ```

## Standard Events
With standard events, you are able to
- attribute: see in Ads Manager how many times the system measures behavior.
- optimize: encourage specific marketing outcomes against a particular behavior.
- create custom audiences.

Note that with the impact of iOS 14.5+, you can only use eight conversion events for campaign optimization. Facebook will initially configure the conversion events we believe are the most relevant to your business based on your activity.

### Code
```js
fbq('init', '1234567890');
fbq('track', 'PageView');
fbq('track', 'AddToCart');
fbq('track', 'ViewContent'); 
fbq('track', 'AddToWishlist');
```

### Customer Journey
Key behaviors that an ecommerce website typically sees by relevant standard events are

`Search` → `ViewContent` → `AddToWishList` → `AddToCart` → `InitiateCheckout` → `AddPaymentInfo` → `Purchase`, 

and standard events can track along the journey if you add them in your pixel code.

## Custom Events
When possible, use the standard events. If they're not suitable for your needs though, you can track your own custom events.
```js
fbq('init', '1234567890');
fbq('trackCustom', 'OpenFAQ');
```
Note that name of custom event should not longer than 50 characters.

## Parameters
### Predefined Parameters
**Standard events** support [predefined parameter objects](https://developers.facebook.com/docs/facebook-pixel/reference#object-properties) with specific object properties. Once tracked, you can use parameters to further define any Custom Audiences you create.

**Custom events don't have predefined parameters** by definition. You can include any parameter in a custom event, but it doesn't aggregate or apply, nor is it as useful as a standard event.

To include a parameter object with a standard or custom event, format it as a JSON object, and include parameters as the third parameter when calling `fbq('track')` or `fbq('trackCustom')`.
```jsx
// call to track when a visitor has completed a Purchase event,
// with currency and value included as parameters
fbq('track', 'Purchase', { currency: "USD", value: 30.00 });

// call to track when a visitor has the specific search behavior
fbq('track', 'Search', {
	search_string: "red shoes",
	content_ids: ["1","6","9"], 
	content_type: "product"
});
```

### Custom Parameters
Custom properties work with **both standard and custom events**, and they can help you further define Custom Audiences.
```js
// standard event, customize appointment type and city as parameters
fbq('track', 'Schedule', { appointment_type: "glasses", city: "New York" });

// custom event, customize promotion as parameter
fbq('trackCustom', 'ShareDiscount', { promotion: 'share_discount_10' });
```

## Multiple Pixels
You can initialize multiple pixels on one page for subsequent use.

When there's a possibility that multiple pixels might interact on your page, you should use the `fbq('trackSingle')` or `fbq('trackSingleCustom')` and specify the pixel ID within it to yield accurate tracking.

> Scenario: If there are two pixels in one page and the code looks like
> ```js
> fbq('init', '1234');
> fbq('track', 'PageView');
> fbq('init', '5678');
> fbq('track', 'Purchase');
> ```
>
> Then the real behavior of pixels is: Pixel 1234 receives a PageView event. Both pixels receive a Purchase event.
>
> The code can be fixed by using
> ```js
> fbq('init', '1234');
> fbq('init', '5678');
> fbq('track', 'PageView');
> fbq('trackSingle', '5678', 'Purchase');
> ```