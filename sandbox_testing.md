## Testing in Sandbox mode

Chillr for business API has a sandbox mode for testing the payments while in  developing. For this you need to get the sandbox credentials, ie **api_key** and **api_secret_key** (this will be mailed to your contact email on setting up the merchant) and a sandbox build.

You can follow the same documentation for sandbox mode except that the chillr wrapper element should be defined as below.

```html
<div id="chillr-element-wrapper" data-base-url="https://sandbox-onlineapi.chillr.in"></div>
```

You will have to install the sandbox build from here to do the testing in sandbox mode.
