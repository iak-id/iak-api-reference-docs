# Payment BPJS Denda

API to pay BPJS Denda.

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
hp | String | BPJS participant number | Yes
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
desc.**premi** | String | Amount that need to be paid | Yes
desc.**kode_cabang** | String | Code of BPJS branch | Yes
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
		"datetime": "20220616104645",
		"hp": "099994301101",
		"tr_name": "RIS** A* DZUH**",
		"period": "0,1",
		"nominal": 108810,
		"admin": 2500,
		"response_code": "00",
		"message": "PAYMENT SUCCESS",
		"price": 111310,
		"selling_price": 110160,
		"balance": 999968076430,
		"noref": "239356524",
		"ref_id": "091283746511",
		"desc": {
			"premi": 0,
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
  <datetime>20220616104645</datetime>
  <hp>099994301101</hp>
  <tr_name>RIS** A* DZUH**</tr_name>
  <period>0,1</period>
  <nominal>108810</nominal>
  <admin>2500</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>111310</price>
  <selling_price>110160</selling_price>
  <balance>999968076430</balance>
  <noref>239356524</noref>
  <ref_id>091283746511</ref_id>
  <desc>
    <premi>0</premi>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "239356798",
    "sign": "{your sign}"
  }
}
```
