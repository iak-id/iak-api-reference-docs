# Inquiry BPJS Kesehatan

API to inquiry BPJS Kesehatan.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
BPJS | 8801234560001 | Success
BPJS | 8801234560003 | Inquiry - Time Out
BPJS | 8801234560004 | Inquiry - Invoice Has Been Paid
BPJS | 8801234560005 | Inquiry - Incorrect Destination Number
BPJS | 8801234560006 | Payment - Payment Failed
BPJS | 8801234560007 | Payment - Pending / transaction in process
BPJS | 8801234560008 | Payment - MISC Error / Biller System Error

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
month | Integer | Number of month you're willing to pay | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "BPJS",
  "hp"       : "8801234560001",
  "ref_id"   : "091283746511",
  "sign"     : "6515c5094421834a85ed9ac7a0fe443b",
  "month"    : "2"
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
  <code>BPJS</code>
  <hp>8801234560001</hp>
  <ref_id>0912837465</ref_id>
  <sign>6515c5094421834a85ed9ac7a0fe443b</sign>
  <month>2</month>
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
    "tr_id": 9732787,
    "code": "BPJS",
    "hp": "8801234560001",
    "tr_name": "VERGIE",
    "period": "02",
    "nominal": 50000,
    "admin": 2500,
    "ref_id": "09128374651",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 52500,
    "selling_price": 52300,
    "desc": {
      "kode_cabang": "0901",
      "nama_cabang": "JAKARTA PUSAT",
      "sisa_pembayaran": "0",
      "jumlah_peserta": "2"
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
  <tr_id>9732787</tr_id>
  <code>BPJS</code>
  <hp>8801234560001</hp>
  <tr_name>VERGIE</tr_name>
  <period>02</period>
  <nominal>50000</nominal>
  <admin>2500</admin>
  <ref_id>1500961531</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>52500</price>
  <selling_price>52500</selling_price>
  <desc>
    <kode_cabang>0901</kode_cabang>
    <nama_cabang>JAKARTA PUSAT</nama_cabang>
    <sisa_pembayaran>0</sisa_pembayaran>
    <jumlah_peserta>2</jumlah_peserta>
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
    "code": "BPJS",
    "hp": "8801234560001",
    "ref_id": "0912837465",
    "sign": "{your sign}",
    "month": "2"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os