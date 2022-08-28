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