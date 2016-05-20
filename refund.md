# Refund
This API is used to initiate a transaction refund. This can be done manually by the merchant from the web interface.

| Path | https://onlineapi.chillr.in/api/v5/transactions/initiate_refund |
| -- | -- |
| Method | POST |

Request params

| Param | Description | Mandatory |
| -- | -- | -- |
| api_key | Your api key | Yes |
| api_secret_key | Your api secret key | Yes |
| transaction_id | Transaction id | Yes |

Sample success response

```json
{
  "status" : "success",
  "message" : "successfully initiated refund"
}
```

### Failure codes
| Status code | Description |
| -- | -- |
| 50 | api_key param is missing |
| 51 | api_secret_key param is missing |
| 64 | transaction_uuid param is missing |
| 54 | Merchant not found Error |
| 58 | Api Secret key doesnt match |
| 53 | You are not an online merchant |
| 55 | Internal server error |
| 56 | Transaction not found |
| 61 | No transaction found under this merchant with specified id |
| 65 | Already initiated the refund |
| 66 | Refund can initiate only for success transactions |


Sample failure response

```json
{
  "status" : "failure",
  "status_code" : 65,
  "message" : "Already initiated the refund"
}
```





