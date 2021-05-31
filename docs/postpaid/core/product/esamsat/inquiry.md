# Inquiry ESAMSAT

API to inquiry ESAMSAT.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
ESAMSAT.JABAR | 9658548523568701 | Success
ESAMSAT.JABAR | 9658548523568703 | Inquiry - Time Out
ESAMSAT.JABAR | 9658548523568704 | Inquiry - Invoice Has Been Paid
ESAMSAT.JABAR | 9658548523568705 | Inquiry - Incorrect Destination Number
ESAMSAT.JABAR | 9658548523568706 | Payment - Payment Failed
ESAMSAT.JABAR | 9658548523568707 | Payment - Pending / transaction in process
ESAMSAT.JABAR | 9658548523568708 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | ESAMSAT payment code | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes
nomor_identitas | String | Registered identity number | Yes

<!-- theme: info -->

> ### A thing to know
>
> Here is the step to get **ESAMSAT payment code** :
> 1. Download Samolnas apps
> 2. Reqister and get payment code

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "ESAMSAT.JABAR",
  "hp"       : "9658548523568701",
  "ref_id"   : "978994691278",
  "sign"     : "6c6a046a14c444e44cfab5e4bbb01b01",
  "nomor_identitas"   : "0212502110170100",
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
  <code>ESAMSAT.JABAR</code>
  <hp>9658548523568701</hp>
  <ref_id>978994691278</ref_id>
  <sign>6c6a046a14c444e44cfab5e4bbb01b01</sign>
  <nomor_identitas>0212502110170100</nomor_identitas>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | ESAMSAT payment code | Yes
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
    "hp": "9658548523568701",
    "tr_name": "TESTING ESAMSAT",
    "period": "20181022-20191022",
    "nominal": 2274500,
    "admin": 5000,
    "ref_id": "978994691299",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 2279500,
    "selling_price": 2277000,
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
        "PKB": "2131000",
        "SWD": "143500"
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
      "ntpd": ""
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
	<hp>9658548523568701</hp>
	<tr_name>TESTING ESAMSAT</tr_name>
	<period>20181022-20191022</period>
	<nominal>2274500</nominal>
	<admin>5000</admin>
	<ref_id>978994691299</ref_id>
	<response_code>00</response_code>
	<message>INQUIRY SUCCESS</message>
	<price>2279500</price>
	<selling_price>2277000</selling_price>
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
			<PKB>2131000</PKB>
			<SWD>143500</SWD>
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
		<ntpd></ntpd>
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
    "code": "ESAMSAT.JABAR",
    "hp": "9658548523568701",
    "ref_id": "0912837465",
    "sign": "{your sign}",
    "nomor_identitas": "0212502110170100"
  }
}
```
