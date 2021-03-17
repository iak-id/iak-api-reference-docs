# Payment Gas Negara

API to pay gas negara.

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
  "tr_id"    : "9732788",
  "sign"     : "032a26153bd4a705f34965c86612ce15"
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
    <tr_id>9732788</tr_id>
    <sign>032a26153bd4a705f34965c86612ce15</sign>
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
hp | String | Gas negara customer number | Yes
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
desc.**address** | String | Customer address | Yes
desc.**first_meter** | String | Initial meter | Yes
desc.**last_meter** | String | Final meter | Yes
desc.**usage** | String | Number of usage | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732788,
    "code": "PGAS",
    "datetime": "20180803171739",
    "hp": "0110014601",
    "tr_name": "NGATIMUN",
    "period": "0917",
    "nominal": 322002,
    "admin": 2500,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 324502,
    "selling_price": 323902,
    "balance": 999166898,
    "noref": "244183135447",
    "ref_id": "151270689512",
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
    <datetime>20171208112252</datetime>
    <hp>0110014601</hp>
    <tr_name>NGATIMUN</tr_name>
    <period>0917</period>
    <nominal>322002</nominal>
    <admin>2500</admin>
    <response_code>00</response_code>
    <message>PAYMENT SUCCESS</message>
    <price>324502</price>
    <selling_price>324002</selling_price>
    <balance>81023</balance>
    <noref>244183135447</noref>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "9732788",
    "sign": "{your sign}"
  }
}
```
