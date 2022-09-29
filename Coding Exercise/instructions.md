# Coding Assessment
In this coding assessment, you'll put what you have learned into practice and gain some hands-on experience on with the Facebook pixel.

Important: Before starting, make sure that you have proper access to create a new pixel in your Business Manager or ad account.

## Bug Report

Please note that Facebook will not conduct individual code reviews on candidate's code or provide feedback as to scores or test results.

This assessment has been calibrated to Facebook best practices for code formatting, as found in the Facebook for Developer Documentation. If you find that your code is passing in Pixel Helper, but not in the assessment, this is likely due to the fact that your code is not correctly formatted and not due to a bug. Please do not file a bug report in this instance and instead work on aligning your code with the formatting and best practices found in the Developer Documentation.

If you recieve an error message when submitting your code that tests failed to run, this is because there is a critical error in your code and you need to debug it. Facebook will not provide feedback on where you have an error in your code.

To report a bug, contact the Blueprint Support Team via this form: https://www.facebook.com/blueprint/support.

## Get Started

While working on this assessment, you'll be able to run your code, check for syntax errors, and use the Pixel Helper. Once done, click Submit within the platform.

## Initialize the Pixel

**Step 1:** Create a new pixel.

**Step 2:** Install the pixel code on your website.

**Step 3:** Verify that your pixel has been initialized successfully and fired 'PageView' event.

## Implement Advanced Matching

**Step 4:** Implement advanced matching on both pages for the following user data:

```
Email: johnsmith@example.com
Full Name: John Smith
City: Menlo Park
State: California
Set Up a Product Catalog
```

**Step 5:** In your Business Manager, create an e-commerce product catalog in your Business Manager. In real-world applications, you would next link your Facebook pixel to the newly created catalog. You would first validate your domain and prioritize events in order to link the catalog to the pixel. While you will need to follow the above steps in real-world applications, you do not need to do so for the purpose of this assessment.

**Step 6:** Add 5 sample products to your catalog. Make sure one of these products are the "Really Comfortable Shoes" that you see in the assessment.

## Send Events

**Step 7:** Using the index.html:

a. Send a ViewContent event when the page is loaded and include all 4 parameters for dynamic ads to match the "Really Comfortable Shoes" with the right ID, price and currency. This allows you to track the user traffic of who visited this product.

b. Indicate that this product belongs to the “Casual” category by passing this information in a suitable parameter.

**Step 8:** Click Purchase.

You'll be redirected to the checkout.html page to confirm your purchase.

**Step 9:** On the purchase confirmation page:

a. Send a Purchase event to indicate a successful conversion for the "Really Comfortable Shoes" and include all 4 parameters for dynamic ads matching its ID, price and currency.

b. Indicate that this product belongs to the “Casual” category by passing this information in a suitable parameter.

**Step 10:** Click Subscribe.

You see that the user wants to register for newsletters from your website.

**Step 11:** Send a CompleteRegistration event only when the Subscribe button in index.html is clicked.

**Step 12:** Submit.

Note: You have only 3 submissions. Make sure that you address all problems shown in the Pixel Helper to maximize your chances of passing.

