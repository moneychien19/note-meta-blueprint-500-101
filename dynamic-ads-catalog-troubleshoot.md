# Troubleshoot Catalog for Dynamic Ads

# Troubleshoot Catalog Issues

## Potential Issues with Catalog
The **Issues (問題)** tab in Commerce Manager categorizes issues into catalog, data sources, events and features.

### Catalog
Any issue with specific items in your catalog, such as an item **missing a required information field**.

### Data Sources
Issues with the data feed connected to your catalog. For example, we might not be able to access your scheduled feed on your **file hosting website**.

### Events
An issue that **comes from the pixel** and how people interact with items on your website. For example, there might be an issue with the pixel you connected to your catalog to run dynamic ads.

### Features
Issues that affect catalog features, such as checkout on Facebook. For example, items may be missing information fields that enable checkout.

## Issue Severity
### Errors 錯誤
Severe issues that can prevent items from uploading to your catalog and appearing in your ads.

### Warnings 警告
Don’t prevent items from appearing in your ads, but may affect the quality of your catalog. For example, an item may miss a recommended field.

## Solve Issues
1. If the issue is that the events data source has missing or invalid event information, select the **Review** button. It takes you directly to the settings for the event source in the **Events** tab. 
2. Follow the steps under **How to Fix**. This is available when you select **Review**. These instructions send you to the part of your catalog where you can fix the problem.

## Top 6 Data Feed File Errors
#### Missing required field:  `image_link`
This error occurs when one or more of your items doesn’t have an image link.

#### Missing universal IDs
You must provide at least one of the following identifiers for products: **brand name**, **Global Trade Identification Number (GTIN)** or **Manufacturer Part Number (MPN)**. This error occurs when none of these identifiers are in your data feed.

#### Multiple data feeds contain the same product
This error occurs when you have the **same ID listed in multiple data feed files**. You can have multiple data feed files, but each individual item can only be in one file.

#### Inaccessible data feed files or bad request
This error occurs when we can’t access your data feed from your server or file hosting website.

#### Unsupported HTML format
This error occurs when you upload a spreadsheet file in the incorrect format or didn't include a valid xml declaration tag in your XML file.

#### Missing required field, such as missing a description
This error occurs when you input one or more items or **the description is in all capital letters**.

## Advertising Policy
Sometimes, the system may flag items in your catalog for violations of [Facebook advertising policies](https://www.facebook.com/policies/ads/). You can also [request a review of a rejected item in your catalog](https://www.facebook.com/business/help/2741254916111768).

## Key Knowledge
- Upload feed file and check the errors and warnings.

# Troubleshoot Catalog Item Match Rate Issues

You can see how many items are available for dynamic ads after you connect a pixel to your catalog. The content IDs in your pixel events code should match the IDs of items in your catalog and return a high match rate. 

The Commerce Manager event source dashboard suggests that a “good” match rate is **90%** or more. This means that of all `content_ids` that Facebook receives, it’s able to match 90% or more of the individual IDs against the catalog.

## Item Match Rate Issues
Match rates display on a pixel level. They occur when pixel events and parameters are incorrectly set up or don't match the expected fields in the catalog. Always check the format and values of the `content_ids` and `content_type` parameters.

If you see no received events and a lower match rate percentage, this may be the result of a common implementation issue.

#### Incorrect Pixel Connected As Event Source
If you **connect the incorrect pixel** as an event source, you may then send pixel data to the wrong catalog asset.

#### Content IDs Not Exist in Feed or Catalog
This may be due to business or **technical reasons**, so it’s important to identify the reason. Once you understand why the item ID doesn't exist in the catalog, you can either disregard it or determine the best course of action to resolve the issue.

#### Product Synchronization Issues
This will occur when
- products on an ecommerce website don't reflect the catalog.
	- For example, a client uses a third-party developer to create the feed, but the data source they provide the developer on a daily basis comes from a different internal data source.
- the catalog is ingested frequently or at an unexpected time.
	- For example, if a feed is scheduled to pull at 12:00 AM and the store updates its inventory at 2:00 AM, the latest set of products ingested into Facebook won’t accurately reflect the latest items in the ecommerce store.

## Items Not in Catalog
You may receive an error because your ad contains an item that was **recently updated or deleted in your feed**. When your catalog updates, new items are reviewed against Meta advertising policies.
1. If you don't see the item in your catalog, wait up to **48 hours** for the system to update.  
2. After 48 hours, check your catalog and publish your ad again.
3. If there's no change after 48 hours, you should review any recently updated items. 
4. Check and update the product set filtering and verify that you used the correct product set. If the filtering is correct, **publish the ad again**.

## Troubleshooting Tools
### Retargeting Pixel Debugger Tool
The [retargeting pixel debugger tool](https://business.facebook.com/ads/retargeting_pixel/debug/) enables you to type in your pixel ID, then it will show two type of data:
- Which catalog is associated with my pixel? 
	- A list of catalog will be shown in this section. If you don't see your catalog ID in the list, it's not connected as a data source.
- Which standard events have fired in the last seven days?
	- Type of standard events and their counts will be shown in a chart. If you don't see a full set of standard events (`ViewContent`, `AddToCart` and `Purchase`) for your site, there's likely an implementation issue.

### Facebook Pixel Helper
There are some section in Pixel Helper
- Warnings: will list warnings such as "Products are missing from your catalog".
- Custom Parameters Sent:  check whether all standard event parameters are correct.
- Event Info: check whether event and parameter data are passed into the pixel without error.

## Events Manager
Events Manager enables you to see which events and parameters your pixel is currently passing. Please be aware that it may take up to **20 minutes** for you to see data.

## Event Source Dashboard
The **Events (事件)** tab in [Commerce Manager](https://www.facebook.com/commerce_manager/) helps you confirm that events and the catalog work correctly. It may take up to **24 hours** for the latest data to be available.

The dashboard contains multiple sections

#### Items available for retargeted ads (可用於再行銷廣告的商品)
Select tabs to check match rate of the pixel against the catalogs.

#### Website conversions with matched content IDs (包含相符內容編號的網站轉換)
Shows a match rate graph. It tracks the match rate over time and indicates whether the past and current status is “good” and has a score of 90% or more.

#### Content IDs missing from your catalogs (你的目錄缺少的內容編號)
Toggle to view problematic content IDs. You can also view potentially problematic URLs. For example, pages that are passing in IDs that don't exist in the catalog.

## Key Knowledge
- Enable to troubleshoot given dashboard and pixel code.



