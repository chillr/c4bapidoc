## Testing in Sandbox mode

Chillr for business API has a sandbox mode for testing the payments while  development. For this you need to get the sandbox credentials, ie **api_key** and **api_secret_key** (You can get it from the merchant [portal](https://sandbox-merchants.chillr.in/merchant_sessions/new) once your account setup is complete). You will also need a sandbox Chillr app.

## Client Side SDK
You can follow the same documentation for sandbox mode for setting up the [Client Side SDK](client_side_sdk.md) except that the chillr wrapper element should be defined as below.

```html
<div id="chillr-element-wrapper" base-url="https://sandbox-onlineapi.chillr.in"></div>
```
And client side sdk will be as follows.

```javascript
<script type="text/javascript" id="chillr-sdk-embedder" class="chillr-async-script-loader">
  (function(global) {
    function async_load(){
      var s = document.createElement("script");
      s.type = "text/javascript";
      s.async = true;
      var theUrl = 'https://sandbox-onlineapi.chillr.in/online-sdk/assets/js/init.min.js';
      s.src = theUrl;
      var embedder = document.getElementById("chillr-sdk-embedder");
      embedder.parentNode.insertBefore(s, embedder);
    }
    if (window.attachEvent){
      window.attachEvent("onload", async_load);
    }
    else{
      window.addEventListener("load", async_load, false);
    }
  })(this);
</script>
```

## Initiate transaction
For [initiate transaction](initiate_transaction.md) you will have to use the sandbox endpoint.

URL: **https://sandbox-onlineapi.chillr.in/api/v5/transactions/new**

## Transaction Status Query
For transaction status query you will have to use the sandbox endpoint.

URL: **https://sandbox-onlineapi.chillr.in/api/v5/transactions/details**

## Refund
For [refund](refund.md) you will have to use the sandbox endpoint

URL: **https://sandbox-onlineapi.chillr.in/api/v5/transactions/initiate_refund**

You will have to install the sandbox build to do the testing in sandbox  mode. Get in touch with us to request for the Chillr Sandbox App.
