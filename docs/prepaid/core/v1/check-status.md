# Check Status

API to check status prepaid transaction.

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index 

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `inquiry` | Yes
 username | String | Your registered phone number | Yes
 ref_id | String | Your order number / reference ID ( must unique ) | Yes
 sign | String | Signature. Value: `md5(username+api_key+ref_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inquiry",
  "username" : "082210138584",
  "ref_id"   : "order001",
  "sign"     : "96e1028f6beaa817ee3670a39c01c69d"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <commands>inquiry</commands>
  <username>082210138584</username>
  <ref_id>order001</ref_id>
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
sn | String | Serial Number (**only appear when status is success**). See [here](../../sn-format.md) for SN format | No
pin | String | Pin (**only appear in games product**) | No
balance | Double | Final Balance | Yes
tr_id | Integer | Transaction ID | Yes
rc | String | Response code. See [response code](../../response-code.md) list | Yes

### Success Response Example

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "ref_id": "order001",
    "status": 1,
    "code": "xld25000",
    "hp": "0817777215",
    "price": 25000,
    "message": "SUCCESS",
    "sn": "123456789",
    "balance": 997061249,
    "tr_id": 3482,
    "rc": "00"
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
  <status>1</status>
  <code>xld25000</code>
  <hp>0817777215</hp>
  <price>25000</price>
  <message>SUCCESS</message>
  <sn>123456789</sn>
  <balance>69000</balance>
  <tr_id>6159309</tr_id>
  <rc>00</rc>
</mp>
```
<!-- type: tab-end -->

### Failed Response Example

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "ref_id": "order001",
    "status": 2,
    "code": "xld25000",
    "hp": "0817777215",
    "price": 25000,
    "message": "FAILED",
    "balance": 997061249,
    "tr_id": 3482,
    "rc": "07"
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
  <status>2</status>
  <code>xld25000</code>
  <hp>0817777215</hp>
  <price>25000</price>
  <message>FAILED</message>
  <balance>69000</balance>
  <tr_id>6159309</tr_id>
  <rc>07</rc>
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
    "commands": "inquiry",
    "username": "{your username}",
    "ref_id": "order001",
    "sign": "{your sign}"
  }
}
```