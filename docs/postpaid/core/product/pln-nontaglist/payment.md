# Payment PLN NONTAGLIST Postpaid

API to pay PLN Non Taglist Postpaid.

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
tr_id | String | IAK inquiry ID | Yes
sign | String | Signature. Value: `md5(username+api_key+tr_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "pay-pasca",
  "username" : "123123123",
  "tr_id"    : "219346114",
  "sign"     : "7c22017cf8c1d137f16c83c03a5aced2"
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
  <tr_id>219346114</tr_id>
  <sign>7c22017cf8c1d137f16c83c03a5aced2</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
datetime | String | Transaction Date | Yes
hp | String | PLN Non Taglist customer number | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
response_code | String | Response code. See [response code](../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
balance | Integer | Current balance | Yes
noref | String | Partner transaction id (if available) | Yes
ref_id | String | Your order number / reference ID. Value: ```ref- + timestamp(D_MMMM_Y_H.mm.ss)``` ( must unique ) | Yes
desc | Object | Product description | Yes
desc.**transaksi** | String | Transaction information | Yes
desc.**no_registrasi** | String | Registration number | Yes
desc.**tanggal_registrasi** | String | Registration date | Yes


<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"tr_id": 219346114,
		"code": "PLNNONH",
		"datetime": "20230103171240",
		"hp": "3225030005922",
		"tr_name": "JAYUSMAN",
		"period": "",
		"nominal": 696400,
		"admin": 1600,
		"response_code": "00",
		"message": "PAYMENT SUCCESS",
		"price": 698000,
		"selling_price": 696200,
		"balance": 726424608,
		"noref": "18147159",
		"ref_id": "09128374655",
		"desc": {
			"transaksi": "PENYAMBUNGAN BARU",
			"no_registrasi": "5392112011703",
			"tanggal_registrasi": "20120524"
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
	<tr_id>219346114</tr_id>
	<code>PLNNONH</code>
	<hp>3225030005922</hp>
	<tr_name>SUBCRIBER NAME</tr_name>
	<period></period>
	<nominal>696400</nominal>
	<admin>1600</admin>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>698000</price>
	<selling_price>696200</selling_price>
  <balance>726424608</balance>
  <noref>18147159</noref>
  <ref_id>09128374655</ref_id>
	<desc>
		<transaksi>PENYAMBUNGAN BARU</transaksi>
		<no_registrasi>5392112011703</daya>
		<tanggal_registrasi>20120524</lembar_tagihan>
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
    "code": "PLNNONH",
    "hp"	      : "3225030005922",
    "ref_id"    : "09128374655",
    "sign": "{your sign}"
  }
}
```
