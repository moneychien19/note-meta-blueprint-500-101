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
