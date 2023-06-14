# Payment Custom Denom

API to pay Custom Denom.

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
  "tr_id"    : "24462352",
  "sign"     : "e4fe9e9c8ba737d6897e7f15bb1380a0"
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
    <tr_id>24462352</tr_id>
    <sign>e4fe9e9c8ba737d6897e7f15bb1380a0</sign>
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
hp | String | Custom Denom payment code | Yes
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
    "datetime": "20230519152953",
    "hp": "082100000001",
    "tr_name": "IAK Sandbox Inquiry",
    "period": "",
    "nominal": 100000,
    "admin": 800,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 100800,
    "selling_price": 100350,
    "balance": 999899650,
    "noref": "f08ff5e3-8543-42a1-b885-04b9f1b521d4",
    "ref_id": "pasca-1684484973",
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
		<datetime>20230519152953</datetime>
		<hp>082100000001</hp>
		<tr_name>IAK Sandbox Inquiry</tr_name>
		<period></period>
		<nominal>100000</nominal>
		<admin>800</admin>
		<response_code>00</response_code>
		<message>PAYMENT SUCCESS</message>
		<price>100800</price>
		<selling_price>100350</selling_price>
		<balance>999899650</balance>
		<noref>f08ff5e3-8543-42a1-b885-04b9f1b521d4</noref>
		<ref_id>pasca-1684484973</ref_id>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "24462352",
    "sign": "{your sign}"
  }
}
```
