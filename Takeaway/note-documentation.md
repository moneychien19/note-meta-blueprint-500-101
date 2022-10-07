# Notes for Meta Pixel Documentation

## Introduction
The Meta Pixel can collect the following data:

- Http Headers – Anything present in HTTP headers. HTTP Headers are a standard web protocol sent between any browser request and any server on the internet. HTTP Headers include **IP addresses**, information about the **web browser**, **page location**, **document**, **referrer** and **person using the website**.
- Pixel-specific Data – Includes **Pixel ID** and the **Facebook Cookie**.
- Button Click Data – Any buttons clicked by site visitors, the labels of those buttons and any pages visited as a result of the button clicks.
- Optional Values – Developers and marketers can optionally choose to send additional information about the visit through Custom Data events
- Form Field Names – Includes website field names like email, address, quantity, etc., for when you purchase a product or service. The field values are captured only when you include them as part of **Advanced Matching** or optional values.

## Get Started
In order to implement the Pixel, you will need:
- access to your website's code base.
- your Pixel's base code or its ID.
- access to the Facebook Ads Manager.

### Base Code
- When run, the base code will download a library of functions which you can then **use for conversion tracking**. It also automatically tracks a single `PageView` conversion by calling the fbq() function each time it loads.
- Recommend to add the base code between `<head>` tags on every page where you will be tracking website visitor actions. To do so,
  - it **reduces** the chances of browsers or third-party **code blocking** the Pixel's execution.
  - it executes the code sooner, **increasing the chance** that your visitors **are tracked** before they leave your page.

### Conversion Tracking
- Standard events
  - **Predefined visitor actions** that correspond to common conversion-related activities, such as searching for a product, viewing a product, or purchasing a product.
  - **Support parameters** such as product IDs, categories, and the number of products purchased.
  - See [full list of standard events](https://developers.facebook.com/docs/meta-pixel/reference#standard-events).
  - Use `fbq('track')` anywhere in your website **between `<body>` tags** to track standard events.
- Custom events
  - **Self-defined visitor actions.**
  - **Support parameters**.
  - Use `fbq('track')` anywhere in your website **between `<body>` tags** to track standard events.
  - Custom events' name are limited in 50 characters.
- Custom Conversions
  - The default `PageView` event record the **referrer URL** of the page. Therefore you can setup a custom conversions that tracks website visitors who have viewed a specific URL.
  - Once tracked, custom conversions can be used to **optimize** your ad campaigns, to **define custom audiences**, and to **further refine custom audiences** that rely on standard or custom events.
  - Create custom conversions in Events Manager.
  - The maximum number of custom conversions **per ad account** is **100**.
- Parameters
  - [Here](https://developers.facebook.com/docs/meta-pixel/reference#object-properties) are predefined parameters supported in standard events.
  - Custom parameters can be used in both standard and custom events.