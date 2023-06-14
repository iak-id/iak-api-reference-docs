# Inquiry Television Telkom Vision

API to inquiry television telkom vision.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
TVTLKMV | 127246500101 | Success
TVTLKMV | 127246500103 | Inquiry - Time Out
TVTLKMV | 127246500104 | Inquiry - Invoice Has Been Paid
TVTLKMV | 127246500105 | Inquiry - Incorrect Destination Number
TVTLKMV | 127246500106 | Payment - Payment Failed
TVTLKMV | 127246500107 | Payment - Pending / transaction in process
TVTLKMV | 127246500108 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Telkom vision customer number | Yes
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
  "code"      : "TVTLKMV",
  "hp"        : "127246500101",
  "ref_id"    : "09128374657",
  "sign"      : "b0c37e10dda176d1f66b3e9d6a7f8607"
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
  <code>TVTLKMV</code>
  <hp>127246500101</hp>
  <ref_id>09128374657</ref_id>
  <sign>b0c37e10dda176d1f66b3e9d6a7f8607</sign>
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
desc.**product_category** | String | Product category (Unused) | Yes
desc.**ppn** | Double | Tax fee (Unused) | Yes
desc.**tagihan** | Object | Invoice data | Yes
desc.tagihan**detail** | Array | Detail of invoice per month | Yes
desc.tagihan.detail.**periode** | String | Bill period for detailed month | Yes
desc.tagihan.detail.**nilai_tagihan** | String | Bill amount for detailed month | Yes
desc.tagihan.detail.**no_ref** | String | Reference number for detailed month | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732314,
    "code": "TVTLKMV",
    "hp": "127246500101",
    "tr_name": "BAITUS MONGJENG",
    "period": "MEI 12",
    "nominal": 99000,
    "admin": 1950,
    "ref_id": "09128374657",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 100950,
    "selling_price": 99950,
    "desc": {
      "bill_quantity": "1",
      "product_category": "",
      "ppn": 0,
      "tagihan": {
        "detail": [
          {
            "periode": "MEI 12",
            "nilai_tagihan": "99000",
            "no_ref": "205A"
          }
        ]
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
	<tr_id>9732314</tr_id>
	<code>TVTLKMV</code>
	<hp>127246500101</hp>
	<tr_name>BAITUS MONGJENG</tr_name>
	<period>MEI 12</period>
	<nominal>99000</nominal>
	<admin>1950</admin>
	<ref_id>09128374657</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>100950</price>
	<selling_price>99950</selling_price>
	<desc>
		<bill_quantity>1</bill_quantity>
		<product_category></product_category>
		<ppn>0</ppn>
		<tagihan>
			<detail>
				<periode>MEI 12</periode>
				<nilai_tagihan>99000</nilai_tagihan>
				<no_ref>205A</no_ref>
			</detail>
		</tagihan>
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
    "code"      : "TVTLKMV",
    "hp"	      : "127246500101",
    "ref_id"    : "09128374657",
    "sign"      : "{your sign}"
  }
}
```
