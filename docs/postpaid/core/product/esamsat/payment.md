# Payment ESAMSAT

API to pay ESAMSAT.

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
  "tr_id"    : "24462352",
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
    <tr_id>24462352</tr_id>
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
hp | String | ESAMSAT payment code | Yes
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
desc.**nomor_identitas** | String | Customer identity number | Yes
desc.**nomor_rangka** | String | Vehicle identification number | Yes
desc.**nomor_mesin** | String | Machine number | Yes
desc.**alamat** | String | Address | Yes
desc.**milik_kenama** | String | Vehicle status whether the vehicle has been sold or not | Yes
desc.**merek_kb** | String | Vehicle brand | Yes
desc.**tahun_buatan** | String | Year made | Yes
desc.**tgl_akhir_pajak_baru** | String | Valid until | Yes
desc.**biaya_pokok** | Object | Basic fee | Yes
desc.biaya_pokok.**BBN** | String | Bea balik nama fee  | Yes
desc.biaya_pokok.**PKB** | String | Pajak kendaraan bermotor fee | Yes
desc.biaya_pokok.**SWD** | String | Sumbangan wajib dana kecelakaan lalu lintas fee | Yes
desc.**biaya_denda** | Object | Penalty fee | Yes
desc.biaya_denda.**BBN** | String | Bea balik nama penalty fee  | Yes
desc.biaya_denda.**PKB** | String | Pajak kendaraan bermotor penalty fee | Yes
desc.biaya_denda.**SWD** | String | Sumbangan wajib dana kecelakaan lalu lintas penalty fee | Yes
desc.**biaya_admin** | Object | Admin fee | Yes
desc.biaya_admin.**stnk** | String | Surat tanda nomor kendaraan admin fee  | Yes
desc.biaya_admin.**tnkb** | String | Tanda nomor kendaraan bermotor admin fee | Yes
desc.**biaya_parkir_pokok** | String | Main parking fee | Yes
desc.**biaya_pajak_progresif** | String | Progressive tax fee | Yes
desc.**ntpd** | String | ESAMSAT transaction number | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 24462352,
    "code": "ESAMSAT.JABAR",
    "datetime": "20190812180154",
    "hp": "9658548523568701",
    "tr_name": "TESTING ESAMSAT",
    "period": "20181022-20191022",
    "nominal": 2274500,
    "admin": 5000,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 2279500,
    "selling_price": 2277000,
    "balance": 999490800,
    "noref": "9658548523568701",
    "ref_id": "978994691299",
    "desc": {
      "nomor_identitas": "0212502110170100",
      "nomor_rangka": "MHKV5EA2JFJ001044",
      "nomor_mesin": "1NRF012268",
      "alamat": "GRIYA BULELENG 2 RT 005 RW 014 BULELENG",
      "nomor_polisi": "DK 1243AL",
      "milik_kenama": "001",
      "merek_kb": "DAIHATSU",
      "model_kb": "XENIA 1.3 R M\/T F653RV-GMDFJ",
      "tahun_buatan": "2018",
      "tgl_akhir_pajak_baru": "20191022",
      "biaya_pokok": {
        "BBN": "0",
        "PKB": "2131500",
        "SWD": "143000"
      },
      "biaya_denda": {
        "BBN": "0",
        "PKB": "0",
        "SWD": "0"
      },
      "biaya_admin": {
        "stnk": "0",
        "tnkb": "0"
      },
      "biaya_parkir_pokok": "0",
      "biaya_pajak_progresif": "0",
      "ntpd": "Q8T3L318R0Z3"
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
  <tr_id>24462352</tr_id>
  <code>ESAMSAT.JABAR</code>
  <datetime>20190812180154</datetime>
  <hp>9658548523568701</hp>
  <tr_name>TESTING ESAMSAT</tr_name>
  <period>20181022-20191022</period>
  <nominal>2274500</nominal>
  <admin>5000</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>2279500</price>
  <selling_price>2277000</selling_price>
  <balance>999490800</balance>
  <noref>9658548523568701</noref>
  <ref_id>978994691299</ref_id>
  <desc>
    <nomor_identitas>0212502110170100</nomor_identitas>
    <nomor_rangka>MHKV5EA2JFJ001044</nomor_rangka>
    <nomor_mesin>1NRF012268</nomor_mesin>
    <alamat>GRIYA BULELENG 2 RT 005 RW 014 BULELENG</alamat>
    <nomor_polisi>DK 1243AL</nomor_polisi>
    <milik_kenama>001</milik_kenama>
    <merek_kb>DAIHATSU</merek_kb>
    <model_kb>XENIA 1.3 R M\/T F653RV-GMDFJ</model_kb>
    <tahun_buatan>2018</tahun_buatan>
    <tgl_akhir_pajak_baru>20191022</tgl_akhir_pajak_baru>
    <biaya_pokok>
      <BBN>0</BBN>
      <PKB>2131500</PKB>
      <SWD>143000</SWD>
    </biaya_pokok>
    <biaya_denda>
      <BBN>0</BBN>
      <PKB>0</PKB>
      <SWD>0</SWD>
    </biaya_denda>
    <biaya_admin>
      <stnk>0</stnk>
      <tnkb>0</tnkb>
    </biaya_admin>
    <biaya_parkir_pokok>0</biaya_parkir_pokok>
    <biaya_pajak_progresif>0</biaya_pajak_progresif>
    <ntpd>Q8T3L318R0Z3</ntpd>
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
    "tr_id": "24462352",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for payment code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for payment code explanation using PHP.

https://youtu.be/koSDjfgYsAM