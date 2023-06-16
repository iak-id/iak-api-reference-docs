# Payment PLN Postpaid

API to pay PLN postpaid.

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
  "tr_id"    : "9732792",
  "sign"     : "a24472de52b037dc0df624f88ae2a5cb"
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
  <sign>a24472de52b037dc0df624f88ae2a5cb</sign>
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
hp | String | PLN postpaid customer number | Yes
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
desc.**tarif** | String | Electrical fare group | Yes
desc.**daya** | Integer | Electrical power | Yes
desc.**lembar_tagihan** | String | Number of bills | Yes
desc.**lembar_tagihan_sisa** | Integer | Number of bills remaining after payment | Yes
desc.**tagihan** | Object | Bill detail | Yes
desc.tagihan.**detail** | Array | Bill detail | Yes
desc.tagihan.detail.**meter_awal** | String | Initial meter value for detailed month | Yes
desc.tagihan.detail.**meter_akhir** | String | Final meter value for detailed month | Yes
desc.tagihan.detail.**periode** | String | Bill period for detailed month | Yes
desc.tagihan.detail.**nilai_tagihan** | String | Bill amount for detailed month | Yes
desc.tagihan.detail.**admin** | String | Admin fee for detailed month | Yes
desc.tagihan.detail.**denda** | String | Penalty fee for detailed month | Yes
desc.tagihan.detail.**total** | Double | Bill total for detailed month | Yes

<!-- theme: info -->

> If **lembar_tagihan_sisa** return value > 0, then you have to include it in your receipt (maximal 4 bill
> quantities per transaction).

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732792,
    "code": "PLNPOSTPAID",
    "datetime": "20180803171844",
    "hp": "530000000001",
    "tr_name": "SUBCRIBER NAME",
    "period": "201608",
    "nominal": 300000,
    "admin": 2500,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 302500,
    "selling_price": 301900,
    "balance": 997586108,
    "noref": "004212C9245F1BA43A77CEBD5CD5DA39",
    "ref_id": "09128374655",
    "desc": {
      "tarif": "R1",
      "daya": 1300,
      "lembar_tagihan": "1",
      "lembar_tagihan_sisa": 0,
      "tagihan": {
        "detail": [
          {
            "meter_awal": "00080000",
            "meter_akhir": "00080000",
            "periode": "201608",
            "nilai_tagihan": "300000",
            "admin": "2500",
            "denda": "0",
            "total": 302500
          }
        ]
      }
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
	<code>PLNPOSTPAID</code>
	<datetime>20170725153910</datetime>
	<hp>530000000001</hp>
	<tr_name>SUBCRIBER NAME</tr_name>
	<period>201608</period>
	<nominal>300000</nominal>
	<admin>2500</admin>
	<response_code>00</response_code>
	<message>PAYMENT SUCCESS</message>
	<price>302500</price>
	<selling_price>301900</selling_price>
	<balance>73657753</balance>
	<no_ref>004212C9245F1BA43A77CEBD5CD5DA39</no_ref>
	<ref_id>09128374655</ref_id>
	<desc>
		<tarif>R1</tarif>
		<daya>1300</daya>
		<lembar_tagihan>1</lembar_tagihan>
		<lembar_tagihan_sisa>0</lembar_tagihan_sisa>
		<tagihan>
			<detail>
				<meter_awal>00080000</meter_awal>
				<meter_akhir>00080000</meter_akhir>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "9732792",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM