# How to add multiple Google AdWord Conversions into Vue.js App

When there are multiple conversions happen in a SPA Vue.js app, we should fire them manually on each button event.

So first we add Global tag script and also all conversions into header of main html. (for example index.html). We should rename default method name of Conversions we grab from GoogleAd.

```
  <head>
    <!-- Global site tag (gtag.js) - Google Ads: XXXXXXXX -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=AW-XXXXXXXX"></script>
  <!-- rest of tags in header -->
  
   <script>
      function gtag_report_conversion_1(url) {
        var callback = function () {
          if (typeof(url) != 'undefined') {
          }
        };
        gtag('event', 'conversion', {
          'send_to': 'XXXXXXXXXXXXXXX',
          'event_callback': callback
        });
        return false;
      }
    </script>

    <script>
      function gtag_report_conversion_2(url) {
        var callback = function () {
          if (typeof(url) != 'undefined') {
          }
        };
        gtag('event', 'conversion', {
          'send_to': 'XXXXXXXXXXXXXXXXXXXXXXXXXX',
          'event_callback': callback
        });
        return false;
      }
    </script>

  </head>
  ```
  Then simply, in any action we want, we can call these functions as they are globaly available in our Vue app.
  
Pay attention that a default from GoogleAd script which is this is removed to prevent page refresh on calling these methods:

  ```
window.location = url;
  ```
