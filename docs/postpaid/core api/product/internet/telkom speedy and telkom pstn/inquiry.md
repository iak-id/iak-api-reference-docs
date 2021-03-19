# Inquiry Internet Telkom Speedy and Telkom PSTN

API to inquiry internet telkom speedy and telkom pstn.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
TELKOMPSTN | 6391601201 | Success - 1 bills
TELKOMPSTN | 6391601202 | Success - 3 bills
TELKOMPSTN | 6391601203 | Inquiry - Time Out
TELKOMPSTN | 6391601204 | Inquiry - Invoice Has Been Paid
TELKOMPSTN | 6391601205 | Inquiry - Incorrect Destination Number
TELKOMPSTN | 6391601206 | Payment - Payment Failed
TELKOMPSTN | 6391601207 | Payment - Pending / transaction in process
TELKOMPSTN | 6391601208 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Internet customer number | Yes
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
  "code"	    : "TELKOMPSTN",
  "hp"        : "6391601202",
  "ref_id"	  : "091283746520",
  "sign"	    : "3bb08f003963c2b18310aa5f339a215d"
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
  <code>TELKOMPSTN</code>
  <hp>6391601202</hp>
  <ref_id>0912837465</ref_id>
  <sign>4275ce4770b72af07b5b7dcba1cc3d81</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Internet customer number | Yes
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
desc.**tagihan** | Object | Invoice data | Yes
desc.tagihan.**detail** | Array | Invoice detail per month | Yes
desc.tagihan.detail.**periode** | String | Bill period for detailed month | Yes
desc.tagihan.detail.**nilai_tagihan** | String | Bill value for detailed month | Yes
desc.tagihan.detail.**admin** | String | Admin fee for detailed month | Yes
desc.tagihan.detail.**total** | String | Bill total for detailed month | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732432,
    "code": "TELKOMPSTN",
    "hp": "6391601202",
    "tr_name": "JAORAH",
    "period": "201405,201407",
    "nominal": 129610,
    "admin": 7500,
    "ref_id": "09128374659",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 137110,
    "selling_price": 133510,
    "desc": {
      "kode_area": "0751",
      "divre": "01",
      "datel": "0006",
      "jumlah_tagihan": 3,
      "tagihan": {
        "detail": [
          {
            "periode": "MEI 2014",
            "nilai_tagihan": "49870",
            "admin": "2500",
            "total": 52370
          },
          {
            "periode": "JUN 2014",
            "nilai_tagihan": "44870",
            "admin": "2500",
            "total": 47370
          },
          {
            "periode": "JUL 2014",
            "nilai_tagihan": "34870",
            "admin": "2500",
            "total": 37370
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
	<tr_id>9732432</tr_id>
	<code>TELKOMPSTN</code>
	<hp>6391601202</hp>
	<tr_name>JAORAH</tr_name>
	<period>201405,201407</period>
	<nominal>129610</nominal>
	<admin>7500</admin>
	<ref_id>1500974395</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>137110</price>
	<selling_price>135910</selling_price>
	<desc>
		<kode_area>0751</kode_area>
		<divre>01</divre>
		<datel>0006</datel>
		<jumlah_tagihan>3</jumlah_tagihan>
		<tagihan>
			<detail>
				<periode>MEI 2014</periode>
				<nilai_tagihan>49870</nilai_tagihan>
				<admin>2500</admin>
				<total>52370</total>
			</detail>
			<detail>
				<periode>JUN 2014</periode>
				<nilai_tagihan>44870</nilai_tagihan>
				<admin>2500</admin>
				<total>47370</total>
			</detail>
			<detail>
				<periode>JUL 2014</periode>
				<nilai_tagihan>34870</nilai_tagihan>
				<admin>2500</admin>
				<total>37370</total>
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
    "code": "TELKOMPSTN",
    "hp": "6391601202",
    "ref_id": "091283746520",
    "sign": "{your sign}"
  }
}
```
