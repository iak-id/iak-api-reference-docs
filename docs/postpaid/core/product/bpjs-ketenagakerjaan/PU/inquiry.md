# Inquiry

API to inquiry BPJS Kesehatan Penerima Upah (PU).

## Path

Method | Path
---------|----------
POST | api/v1/bill/check

## Test Case

Code | Number | Response
---------|----------|---------
BPJSTK | 210300016066 | Success

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | Bill Number | Yes
ref_id | String | Your order number / reference ID ( must unique ) | Yes
sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inq-pasca",
  "username" : "123123123",
  "code"     : "BPJSTKPU",
  "hp"       : "210300016066",
  "ref_id"   : "091283746511",
  "sign"     : "6515c5094421834a85ed9ac7a0fe443b"
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
  <code>BPJSTKPU</code>
  <hp>210300016066</hp>
  <ref_id>091283746511</ref_id>
  <sign>6515c5094421834a85ed9ac7a0fe443b</sign>
  <month>1</month>
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
hp | String | NIK | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
response_code | String | Response code. See [response code](../../../../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
balance | Double | Client remaining balance | Yes
noref | String | Biller reference number (if exist) | No
ref_id | String | Your order number / reference ID ( must unique ) | Yes
desc | Object | Product description | Yes
desc.**kode_iuran** | String | 	Contribution Code | Yes
desc.**jht** | Integer | 	Pension Plan Fee | Yes
desc.**jkk** | Integer | 	Accident Insurance Fee | Yes
desc.**jkm** | Integer | 	Death Insurance Fee | Yes
desc.**jpk** | Integer | 	Lost Job Fee | Yes
desc.**jpn** | Integer | 	Pension Plan Fee | Yes
desc.**npp** | String  | Company Registration Number | Yes
desc.**kode_divisi** | String | Division Code | Yes

<!--
type: tab
title: JSON
-->

```json
{
    "data": {
        "tr_id": 219342904,
        "code": "BPJSTKPU",
        "hp": "210300016066",
        "tr_name": "PT LIMABELAS",
        "period": "202104",
        "nominal": 100000,
        "admin": 2500,
        "ref_id": "ref-19_May_2022_16.36.47",
        "response_code": "00",
        "message": "INQUIRY SUCCESS",
        "price": 102500,
        "selling_price": 100500,
        "desc": {
            "kode_iuran": "210300016066",
            "jht": 61688,
            "jkk": 1082,
            "jkm": 2166,
            "jpk": 2597,
            "jpn": 32467,
            "npp": "15092873",
            "kode_divisi": "000"
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
    <tr_id>219342904</tr_id>
    <code>BPJSTKPU</code>
    <hp>210300016066</hp>
    <tr_name>PT LIMABELAS</tr_name>
    <period>202104</period>
    <nominal>100000</nominal>
    <admin>2500</admin>
    <ref_id>ref-19_May_2022_16.36.47</ref_id>
    <response_code>00</response_code>
    <message>INQUIRY SUCCESS</message>
    <price>102500</price>
    <selling_price>100500</selling_price>
    <desc>
        <kode_iuran>210300016066</kode_iuran>
        <jht>61688</jht>
        <jkk>1082</jkk>
        <jkm>2166</jkm>
        <jpk>2597</jpk>
        <jpn>32467</jpn>
        <npp>15092873</npp>
        <kode_divisi>000</kode_divisi>
    </desc>
</mp>
```
<!-- type: tab-end -->