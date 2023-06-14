# Inquiry PLN Postpaid

API to inquiry PLN postpaid.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
PLNPOSTPAID | 530000000001 | Success - 1 bill
PLNPOSTPAID | 530000000002 | Success - 8 bills
PLNPOSTPAID | 530000000003 | Inquiry - Time Out
PLNPOSTPAID | 530000000004 | Inquiry - Invoice Has Been Paid
PLNPOSTPAID | 530000000005 | Inquiry - Incorrect Destination Number
PLNPOSTPAID | 530000000006 | Payment - Payment Failed
PLNPOSTPAID | 530000000007 | Payment - Pending / transaction in process
PLNPOSTPAID | 530000000008 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | PLN postpaid customer number | Yes
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
  "code"	    : "PLNPOSTPAID",
  "hp"	      : "530000000001",
  "ref_id"    : "09128374655",
  "sign"	    : "1ac8362ae9a517eadf4a47715555b022"
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
  <code>PLNPOSTPAID</code>
  <hp>530000000001</hp>
  <ref_id>09128374655</ref_id>
  <sign>1ac8362ae9a517eadf4a47715555b022</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | PLN postpaid customer number | Yes
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
desc.**tarif** | String | Electrical fare group | Yes
desc.**daya** | Integer | Electrical power | Yes
desc.**lembar_tagihan** | String | Number of bills | Yes
desc.**tagihan** | Object | Bill detail | Yes
desc.tagihan.**detail** | Array | Bill detail | Yes
desc.tagihan.detail.**periode** | String | Bill period for detailed month | Yes
desc.tagihan.detail.**nilai_tagihan** | String | Bill amount for detailed month | Yes
desc.tagihan.detail.**admin** | String | Admin fee for detailed month | Yes
desc.tagihan.detail.**denda** | String | Penalty fee for detailed month | Yes
desc.tagihan.detail.**total** | Double | Bill total for detailed month | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732792,
    "code": "PLNPOSTPAID",
    "hp": "530000000001",
    "tr_name": "SUBCRIBER NAME",
    "period": "201608",
    "nominal": 300000,
    "admin": 2500,
    "ref_id": "09128374655",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 302500,
    "selling_price": 301900,
    "desc": {
      "tarif": "R1",
      "daya": 1300,
      "lembar_tagihan": "1",
      "tagihan": {
        "detail": [
          {
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
	<hp>530000000001</hp>
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
    "code": "PLNPOSTPAID",
    "hp"	      : "530000000001",
    "ref_id"    : "09128374655",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os