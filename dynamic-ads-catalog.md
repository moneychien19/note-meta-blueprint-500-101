# Introduction
Dynamic ads use your online catalog to **automatically generate ads** that show **product recommendations** tailored to each person in your target audience. They offer powerful targeting options to help you reach people interested in your products.

## About Catalog
A catalog is a container of information about the items you want to advertise and sell on Facebook or Instagram. To show your items to people who might want to buy them, you must **connect your catalog to dynamic ads**.

The system uses catalog **fields** to populate the dynamic ads for each item. These fields include important information, such as the item description, images, size or color variants, price and inventory.

## How Catalog for Dynamic Ads Works
### Process
1. Create your catalog.
2. Add your items.
3. Connect your pixel.

### Considerations Before Adding Items to Catalog
#### Number of Items
If you have a small number of products, you can manually add them in the Facebook interface. If you have a store with a large number of items, the system can do this **dynamically on a regular basis**.

#### Language and Currency
The languages and currencies you use helps you determine if **individual feeds** are necessary and the type of feed to use. They also help you determine guidelines around **multi-country** and language catalogs.

#### Inventory and Price
Inventory and price dynamics enable you to plan your feed schedule for when and how often you must generate your feed. You should also use this information to set up any replacement or update schedules for Facebook to pull in your feed.

#### Item Structure
The nature of your business, how your products are structured and how you handle variants, such as size and color, determine which **IDs** you can add to the feed (for example, `id` and `item_group_id`) and which IDs you can pass through the pixel.

#### Item Display
The way **ecommerce websites present items** to customers may give you an indication as to what IDs you need to add to your feed and pass into the pixel.

### Ways to Add Items to Your Catalog
Consider your inventory size and how frequently your inventory changes to determine how you add items to the catalog, there are three ways to add items.

#### Manually
When you have **small inventory and it rarely changes**, you can add manually. You will have to fill in a form to add items to your catalog one at a time. Enter an ID for each item that matches the content ID for that item in your Facebook pixel code.

#### Bulk Upload
When you have **large inventory and it changes regularly**, you can upload a data feed file in CSV, TSV or XML format or use Google Sheets. You can upload a file once or set up scheduled uploads.

#### Facebook Pixel
When you have **large inventory and it changes daily or hourly**, use your pixel to import and automatically update the items in your catalog each time someone visits the website.

Following are additional considerations that may impact which is the best way to add items to your catalog.

|                          | Manually                                          | Bulk Upload                                                                                      | Facebook Pixel                                                            |
| ------------------------ | ------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| Inventory Size           | small                                             | medium to Large                                                                                  | medium to large                                                           |
| Change Frequency         | not often                                         | often                                                                                            | very often                                                                |
| Inventory Type           | products, flights, hotels, destinations, vehicles | products, flights, hotels, destinations, vehicles, home listings                                 | products only                                                             |
| What You Need            | item details and images                           | data feed file with correct specifications                                                       | pixel installed, microdata tags on product pages, recent website activity |
| Effort to Set Up         | low                                               | medium                                                                                           | high                                                                      |
| Effort to Manage         | high                                              | medium                                                                                           | low                                                                       |
| Technical Resources      | none                                              | developer to create the feed from the back end of the store, or a member to deal with CSV or XML | developers to set up the metatags and implement the pixel                 |
| Infrastructure Available | none                                              | HTTP or (S)FTP server to host the updated file for automatically data pull                       | none                                                                      | 

## Key Knowledge
- Determine what way of adding items to a catalog should be applied under a given situation.

# Prepare the Data Feed File
A data feed file is a plaintext or spreadsheet file that represents the items in your business in a structured way. It also enables you to bulk upload many items to your catalog at once.

## Supported File Format
### Format
- Flat file: CSV, TSV, RSS, XML, ATOM XXL.
- Compressed CSV/XML: ZIP, GZIP, BZ2 compressed.
- Web link: Google Sheet.

### Size Limit
- Scheduled feed upload: **8GB**.
- Compressed files: **30GB** when uncompressed.
- One-time file upload: **100MB**.

## Support Fields
### Required
- `id`: unique ID same as content ID reported by pixel.
- `title`: specific title of item.
- `description`: description of item.
	- The description must be in sentence case, not all upper case.
