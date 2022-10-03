## Business Manager
#### Why Use Business Manager
- To run ads on Facebook / Instagram.
- To grant or gain access to Facebook assets. **(1 ~ 2 questions)**

#### Tools in Business Manager
- Ad Account (廣告帳號): to purchase advertising on connected Pages or Facebook apps.
- [Ads Manager (廣告管理員)](https://business.facebook.com/adsmanager): to house all **ad accounts** and can have 25 associated users.
<img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/ads%20manager.png" alt="ads manager" width="200"/>
- [Events Manager (事件管理工具)](https://business.facebook.com/events_manager2): central view of all events (including **pixels** and **conversions**) in your website.
<img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/events%20manager.png" alt="events manager" width="200"/>
- [Commerce Manager (商務管理工具)](https://business.facebook.com/commerce/): to manage **catalog** and **dynamic ads**.
<img src="https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/commerce%20manager.png" alt="commerce manager" width="200"/>

To setup Business Manager, you must use your personal Facebook account instead of create a new Facebook user. **(1 question)**

#### Assets
- Add Pages (粉絲專頁) to BM.
  - You must be an **admin on a Page** for more than **7 days**.
  - You must be **admin** in the Business Manager.
- Add pixels (像素) to
  - ad account: limit to **1**.
  - Business Manager: limit to **100**, and you must be **admin** in the Business Manager.
- Add ad accounts (廣告帳號) to BM.
  - You can add up to **25** ad accounts.
  - You can only add prepaid ad accounts to Business Managers if they're from certain locations.
  - You can't add an ad account which has already been added to another BM.
  
To gain or grant access, you can follow the flow chart below. **(1 ~ 2 questions)**
![Flow Chart of BM Access](https://github.com/moneychien19/note-meta-blueprint-500-101/blob/main/Takeaway/Flow%20Chart%20-%20BM%20access.jpg)

Access layer
- First layer: asset allocation
  - For example, there are two admin of Business Manager, one can access to Ad Manager 1, whereas one can access to Ad Manager 1, 2, and 3. Just because they are both admin doesn't mean that they can both access to all assets under the Business Manager.
- Second layer: asset control
  - For example, an analyst doesn't need to manage campaigns.

Setup Ad Accounts
- At least one person has been authorized to run ads.
- Each ad account needs an associated payment method.
- Ad account access can be shared both internally and externally.
- Business Manager should be owned by a party.

There are limited amount of pixels in Business Manager and Ad Account:
- Business Manager: 100,
- Ad Account: 1,

and once pixel is created, it cannot be deleted, it can only be repurposed.
> What do you do with a pixel when you no longer need it? Remove the code from your website and that will make it stop sending data.

Possible Conversion Goals
- Amount of item sold.
- Total value of item sold.
- Amount of newly registration.

Hashing
1. Data is hashed by SHA-256 before being sent to Facebook.
2. After the match process, Facebook deletes all the individual data. **(1 question)**
> Is the data being sent to Facebook secure? Yes, it is secure by hashed.
>
> When do you hash or normalize data? Always.
> - Hashing: It just depends whether you hash it manually or it's done automatically from Facebook. If you use `fbq()`, data is hashed automatically, but if you use `<img>` tags, you need to hash it.
> - Normalize: It just means follow specific formats such as removing spaces or lowercasing.
>
> Do login or financial data from the page get sent to Facebook? No.

Pixel has two parts:
- Base code: installed on all pages to provide baseline measurement (usually with `PageView` event).
- Event code: added to base code and used on specific page to track events. For example, `AddToCart` or `Purchase` event.
> Should pixel be included on all pages? Yes, basic code should be included on all pages.

Base Code
- The code will be like:
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
- The pixel code is always placed within open and close header tags. **(1 question)**
- The pixel code contains Javascript and no-Javascript parts. **(1 ~ 2 questions)**
- By default it starts capturing HTTP data and the on-page metadata.

Key Advanced Matching Fields
| User Data | Parameter | Format | Example |
| - | - | - | - |
| Email | em | string | 'johnsmith@test.com' |
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

Advanced Matching Code Example
- Javascript
  ```js
  fbq('init', '123456789', {
    em: 'email@email.com', 
    fn: 'john', 
    ln: 'smith',
    ph: '0901119955',
    external_id: 'js123456',
    ge: 'm',
    db: '19910526',
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

Required Events for Dynamic Ads
| Event Name | Required Parameters |
| - | - |
| `ViewContent` | `content_type`, `contents`/`content_ids` |
| `AddToCart` | `content_type`, `contents`/`content_ids` |
| `Purchase` | `content_type`, `contents`/`content_ids`, `currency`, `value` |

Manage Catalog
- Add manually
- Bulk upload
- Facebook pixel: If a product hasn't been viewed, it won't ever be entered the catalog.

| | Not Change Often | Change Daily/Weekly | Change More Than Daily or Realtime |
| - | - | - | - |
| Small Inventory | Add Manually | Bulk Upload + Scheduled Feed | Facebook Pixel |
| Medium to Large Inventory | Add Manually + Bulk Upload | Bulk Upload + Scheduled Feed | Facebook Pixel |

Troubleshoot Catalog & Dynamic Ads
- Not seeing any data within catalog / low catalog match rate / audience size drop.
  - The catalog and pixel aren't linked.
  - `content_ids` from the pixel don't match ids in catalog.
  - Not all items on the website are included in the catalog.
-  Feed upload isn't updating catalog.
  - File/feed size is too big.
- Ads showing repetitive ads of the same item but in different colors.
  - Add `item_group_id` column.
- Sudden decrease in campaign performance.
  - Items are sold out but aren't updated in catalog, therefore they are still shown. Increase frequency of feed upload and update to fix this.