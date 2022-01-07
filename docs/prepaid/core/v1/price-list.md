# Price List

API to get pricelist of IAK prepaid products. 价位表

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index/:type/:operator

### Path Parameters

<!-- title: Path Parameters -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 type | String | Product type. See [here](../../product-type.md) for product type list | No
 operator | String | Product operator. See [here](../../product-type.md) for product operator list | No

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `pricelist` | Yes
 username | String | Your registered phone number | Yes
 sign | String | Signature. Value: `md5(username+api_key+'pl')` | Yes
 status | String | Product status. <br> Value: `all`, `active`, `non active` | No

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "pricelist",
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
  <commands>pricelist</commands>
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
 pulsa_code | String | Product code | Yes
 pulsa_op | String | Product operator name | Yes
 pulsa_details | String | Product description | Yes
 pulsa_nominal | String | Product denomination | Yes
 pulsa_price | Double | Product price | Yes
 pulsa_type | String | Product type | Yes
 masaaktif | String | Product aActive time period of reload (only applied for **pulsa and data**) | Yes
 status | String | Product status. <br> Value: `active`, `non active` | Yes
 icon_url| String | URL icon for each product | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": [
    {
      "pulsa_code": "alfamart100",
      "pulsa_op": "Alfamart Voucher",
      "pulsa_nominal": "Voucher Alfamart Rp 100.000",
      "pulsa_details": "-",
      "pulsa_price": 100000,
      "pulsa_type": "voucher",
      "masaaktif": "0",
      "status": "active",
      "icon_url": "https://cdn.mobileproduct.net/img/product/operator_list/140119034649-Alfa-01.png"
    },
    {
      "pulsa_code": "altel10",
      "pulsa_op": "Malaysia Topup",
      "pulsa_nominal": "10",
      "pulsa_details": "-",
      "pulsa_price": 39750,
      "pulsa_type": "malaysia",
      "masaaktif": "0",
      "status": "active",
      "icon_url": "-"
    },
    {
      "pulsa_code": "altel100",
      "pulsa_op": "Malaysia Topup",
      "pulsa_nominal": "100",
      "pulsa_details": "-",
      "pulsa_price": 397500,
      "pulsa_type": "malaysia",
      "masaaktif": "0",
      "status": "active",
      "icon_url": "-"
    }
  ]
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <pulsa>
    <pulsa_code>hindosat10000</pulsa_code>
    <pulsa_op>Indosat</pulsa_op>
    <pulsa_nominal>10000</pulsa_nominal>
    <pulsa_details>-</pulsa_details>
    <pulsa_price>11000</pulsa_price>
    <pulsa_type>pulsa</pulsa_type>
    <masaaktif>15</masaaktif>
    <status>active</status>
    <icon_url>https://cdn.mobileproduct.net/img/product/operator_list/140119034649-Alfa-01.png</icon_url>
  </pulsa>
  <pulsa>
    <pulsa_code>hindosat100000</pulsa_code>
    <pulsa_op>Indosat</pulsa_op>
    <pulsa_nominal>100000</pulsa_nominal>
    <pulsa_details>-</pulsa_details>
    <pulsa_price>100000</pulsa_price>
    <pulsa_type>pulsa</pulsa_type>
    <masaaktif>60</masaaktif>
    <status>active</status>
    <icon_url>-</icon_url>
  <pulsa>
    <pulsa_code>hindosat1000000</pulsa_code>
    <pulsa_op>Indosat</pulsa_op>
    <pulsa_nominal>1000000</pulsa_nominal>
    <pulsa_details>-</pulsa_details>
    <pulsa_price>950000</pulsa_price>
    <pulsa_type>pulsa</pulsa_type>
    <masaaktif>60</masaaktif>
    <status>active</status>
    <icon_url>-</icon_url>
  </pulsa>
<mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://testprepaid.mobilepulsa.net/v1/legacy/index",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "commands": "pricelist",
    "username": "{your username}",
    "sign": "{your sign}",
    "status": "all"
  }
}
```