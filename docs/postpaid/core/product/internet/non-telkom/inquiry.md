# Inquiry Internet Non Telkom Speedy and Telkom PSTN

API to inquiry internet non telkom speedy and telkom pstn.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
CBN | 01927101 | Success
CBN | 01783002 | Success
CBN | 01783003 | Inquiry - Time Out
CBN | 01783004 | Inquiry - Invoice Has Been Paid
CBN | 01783005 | Inquiry - Incorrect Destination Number
CBN | 01783006 | Payment - Payment Failed
CBN | 01783007 | Payment - Pending / transaction in process
CBN | 01783008 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Gas negara customer number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "CBN",
  "hp"       : "01927101",
  "ref_id"   : "578912993899",
  "sign"     : "01a6e0b7880edc11d155ca2e79c02899"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" ?>
<mp>
  <commands>inq-pasca</commands>
  <username>123123123</username>
  <code>CBN</code>
  <hp>01927101</hp>
  <ref_id>578912993899</ref_id>
  <sign>01a6e0b7880edc11d155ca2e79c02899</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Internet customer number | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
response_code | String | Response code. See [response code](../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
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
    "hp": "01927101",
    "tr_name": "Budi",
    "period": "201905",
    "nominal": 30000,
    "admin": 0,
    "ref_id": "578912993899",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 30000,
    "selling_price": 29000,
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
  <hp>01927101</hp>
  <tr_name>Budi</tr_name>
  <period>201905</period>
  <nominal>30000</nominal>
  <admin>0</admin>
  <ref_id>578912993899</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>30000</price>
  <selling_price>29000</selling_price>
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
    "commands": "inq-pasca",
    "username": "{your username}",
    "code": "CBN",
    "hp": "01927101",
    "ref_id": "578912993899",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os