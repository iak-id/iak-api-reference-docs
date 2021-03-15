# Check Balance

API to get remaining balance in your IAK wallet.

## Path

Method | Path 
---------|----------
 POST | api/check-balance

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Your registered phone number | Yes
 sign | String | Signature. Value: `md5(username+api_key+'bl')` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "username" : "123123123",
  "sign"     : "df5e80e8ab7f94a905617282ad8c26f3"
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
  <sign>df5e80e8ab7f94a905617282ad8c26f3</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 balance | Double | Your balance | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../response-code.md) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "balance": 997136249,
    "message": "SUCCESS",
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
  <balance>997136249</balance>
  <message>SUCCESS</message>
  <rc>00</rc>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://testprepaid.mobilepulsa.net/api/check-balance",
  "body": {
    "username": "{your username}",
    "sign": "{your sign}",
  }
}
```