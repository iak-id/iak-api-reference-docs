# Inquiry Television Non Telkom Vision

API to inquiry television non telkom vision.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
TVBIG | 1072161401 | Success
TVBIG | 1072161403 | Inquiry - Time Out
TVBIG | 1072161404 | Inquiry - Invoice Has Been Paid
TVBIG | 1072161405 | Inquiry - Incorrect Destination Number
TVBIG | 1072161406 | Payment - Payment Failed
TVBIG | 1072161407 | Payment - Pending / transaction in process
TVBIG | 1072161408 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Television customer number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands"  : "inq-pasca",
  "username"  : "123123123",
  "code"      : "TVBIG",
  "hp"        : "1072161401",
  "ref_id"    : "09128374656",
  "sign"      : "15011812f64ce888747de76059aa0b20"
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
  <code>TVBIG</code>
  <hp>1072161401</hp>
  <ref_id>09128374656</ref_id>
  <sign>15011812f64ce888747de76059aa0b20</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Television customer number | Yes
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
    "hp": "1072161401",
    "tr_name": "Mr. syahrun as",
    "period": "",
    "nominal": 138499,
    "admin": 0,
    "ref_id": "09128374656",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 138499,
    "selling_price": 137399,
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
	<hp>1072161401</hp>
	<tr_name>Mr. syahrun as</tr_name>
	<period></period>
	<nominal>138499</nominal>
	<admin>0</admin>
	<ref_id>09128374656</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>138499</price>
	<selling_price>137499</selling_price>
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
    "commands"  : "inq-pasca",
    "username"  : "{your username}",
    "code"      : "TVBIG",
    "hp"	      : "1072161401",
    "ref_id"    : "09128374656",
    "sign"      : "{your sign}"
  }
}
```
