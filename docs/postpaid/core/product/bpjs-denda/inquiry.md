# Inquiry BPJS Denda

API to inquiry BPJS Denda.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
BPJSDENDA | 099994301101 | Success
BPJSDENDA | 099994301103 | Inquiry - Time Out
BPJSDENDA | 099994301104 | Inquiry - Invoice Has Been Paid
BPJSDENDA | 099994301105 | Inquiry - Incorrect Destination Number
BPJSDENDA | 099994301106 | Payment - Payment Failed
BPJSDENDA | 099994301107 | Payment - Pending / transaction in process
BPJSDENDA | 099994301108 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | BPJS participant number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "BPJSDENDA",
  "hp"       : "099994301101",
  "ref_id"   : "091283746511",
  "sign"     : "6515c5094421834a85ed9ac7a0fe443b",
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
  <code>BPJSDENDA</code>
  <hp>099994301101</hp>
  <ref_id>091283746511</ref_id>
  <sign>6515c5094421834a85ed9ac7a0fe443b</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | BPJS participant number | Yes
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
desc.**kode_cabang** | String | Code of BPJS branch | Yes
desc.**nama_badan_usaha** | String | Name of company | Yes
desc.**nama_cabang** | String | Name of BPJS branch | Yes
desc.**sisa_pembayaran** | String | Residual payment | Yes
desc.**jumlah_peserta** | String | BPJS participant | Yes

<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"tr_id": 239356798,
		"code": "BPJSDENDA",
		"hp": "099994301101",
		"tr_name": "RIS** A* DZUH**",
		"period": "0,1",
		"nominal": 108810,
		"admin": 2500,
		"ref_id": "091283746511",
		"response_code": "00",
		"message": "INQUIRY SUCCESS",
		"price": 111310,
		"selling_price": 110160,
		"desc": {
			"nama_badan_usaha": "RESKA MULTI USAHA PT PUSAT",
			"kode_cabang": "",
			"nama_cabang": "",
			"sisa_pembayaran": "",
			"jumlah_peserta": 1
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
  <tr_id>239356798</tr_id>
  <code>BPJSDENDA</code>
  <hp>099994301101</hp>
  <tr_name>RIS** A* DZUH**</tr_name>
  <period>0,1</period>
  <nominal>50108810000</nominal>
  <admin>2500</admin>
  <ref_id>091283746511</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>111310</price>
  <selling_price>110160</selling_price>
  <desc>
    <nama_badan_usaha>RESKA MULTI USAHA PT PUSAT</nama_badan_usaha>
    <kode_cabang></kode_cabang>
    <nama_cabang></nama_cabang>
    <sisa_pembayaran></sisa_pembayaran>
    <jumlah_peserta>1</jumlah_peserta>
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
    "code": "BPJSDENDA",
    "hp": "099994301101",
    "ref_id": "091283746512",
    "sign": "{your sign}"
  }
}
```
