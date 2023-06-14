# Check Balance

API to get remaining balance in your IAK wallet.

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index 

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `balance` | Yes
 username | String | Your registered phone number | Yes
 sign | String | Signature. Value: `md5(username+api_key+'bl')` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "balance",
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
  <commands>balance</commands>
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

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "balance": 997136249
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
    "commands": "balance",
    "username": "{your username}",
    "sign": "{your sign}",
  }
}
```

## Tutorial Video
You can see this video for check balance code explanation using Laravel.

https://youtu.be/WiyhNdPmLMM

Or you can see this video for check balance code explanation using PHP.

https://youtu.be/zr9ht9aPWtg