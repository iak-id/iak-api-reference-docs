# Price List

API to get pricelist of IAK prepaid products.

## Path

Method | Path 
---------|----------
 POST | api/pricelist/:type/:operator

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
 username | String | Your registered phone number | Yes
 sign | String | Signature. Value: `md5(username+api_key+'pl')` | Yes
 status | String | Product status. <br> Value: `all`, `active`, `non active` | No

<!--
type: tab
title: JSON
-->

```json
{
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
 product_code | String | Product code | Yes
 product_description | String | Product operator name | Yes
 product_details | String | Product description | Yes
 product_nominal | String | Product denomination | Yes
 product_price | Double | Product price | Yes
 product_type | String | Product type | Yes
 active_period | String | Product aActive time period of reload (only applied for **pulsa and data**) | Yes
 status | String | Product status. <br> Value: `active`, `non active` | Yes
 icon_url| String | URL icon for each product | Yes
 product_category | String | Product category | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../../response-code.md) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": [
    {
      "product_code": "alfamart100",
      "product_description": "Alfamart Voucher",
      "product_nominal": "Voucher Alfamart Rp 100.000",
      "product_details": "-",
      "product_price": 100000,
      "product_type": "voucher",
      "active_period": "0",
      "status": "active",
      "icon_url": "https://cdn.mobileproduct.net/img/product/operator_list/140119034649-Alfa-01.png",
      "product_category": "voucher",
    },
    {
      "product_code": "altel10",
      "product_description": "Malaysia Topup",
      "product_nominal": "10",
      "product_details": "-",
      "product_price": 39750,
      "product_type": "malaysia",
      "active_period": "0",
      "status": "active",
      "icon_url": "-"
      "product_category": "international",
    },
    {
      "product_code": "altel100",
      "product_description": "Malaysia Topup",
      "product_nominal": "100",
      "product_details": "-",
      "product_price": 397500,
      "product_type": "malaysia",
      "active_period": "0",
      "status": "active",
      "icon_url": "-"
      "product_category": "international",
    }
  ]
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
	<pricelist>
		<product_code>alfamart100</product_code>
		<product_description>Alfamart Voucher</product_description>
		<product_nominal>Voucher Alfamart Rp 100.000</product_nominal>
		<product_details>-</product_details>
		<product_price>99750</product_price>
		<product_type>voucher</product_type>
		<active_period>0</active_period>
		<status>active</status>
		<icon_url>https://cdn.mobilepulsa.net/img/product/operator_list/140119034649-Alfa-01.png</icon_url>
		<product_category>voucher</product_category>
	</pricelist>
	<pricelist>
		<product_code>altel10</product_code>
		<product_description>Malaysia Topup</product_description>
		<product_nominal>10</product_nominal>
		<product_details>-</product_details>
		<product_price>39750</product_price>
		<product_type>malaysia</product_type>
		<active_period>0</active_period>
		<status>active</status>
		<icon_url>-</icon_url>
		<product_category>international</product_category>
	</pricelist>
	<pricelist>
		<product_code>altel100</product_code>
		<product_description>Malaysia Topup</product_description>
		<product_nominal>100</product_nominal>
		<product_details>-</product_details>
		<product_price>397500</product_price>
		<product_type>malaysia</product_type>
		<active_period>0</active_period>
		<status>active</status>
		<icon_url>-</icon_url>
		<product_category>international</product_category>
	</pricelist>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://prepaid.iak.dev/api/pricelist",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "{your username}",
    "sign": "{your sign}",
    "status": "all"
  }
}
```

## Tutorial Video
You can see this video for pricelist code explanation using Laravel.

https://youtu.be/WiyhNdPmLMM

Or you can see this video for pricelist code explanation using PHP.

https://youtu.be/zr9ht9aPWtg