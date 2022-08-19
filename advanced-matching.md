# Advanced Matching for Websites

# Introduction
Advanced matching can help you optimize your Facebook ads to produce better results. With advanced matching for websites, you can send Facebook **hashed customer information** along with your pixel events, which can help you **attribute more conversions** and reach more people.

You can only use advanced matching if people with **iOS 14.5+** devices **opt-in** on the Facebook or Instagram app on that device.

The process is as follow:
1. Capture hashed customer information, such as email addresses, that businesses collect from their website during checkout, account login, registration.
2. Transform the information into an indecipherable format through hashing.
3. Once Facebook receives that hashed data and the event, the system tries to match both with a customer.

## Value of Advanced Matching
- Help you understand the impact your ads have on website conversions.
- Increase your Custom Audience size.
- Enable you to deliver ads to the types of people who are likely to take the actions you want, which helps **conversion-optimized campaigns** operate more efficiently.

## Advanced Matching Methods
The two methods work differently, so you can use both to achieve maximum performance from advanced matching.

### Automatic Advanced Matching
Use this if
- you don't have a developer (this method doesn't require code modification).
- your website doesn't use an IMG pixel.
- your pixel isn't in an iFrame.
- your business isn't in regulated verticals such as investment banking and brokerage, insurance, financial services, retail, credit union and commercial banking, credit, financing, mortgage lending, pharmaceutical or health. 
- your business is using the Shopify platform.
- your site should have **form fields** where visitors will enter the relevant information, such as email addresses or phone numbers.

### Manual Advanced Matching
Use this if
- you can do code modification.
- your website uses an **IMG pixel**, in which case, you must manually format and hash customer information. 
- your pixel is in an **iFrame**. 
- your business is in a **regulated vertical**, which is prohibited from the use of the automatic version.

## Privacy and Transparency
Advertisers who want to use advanced matching must adhere to specific rules, terms and regulations including
- [Terms of Service 服務條款](https://www.facebook.com/terms.php)
- [Facebook Business Tools Terms 商業工具使用條款](https://www.facebook.com/legal/terms/businesstools)
- [General Data Protection Regulation (GDPR)](https://developers.facebook.com/docs/meta-pixel/implementation/gdpr)
- [California Consumer Privacy Act (CCPA)](https://developers.facebook.com/docs/marketing-apis/data-processing-options)

Note that Facebook ignores matching requests that send unhashed information values. Customer information **must be hashed** before transmission to Facebook.
- When the pixel can't automatically hash customer information (for example, an IMG pixel) you have to hash the data manually before transmitting to Facebook.
- Otherwise customer information is hashed automatically in the browser. It can directly be passed to Facebook.

## How Customer Information is Hashed
In hashing process, a hash function converts data to a series of numbers and letters in a process that can't be reversed. Facebook uses one of the most advanced functions, which is called **SHA-256**.

For people on iOS 14.5+ devices, we can’t use hashed customer data from advanced matching for opted-out events. We can only receive limited information consistent with Aggregated Event Measurement for opted-out events.

## Key Knowledge
- Determine whether automatic or manual advanced matching should be applied under a given situation (ie, whether there is a developer, or whether the industry is regulated).

# Set Up Advanced Matching for Websites