# Client Side SDK

This document explains the steps to implement the client side Chillr SDK widget onto a webpage.

## 1.Include the Javascript snippet

```javascript
<script type="text/javascript" id="chillr-sdk-embedder">
(function(global) {
  function async_load(){
    var s = document.createElement("script");
    s.type = "text/javascript";
    s.async = true;
    var theUrl = "https://onlineapi.chillr.in//online-sdk/assets/js/init.min.js";
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

## 2. Include the button & wrapper elements

```html
<a href="#" id="chillr-button">Pay using Chillr</a>

<div id="chillr-element-wrapper"></div>
```

If you are doing testing in sandbox mode change the wrapper element as in [this](sandbox_mode.md) section

| Element | Description |
| ------- | ------------|
| chillr-button| This is the element that the user clicks to initiate a payment.|
| chillr-element-wrapper | Chillr transaction card gets appended here.|


## 3. Initialize the widget

The merchant has to call the following method in order to initiate the widget. The values of the parameters _qr\_code_, _alpha_code_,_id_, _amount_, _expiry\_time_ and _created\_at_ are available from the response of [the server side API call](server_side_api_reference.md). 

The retry parameter is optional, if set to true then there will be a retry option in case the payment is a failure.

```javascript
window.chillrOnlineSDK.chillrTransactionCreated(
    qr_code, 
    transaction_code, 
    id, 
    amount, 
    expiry_time, 
    created_at,
    { retry_button: true});  // last parameter is optional.
```


