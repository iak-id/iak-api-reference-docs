# Inquiry PLN NONTAGLIST Postpaid

API to inquiry PLN NONTAGLIST postpaid.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
PLNNONH | 3225030005922 | Success
PLNNONH | 1811217010329 | Success
PLNNONH | 3226015008229 | Success

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | PLN Non Taglist customer number | Yes
ref_id | String | Your order number / reference ID. Value: ```ref- + timestamp(D_MMMM_Y_H.mm.ss)``` ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands"	: "inq-pasca",
  "username"	: "123123123",
  "code"	    : "PLNNONH",
  "hp"	      : "3225030005922",
  "ref_id"    : "09128374655",
  "sign"	    : "0f32cc44bb9469687ef24b6ea857db06"
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
  <code>PLNNONH</code>
  <hp>3225030005922</hp>
  <ref_id>09128374655</ref_id>
  <sign>0f32cc44bb9469687ef24b6ea857db06</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | PLN Non Taglist customer number | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
ref_id | String | Your order number / reference ID. Value: ```ref- + timestamp(D_MMMM_Y_H.mm.ss)``` ( must unique ) | Yes
response_code | String | Response code. See [response code](../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
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
		"tr_id": 219346108,
		"code": "PLNNONH",
		"hp": "3225030005922",
		"tr_name": "JAYUSMAN",
		"period": "",
		"nominal": 696400,
		"admin": 1600,
		"ref_id": "09128374655",
		"response_code": "00",
		"message": "INQUIRY SUCCESS",
		"price": 698000,
		"selling_price": 696200,
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
	<tr_id>219346108</tr_id>
	<code>PLNNONH</code>
	<hp>3225030005922</hp>
	<tr_name>SUBCRIBER NAME</tr_name>
	<period></period>
	<nominal>696400</nominal>
	<admin>1600</admin>
	<ref_id>09128374655</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>698000</price>
	<selling_price>696200</selling_price>
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
    "commands": "inq-pasca",
    "username": "{your username}",
    "code": "PLNNONH",
    "hp"	      : "3225030005922",
    "ref_id"    : "09128374655",
    "sign": "{your sign}"
  }
}
```
