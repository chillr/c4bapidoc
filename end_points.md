# End Points

### Generate Transaction

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
| extra\_param\_1 _(string)_ | For use by merchant if needed | _Null_ |
| extra\_param\_2 _(string)_ | For use by merchant if needed | _Null_ |

##### Response Fields

| # | Field| Description |
| -- | -- | -- |
| 1 | status | Status of the API response |
| 2 | message | Human readable description of the response |
| 3 | data | Contains the transaction details as explained below |
| &#149; | status | Status of the transaction |
| &#149; | amount | Transaction Amount |
| &#149; | transaction\_id | QR Code String for the transaction |
| &#149; | transaction\_code | 4 character code for the transaction |
| &#149; | expiry_time | At what time the transaction will expire |
| &#149; | id | Unique ID of the transaction |
| &#149; | created_at | Timestamp |


##### Sample Response
```json
{
  status: 'success',
  message: 'Transaction initiated',
  data: {
     status: 'initiated'
     amount: 50,
     description: "transaction initiated",
     transaction_id: "CHILLR:QRPAY:569f7a586368694380080000",
     transaction_code: "QOCT",
     expiry_time: "2016/01/20 17:50:20",
     id: "569f7a586368694380080000",
     created_at: "2016/01/20 17:45:20"
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
| 53 | Merchant is not approved to use the API yet. |
| 54 | Merchant not found or invalid. |

##### Sample Failure Response
```json
{ 
   status: 'failure',
   status_code: 55,
   message: "We could not process your request due to a technical reasons. Sorry for the trouble."             
}
```

