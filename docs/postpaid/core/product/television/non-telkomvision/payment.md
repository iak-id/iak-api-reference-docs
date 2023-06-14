# Payment Television Non Telkom Vision

API to pay television non telkom vision.

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
  "tr_id"    : "9732793",
  "sign"     : "076d19deca1256870ca9eb048dbfd9d8"
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
	<tr_id>9732793</tr_id>
	<sign>076d19deca1256870ca9eb048dbfd9d8</sign>
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
hp | String | PLN postpaid customer number | Yes
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
desc.**bill_quantity** | String | Bill quantity | Yes
desc.**product_category** | String | Product category | Yes
desc.**ppn** | Double | Tax fee | Yes
desc.**tagihan** | Object | - (Unused) | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732793,
    "code": "TVBIG",
    "datetime": "20180803171903",
    "hp": "1072161401",
    "tr_name": "Mr. syahrun as",
    "period": "",
    "nominal": 138499,
    "admin": 0,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 138499,
    "selling_price": 137399,
    "balance": 997448709,
    "noref": "339062465",
    "ref_id": "091283746517",
    "desc": {
      "bill_quantity": "1",
      "product_category": "",
      "ppn": 0,
      "tagihan": {
        "detail": []
      }
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
	<tr_id>9732793</tr_id>
	<code>TVBIG</code>
	<datetime>20170725155717</datetime>
	<hp>1072161401</hp>
	<tr_name>Mr. syahrun as</tr_name>
	<period></period>
	<nominal>138499</nominal>
	<admin>0</admin>
	<ref_id>1500972821</ref_id>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>138499</price>
	<selling_price>137499</selling_price>
	<balance>73520354</balance>
	<no_ref>339062465</no_ref>
	<ref_id>091283746517</ref_id>
	<desc>
		<bill_quantity>1</bill_quantity>
		<product_category></product_category>
		<ppn>0</ppn>
		<tagihan/>
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
    "tr_id": "9732793",
    "sign": "{your sign}"
  }
}
```
