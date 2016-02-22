# Chillr Online API Documentation


## Initiate transaction

Initiate a new transaction through [Chillr](https://chillr.com).

**URL** onlineapi.chillr.in/api/v5/transactions/new

**METHOD** POST

**SCHEME** https

**PARAMETERS**

| Parameter name | Parameter Type | Mandatory/Optional |
| -- | -- | -- |
| amount | Integer eg: 450 | M |
| invoice_id | String eg: INV#1032 | O |
| order_id | String eg: 5464784 | M |
| timeout | Integer eg: 5 | O |
| api_key | String | M |
| api_secret_key | String | M |
| remarks | String | O |
| extra_param_1 | String | O |
| extra_param_2 | String | O |


**timeout** is in minutes

**JSON** format

```json
{
  amount: 450,
  invoice_id: "INV#1",
  order_id: "5464784",
  timout: 5,
  api_key: "5695d71a6368690fff30000",
  api_secret_key: "00e9da44cdffc119a0e78f0dcef1da4f8",
  remarks: "Order for domain from domainsnmore.in",
  extra_param_1: "Deepak Kumar",
  extra_param_2: "Kochi, Kerala"
}
```

**RESPONSE**

A sample success response

```json
{
  status: "success",
  message: "Transaction initiated",
  data: {
    status: "initiated",
    amount: 450,
    description: "transaction initiated",
    transaction_id: "CHILLR:QRPAY:569f7a586368694380080000",
    transaction_code: "QOCT",
    expiry_time: "2016/01/20 17:50:20",
    id: "569f7a586368694380080000",
    created_at: "2016/01/20 17:45:20"
  }
}
```

| Response key | Description |
| -- | -- |
| status | Status of the api response |
| message | Message after initiating the transaction |
| data | Contains data regarding the initiated transaction |
| - status | status of the transaction |
| - amount | transaction amount |
| - transaction_id | QR code string for the transaction |
| - transaction_code | 4 character transaction code |
| - expiry_time | At what time the transaction will expire. |
| - id | Unique id for the transaction |
| - created_at | Transaction created time. |

