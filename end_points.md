# API Reference

### 1. Create Transaction

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
| &#149; | id | Unique ID of the transaction. (This id needs to be passed for the transaction status query API) |
| &#149; | created_at | Timestamp |


##### Sample Response
```json
{
  "status": "success",
  "message": "Transaction initiated",
  "data": {
     "status": "initiated",
     "amount": 50,
     "description": "transaction initiated",
     "transaction_id": "CHILLR:QRPAY:569f7a586368694380080000",
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

### 2. Transaction Status Query

This API is used to query the status of a created transaction.

| Path | https://onlineapi.chillr.in/api/v5/transactions/details |
| -- | -- |
| **Method** | POST |

##### Request Fields

| Field | Description | Default |
| -- | -- | -- |
| api_key | The API key of the merchant | _Mandatory Field_ |
| id | The id of the transaction created | _Mandatory Field_ |


##### Response Format
The response has 2 fields - _status_ and _data_ as a JSON. The _data_ is a Base64 encrypted JSON block which needs to be decrypted in order to reveal the actual status response. Please see Response Decryption for details on how to decrypt.


##### Response Fields

> _Note:_ This describes the fields present in the 'data' field after decrypting the input. 

| Field| Description |
|  -- | -- |
| status | The status of the transaction| 
| invoice\_id | Invoice id passed in the request|
| order\_id | Order id passed in the request |
| remarks | Remarks as passed in the request |
| extra\_param\_1 | Extra parameter passed in the request |
| extra\_param\_2 | Extra parameter passed in the request |
| transaction_id | The Chillr transaction ID |

##### Sample Response

_Before Decryption_

```json
{
    "status": "success",
    "data": "MhfldSjJR2H2ykKk7e4x8CnhV0LXlXohOqFiKzgd266Ib5QAMB35WF35YErY\nXQtv8ogVflJzIB1R1kziWx/0zhqpHW52EgFpgPjwbD5OIsXGdbeaO3di1inn\nG77NCG+pAaOYMzZb2p70WMfflEkA+GJO8DXU89pcNXZZosuWLsnZZENvAOQ7\n9+Qis+mxDPdSo/7U91FtvyqXTKqxgUQWqIw2zrYV+684R9gyhx+ayHM=\n"
}
```

_After Decryption of 'data' parameter_ 
```json
{
  "status":"success",
  "order_id":"d24gfg1354",
  "transaction_id":"56af47b663686948462a0000",
  "invoice_id":"INV#1",
  "extra_param_1":"John",
  "extra_param_2":"8089123456",
  "remarks":"Chillr transaction"
}
```

##### Failure Codes

If there is a failure; then there is a status code returned in the response along with the status field set to 'failure'.

| Status Code | Description |
| -- | -- |
| 55 | A generic internal failure occurred. |
| 50 | API Key is missing or invalid. |
| 60 | ID parameter is missing. |
| 61 | This transaction is not owned by the requesting merchant.|
| 59 | API Secret Key is missing. |
| 58 | API Secret Key is not matching assigned key. |
| 53 | Merchant is not approved to use the API yet. |
| 54 | Merchant not found or invalid. |


##### Sample Failure Response
```json
{ 
   "status": "failure",
   "status_code": 60,
   "message": "id param is missing"
}
```