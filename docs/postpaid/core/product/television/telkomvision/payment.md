# Payment Television Telkom Vision

API to pay television telkom vision.

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
  "tr_id"    : "9732314",
  "sign"     : "e87a1e5da86ac0d67330527b48f9b8ce"
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
	<tr_id>9732314</tr_id>
	<sign>e87a1e5da86ac0d67330527b48f9b8ce</sign>
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
    "datetime": "20180803171924",
    "hp": "127246500101",
    "tr_name": "BAITUS MONGJENG",
    "period": "MEI 12",
    "nominal": 99000,
    "admin": 1950,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 100950,
    "selling_price": 99950,
    "balance": 997348759,
    "noref": "18141775",
    "ref_id": "09128374657",
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
	<datetime>20170725164058</datetime>
	<hp>127246500101</hp>
	<tr_name>BAITUS MONGJENG</tr_name>
	<period>MEI 12</period>
	<nominal>99000</nominal>
	<admin>1950</admin>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>100950</price>
	<selling_price>99950</selling_price>
	<balance>73176494</balance>
	<no_ref>18141775</no_ref>
	<ref_id>09128374657</ref_id>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "9732314",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM