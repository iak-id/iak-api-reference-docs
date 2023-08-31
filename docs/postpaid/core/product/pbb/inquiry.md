# Inquiry PBB

API to inquiry PBB.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
PBBKOT.CIMAHI | 329801092375999901 | Success
PBBKOT.CIMAHI | 329801092375999903 | Inquiry - Time Out
PBBKOT.CIMAHI | 329801092375999904 | Inquiry - Invoice Has Been Paid
PBBKOT.CIMAHI | 329801092375999905 | Inquiry - Incorrect Destination Number
PBBKOT.CIMAHI | 329801092375999906 | Payment - Payment Failed
PBBKOT.CIMAHI | 329801092375999907 | Payment - Pending / transaction in process
PBBKOT.CIMAHI | 329801092375999908 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Tax object number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes
year | String | Number of year you're willing to pay | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "PBBKOT.CIMAHI",
  "hp"       : "329801092375999901",
  "ref_id"   : "978994691278",
  "sign"     : "6c6a046a14c444e44cfab5e4bbb01b01"
  "year"     : "2023",
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
  <code>PBBKOT.CIMAHI</code>
  <hp>329801092375999901</hp>
  <ref_id>978994691278</ref_id>
  <sign>6c6a046a14c444e44cfab5e4bbb01b01</sign>
  <year>2023</year>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | Tax object number | Yes
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
desc.**tanggal** | Double | Date | Yes
desc.**nop** | String | Tax object number | Yes
desc.**tahun_pajak** | String | Year of the tax | Yes
desc.**lokasi** | String | Asset location | Yes
desc.**kelurahan** | String | Village office | Yes
desc.**kecamatan** | Double | Districts | Yes
desc.**kab_kota** | Double | Districts / city | Yes
desc.**luas_tanah** | Double | Wide of surface area | Yes
desc.**luas_gedung** | String | Wide of building area | Yes
desc.**jatuh_tempo** | String | Due date | Yes
desc.**total_tagihan** | Float | Total bill | Yes
desc.**denda** | Float | Penalty fee | Yes
desc.**admin** | Integer | Admin fee | Yes
desc.**total_bayar** | Float | Total payment | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 24462730,
    "code": "PBBKOT.CIMAHI",
    "hp": "329801092375999901",
    "tr_name": "TESTING PBB",
    "period": "201909",
    "nominal": 203857,
    "admin": 5000,
    "ref_id": "978994691299",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 208857,
    "selling_price": 208857,
    "desc": {
      "tanggal": "2019-08-14 14:38:59",
      "nop": "328073000401005610",
      "tahun_pajak": "2019",
      "lokasi": "KO. GRIYA ASRI CIPAGERAN",
      "kelurahan": "CIPAGERAN",
      "kecamatan": "CIMAHI UTARA",
      "kode_kab_kota": "0023",
      "kab_kota": "PEMKOT CIMAHI",
      "luas_tanah": "113 M2"
      "luas_gedung": "47 M2",
      "jatuh_tempo": "31/10/2019",
      "total_tagihan": 203857,
      "denda": 0,
      "admin": 5000,
      "total_bayar": 208857
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
  <tr_id>24462730</tr_id>
  <code>PBBKOT.CIMAHI</code>
  <hp>329801092375999901</hp>
  <tr_name>TESTING PBB</tr_name>
  <period>201909</period>
  <nominal>203857</nominal>
  <admin>5000</admin>
  <ref_id>978994691299</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>208857</price>
  <selling_price>208857</selling_price>
  <desc>
    <tanggal>2019-08-14 14:38:59</tanggal>
    <nop>328073000401005610</nop>
    <tahun_pajak>2019</tahun_pajak>
    <lokasi>KO. GRIYA ASRI CIPAGERAN</lokasi>
    <kelurahan>CIPAGERAN</kelurahan>
    <kecamatan>CIMAHI UTARA</kecamatan>
    <kode_kab_kota>0023</kode_kab_kota>
    <kab_kota>PEMKOT CIMAHI</kab_kota>
    <luas_tanah>113 M2</luas_tanah>
    <luas_gedung>47 M2</luas_gedung>
    <jatuh_tempo>31/10/2019</jatuh_tempo>
    <total_tagihan>203857</total_tagihan>
    <denda>0</denda>
    <admin>5000</admin>
    <total_bayar>208857</total_bayar>
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
    "code": "PBBKOT.CIMAHI",
    "hp": "329801092375999901",
    "ref_id": "978994691278",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os