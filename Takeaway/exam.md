# Exam Cheat Sheet
## Road Map
- [Business Manager](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#business-manager)
  - Tools
  - Assets
  - Access
- [Pixel](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#pixel)
  - Hash
  - Pixel Code
  - Target: standard parameters/custom parameters/custom events/custom conversions
  - Multiple Pixels
  - Impact of iOS 14.5
- [Advanced Matching](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#advanced-matching)
  - Methods: manual/automatic
  - Fields
  - Advanced Matching Code
- [Catalog and Dynamic Ads](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#catalog-and-dynamic-ads)
  - Methods: manual/bulk upload/pixel
  - Support Fields (Upload)
  - Required Events (Pixel)
- [Troubleshoot Catalog & Dynamic Ads](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#troubleshoot-catalog--dynamic-ads)
- [Troubleshoot Pixels](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#troubleshoot-pixels)
  - Common Mistakes
  - Troubleshoot Tools
- [Useful Links to Ducumentation](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/exam.md#useful-links-to-documentation)

## Business Manager
### Why Use Business Manager
- To run ads on Facebook / Instagram.
- To grant or gain access to Facebook assets.

### Tools in Business Manager
- Ad Account (廣告帳號): to purchase advertising on connected Pages or Facebook apps.
- [Ads Manager (廣告管理員)](https://business.facebook.com/adsmanager): to house all **ad accounts** and can have **25** associated users.
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/ads%20manager.png" alt="ads manager" width="500" style="marginTop: 12;"/>
- [Events Manager (事件管理工具)](https://business.facebook.com/events_manager2): central view of all events (including **pixels** and **conversions**) in your website.
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/events%20manager.png" alt="events manager" width="500" style="marginTop: 12;"/>
- [Commerce Manager (商務管理工具)](https://business.facebook.com/commerce/): to manage **catalog** and **dynamic ads**.
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/commerce%20manager.png" alt="commerce manager" width="500" style="marginTop: 12;"/>

### Assets
To setup Business Manager, you must use your **personal Facebook account** instead of create a new Facebook user.
#### Pages (粉絲專頁)
- Add Pages to BM.
  - You must be an **admin on a Page** for more than **7 days**.
  - You must be **admin** in the Business Manager.
#### Pixels (像素)
- Add pixels to BM.
  - The amount is limited to **100**.
  - You must be **admin** in the BM.
- Add pixels in ad account.
  - The amount is limited to **1**.
- Once pixel is created, it cannot be deleted, it can only be repurposed.
  > What do you do with a pixel when you no longer need it? Remove the code from your website and that will make it stop sending data.
#### Ad Accounts (廣告帳號)
- Add ad accounts to BM.
  - You can add up to **25** ad accounts.
  - You can only add prepaid ad accounts to Business Managers if they're from certain locations.
  - You can't add an ad account which has already been added to another BM.
- Setup Ad Accounts
  - At least one person has been authorized to run ads.
  - Each ad account needs an associated payment method.
  - Ad account access can be shared both internally and externally.
  - Business Manager should be owned by a party.
  
### Access
- There are `people` (employee/admin), `partner`, and `system user` three types of users in BM.
  > Khadija, a marketing developer at Little Lemon, needs to share some of her assets in Business Manager with a consultant. How should Khadija add him to the Little Lemon Business Manager, so he can access these assets? Add the consultant as a partner.

- Determine what to do to gain or grant access, follow the flow chart below.
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/Flow%20Chart%20-%20BM%20access.jpg" alt="Flow Chart of BM Access" width="800" style="marginTop: 6;"/>
- Access layer
  - **First layer: asset allocation**
    - Assign `people` the role of either employee or admin.
    - For example, there are two admin of Business Manager, one can access to Ad Manager 1, whereas one can access to Ad Manager 1, 2, and 3. Just because they are both admin doesn't mean that they can both access to all assets under the Business Manager.
  - **Second layer: asset control**
    - Limit each people's access to assets.
    - Each asset are divided into two categories, **standard access** and **admin access**.
    - For example, an analyst doesn't need to manage campaigns.

## Pixel

The Meta Pixel can collect the following data:

- Http Headers – Anything present in HTTP headers. HTTP Headers are a standard web protocol sent between any browser request and any server on the internet. HTTP Headers include **IP addresses**, information about the **web browser**, **page location**, **document**, **referrer** and **person using the website**.
- Pixel-specific Data – Includes **Pixel ID** and the **Facebook Cookie**.
- Button Click Data – Any buttons clicked by site visitors, the labels of those buttons and any pages visited as a result of the button clicks.
- Optional Values – Developers and marketers can optionally choose to send additional information about the visit through Custom Data events
- Form Field Names – Includes website field names like email, address, quantity, etc., for when you purchase a product or service. The field values are captured only when you include them as part of **Advanced Matching** or optional values.

### Possible Conversion Goals
- Amount of item sold.
- Total value of item sold.
- Amount of newly registration.

### Hash
1. Data is hashed by SHA-256 before being sent to Facebook.
2. Facebook will match the hash data and their own hash data. Once they've matched, they create aggregated view of that data and pass into Events Manager.
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/hash.jpg" alt="hash process" width="800" style="marginTop: 12;"/>
3. After the match process, Facebook deletes all the individual data.

> 1. Is the data being sent to Facebook secure? Yes, it is secure by hashed.
>
> 2. When do you hash or normalize data? Always.
> - Hashing: It just depends whether you hash it manually or it's done automatically from Facebook. If you use `fbq()`, data is hashed automatically, but if you use `<img>` tags, you need to hash it.
> - Normalize: It just means follow specific formats such as removing spaces or lowercasing.
> 
> 3. Do login or financial data from the page get sent to Facebook? No.

### Pixel Code
#### Base Code
Installed on all pages to provide baseline measurement (usually with `PageView` event).
```html
<script> 
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod? n.callMethod.apply(n,arguments):n.queue.push(arguments)}; 
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0'; 
  n.queue=[];t=b.createElement(e);t.async=!0; 
  t.src=v;s=b.getElementsByTagName(e)[0]; 
  s.parentNode.insertBefore(t,s)}(window, document,'script', 'https://connect.facebook.net/en_US/fbevents.js');

  fbq('init', '{your-pixel-id}'); 
  fbq('track', 'PageView'); 
  
</script> 
<noscript><img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id={your-pixel-id}&ev=PageView&noscript=1" /></noscript>
```
- When run, the base code will download a library of functions which you can then **use for conversion tracking**. It also automatically tracks a single `PageView` conversion by calling the `fbq()` function each time it loads.
- The code is always placed within open and close **header tags**. Because
  - it **reduces** the chances of browsers or third-party **code blocking** the Pixel's execution.
  - it executes the code sooner, **increasing the chance** that your visitors **are tracked** before they leave your page.
- The code contains Javascript and no-Javascript parts.

> Should pixel be included on all pages? Yes, basic code should be included on all pages.

#### Event Code
Added to base code and used on specific page to track standard events. For example, `AddToCart`, `ViewContent` or `Purchase` event.

Other common standard events
- AddPaymentInfo, CompleteRegistration, InitiateCheckout, Lead, Search, Subscribe
- AddToWishlist, Contact, CustomizeProduct, Donate, FindLocation, Schedule, StartTrial, SubmitApplication

### Target More specifically
If you want to target more specifically, consider using **standard parameters**, **custom parameters**, **custom events**, or **URL-based custom conversion**.
#### Standard Parameters (Use This First)
[Standard parameters](https://developers.facebook.com/docs/meta-pixel/reference#object-properties) are listed in documentation.

Here are some common parameters.

| Parameter | Type | Example |
| - | - | - |
| content_type | string | must be `product` or `product_group` |
| content_ids | string[] | ['product_1', 'product_2'] |
| contents | Object[] | [{ id: 'product_1', quantity: 2 }, { id: 'product_2', quantity: 3 }] |
| currency | string | 'USD', 'GBP' |
| value | number | 19.99 |
| content_category | string | 'shoes' |

Other parameters
- content_name (string) 產品名稱
- num_items (int) 初始化結帳的項目數量
- predicted_ltv (number) 由廣告商定義之訂閱者的預測終身價值
- search_string (string) 搭配 `Search` 事件使用，使用者在搜尋中輸入的字串
- status (bool) 搭配 `CompleteRegistration` 事件使用，以顯示註冊的狀態

#### Custom Parameters (Use This Second)
By putting the details on the standard event, we can get reporting the types of people we're converting for. This can be used in the whole customer journey.

Custom parameters can be used in both standard and custom events.

#### Custom Events
By defining custom events, all stages except the final conversion stage in the journey can be used. Note that
- Custom events can't be optimized.
- Custom events' name are limited in 50 characters.

#### URL-based Custom Conversions
- The default `PageView` event record the **referrer URL** of the page. Therefore you can setup a custom conversions that tracks website visitors who have viewed a specific URL. This can be used in the final stage, that is conversion.
- Once tracked, custom conversions can be used to **optimize** your ad campaigns, to **define custom audiences**, and to **further refine custom audiences** that rely on standard or custom events.
- Custom conversions are created in Events Manager.
- The maximum number of custom conversions **per ad account** is **100**.

<img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/customer%20journey.png" alt="hash process" width="900" style="margin-top: 12;"/>

### Multiple Pixels
If there are multiple pixels in a website, use `fbq('trackSingle', '{pixel_id}', '{event_name}');` to track specific pixel.

### Impact of iOS 14.5+
With the enforcement of the **ATT(App Tracking Transparency) prompt**, you can only use eight conversion events for campaign optimization.

Go to `Events Manager > pixel`, there is a tab `Aggregated Event Measurement(彙總事件成效衡量)`, contains a list of the top eight events that Facebook automatically configures based on your previous activity. Click `Configure Web Event(設定網站事件) > Edit Events(管理事件)` to update, add or rank the prioritization of your events for optimization.

Note that to edit events, you should first **verify the domains**.

## Advanced Matching

Advanced matching helps to match users more accurately by passing additional hashed information such as email, phone, gender, or location. To do so, **custom audiences size** can be increased, and  **conversion-optimized campaigns** operate more efficiently.

### Methods
#### Automatic
- Go to Events Manager > Pixel > Setting and toggle on advanced matching parameters.
- The change will take 48 hours to see the result.
- Rules
  - JavaScript only, and must have base code already implemented on the website.
  - No iFrame.
  - Not sensitive customer businesses such as health and finance.
#### Manual
- Can use under JavaScript and **no-Javascript**, no-iFrame and **iFrame** circumstances. Can use on **regulated businesses**.
- Required developers.

### Fields
| User Data | Parameter | Format | Example |
| - | - | - | - |
| Email | em | string/hashed value | 'johnsmith@test.com' |
| Phone | ph | number | 0901119955 |
| External ID | external_id | string | '123abc' |
| First Name | fn | string with all lowercase | 'john' |
| Last Name | ln | string with all lowercase | 'smith' |
| Gender | ge | 'm' or 'f' | 'm' |
| Birthdate | db | number (yyyymmdd) | 19910526 |
| City | ct | string | 'taipei' |
| State / Province | st | string (2 letter code) | 'ca' |
| Zip or Post Code | zp | string | '94011' |
| Country | country | string (2 letter code) | 'us' |

### Advanced Matching Code Example
- Javascript
  ```js
  fbq('init', '123456789', {
    em: 'email@email.com', 
    fn: 'john', 
    ln: 'smith',
    ph: 0901119955,
    external_id: 'js123456',
    ge: 'm',
    db: 19910526,
    ct: 'menlopark',
    st: 'ca',
    zp: '94025',
    country: 'us'
  });
  ```
- Image Tag (Non-Javascript)
  ```html
  <img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=123456789&ev=Purchase&ud[em]=f3273dd18d95bc19d51d3e6356e4a679e6f13824497272a270e7bb540b0abb9d" />
  <!-- parameters should be hashed manually -->
  ``` 

## Catalog and Dynamic Ads
### Methods to Manage Catalog
#### Add manually
#### Bulk upload
There are size limits towards files to be uploaded:
- scheduled feed upload: **8GB**.
- compressed files: **30GB** when uncompressed.
- one-time file upload: **100MB**.
#### Facebook pixel
Import the details of the product automatically by scraping the data off the product page, and the scrap only happen when a visitor visits the product. Note that **if a product hasn't been viewed, it won't ever be entered the catalog.**

| | Not Change Often | Change Daily/Weekly | Change More Than Daily or Realtime |
| - | - | - | - |
| Small Inventory | Add Manually | Bulk Upload + Scheduled Feed | Facebook Pixel |
| Medium to Large Inventory | Add Manually + Bulk Upload | Bulk Upload + Scheduled Feed | Facebook Pixel |

### Support Fields (Upload)
Check [documentation](https://developers.facebook.com/docs/commerce-platform/catalog/fields) to learn required and optional fields in catalog.

#### Required Fields
| Field | Type | Example |
| - | - | - |
| id | string (limit 100 char) | 'product_1' |
| title | string (limit 150 char) | 'Blue Cotton T-Shirt' |
| description | string (limit 9999 char) | |
| availability | string | must be `in stock`, `out of stock` or `available for order` |
| condition | string | must be `new`, `refurbished` or `used` |
| price | string (price + currency code) | '9.99 USD' |
| link | string (begin with **http://** or **https://**) | |
| image_link | string (begin with **http://** or **https://**, end with **jpg** or **png**) | |
| brand | string (limit 100 char) | 'Jasper's Market' | 

### Required Events (Pixel)
By passing the three events, the pixel and the catalog are able to link viewed product with a user profile.

| Event Name | Required Parameters |
| - | - |
| `ViewContent` | `content_type`, `contents`/`content_ids` |
| `AddToCart` | `content_type`, `contents`/`content_ids` |
| `Purchase` | `content_type`, `contents`/`content_ids`, `currency`, `value` |
#### content_type
Can be **product** or **product_group**.
- When `content_type: 'product'`, ID being passed into contents/content_ids should be **IDs of product (`id`)**.
- When `content_type: 'product_group'`, ID being passed into contents/content_ids should be **IDs of product group (`item_group_id`)**.

#### contents/content_ids
```js
// content_ids
fbq('track', 'Purchase', {
  content_ids: ['ABC123', 'CDE234'],
  content_type: 'product'
});
// contents
fbq('track', 'Purchase', {
  contents: [
    { id: 'ABC123', quantity: 1 }, 
    { id: 'CDE234', quantity: 2 }
  ],
  content_type: 'product'
});
```

## Troubleshoot Catalog & Dynamic Ads
#### Not seeing any data within catalog / **low catalog match rate** / audience size drop.
- The catalog and pixel aren't linked.
- `content_ids` from the pixel don't match ids in catalog.
- Not all items on the website are included in the catalog.
#### Feed upload isn't updating catalog.
- File/feed size is too big.
#### Ads showing repetitive ads of the same item but in different colors.
- Add `item_group_id` column.
#### Sudden decrease in campaign performance.
- Items are sold out but aren't updated in catalog, therefore they are still shown. **Increase frequency of feed upload** and update to fix this.

#### Business has multiple markets or languages.
- Set up one pixel per market/language.

## Troubleshoot Pixels
### Common Pixel Setup Mistakes
#### `contents: [{ id: 'ABC123' }, { id: 'CDE234' }]`
- Missing `quantity` property in each product object.
#### `content_type: 'soap'`
- Content type should be either `product` or `product_group`.
#### `content_category` vs. `content_type`
- `content_category` can be any string you want, but `content_type` can only be either `product` or `product_group`.
#### `value: 5000,000`
- Wrong format, value can contain decimal point but no comma.
#### `currency: $`
- We never use the `$` symbol, use three letter code such as `USD`.

### Troubleshoot Tools
#### Pixel Helper
- Are pixels firing correctly with the correct parameters?
- Time lag: no.
#### Events Manager
- Are pixel events reaching BM account?
- Time lag: **20 minutes**.
#### Facebook Debug Tools
- [Product Catalog Debug Tool (Microdata Debug Tool)](https://business.facebook.com/ads/microdata/debug): check if metadata in a website be correctly setup. The errors will show like this
  <img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/microdata%20debug%20tool.png" alt="microdata debug tool" width="800" />
- [Retargeting Pixel Debug Tool](https://business.facebook.com/ads/retargeting_pixel/debug/): check if the catalog is associated with pixel.
  1. Show a list of catalog.
  2. Show a chart with types of standard events and their counts. You should see a full set of standard events (`ViewContent`, `AddToCart` and `Purchase`).
#### Chrome DevTools
- See all data being passed to Facebook.

## Useful Links to Documentation
- [Full list of standard events](https://developers.facebook.com/docs/meta-pixel/reference#standard-events)
- [Event parameters](https://developers.facebook.com/docs/meta-pixel/reference#object-properties)