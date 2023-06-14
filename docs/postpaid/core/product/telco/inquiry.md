# Inquiry Telco Postpaid

API to inquiry telco postpaid.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
HPTHREE | 08991234501 | Success
HPTHREE | 08991234503 | Inquiry - Time Out
HPTHREE | 08991234504 | Inquiry - Invoice Has Been Paid
HPTHREE | 08991234505 | Inquiry - Incorrect Destination Number
HPTHREE | 08991234506 | Payment - Payment Failed
HPTHREE | 08991234507 | Payment - Pending / transaction in process
HPTHREE | 08991234508 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Telco postpaid customer number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands"	: "inq-pasca",
  "username"	: "123123123",
  "code"	: "HPTHREE",
  "hp"        : "08991234501",
  "ref_id"    : "09128374658",
  "sign"	: "1231656ad1449ea56be648495e195ea4"
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
  <code>HPTHREE</code>
  <hp>08991234501</hp>
  <ref_id>09128374658</ref_id>
  <sign>1231656ad1449ea56be648495e195ea4</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Telco postpaid customer number | Yes
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
desc.**kode_area** | String | Area code | Yes
desc.**divre** | String | Divre | Yes
desc.**datel** | String | Datel | Yes
desc.**jumlah_tagihan** | Integer | Number of invoice | Yes
desc.**tagihan** | Object | Invoice data | Yes
desc.tagihan.**detail** | Array | Detail of invoice per month | Yes
desc.tagihan.detail.**periode** | String | Bill period for detailed month | Yes
desc.tagihan.detail.**nilai_tagihan** | String | Bill amount for detailed month | Yes
desc.tagihan.detail.**admin** | String | Admin fee for detailed month | Yes
desc.tagihan.detail.**total** | String | Bill total for detailed month | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732412,
    "code": "HPTHREE",
    "hp": "08991234501",
    "tr_name": "INTAN NUR AZIZA",
    "period": "",
    "nominal": 55000,
    "admin": 0,
    "ref_id": "09128374658",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 55000,
    "selling_price": 54000,
    "desc": {
      "kode_area": "",
      "divre": "",
      "datel": "",
      "jumlah_tagihan": 1,
      "tagihan": {
        "detail": [
          {
            "periode": "",
            "nilai_tagihan": "",
            "admin": "",
            "total": ""
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
	<tr_id>9732412</tr_id>
	<code>HPTHREE</code>
	<hp>08991234501</hp>
	<tr_name>INTAN NUR AZIZA</tr_name>
	<period></period>
	<nominal>55000</nominal>
	<admin>0</admin>
	<ref_id>09128374658</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>55000</price>
	<selling_price>54000</selling_price>
	<desc>
		<kode_area></kode_area>
		<divre></divre>
		<datel></datel>
		<jumlah_tagihan>1</jumlah_tagihan>
		<tagihan>
			<detail>
				<periode></periode>
				<nilai_tagihan></nilai_tagihan>
				<admin></admin>
				<total></total>
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
    "commands"  : "inq-pasca",
    "username"  : "{your username}",
    "code"      : "HPTHREE",
    "hp"	      : "530000000001",
    "ref_id"    : "09128374658",
    "sign"      : "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os