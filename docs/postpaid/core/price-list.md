# Price List

API to get pricelist of IAK postpaid products.

## Path

Method | Path 
---------|----------
 POST | api/v1/bill/check/:type

### Path Parameters

<!-- title: Path Parameters -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 type | String | Product type | No

Available product type : 

  - pdam
  - bpjs
  - internet
  - pajak-kendaraan
  - finance
  - hp
  - estate
  - emoney
  - kereta
  - tv
  - airline
  - o2o
  - pbb
  - gas
  - pajak-daerah
  - pln
  - pasar
  - retribusi
  - pendidikan
  - asuransi

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
commands | String | Value: `pricelist-pasca` | Yes
username | String | Your registered phone number | Yes
sign | String | Signature. Value: `md5(username+api_key+'pl')` | Yes
status | String | Product status. <br> Value: `all`, `active`, `non active` | No
province | String | 34 Provinces in Indonesia, this field only for PDAM type | No

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "pricelist-pasca",
  "username" : "123123123",
  "sign"     : "6bc194c0d23c18a12f5d6919aa72bc30",
  "status"   : "all"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" ?>
<mp>
  <commands>pricelist-pasca</commands>
  <username>123123123</username>
  <sign>6bc194c0d23c18a12f5d6919aa72bc30</sign>
  <status>all</status>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 code | String | Product code | Yes
 name | String | Product name | Yes
 status | Integer | Product status. <br> Value: 1=`active`, 4=`non active` | Yes
 fee | Double | Admin fee | Yes
 komisi | Double | Commision to client | Yes
 type | String | Product type. See [here](#path-parameters) for available type | Yes
 category | String | Product category | Yes
 province | String | 34 Provinces in Indonesia, this field only for PDAM type | No

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "pasca": [
      {
        "code": "AETRA",
        "name": "AETRA",
        "status": 1,
        "fee": 2500,
        "komisi": 700,
        "type": "pdam",
        "category": "postpaid"
      },
      {
        "code": "BPJS",
        "name": "BPJS Kesehatan",
        "status": 1,
        "fee": 2000,
        "komisi": 100,
        "type": "bpjs",
        "category": "postpaid"
      }
    ]
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
  <data>
    <pasca>
      <code>AETRA</code>
      <name>AETRA</name>
      <status>1</status>
      <fee>2500</fee>
      <komisi>700</komisi>
      <type>pdam</type>
      <category>postpaid</category>
    </pasca>
    <pasca>
      <code>BPJS</code>
      <name>BPJS Kesehatan</name>
      <status>1</status>
      <fee>2500</fee>
      <komisi>1150</komisi>
      <type>bpjs</type>
      <category>postpaid</category>
    </pasca>
  </data>
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
    "commands": "pricelist-pasca",
    "username": "{your username}",
    "sign": "{your sign}",
    "status": "all"
  }
}
```

## Tutorial Video
You can see this video for pricelist code explanation using Laravel.

https://youtu.be/OF1jyOQ5kik

Or you can see this video for pricelist code explanation using PHP.

https://youtu.be/DeTTmq718Os