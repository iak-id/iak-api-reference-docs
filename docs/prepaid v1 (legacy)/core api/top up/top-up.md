# Top Up

API to top up prepaid products.

<!-- theme: info -->

> ### A thing to know
>
> 1. For the first time, top up will always response **processing**. IAK will send callback once the transaction become > success / failed. Learn more about callback [here](../../callback.md)
> 
> 2. If you top up again with the same ref_id, then it we will not proceed the transaction but it will become check status. Learn more about check status [here](../check-status.md)

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index 

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `topup` | Yes
 username | String | Your registered phone number | Yes
 ref_id | String | Your order number / reference ID ( must unique ) | Yes
 hp | String | Customer ID | Yes
 pulsa_code | String | Product Code. You can get list of product code in [pricelist api](price-list.md) or from pricelist [here](https://iak.id/webapp/pricelist) | Yes
 sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!-- theme: info -->

> ### A thing to know
>
> Here is the customer ID for each product type: 
> 1. **pulsa**: Phone Number / MSISDN
> 2. **data**: Phone Number / MSISDN
> 3. **pln**: Meter Number (11 digits)
> 4. **games**: MSISDN (we don't send SMS). See [here] for example.

<!--
type: tab
title: JSON
-->

```json
{
  "commands"   : "topup",
  "username"   : "123123123",
  "ref_id"     : "order001",
  "hp"         : "0817777215",
  "pulsa_code" : "xld25000",
  "sign"       : "96e1028f6beaa817ee3670a39c01c69d"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0" ?>
<mp>
  <commands>topup</commands>
  <username>123123123</username>
  <ref_id>order001</ref_id>
  <hp>0817777215</hp>
  <pulsa_code>xld25000</pulsa_code>
  <sign>96e1028f6beaa817ee3670a39c01c69d</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
ref_id | String | Your order number / reference ID ( must unique ) | Yes
 status | Double | Transaction Status. List of status: <br> `0:PROCESS` `1:SUCCESS` `2:FALIED` | Yes
 code | String | Product Code | Yes
 hp | String | Customer ID | Yes
 price | Double | Product price | Yes
 message | String | Message | Yes
 balance | Double | Final Balance | Yes
 tr_id | Integer | Transaction ID | Yes
 rc | String | Response code. See [response code](../response-code.md) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "ref_id": "order001",
    "status": 0,
    "code": "xld25000",
    "hp": "0817777215",
    "price": 25000,
    "message": "PROCESS",
    "balance": 997061249,
    "tr_id": 3482,
    "rc": "39"
  }
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <ref_id>order001</ref_id>
  <status>0</status>
  <code>xld25000</code>
  <hp>0817777215</hp>
  <price>25000</price>
  <message>PROCESS</message>
  <balance>69000</balance>
  <tr_id>6159309</tr_id>
  <rc>39</rc>
</mp>
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
    "commands": "topup",
    "username": "{your username}",
    "hp": "0817777215",
    "ref_id": "order001",
    "pulsa_code": "xld25000",
    "sign": "{your sign}"
  }
}
```