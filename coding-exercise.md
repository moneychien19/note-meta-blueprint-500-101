# Coding Exercise Key Knowledge

## Initial the Pixel
1. Create a new pixel.
2. Install the pixel code on your website for each page.
  - Insert the code between `head` tag on every page.
  ```html
  <script> 
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod? n.callMethod.apply(n,arguments):n.queue.push(arguments)}; 
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0'; 
  n.queue=[];t=b.createElement(e);t.async=!0; 
  t.src=v;s=b.getElementsByTagName(e)[0]; 
  s.parentNode.insertBefore(t,s)}(window, document,'script', 'https://connect.facebook.net/en_US/fbevents.js');

  fbq('init', '1218369535643821'); 
  fbq('track', 'PageView'); 
  
  </script> 
  <noscript><img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=1218369535643821&ev=PageView&noscript=1" /></noscript>
  ```
3. Verify that your pixel has been initialized successfully and fired 'PageView' event for each page.

## Send Events and Parameters
4. On the page index.html, fire a `ViewContent` event. The user visited `index.html` to view more details of Casual Shoes. Please send a `ViewContent` event when the page is loaded and include parameters price and currency.
  - Insert the code under `fbq('track', 'PageView');`
  ```js
  fbq('track', 'ViewContent', {
    currency: 'EUR',
    value: 49.99
  });
  ```

## Advanced Matching
5. Implement advanced matching on only when the **Submit** button on the page is clicked. You can see that the form has already been filled. Please do not modify the form and use the given value to implement advanced matching.
  - Modify the base code in head tag (only on this page). 
  ```js
  fbq('init', '1218369535643821', {
    fn: 'john',
    ln: 'smith', 
    em: 'jsmith@example.com', 
    zp: '12345', 
    db: 19910526
  });
  ```

6. Send a `Lead` event only when the Submit button on the page is clicked.
  - Define track function right after the basic code.
  ```js
  function trackLead() {
    fbq('track', 'Lead');
  }
  ```
  - Modify the button onclick event.
  ```html
  <button
    type="button"
    class="btn btn-success" 
    id="submit_btn"
    onclick="trackLead()"
  >
    Submit
  </button>
  ```