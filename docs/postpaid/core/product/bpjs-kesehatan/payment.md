# Payment BPJS Kesehatan

API to pay BPJS Kesehatan.

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
    "datetime": "20180803170750",
    "hp": "8801234560001",
    "tr_name": "VERGIE",
    "period": "02",
    "nominal": 50000,
    "admin": 2500,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 52500,
    "selling_price": 52300,
    "balance": 999490800,
    "noref": "148732328035714773",
    "ref_id": "091283746511",
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
  <datetime>20170725124941</datetime>
  <hp>8801234560001</hp>
  <tr_name>VERGIE</tr_name>
  <period>02</period>
  <nominal>50000</nominal>
  <admin>2500</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>52500</price>
  <selling_price>52500</selling_price>
  <balance>75899043</balance>
  <noref>148732328035714773</noref>
  <ref_id>1500961531</ref_id>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "9732787",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM