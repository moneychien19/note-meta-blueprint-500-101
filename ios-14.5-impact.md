# Impact of iOS 14.5+ on Certified Marketing Developer Collection 

A quick overview of iOS 14.5+ updates that may impact content in the Certified Marketing Developer Collection.

## Pixel
### Domain Verification
- As best practice, all businesses should [verify their domain](https://developers.facebook.com/docs/sharing/domain-verification).
- Especially if you have multiple pixels that belong to multiple businesses or personal ad accounts, verify your domain.
- Complete domain verification before you update your event configuration.

### Conversion Events for Optimization
- With the enforcement of the **ATT prompt**, you can only use **eight conversion events for campaign optimization**.
- Facebook **prioritizes** the eight conversion events by default based on your business activity.
- The limitation affect standard events and custom conversions, but doesn't affect `PageView`, link clicks and landing page views.
- In Events Manager, you can
  - view a list of the top eight events that facebook automatically configures.
  - view a list of domains that you own and events that are automatically configured for each domain.
  - update, add or rank the prioritization of your events for optimization.

## Advanced Matching
- Advanced matching can only be used if people with **iOS 14.5+** devices **opt in to tracking** at the Apple prompt on the Facebook or Instagram app on that device.
- For people on iOS 14.5+ devices, we can’t use hashed customer data from advanced matching on people who opted out of the Apple prompt on Facebook or Instagram. For **opted-out events**, we can only receive **limited information** consistent with Aggregated Event Measurement.

## Catalog & Dynamic Ads
As a result of iOS 14.5 changes, certain kinds of data collection are prohibit unless people opt into tracking on iOS 14.5+ devices. This also means that the size of your **retargeting audiences may decrease**.

### One Pixel Per Catalog and Domain
If possible, use only one pixel per catalog and domain for the accuracy reason.

### Dynamic Ads Event Configuration
- It **isn't necessary to include `ViewContent`, `AddToCart` and `Purchase` in the top eight events** for dynamic ads to function. Continue to send these events through the pixel to help ensure dynamic ads can use them for people on non-iOS 14.5+ devices and for people on iOS 14.5+ devices who opted into Facebook or Instagram.

### Tips for Multiple Pixels or Domains
| Multiple Pixels | Multiple Domains |
| - | - |
| Confirm each pixel is installed to the domain and linked to the catalog. | For each domain you use as a product URL, ensure that the associated conversion event is one of your eight prioritized events. |
