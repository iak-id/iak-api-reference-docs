# Payment PBB

API to pay PBB.

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
  "commands" : "inq-pasca",
  "username" : "123123123",
  "tr_id"    : "24462730",
  "sign"     : "8ad94262a61ac27676a8b2b11fb80ee2"
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
  <tr_id>24462730</tr_id>
  <sign>8ad94262a61ac27676a8b2b11fb80ee2</sign>
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
hp | String | Tax object number | Yes
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
    "datetime": "20190916152947",
    "hp": "329801092375999901",
    "tr_name": "TESTING PBB",
    "period": "201909",
    "nominal": 203857,
    "admin": 5000,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 208857,
    "selling_price": 208857,
    "balance": 274686,
    "noref": "190814738977",
    "ref_id": "9955945110828",
    "desc": {
      "tanggal": "2019-08-14 13:57:54",
      "nop": "328073000401005610",
      "tahun_pajak": "2019",
      "lokasi": "KO. GRIYA ASRI CIPAGERAN",
      "kelurahan": "CIPAGERAN",
      "kecamatan": "CIMAHI UTARA",
      "kode_kab_kota": "0023",
      "kab_kota": "PEMKOT CIMAHI",
      "luas_tanah": "113 M2",
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
  <datetime>20190916152947</datetime>
  <hp>329801092375999901</hp>
  <tr_name>TESTING PBB</tr_name>
  <period>201909</period>
  <nominal>203857</nominal>
  <admin>5000</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>208857</price>
  <selling_price>208857</selling_price>
  <balance>274686</balance>
  <noref>190814738977</noref>
  <ref_id>9955945110828</ref_id>
  <desc>
    <tanggal>2019-08-14 13:57:54</tanggal>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "24462730",
    "sign": "{your sign}"
  }
}
```
