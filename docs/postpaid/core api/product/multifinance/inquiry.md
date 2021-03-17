# Inquiry Multifinance

API to inquiry multifinance.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
FNMEGA | 6391601201 | Success
FNMEGA | 6391601203 | Inquiry - Time Out
FNMEGA | 6391601204 | Inquiry - Invoice Has Been Paid
FNMEGA | 6391601205 | Inquiry - Incorrect Destination Number
FNMEGA | 6391601206 | Payment - Payment Failed
FNMEGA | 6391601207 | Payment - Pending / transaction in process
FNMEGA | 6391601208 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Contract number | Yes
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
  "code" 	    : "FNMEGA",
  "hp"	      : "6391601201",
  "ref_id"	  : "09128374652",
  "sign"	    : "3743ec3e02f9076ea56e2f61be698a8e"
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
  <username>082210138584</username>
  <code>FNMEGA</code>
  <hp>6391601201</hp>
  <ref_id>09128374652</ref_id>
  <sign>3743ec3e02f9076ea56e2f61be698a8e</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Gas negara customer number | Yes
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
desc.**misc_fee** | Double | Other fee | Yes
desc.**item_name** | String | Item name | Yes
desc.**no_rangka** | String | Chassis number | Yes
desc.**no_pol** | String | Police number | Yes
desc.**tenor** | String | Tenor | Yes
desc.**installment** | Double | Installment fee | Yes
desc.**penalty_bill** | Double | Penalty fee | Yes
desc.**max_payment** | Double | Max payment | Yes
desc.**last_paid_due_date** | String | Last paid due date | Yes
desc.**id_ref** | String | Finance reff number | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732789,
    "code": "FNMEGA",
    "hp": "6391601201",
    "tr_name": "ABDUL SAMID HARAHAP",
    "period": "005",
    "nominal": 661000,
    "admin": 0,
    "ref_id": "09128374652",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 661000,
    "selling_price": 660500,
    "desc": {
      "misc_fee": 0,
      "item_name": "HONDA VARIO TECHNO 125 PGM FI NON CBS",
      "no_rangka": "MH1JFB111CK196426",
      "no_pol": "B6213UWX",
      "tenor": "030",
      "installment": 657695,
      "penalty_bill": 3305,
      "max_payment": 0,
      "last_paid_due_date": "14 Dec 12",
      "id_ref": "514367"
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
  <tr_id>9732789</tr_id>
  <code>FNMEGA</code>
  <hp>6391601201</hp>
  <tr_name>ABDUL SAMID HARAHAP</tr_name>
  <period>005</period>
  <nominal>661000</nominal>
  <admin>0</admin>
  <ref_id>09128374652</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>661000</price>
  <selling_price>660500</selling_price>
  <desc>
    <misc_fee>0</misc_fee>
    <item_name>HONDA VARIO TECHNO 125 PGM FI NON CBS</item_name>
    <no_rangka>MH1JFB111CK196426</no_rangka>
    <no_pol>B6213UWX</no_pol>
    <tenor>030</tenor>
    <installment>657695</installment>
    <penalty_bill>3305</penalty_bill>
    <max_payment>0</max_payment>
    <last_paid_due_date>14 Dec 12</last_paid_due_date>
    <id_ref>514367</id_ref>
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
    "code": "FNMEGA",
    "hp": "6391601201",
    "ref_id": "09128374652",
    "sign": "{your sign}"
  }
}
```
