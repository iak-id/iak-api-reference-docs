# Payment Insurance

API to pay insurance.

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
  <tr_id>268137898</tr_id>
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
desc | Object | Product description, please refer to [insurance object](./insurance-object.md) | Yes

<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"tr_id": 268137898,
		"code": "AIA.PREMICONVEN",
		"datetime": "20221110143144",
		"hp": "10202001",
		"tr_name": "USER TESTING AIA",
		"period": "",
		"nominal": 1250000,
		"admin": 3000,
		"response_code": "00",
		"message": "PAYMENT SUCCESS",
		"price": 1253000,
		"selling_price": 1252500,
		"balance": 99890200908,
		"noref": "2022080917161681291 0000000252",
		"ref_id": "09128374652",
		"desc": {
			"insured": "XX",
			"policy_status": "XX",
			"due_date": "XX",
			"footer": [
				"AIA CUSTOMER CARE 1500980"
			]
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
<?xmlversion="1.0"encoding="UTF-8"?>
<mp>
	<tr_id>268137898</tr_id>
	<code>AIA.PREMICONVEN</code>
	<datetime>20221110143144</datetime>
	<hp>10202001</hp>
	<tr_name>USERTESTINGAIA</tr_name>
	<period></period>
	<nominal>1250000</nominal>
	<admin>3000</admin>
	<response_code>00</response_code>
	<message>PAYMENTSUCCESS</message>
	<price>1253000</price>
	<selling_price>1252500</selling_price>
	<balance>99890200908</balance>
	<noref>20220809171616812910000000252</noref>
	<ref_id>09128374652</ref_id>
	<desc>
		<insured>XX</insured>
		<policy_status>XX</policy_status>
		<due_date>XX</due_date>
		<footer>AIACUSTOMERCARE1500980</footer>
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

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM