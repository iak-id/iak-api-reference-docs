# Payment Multifinance

API to pay multifinance.

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
  "tr_id"    : "9732789",
  "sign"     : "203d8ff7eff07fe51c2a009450b1202c"
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
  <tr_id>9732789</tr_id>
  <sign>203d8ff7eff07fe51c2a009450b1202c</sign>
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
hp | String | Contract number | Yes
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
desc | Object | Product description, please refer to [multifinance object](./multifinance-object.md) | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732789,
    "code": "FNMEGA",
    "datetime": "20180803171802",
    "hp": "6391601201",
    "tr_name": "ABDUL SAMID HARAHAP",
    "period": "005",
    "nominal": 661000,
    "admin": 0,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 661000,
    "selling_price": 660500,
    "balance": 998506398,
    "noref": "49911296",
    "ref_id": "091283746513",
    "desc": {
      "misc_fee": 0,
      "item_name": "HONDA VARIO TECHNO 125 PGM FI NON CBS",
      "no_rangka": "MH1JFB111CK196426",
      "no_pol": "B6213UWX",
      "tenor": "030",
      "installment": 657695,
      "penalty_bill": 3305,
      "max_payment": 0,
      "last_paid_due_date": "14 Dec 12",
      "id_ref": "514367"
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
  <tr_id>9732789</tr_id>
  <code>FNMEGA</code>
  <datetime>20170725134000</datetime>
  <hp>6391601201</hp>
  <tr_name>ABDUL SAMID HARAHAP</tr_name>
  <period>005</period>
  <nominal>661000</nominal>
  <admin>0</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>661000</price>
  <selling_price>660500</selling_price>
  <balance>74578043</balance>
  <noref>49911296</noref>
  <ref_id>1500964767</ref_id>
  <desc>
    <misc_fee>0</misc_fee>
    <item_name>HONDA VARIO TECHNO 125 PGM FI NON CBS</item_name>
    <no_rangka>MH1JFB111CK196426</no_rangka>
    <no_pol>B6213UWX</no_pol>
    <tenor>030</tenor>
    <installment>657695</installment>
    <penalty_bill>3305</penalty_bill>
    <max_payment>0</max_payment>
    <last_paid_due_date>14 Dec 12</last_paid_due_date>
    <id_ref>514367</id_ref>
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
    "tr_id": "9732789",
    "sign": "{your sign}"
  }
}
```
