# Callback

IAK will send response to your callback URL to inform you about prepaid transaction you did before. There are only two possible response that IAK will send to your callback URL: **success/failed** response.

<!-- theme: info -->

> See [here](https://api.iak.id/docs/platform/docs/security.md#callback-notification) how to secure your callback.

## Production

In production environment, IAK will send the response to your callback URL automatically. 

Set your production callback URL [here](https://developer.iak.id/prod-setting)

## Development

In development environment, IAK don't send response automatically to your callback URL. You can simulate the response to your callback URL through sandbox report. 

Set your development callback URL [here](https://developer.iak.id/dev-setting)

Learn more about [sandbox report](https://api.iak.id/docs/platform/docs/integration/sandbox-report.md)

## Response parameter

IAK will send below response to your callback URL for both version 1 and version 2. 

See the different between version 1 and 2 [here](core/v1-vs-v2.md)

<!--
type: tab
title: Version 1
-->

Field | Type | Description | Mandatory
---------|----------|--------- |--------
 ref_id | String | Your order number / reference ID (must unique) | Yes 
 status | String | Transaction status. List of status: <br> `0:PROCESS` `1: SUCCESS` `2:FAILED` | Yes
 code | String | Product Code | Yes
 hp | String | Customer ID | Yes
 price | String | Product price | Yes
 message | String | Topup message | Yes
 sn | String | Serial number. See [sn format](./sn-format.md) | No
 pin | String | Pin. Will only appear in several Games Vouchers | No
 balance | String | Final balance | Yes
 tr_id | String | IAK transaction ID | Yes
 rc | String | IAK response code. See [rc list](./response-code.md)| Yes
 sign | String | md5(username+api_key+ref_id) | Yes

<!--
type: tab
title: Version 2
-->

Field | Type | Description | Mandatory
---------|----------|--------- |--------
 ref_id | String | Your order number / reference ID (must unique) | Yes 
 status | String | Transaction status. List of status: <br> `0:PROCESS` `1: SUCCESS` `2:FAILED` | Yes
 product_code | String | Product Code | Yes
 customer_id | String | Customer ID | Yes
 price | String | Product price | Yes
 message | String | Topup message | Yes
 sn | String | Serial number. See [sn format](./sn-format.md) | No
 pin | String | Pin. Will only appear in several Games Vouchers | No
 balance | String | Final balance | Yes
 tr_id | String | IAK transaction ID | Yes
 rc | String | IAK response code. See [rc list](./response-code.md)| Yes
 sign | String | md5(username+api_key+ref_id) | Yes

<!-- type: tab-end -->

 ### Success Response Example

 Below is the example of success response that will sent to your callback URL.

  1. **Game**

<!--
type: tab
title: Version 1
-->

**JSON**

```json
{
  "data": {
    "ref_id": "order001",
    "status": "1",
    "code": "hsteam12000",
    "hp": "0817777215",
    "price": "16500",
    "message": "SUCCESS",
    "sn": "ABCD-EFGH-IJKL-MNOP",
    "pin": "123456789",
    "balance": "996994749",
    "tr_id": "3487",
    "rc": "00",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order001</ref_id>
  <status>1</status>
  <code>hsteam12000</code>
  <hp>0817777215</hp>
  <price>16500</price>
  <message>SUCCESS</message>
  <sn>ABCD-EFGH-IJKL-MNOP</sn>
  <pin>123456789</pin>
  <balance>996994749</balance>
  <tr_id>3487</tr_id>
  <rc>00</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!--
type: tab
title: Version 2
-->


**JSON**

```json
{
  "data": {
    "ref_id": "order001",
    "status": "1",
    "product_code": "hsteam12000",
    "customer_id": "0817777215",
    "price": "16500",
    "message": "SUCCESS",
    "sn": "ABCD-EFGH-IJKL-MNOP",
    "pin": "123456789",
    "balance": "996994749",
    "tr_id": "3487",
    "rc": "00",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order001</ref_id>
  <status>1</status>
  <product_code>hsteam12000</product_code>
  <customer_id>0817777215</customer_id>
  <price>16500</price>
  <message>SUCCESS</message>
  <sn>ABCD-EFGH-IJKL-MNOP</sn>
  <pin>123456789</pin>
  <balance>996994749</balance>
  <tr_id>3487</tr_id>
  <rc>00</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!-- type: tab-end -->

  2. **Other Than Game**

<!--
type: tab
title: Version 1
-->

**JSON**

```json
{
  "data": {
    "ref_id": "order002",
    "status": "1",
    "code": "xld25000",
    "hp": "0817777215",
    "price": "25000",
    "message": "SUCCESS",
    "sn": "123456789",
    "balance": "997061249",
    "tr_id": "3482",
    "rc": "00",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order002</ref_id>
  <status>1</status>
  <code>xld25000</code>
  <hp>0817777215</hp>
  <price>25000</price>
  <message>SUCCESS</message>
  <sn>123456789</sn>
  <balance>997061249</balance>
  <tr_id>3482</tr_id>
  <rc>00</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!--
type: tab
title: Version 2
-->


**JSON**

```json
{
  "data": {
    "ref_id": "order002",
    "status": "1",
    "product_code": "xld25000",
    "customer_id": "0817777215",
    "price": "25000",
    "message": "SUCCESS",
    "sn": "123456789",
    "balance": "997061249",
    "tr_id": "3482",
    "rc": "00",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order002</ref_id>
  <status>1</status>
  <product_code>xld25000</product_code>
  <customer_id>0817777215</customer_id>
  <price>25000</price>
  <message>SUCCESS</message>
  <sn>123456789</sn>
  <balance>997061249</balance>
  <tr_id>3482</tr_id>
  <rc>00</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!-- type: tab-end -->

### Failed Response Example

 Below is the example of failed response that will sent to your callback URL.

<!--
type: tab
title: Version 1
-->

**JSON**

```json
{
  "data": {
    "ref_id": "order003",
    "status": "2",
    "code": "xld50000",
    "hp": "0817777215",
    "price": "50000",
    "message": "FAILED",
    "balance": "997011249",
    "tr_id": "3486",
    "rc": "07",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order003</ref_id>
  <status>2</status>
  <code>xld50000</code>
  <hp>0817777215</hp>
  <price>50000</price>
  <message>FAILED</message>
  <balance>997011249</balance>
  <tr_id>3486</tr_id>
  <rc>07</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!--
type: tab
title: Version 2
-->

**JSON**

```json
{
  "data": {
    "ref_id": "order003",
    "status": "2",
    "product_code": "xld50000",
    "customer_id": "0817777215",
    "price": "50000",
    "message": "FAILED",
    "balance": "997011249",
    "tr_id": "3486",
    "rc": "07",
    "sign": "96e1028f6beaa817ee3670a39c01c69d"
  }
}
```

**XML**

```json
<?xml version="1.0" encoding="UTF-8" ?>
<mp>
  <ref_id>order003</ref_id>
  <status>2</status>
  <product_code>xld50000</product_code>
  <customer_id>0817777215</customer_id>
  <price>50000</price>
  <message>FAILED</message>
  <balance>997011249</balance>
  <tr_id>3486</tr_id>
  <rc>07</rc>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```

<!-- type: tab-end -->

## Tutorial Video
You can see this video for callback code explanation using Laravel.

https://youtu.be/HPHEuTeewyc

Or you can see this video for callback code explanation using PHP.

https://youtu.be/wqEtalW4pIg