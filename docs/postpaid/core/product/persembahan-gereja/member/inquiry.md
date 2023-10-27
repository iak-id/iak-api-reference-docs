# Inquiry Member Church Offerings

API to inquiry Member Church Offerings.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1001 | Success
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1002 | Success
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1003 | Inquiry - Time Out
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1004 | Inquiry - Invoice Has Been Paid
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1005 | Inquiry - Incorrect Destination Number
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1006 | Payment - Payment Failed
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1007 | Payment - Pending / transaction in process
MEMBER.Shiftsoft_MMS-Perpuluhan_2022 | 1008 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Custom Denom payment code | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes
desc | Obejct | Product description | Yes
desc.**amount** | Integer | Custom nominal amount | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "MEMBER.Shiftsoft_MMS-Perpuluhan_2022",
  "hp"       : "1001",
  "ref_id"   : "0897654321",
  "sign"     : "6c6a046a14c444e44cfab5e4bbb01b01"
  "desc"     : {
    "amount" : 10000
  }
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
	<code>MEMBER.Shiftsoft_MMS-Perpuluhan_2022</code>
	<hp>1001</hp>
	<ref_id>0897654321</ref_id>
	<sign>6c6a046a14c444e44cfab5e4bbb01b01</sign>
	<desc>
		<amount>10000</amount>
	</desc>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Custom Denom payment code | Yes
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

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 131024523,
    "code": "MEMBER.Shiftsoft_MMS-Perpuluhan_2022",
    "hp": "1001",
    "tr_name": "IAK Sandbox Testing",
    "period": "202310",
    "nominal": 100000,
    "admin": 800,
    "ref_id": "0897654321",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 100800,
    "selling_price": 100350,
    "desc": []
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
	<tr_id>131024523</tr_id>
	<code>MEMBER.Shiftsoft_MMS-Perpuluhan_2022</code>
	<hp>1001</hp>
	<tr_name>IAK Sandbox Testing</tr_name>
	<period>202310</period>
	<nominal>100000</nominal>
	<admin>800</admin>
	<ref_id>08976543213</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>100800</price>
	<selling_price>100350</selling_price>
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
    "code": "MEMBER.Shiftsoft_MMS-Perpuluhan_2022",
    "hp": "1001",
    "ref_id": "0897654321",
    "sign": "{your sign}"
  }
}
```
