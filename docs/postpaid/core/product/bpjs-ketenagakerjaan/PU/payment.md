# Payment BPJS Ketenagakerjaan Penerima Upah

API to pay BPJS Ketenagakerjaan Penerima Upah (PU).

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
  "tr_id"    : "9732787",
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
    <tr_id>9732787</tr_id>
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
hp | String | NIK | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
response_code | String | Response code. See [response code](../../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
balance | Double | Client remaining balance | Yes
noref | String | Biller reference number (if exist) | No
ref_id | String | Your order number / reference ID ( must unique ) | Yes
desc | Object | Product description | Yes
desc.**kode_iuran** | String | 	Contribution Code | Yes
desc.**kode_program** | String | 	Choosen Program Code | Yes
desc.**jht** | String | 	Pension Plan Fee | Yes
desc.**jkk** | String | 	Accident Insurance Fee | Yes
desc.**jkm** | String | 	Death Insurance Fee | Yes
desc.**jpk** | String | 	Lost Job Fee | Yes
desc.**jpn** | String | 	Pension Plan Fee | Yes

<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"tr_id": 219342904,
		"code": "BPJSTKPU",
		"datetime": "20220519163651",
		"hp": "210300016066",
		"tr_name": "PT LIMABELAS",
		"period": "202104",
		"nominal": 100000,
		"admin": 2500,
		"response_code": "00",
		"message": "PAYMENT SUCCESS",
		"price": 102500,
		"selling_price": 100500,
		"balance": 998359000,
		"noref": "iak62860fafe04c3",
		"ref_id": "ref-19_May_2022_16.36.47",
		"desc": {
			"kode_iuran": "210300016066",
			"kode_program": "",
			"jht": 61688,
			"jkk": 1082,
			"jkm": 2166,
			"jpk": 2597,
			"jpn": 32467
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
	<tr_id>219342904</tr_id>
	<code>BPJSTKPU</code>
	<datetime>20220519163651</datetime>
	<hp>210300016066</hp>
	<tr_name>PT LIMABELAS</tr_name>
	<period>202104</period>
	<nominal>100000</nominal>
	<admin>2500</admin>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>102500</price>
	<selling_price>100500</selling_price>
	<balance>998359000</balance>
	<noref>iak62860fafe04c3</noref>
	<ref_id>ref-19_May_2022_16.36.47</ref_id>
	<desc>
		<kode_iuran>210300016066</kode_iuran>
		<kode_program></kode_program>
		<jht>61688</jht>
		<jkk>1082</jkk>
		<jkm>2166</jkm>
		<jpk>2597</jpk>
		<jpn>32467</jpn>
	</desc>
</mp>
```
<!-- type: tab-end -->
