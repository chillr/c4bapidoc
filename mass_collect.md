# Mass collect API
Mass collect api can be used by a vendor to send bill collect request to his  users. The users need to have Chillr app installed to make the payment.

There are two api's for mass collect.

1. To create a batch containing payment information and receiver information.
2. To check the status of a batch, ie. How many successfully paid and how many are pending or failed due to some reason.

## Create batch

URL: **https://onlineapi.chillr.in/api/v5/collect**
METHOD: **POST**

Parameters:

| Field | Description | Mandatory |
| -- | -- | -- |
| api_key | Your API key | Yes |
| api_secret_key | Your API secret key | Yes |
| name | Name of the batch | Yes |
| expiry_date | Expiry date for the batch (dd-mm-yyyy) | Yes |
| customers | Array of customer details | Yes |
