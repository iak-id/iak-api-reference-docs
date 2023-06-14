# Check Status

API to check status.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `checkstatus` | Yes
username | String | Your registered phone number | Yes
ref_id | String | Your order number / reference ID | Yes
sign | String | Signature. Value: `md5(username+api_key+'cs')` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "checkstatus",
  "username" : "123123123",
  "ref_id"   : "091283746520",
  "sign"     : "6bc194c0d23c18a12f5d6919aa72bc30"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" ?>
<mp>
  <commands>checkstatus</commands>
  <username>123123123</username>
  <ref_id>091283746520</ref_id>
  <sign>6bc194c0d23c18a12f5d6919aa72bc30</sign>
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
hp | String | Customer number | Yes
tr_name | String | Bill account name | Yes
period | String | Bill period | Yes
nominal | Double | Bill nominal | Yes
admin | Double | Admin fee | Yes
status | Integer | Transaction status. List of status : <br> `0: Payment request haven't been receieved` `1:Payment success` `2:Payment failed` `3:Payment is being process` | Yes
response_code | String | Response code. See [response code](../response-code.md) list | Yes
message | String | Message | Yes
price | Double | Total price that must be paid (nominal + admin fee) | Yes
selling_price | Double | Deducted balance | Yes
balance | Double | Client remaining balance | Yes
noref | String | Biller reference number (if exist) | No
ref_id | String | Your order number / reference ID ( must unique ) | Yes
desc | Object | Product description (See in each product segment) | Yes

### Payment Success Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732795,
    "code": "TELKOMPSTN",
    "datetime": "20180803171608",
    "hp": "6391601202",
    "tr_name": "JAORAH",
    "period": "201405,201407",
    "nominal": 129610,
    "admin": 7500,
    "status": 1,
    "response_code": "00",
    "message": "PAYMENT SUCCESS",
    "price": 137110,
    "selling_price": 133510,
    "balance": 996850749,
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <tr_id>9732795</tr_id>
  <code>TELKOMPSTN</code>
  <datetime>20180803171608</datetime>
  <hp>6391601202</hp>
  <tr_name>JAORAH</tr_name>
  <period>201405,201407</period>
  <nominal>129610</nominal>
  <admin>7500</admin>
  <status>1</status>
  <response_code>00</response_code>
  <message>PAYMENT SUCCESS</message>
  <price>137110</price>
  <selling_price>133510</selling_price>
  <balance>996850749</balance>
  <noref>1609626</noref>
  <ref_id>091283746520</ref_id>
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

### Payment Request Haven't Been Receieved Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732795,
    "code": "TELKOMPSTN",
    "datetime": "20180803171608",
    "hp": "6391601202",
    "tr_name": "JAORAH",
    "period": "201405,201407",
    "nominal": 129610,
    "admin": 7500,
    "ref_id": "091283746520",
    "status": 0,
    "response_code": "42",
    "message": "REQUEST PEMBAYARAN BELUM DITERIMA",
    "price": 137110,
    "selling_price": 133510,
    "balance": 996850749,
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <tr_id>9732795</tr_id>
  <code>TELKOMPSTN</code>
  <datetime>20180803171608</datetime>
  <hp>6391601202</hp>
  <tr_name>JAORAH</tr_name>
  <period>201405,201407</period>
  <nominal>129610</nominal>
  <admin>7500</admin>
  <ref_id>091283746520</ref_id>
  <status>0</status>
  <response_code>42</response_code>
  <message>REQUEST PEMBAYARAN BELUM DITERIMA</message>
  <price>137110</price>
  <selling_price>133510</selling_price>
  <balance>996850749</balance>
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

### Payment Is Being Process Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 47794331,
    "code": "TELKOMPSTN",
    "hp": "6391601207",
    "tr_name": "CATH",
    "period": "202103",
    "nominal": 49870,
    "admin": 2500,
    "ref_id": "091283746520",
    "status": 3,
    "response_code": "39",
    "message": "PENDING \/ TRANSAKSI SEDANG DIPROSES",
    "price": 52370,
    "selling_price": 51170,
    "balance": 99995833900,
    "desc": {
      "kode_area": "0751",
      "divre": "01",
      "datel": "0006",
      "jumlah_tagihan": 1,
      "tagihan": {
        "detail": [
          {
            "periode": "MAR 2021",
            "nilai_tagihan": "49870",
            "admin": "2500",
            "total": 52370
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <tr_id>47794331</tr_id>
  <code>TELKOMPSTN</code>
  <hp>6391601207</hp>
  <tr_name>CATH</tr_name>
  <period>202103</period>
  <nominal>49870</nominal>
  <admin>2500</admin>
  <ref_id>091283746520</ref_id>
  <status>3</status>
  <response_code>39</response_code>
  <message>PENDING / TRANSAKSI SEDANG DIPROSES</message>
  <price>52370</price>
  <selling_price>51170</selling_price>
  <balance>99995833900</balance>
  <desc>
    <kode_area>0751</kode_area>
    <divre>01</divre>
    <datel>0006</datel>
    <jumlah_tagihan>1</jumlah_tagihan>
    <tagihan>
      <detail>
        <periode>MAR 2021</periode>
        <nilai_tagihan>49870</nilai_tagihan>
        <admin>2500</admin>
        <total>52370</total>
      </detail>
    </tagihan>
  </desc>
</mp>
```
<!-- type: tab-end -->

### Payment Failed Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 47794331,
    "code": "TELKOMPSTN",
    "datetime": "20210316174828",
    "hp": "6391601207",
    "tr_name": "CATH",
    "period": "202103",
    "nominal": 49870,
    "admin": 2500,
    "status": 2,
    "response_code": "37",
    "message": "PEMBAYARAN GAGAL",
    "price": 52370,
    "selling_price": 51170,
    "balance": 99995833900,
    "noref": "",
    "ref_id": "091283746520",
    "desc": {
      "kode_area": "0751",
      "divre": "01",
      "datel": "0006",
      "jumlah_tagihan": 1,
      "tagihan": {
        "detail": [
          {
            "periode": "MAR 2021",
            "nilai_tagihan": "49870",
            "admin": "2500",
            "total": 52370
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
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <tr_id>47794331</tr_id>
  <code>TELKOMPSTN</code>
  <datetime>20210316174828</datetime>
  <hp>6391601207</hp>
  <tr_name>CATH</tr_name>
  <period>202103</period>
  <nominal>49870</nominal>
  <admin>2500</admin>
  <status>2</status>
  <response_code>37</response_code>
  <message>PEMBAYARAN GAGAL</message>
  <price>52370</price>
  <selling_price>51170</selling_price>
  <balance>99995833900</balance>
  <noref></noref>
  <ref_id>091283746520</ref_id>
  <desc>
    <kode_area>0751</kode_area>
    <divre>01</divre>
    <datel>0006</datel>
    <jumlah_tagihan>1</jumlah_tagihan>
    <tagihan>
      <detail>
        <periode>MAR 2021</periode>
        <nilai_tagihan>49870</nilai_tagihan>
        <admin>2500</admin>
        <total>52370</total>
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
    "commands": "checkstatus",
    "username": "{your username}",
    "ref_id": "{your ref_id}",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for check status code explanation using Laravel.

https://youtu.be/5FllEMzrF4A

Or you can see this video for check status code explanation using PHP.

https://youtu.be/koSDjfgYsAM