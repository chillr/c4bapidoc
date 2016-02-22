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
