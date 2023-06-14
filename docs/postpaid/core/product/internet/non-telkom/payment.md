# Payment Internet Non Telkom Speedy and Telkom PSTN

API to payment internet non telkom speedy and telkom pstn.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `pay-pasca` | Yes
username | String | Your registered phone number | Yes
tr_id | Integer | IAK inquiry ID | Yes
sign | String | Signature. Value: `md5(username+api_key+tr_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "pay-pasca",
  "username" : "123123123", 
  "tr_id"    : "24462351",
  "sign"     : "359d3163485721fb518536384dec4e4f"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" ?>
<mp>
  <commands>pay-pasca</commands>
  <username>123123123</username>
  <tr_id>24462351</tr_id>
  <sign>359d3163485721fb518536384dec4e4f</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
datetime | String | Transaction time (Format **YmdHis**) | Yes 
hp | String | Internet customer number | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
response_code | String | Response code. See [response code](../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
balance | Double | Client remaining balance | Yes
noref | String | Biller reference number (if exist) | No
ref_id | String | Your order number / reference ID ( must unique ) | Yes
desc | Object | Product description | Yes
desc.**product_desc** | String | Product detail description | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 24462351,
    "code": "CBN",
    "datetime": "20190812143154",
    "hp": "01927101",
    "tr_name": "Budi",
    "period": "201905",
    "nominal": 30000,
    "admin": 0,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 30000,
    "selling_price": 29000,
    "balance": 999490800,
    "noref": "0109101/07/2019",
    "ref_id": "578912993899",
    "desc": {
      "product_desc": "CBN Anywhere Basic"
    }
  },
  "meta": []
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <tr_id>24462351</tr_id>
  <code>CBN</code>
  <datetime>20190812143154</datetime>
  <hp>01927101</hp>
  <tr_name>Budi</tr_name>
  <period>201905</period>
  <nominal>30000</nominal>
  <admin>0</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>30000</price>
  <selling_price>29000</selling_price>
  <balance>75899043</balance>
  <noref>0109101/07/2019</noref>
  <ref_id>578912993899</ref_id>
  <desc>
    <product_desc>CBN Anywhere Basic</product_desc>
  </desc>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://testpostpaid.mobilepulsa.net/api/v1/bill/check",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "24462351",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM