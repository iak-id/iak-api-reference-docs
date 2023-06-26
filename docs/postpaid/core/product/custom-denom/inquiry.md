# Inquiry Custom Denom

API to inquiry Custom Denom.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
SHOPEEPAY | 082100000001 | Success
SHOPEEPAY | 082100000002 | Success
SHOPEEPAY | 082100000003 | Inquiry - Time Out
SHOPEEPAY | 082100000004 | Inquiry - Invoice Has Been Paid
SHOPEEPAY | 082100000005 | Inquiry - Incorrect Destination Number
SHOPEEPAY | 082100000006 | Payment - Payment Failed
SHOPEEPAY | 082100000007 | Payment - Pending / transaction in process
SHOPEEPAY | 082100000008 | Payment - MISC Error / Biller System Error

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
  "code"     : "SHOPEEPAY",
  "hp"       : "082100000001",
  "ref_id"   : "pasca-978994691278",
  "sign"     : "6c6a046a14c444e44cfab5e4bbb01b01",
  "desc"     : {
    "amount" : 100000
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
	<code>SHOPEEPAY</code>
	<hp>082100000001</hp>
	<ref_id>pasca-978994691278</ref_id>
	<sign>6c6a046a14c444e44cfab5e4bbb01b01</sign>
	<desc>
		<amount>100000</amount>
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
desc.**footer** | String | Product description | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 131024523,
    "code": "SHOPEEPAY",
    "hp": "082100000001",
    "tr_name": "IAK Sandbox Inquiry",
    "period": "",
    "nominal": 100000,
    "admin": 800,
    "ref_id": "pasca-978994691278",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 100800,
    "selling_price": 100350,
    "desc": {
      "footer": ""
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
  <tr_id>131024523</tr_id>
  <code>SHOPEEPAY</code>
  <hp>082100000001</hp>
  <tr_name>IAK Sandbox Inquiry</tr_name>
  <period></period>
  <nominal>100000</nominal>
  <admin>800</admin>
  <ref_id>pasca-978994691278</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>100800</price>
  <selling_price>100350</selling_price>
  <desc>
    <footer></footer>
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
    "code": "SHOPEEPAY",
    "hp": "082100000001",
    "ref_id": "pasca-978994691278",
    "sign": "{your sign}",
    "desc": {
      "amount": 100000
    }
  }
}
```
