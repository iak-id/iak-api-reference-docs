# Inquiry Insurance

API to inquiry insurance.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
FNMEGA | 6391601201 | Success
FNMEGA | 6391601203 | Inquiry - Time Out
FNMEGA | 6391601204 | Inquiry - Invoice Has Been Paid
FNMEGA | 6391601205 | Inquiry - Incorrect Destination Number
FNMEGA | 6391601206 | Payment - Payment Failed
FNMEGA | 6391601207 | Payment - Pending / transaction in process
FNMEGA | 6391601208 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Contract number | Yes
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
  "code" 	    : "AIA.PREMICONVEN",
  "hp"	      : "10202001",
  "ref_id"	  : "09128374652",
  "sign"	    : "3743ec3e02f9076ea56e2f61be698a8e"
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
  <username>082210138584</username>
  <code>AIA.PREMICONVEN</code>
  <hp>10202001</hp>
  <ref_id>09128374652</ref_id>
  <sign>3743ec3e02f9076ea56e2f61be698a8e</sign>
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
		"hp": "10202001",
		"tr_name": "USER TESTING AIA",
		"period": "",
		"nominal": 1250000,
		"admin": 3000,
		"ref_id": "09128374652",
		"response_code": "00",
		"message": "INQUIRY SUCCESS",
		"price": 1253000,
		"selling_price": 1252500,
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
<?xml version="1.0" encoding="UTF-8"?>
<mp>
	<tr_id>268137898</tr_id>
	<code>AIA.PREMICONVEN</code>
	<hp>10202001</hp>
	<tr_name>USER TESTING AIA</tr_name>
	<period></period>
	<nominal>1250000</nominal>
	<admin>3000</admin>
	<ref_id>09128374652</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>1253000</price>
	<selling_price>1252500</selling_price>
	<desc>
		<insured>XX</insured>
		<policy_status>XX</policy_status>
		<due_date>XX</due_date>
		<footer>AIA CUSTOMER CARE 1500980</footer>
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
    "code": "FNMEGA",
    "hp": "6391601201",
    "ref_id": "09128374652",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os