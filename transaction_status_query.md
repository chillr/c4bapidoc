# Transaction Status Query

This API query gets the status of a created transaction.

| Path | https://onlineapi.chillr.in/api/v5/transactions/details |
| -- | -- |
| **Method** | POST |

##### Request Fields

| Field | Description | Default |
| -- | -- | -- |
| **api_key** | The API key of the merchant | _Mandatory Field_ |
| **id** | The id of the transaction created | _Mandatory Field_ |


##### Response Format
The response has 2 fields - _status_ and _data_ as a JSON. The _data_ is a Base64 encrypted JSON block which needs to be decrypted in order to reveal the actual status response. Please see [Encryption Schemes](encryption_schemes.md) for details on how to decrypt.


##### Response Fields

> _Note:_ This describes the fields present in the 'data' field after decrypting the input. 

| Field| Description |
|  -- | -- |
| status | The status of the transaction| 
| invoice\_id | Invoice id passed in the request|
| order\_id | Order id passed in the request |
| remarks | Remarks as passed in the request |
| customer_email | Customer email |
| customer_phone_no | Customer phone number |
| customer_name | Customer name | 
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
  "customer_email":"sachin.jose@example.com",
  "customer_phone_no": "+919837836736",
  "customer_name": "Sachin",
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
