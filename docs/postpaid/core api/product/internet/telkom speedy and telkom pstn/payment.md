# Payment Internet Telkom Speedy and Telkom PSTN

API to payment internet telkom speedy and telkom pstn.

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
  "tr_id"    : "9732795",
  "sign"     : "06c2a1c20223e402e18365a3e5117c3a"
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
  <tr_id>9732795</tr_id>
  <sign>06c2a1c20223e402e18365a3e5117c3a</sign>
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
hp | String | Internet customer number | Yes
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
    "tr_id": 9732795,
    "code": "TELKOMPSTN",
    "datetime": "20180803172000",
    "hp": "6391601201",
    "tr_name": "JAORAH",
    "period": "201405,201407",
    "nominal": 129610,
    "admin": 7500,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 137110,
    "selling_price": 133510,
    "balance": 997161249,
    "noref": "1609626",
    "ref_id": "091283746520",
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
            "periode": "JUL2014",
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
  <tr_id>9732795</tr_id>
  <code>TELKOMPSTN</code>
  <datetime>20170725162507</datetime>
  <hp>6391601201</hp>
  <tr_name>JAORAH</tr_name>
  <period>201405,201407</period>
  <nominal>129610</nominal>
  <admin>7500</admin>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>137110</price>
  <selling_price>135910</selling_price>
  <balance>1500974395</balance>
  <no_ref>73276444</no_ref>
  <ref_id>1609626</ref_id>
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
    "commands": "pay-pasca",
    "username": "{your username}",
    "tr_id": "9732795",
    "sign": "{your sign}"
  }
}
```
