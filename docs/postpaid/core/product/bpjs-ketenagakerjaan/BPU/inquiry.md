# Inquiry

API to inquiry BPJS Kesehatan Bukan Pemberi Upah (BPU).

## Path

Method | Path
---------|----------
POST | api/v1/bill/check

## Test Case

Code | Number | Response
---------|----------|---------
BPJSTK | 1271215712960003 | Success

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | NIK | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes
month | Integer | Number of month you're willing to pay | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "BPJSTK",
  "hp"       : "1271215712960003",
  "ref_id"   : "091283746511",
  "sign"     : "6515c5094421834a85ed9ac7a0fe443b",
  "month"    : 1
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
  <code>BPJSTK</code>
  <hp>1271215712960003</hp>
  <ref_id>091283746511</ref_id>
  <sign>6515c5094421834a85ed9ac7a0fe443b</sign>
  <month>1</month>
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
period | String | Number of month to pay | Yes
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
desc.**kode_program** | String | 	Chosen Program Code | Yes
desc.**jht** | Integer | 	Pension Plan Fee | Yes
desc.**jkk** | Integer | 	Accident Insurance Fee | Yes
desc.**jkm** | Integer | 	Death Insurance Fee | Yes
desc.**kantor_cabang** | String | 	Branch Office | Yes
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
		"hp": "1271215712960003",
		"tr_name": "DWI TAMARA ANGGITA",
		"period": "1",
		"nominal": 16800,
		"admin": 3500,
		"ref_id": "091283746511",
		"response_code": "00",
		"message": "INQUIRY SUCCESS",
		"price": 20300,
		"selling_price": 17800,
		"desc": {
			"kode_iuran": "",
			"kode_program": "JKK,JKM",
			"jht": 0,
			"jkk": 10000,
			"jkm": 6800,
      "kantor_cabang": "KABUPATEN TANGERANG",
			"tgl_efektif": "05-11-2022",
			"tgl_expired": "09-10-2026"
		}
	},
	"meta": []
}.

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
	<hp>1271215712960003</hp>
	<tr_name>DWI TAMARA ANGGITA</tr_name>
	<period>1</period>
	<nominal>16800</nominal>
	<admin>3500</admin>
	<ref_id>091283746511</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>20300</price>
	<selling_price>17800</selling_price>
	<desc>
		<kode_iuran></kode_iuran>
		<kode_program>JKK,JKM</kode_program>
		<jht>0</jht>
		<jkk>10000</jkk>
		<jkm>6800</jkm>
    <kantor_cabang>KABUPATEN TANGERANG</kantor_cabang>
		<tgl_efektif>2022-05-11</tgl_efektif>
		<tgl_expired>2024-08-10</tgl_expired>
	</desc>
</mp>
```
<!-- type: tab-end -->