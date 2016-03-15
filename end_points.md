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



