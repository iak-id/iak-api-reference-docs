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
  "tr_id"    : "9732792",
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
  <tr_id>9732792</tr_id>
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
ref_id | String | Your order number / reference ID ( must unique ) | Yes
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
		"hp": "10202001",
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
		"ref_id": "ref-3_January_2023_17.12.19",
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
	<tr_id>9732792</tr_id>
	<code>PLNNONH</code>
	<hp>10202001</hp>
	<tr_name>SUBCRIBER NAME</tr_name>
	<period>201608</period>
	<nominal>300000</nominal>
	<admin>2500</admin>
	<ref_id>09128374655</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>302500</price>
	<selling_price>302500</selling_price>
	<desc>
		<tarif>R1</tarif>
		<daya>1300</daya>
		<lembar_tagihan>1</lembar_tagihan>
		<tagihan>
			<detail>
				<periode>201608</periode>
				<nilai_tagihan>300000</nilai_tagihan>
				<admin>2500</admin>
				<denda>0</denda>
				<total>302500</total>
			</detail>
		</tagihan>
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
    "hp"	      : "10202001",
    "ref_id"    : "09128374655",
    "sign": "{your sign}"
  }
}
```
