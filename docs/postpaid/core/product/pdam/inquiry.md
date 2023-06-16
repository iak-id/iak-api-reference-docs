# Inquiry PDAM

API to inquiry PDAM.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check

## Test Case

Code | Number | Response 
---------|----------|---------
PDAMKOTA.SURABAYA | 10202001 | Success - 1 bills
PDAMKOTA.MEDAN | 10202002 | Success - 4 bills
AETRA | 10202003 | Inquiry - Time Out
AETRA | 10202004 | Inquiry - Invoice Has Been Paid
AETRA | 10202005 | Inquiry - Incorrect Destination Number
PDAMKOTA.MEDAN | 10202006 | Payment - Payment Failed
PDAMKOTA.MEDAN | 10202007 | Payment - Pending / transaction in process
PDAMKOTA.MEDAN | 10202008 | Payment - MISC Error / Biller System Error

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `inq-pasca` | Yes
username | String | Your registered phone number | Yes
code | String | Product Code. You can get list of product code in [pricelist api](../../price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
hp | String | PDAM customer number | Yes
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
  "code"	    : "PDAMKOTA.SURABAYA",
  "hp"	      : "10202001",
  "ref_id"	  : "0912837465",
  "sign"      : "ebb8b87be79243370bd29bfb8894e8d7"
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
  <code>PDAMKOTA.SURABAYA</code>
  <hp>10202001</hp>
  <ref_id>0912837465</ref_id>
  <sign>ebb8b87be79243370bd29bfb8894e8d7</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
tr_id | Integer | IAK inquiry ID | Yes
code | String | Product code | Yes
hp | String | PDAM customer number | Yes
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
desc.**bill_quantity** | Integer | Bill quantity | Yes
desc.**address** | String | Invoice Address | Yes
desc.**biller_admin** | String | Admin fee | Yes
desc.**pdam_name** | String | PDAM name | Yes
desc.**stamp_duty** | String | Stamp duty fee | Yes
desc.**due_date** | String | Due date (only for **PDAMKOTA.SURABAYA**) | No
desc.**kode_tarif** | String | Fare code (only for **PDAMKOTA.SURABAYA**) | No
desc.**bill** | Object | Bill details | Yes
desc.bill.**detail** | Array | Bill details | Yes
desc.bill.detail.**period** | String | Bill period of detailed month | Yes
desc.bill.detail.**first_meter** | Integer | Initial meter of detailed month | Yes
desc.bill.detail.**last_meter** | Integer | Final meter of detailed month | Yes
desc.bill.detail.**penalty** | Double | Penalty fee of detailed month | Yes
desc.bill.detail.**bill_amount** | Double | Bill amount of detailed month | Yes
desc.bill.detail.**misc_amount** | Double | Others fee of detailed month | Yes
desc.bill.detail.**stand** | String | Current PDAM stand of detailed month (only for **PDAMKOTA.SURABAYA**) | No

There are 2 types of PDAM response : 

  1. Separated **desc.bill.detail** for each period

  For example when there is PDAM bill 2 periods, then the desc.bill.detail will be 2 index array that contain detail for each period. 

  2. Unified **desc.bill.detail** for all period

  For example when there is PDAM bill 2 periods, then the desc.bill.detail just 1 index array that contain detail for all period.
Below table is a list of PDAM products for unified detail for all period:

<!-- title: Unified Detail-->
-| - | -
---------|----------|---------
PDAMKAB.ACEHBESAR | PDAMKAB.ACEHTAMIANG | PDAMKAB.ACEHUTARA
PDAMKAB.AGAM | PDAMKAB.BANDUNGB | PDAMKAB.BANGGAI
PDAMKAB.BANGKABARAT | PDAMKAB.BANTUL | PDAMKAB.BANYUASIN
PDAMKAB.BATANGHARI | PDAMKAB.BEKASI | PDAMKAB.BELITUNGTIMUR
PDAMKAB.BENGKAYANG | PDAMKAB.BONE | PDAMKAB.BONEBOLANGO
PDAMKAB.BULUNGANTANJUNGSELOR | PDAMKAB.BUTON | PDAMKAB.CILACAPNONREGULER
PDAMKAB.DOMPU | PDAMKAB.ENREKANG | PDAMKAB.GIANYAR
PDAMKAB.GIANYARNONAIR | PDAMKAB.GORONTALO | PDAMKAB.GORONTALOLIMBOTO
PDAMKAB.GOWA | PDAMKAB.GUNUNGKIDUL | PDAMKAB.HALMAHERAUTARA
PDAMKAB.HULUSUNGAIUTARAAMUNTAI | PDAMKAB.JEMBRANA | PDAMKAB.KAPUASHULU
PDAMKAB.KARAWANGB | PDAMKAB.KEDIRI | PDAMKAB.KERINCI
PDAMKAB.KETAPANG | PDAMKAB.KOLAKA | PDAMKAB.KOLAKAUTARA
PDAMKAB.KOTABARUPULAULAUT | PDAMKAB.KUDUS | PDAMKAB.KUPANG
PDAMKAB.KUTAIBARAT | PDAMKAB.KUTAIKERTANEGARA | PDAMKAB.LAMANDAU
PDAMKAB.LAMONGAN | PDAMKAB.LAMPUNGSELATAN | PDAMKAB.LEBAK
PDAMKAB.LIMAPULUHKOTA | PDAMKAB.LOMBOKTIMUR | PDAMKAB.LUWU
PDAMKAB.LUWUTIMUR | PDAMKAB.LUWUUTARA | PDAMKAB.MAGELANG
PDAMKAB.MAGETAN | PDAMKAB.MAJALENGKA | PDAMKAB.MALINAU
PDAMKAB.MALUKUTENGGARA | PDAMKAB.MANGGARAI | PDAMKAB.MAROS
PDAMKAB.MEMPAWAH | PDAMKAB.MERANGIN | PDAMKAB.MINAHASAUTARA
PDAMKAB.MUARABUNGO | PDAMKAB.MUARAENIM | PDAMKAB.MUAROJAMBI
PDAMKAB.MUSIBANYUASIN | PDAMKAB.NGAWI | PDAMKAB.OGANILIR
PDAMKAB.OKUBATURAJA | PDAMKAB.OKUSELATAN | PDAMKAB.PACITAN
PDAMKAB.PADANGPARIAMAN | PDAMKAB.PAMEKASAN | PDAMKAB.PANDEGLANG
PDAMKAB.PESSEL | PDAMKAB.POLMAN | PDAMKAB.PRABUMULIH
PDAMKAB.PURWAKARTA | PDAMKAB.SANGGAU | PDAMKAB.SAROLANGUN
PDAMKAB.SERANG | PDAMKAB.SERDANG | PDAMKAB.SERUYAN
PDAMKAB.SIDRAP | PDAMKAB.SIJUNJUNG | PDAMKAB.SIKKA
PDAMKAB.SINJAI | PDAMKAB.SOLOK | PDAMKAB.SRAGEN
PDAMKAB.SUMBAWA | PDAMKAB.SUMENEP | PDAMKAB.TABALONG
PDAMKAB.TANAHBUMBU | PDAMKAB.TANAHDATAR | PDAMKAB.TANGERANG
PDAMKAB.TANJUNGJABUNGBARAT | PDAMKAB.TEBO | PDAMKAB.TIMORTENGAHUTARA
PDAMKAB.TRENGGALEK | PDAMKAB.TUBAN | PDAMKAB.TULUNGAGUNG
PDAMKAB.WAJO | PDAMKOTA.BIMA | PDAMKOTA.BLITAR
PDAMKOTA.BONEWATAMPONE | PDAMKOTA.BONTANG | PDAMKOTA.BUKITTINGGI
PDAMKOTA.CILEGON | PDAMKOTA.DAROY | PDAMKOTA.DKIPALYJA
PDAMKOTA.GORONTALO | PDAMKOTA.JAMBI | PDAMKOTA.KANDANGAN
PDAMKOTA.KENDARI | PDAMKOTA.KUTAITIMUR | PDAMKOTA.LANGSA
PDAMKOTA.LUBUKLINGGAU | PDAMKOTA.MAGELANG | PDAMKOTA.MOJOKERTO
PDAMKOTA.PALOPO | PDAMKOTA.PALU | PDAMKOTA.PANGKALPINANG
PDAMKOTA.PAREPARE | PDAMKOTA.PARIAMAN | PDAMKOTA.PEKANBARU
PDAMKOTA.PEMATANGSIANTAR | PDAMKOTA.RANTAUPRAPAT | PDAMKOTA.SABANG
PDAMKOTA.SAMPIT | PDAMKOTA.SINGKAWANG | PDAMKOTA.TANJUNGBALAI
PDAMKOTA.TANJUNGPINANG | PDAMKOTA.TARAKAN | PDAMKOTA.TARUTUNG
PDAMKOTA.TASIKMALAYA | PDAMKOTA.TEBINGTINGGI | PDAMKOTA.TEMBILAHAN
PDAMKOTA.TERNATE | PDAMKOTA.TOMOHON | PDAMKOTA.WISATABATU
PDAMKOTA.YOGYAKARTA | - | - 

<!-- theme: info -->

> Other than above table is **separated detail**

### Separated Detail Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732791,
    "code": "PDAMKOTA.SURABAYA",
    "hp": "10202001",
    "tr_name": "DADANG SOEKARDI",
    "period": "201412",
    "nominal": 35490,
    "admin": 2000,
    "ref_id": "0912837465",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 37490,
    "selling_price": 36790,
    "desc": {
      "bill_quantity": 1,
      "address": "WONOKROMO S.S BARU 2 8",
      "biller_admin": "",
      "pdam_name": "PDAM SURABAYA",
      "stamp_duty": "",
      "due_date": "1-15 DES 2014",
      "kode_tarif": "3A",
      "bill": {
        "detail": [
          {
            "period": "201412",
            "first_meter": 4589,
            "last_meter": 4613,
            "penalty": 7500,
            "bill_amount": 27240,
            "misc_amount": 750,
            "stand": ""
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
  <tr_id>9732791</tr_id>
  <code>PDAMKOTA.SURABAYA</code>
  <hp>10202001</hp>
  <tr_name>DADANG SOEKARDI</tr_name>
  <period>201412</period>
  <nominal>35490</nominal>
  <admin>2000</admin>
  <ref_id>0912837465</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>37490</price>
  <selling_price>36790</selling_price>
  <desc>
    <bill_quantity>1</bill_quantity>
    <address>WONOKROMO S.S BARU 2 8</address>
    <biller_admin></biller_admin>
    <pdam_name>PDAM SURABAYA</pdam_name>
    <stamp_duty></stamp_duty>
    <due_date>1-15 DES 2014</due_date>
    <kode_tarif>3A</kode_tarif>
    <bill>
      <detail>
        <period>201412</period>
        <first_meter>4589</first_meter>
        <last_meter>4613</last_meter>
        <penalty>7500</penalty>
        <bill_amount>27240</bill_amount>
        <misc_amount>750</misc_amount>
        <stand></stand>
      </detail>
    </bill>
  </desc>
</mp>
```
<!-- type: tab-end -->

### Unified Detail Response

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "tr_id": 9732791,
    "code": "PDAMKOTA.YOGYAKARTA",
    "hp": "10202001",
    "tr_name": "DADANG SOEKARDI",
    "period": "201803,201804",
    "nominal": 35490,
    "admin": 2000,
    "ref_id": "09128374654",
    "response_code": "00",
    "message": "INQUIRY SUCCESS",
    "price": 37490,
    "selling_price": 36790,
    "desc": {
      "bill_quantity": 1,
      "address": "WONOKROMO S.S BARU 2 8",
      "biller_admin": "",
      "pdam_name": "PDAM KOTA YOGYAKARTA",
      "stamp_duty": "",
      "kode_tarif": "",
      "bill": {
        "detail": [
          {
            "period": "201803,201804",
            "first_meter": 4589,
            "last_meter": 4613,
            "penalty": 7500,
            "bill_amount": 27240,
            "misc_amount": 750
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
  <tr_id>9732791</tr_id>
  <code>PDAMKOTA.YOGYAKARTA</code>
  <hp>10202001</hp>
  <tr_name>DADANG SOEKARDI</tr_name>
  <period>201803,201804</period>
  <nominal>35490</nominal>
  <admin>2000</admin>
  <ref_id>09128374654</ref_id>
  <response_code>00</response_code>
  <message>INQUIRY SUCCESS</message>
  <price>37490</price>
  <selling_price>36790</selling_price>
  <desc>
    <bill_quantity>1</bill_quantity>
    <address>WONOKROMO S.S BARU 2 8</address>
    <biller_admin></biller_admin>
    <pdam_name>PDAM KOTA YOGYAKARTA</pdam_name>
    <stamp_duty></stamp_duty>
    <kode_tarif></kode_tarif>
    <bill>
      <detail>
        <period>201803,201804</period>
        <first_meter>4589</first_meter>
        <last_meter>4613</last_meter>
        <penalty>7500</penalty>
        <bill_amount>27240</bill_amount>
        <misc_amount>750</misc_amount>
      </detail>
    </bill>
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
    "code": "PDAMKOTA.SURABAYA",
    "hp": "10202001",
    "ref_id": "0912837465",
    "sign": "{your sign}"
  }
}
```

## Tutorial Video
You can see this video for inquiry code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for inquiry code explanation using PHP.

https://youtu.be/DeTTmq718Os