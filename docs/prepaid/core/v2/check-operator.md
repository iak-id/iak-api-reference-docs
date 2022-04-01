# Check Operator Prefix

API to get operator name from customer id prefix. You can refer to [here](../../prefix-list.md) for operator prefix

## Path

Method | Path 
---------|----------
 POST | api/check-operator

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Your registered phone number | Yes
 customer_id | String | Customer ID | Yes
 sign | String | Signature. Value: `md5(username+api_key+'op')` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "username" : "123123123",
  "customer_id" : "0817777215",
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
  <customer_id>0817777215</customer_id>
  <sign>df5e80e8ab7f94a905617282ad8c26f3</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 operator | String | Operator name | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../../response-code.md) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "operator": "XL",
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
  <operator>XL</operator>
  <message>SUCCESS</message>
  <rc>00</rc>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://prepaid.iak.dev/api/check-operator",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "{your username}",
    "customer_id": "{your customer id}",
    "sign": "{your sign}",
  }
}
```