

# Initiate Transaction

This API is used to initiate a transaction through Chillr.

| Path | https://onlineapi.chillr.in/api/v5/transactions/new |
| -- | -- |
| **Method** | POST |

##### Request Fields

| Field | Description | Default |
| -- | -- | -- |
| amount _(integer)_| The amount to be charged | _Mandatory Field_ |
| api\_key _(string)_| Your API Key | _Mandatory Field_ |
| api\_secret\_key _(string)_ | Your API secret | _Mandatory Field_ |
| timeout _(integer)_ | Time out in minutes | 5 |
| invoice\_id (string) | Invoice ID | _Null_
| order\_id _(string)_ | Internal tracking ID for merchant | _Mandatory Field_ |
| remarks _(string)_ | Remarks | _Null_ |
| customer_email (string) | Customer email | _Null_ |
| customer_phone_no (string) | Customer phone number, (If this is present then the customer will get a push notification.) | _Null_ |
| customer_name (string) | Customer name | _Null_ | 
| extra\_param\_1 _(string)_ | For use by merchant if needed | _Null_ |
| extra\_param\_2 _(string)_ | For use by merchant if needed | _Null_ |

**NB**

Use [sandbox](sandbox_testing.md) url and sandbox credentials while you are doing development.

##### Response Fields and their Descriptions

1. **status** - Status of the API response 
2. **message** - Human readable description of the response 
3. **data** - Contains the transaction details as explained below 
   * *status* - Status of the transaction 
   * *amount* - Transaction Amount 
   * *qr\_code* - QR Code String for the transaction 
   * *transaction\_code* - 4 character code for the transaction 
   * *expiry_time* - At what time the transaction will expire 
   * *id* - Unique ID of the transaction. (This id needs to be passed for the transaction status query API) 
   * *created_at* - Timestamp 

##### Sample Response
```json
{
  "status": "success",
  "message": "Transaction initiated",
  "data": {
     "status": "initiated",
     "amount": 50,
     "description": "transaction initiated",
     "qr_code": "CHILLR:QRPAY:569f7a586368694380080000",
     "transaction_code": "QOCT",
     "expiry_time": "2016/01/20 17:50:20",
     "id": "569f7a586368694380080000",
     "created_at": "2016/01/20 17:45:20"
   }
 }
```

##### Failure Codes

If there is a failure; then there is a status code returned in the response along with the status field set to 'failure'.

| Status Code | Description |
| -- | -- |
| 55 | A generic internal failure occurred. |
| 50 | API Key is missing or invalid. |
| 51 | Amount parameter is missing or is beyond limits. |
| 59 | API Secret Key is missing. |
| 58 | API Secret Key is not matching assigned key. |
| 57 | API unacceptable parameters |
| 53 | Merchant is not approved to use the API yet. |
| 54 | Merchant not found or invalid. |

##### Sample Failure Response
```json
{ 
   "status": "failure",
   "status_code": 55,
   "message": "We could not process your request due to a technical reasons. Sorry for the trouble."             
}
```

