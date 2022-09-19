# Payment BPJS Ketenagakerjaan

API to pay BPJS Ketenagakerjaan Bukan Pemberi Upah (BPU).

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
desc.**tgl_efektif** | String | 	Effective date. Format: `d-m-Y` | Yes
desc.**tgl_expired** | String | 	Expired Date. Format: `d-m-Y` | Yes

<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"tr_id": 219342820,
		"code": "BPJSTK",
		"datetime": "20220514000809",
		"hp": "1271215712960003",
		"tr_name": "DWI TAMARA ANGGITA",
		"period": "1",
		"nominal": 16800,
		"admin": 3500,
		"response_code": "00",
		"message": "PAYMENT SUCCESS",
		"price": 20300,
		"selling_price": 17800,
		"balance": 2436395,
		"noref": "iak627e8f6bba054",
		"ref_id": "ref-14_May_2022_0.03.39",
		"desc": {
			"kode_iuran": "922053115900",
			"kode_program": "JKK,JKM",
			"jht": 0,
			"jkk": 10000,
			"jkm": 6800,
			"tgl_efektif": "2022-05-11 05:29:52",
			"tgl_expired": "2026-09-10 00:00:00"
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
	<tr_id>219342820</tr_id>
	<code>BPJSTK</code>
	<datetime>20220514000809</datetime>
	<hp>1271215712960003</hp>
	<tr_name>DWI TAMARA ANGGITA</tr_name>
	<period>1</period>
	<nominal>16800</nominal>
	<admin>3500</admin>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>20300</price>
	<selling_price>17800</selling_price>
	<balance>2436395</balance>
	<noref>iak627e8f6bba054</noref>
	<ref_id>ref-14_May_2022_0.03.39</ref_id>
	<desc>
		<kode_iuran>922053115900</kode_iuran>
		<kode_program>JKK,JKM</kode_program>
		<jht>0</jht>
		<jkk>10000</jkk>
		<jkm>6800</jkm>
		<tgl_efektif>05-11-2022</tgl_efektif>
		<tgl_expired>08-10-2024</tgl_expired>
	</desc>
</mp>
```
<!-- type: tab-end -->