- `availability`: for example, `in stock`.
- `condition`: for example, `new`.
- `price`: cost and currency of item.
- `link`: URL of product page where to buy item.
- `brand`: brand name.
- `image_link`: URL of main image of item (limit in 8MB).
	- additional image size requirements
		- Instagram shopping (square 1:1 format)
			- Minimum resolution: 500 x 500px.
			- Recommended (best quality): 1024 x 1024 px.
		- Carousel ads (square 1:1 format)
			- Min resolution: 500 x 500px.
			- Recommended (best quality): 1024 x 1024px.
		- Single image ads (1.91:1 aspect ratio)
			- Min resolution: 500 x 500px.
			- Recommended (best quality): 1200 x 628px.

### Optional
- `item_group_id`: accounts for product variants, such as size or color, when there are parent and child SKUs. Multiple products can be grouped in the same `item_group_id`.
- `google_product_category`: categorize items or create product sets for a more specific grouping of your items. It can make the data feed file as compatible as possible with other shopping or marketing channels.
- `sale_price` / `sale_price_effective_date`: add this when you put your products on sale. This way, when you set up your ads, the user can see the latest prices.
- `custom_label_[0-4]`: use to create custom product sets.
	- Note that each field has a 100-character limit.

## Feed Hosting and Storage
If you choose to generate your feed dynamically from your ecommerce website, here are some requirements and recommendations to remember.
- The URL or (S)FTP server must be publicly accessible.
- The feed generated on the ecommerce website can be hosted on the same website.
- Use a compressed feed file to optimize the upload process.
- Add HTTP basic authentication to your HTTP endpoint if you want to protect the feed.

## Key Knowledge
- All the required fields and their rules.

# Prepare the Assets
In this section you will learn how to manage catalog in Business Manager.

## Create a Catalog
1. Go to [Commerce Manager](https://business.facebook.com/commerce_manager).
2. Select **Create a Catalog (建立目錄)** or **Add Catalog (新增目錄)**.
3. Select the type of inventory you sell.
	- If you select **Ecommerce (電子商務)**, select how you want to add items to your catalog
		- Select **Upload Product Info (上傳商品資料)** to add items yourself.
		- Select **Connect Ecommerce Platform (連結合作夥伴平台)** if you host your products on a partner platform.
4. Enter a name for your catalog and create.

## Upload or Schedule Data Feed File
You can upload data feed files manually or automatically on an hourly, daily or weekly schedule.

### Manual Upload
1. In Commerce Manager, choose the catalog you've created.
2. Select **Data Sources (資料來源)**, and choose way you want to do manually upload.
	- **Add Manually (手動)** allows you to type in items data one by one.
	- **Use Bulk Upload (資料摘要)** allows you to upload files.

### Automatic Schedule
- File hosting: save your file on a file hosting website, such as Dropbox, and provide the URL to schedule the feed uploads.
- Protocol: your URL must begin with http, https, ftp or sftp.
- Format: your URL must also link to your downloadable data feed file in a supported format, such as CSV, TSV or XML. The URL can't go to a product page on a website, Page or anywhere else.
- Protection: provide the username and password if your file is password-protected.

Note that you should set your schedule to pull after the file is on the server. 
For example, if you generate your product feed at midnight every day, set a schedule on Facebook to pull the latest data at 12:30 a.m.

## Delete a Feed
Once you [delete items](https://www.facebook.com/business/help/428079314773256?id=725943027795860), they don't appear in ads that use that catalog anymore. You can also deactivate items to hide them instead.

## Create a Product Set
A product set is a **subset of products in your catalog** that dynamic ads use to showcase items. 
- The default product set for each catalog contains **all products**.
- You can also **select a set** when you create an ad in Ads Manager. 
	- A set for ads must contain four or more items. 
	- A product set is necessary to create an ad set for your dynamic ads campaign.

# Connect a Pixel to the Catalog
Learn how to measure customer activity and use dynamic ads to deliver relevant items to people based on their interests, intent and actions.

## Required Standard Events and Parameters
For dynamic ads to work properly, you must create and install a pixel. If possible, use **only one pixel per catalog and domain**. If you use more than one, we may not be able to accurately capture and optimize for the conversion events that you care the most about on iOS 14.5+ devices.

You need to add required events and parameters to your pixel code.
### Required Events
For dynamic ads specifically, you must add the `ViewContent`, `AddToCart`  and `Purchase` standard events. These events help you understand when someone takes those particular actions.

### Required Parameters
You’re required to include the `content_type` and either the `content_ids` or `contents` parameter with each standard event.

### Content IDs
There are two ways to pass in content IDs to the pixel that are functionally equivalent.

You can use both the `content_ids` and `contents` parameters.
- `contents` parameter is an array of JSON objects with id and quantities contained within, and it's required for Collaborative Ads. Collaborative Ads is a feature of dynamic ads.