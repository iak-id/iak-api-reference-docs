# Inquiry Gas Negara

API to inquiry gas negara.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
PGAS | 0110014601 | Success
PGAS | 0110014603 | Inquiry - Time Out
PGAS | 0110014604 | Inquiry - Invoice Has Been Paid
PGAS | 0110014605 | Inquiry - Incorrect Destination Number
PGAS | 0110014606 | Payment - Payment Failed
PGAS | 0110014607 | Payment - Pending / transaction in process
PGAS | 0110014608 | Payment - MISC Error / Biller System Error

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
  "commands"	: "inq-pasca",
  "username"	: "123123123",
  "code"      : "PGAS",
  "hp"        : "0110014601",
  "ref_id"    : "151270689512",
  "sign"	    : "12fe359b0638d81d70ea1d278f400ab1"
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
  <code>PGAS</code>
  <hp>0110014601</hp>
  <ref_id>1512706895</ref_id>
  <sign>802407f89a1a46c635621099e0bb9522</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Gas negara customer number | Yes
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
desc.**address** | String | Customer address | Yes
desc.**first_meter** | String | Initial meter | Yes
desc.**last_meter** | String | Final meter | Yes
desc.**usage** | Integer | Number of usage | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732788,
    "code": "PGAS",
    "hp": "0110014601",
    "tr_name": "NGATIMUN",
    "period": "0917",
    "nominal": 322002,
    "admin": 2500,
    "ref_id": "1512706895",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 324502,
    "selling_price": 323902,
    "desc": {
      "address": "-",
      "first_meter": "006538",
      "last_meter": "006573",
      "usage": 35
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
  <tr_id>9732788</tr_id>
  <code>PGAS</code>
  <hp>0110014601</hp>
  <tr_name>NGATIMUN</tr_name>
  <period>0917</period>
  <nominal>322002</nominal>
  <admin>2500</admin>
  <ref_id>1512706895</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>324502</price>
  <selling_price>324002</selling_price>
  <desc>
    <address>-</address>
    <first_meter>006538</first_meter>
    <last_meter>006573</last_meter>
    <usage>35</usage>
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
    "code": "PGAS",
    "hp": "0110014601",
    "ref_id": "1512706895",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os