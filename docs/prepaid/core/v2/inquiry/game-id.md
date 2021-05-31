# Inquiry Game ID

API to check game ID.

## Path

Method | Path 
---------|----------
 POST | api/inquiry-game

## Test Case

Use below test case in **development** environment only. 

<!-- title: Test Case List -->
game_code | customer_id | Response Message
---------|----------|---------
 103 | 156378300\|8483 | SUCCESS
 Other than 103 | 156378300\|8483 | CODE NOT FOUND
 103 | Other than 156378300\|8483 | INCORECT DESTINATION NUMBER

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Your registered phone number | Yes
 game_code | String | Game Code. See [here](../../../game-format.md#inquiry-game-id) for game_code list | Yes
 customer_id | String | Customer ID. See [here](../../../game-format.md#inquiry-game-id) for customer_id formula | Yes
 sign | String | Signature. Value: `md5(username+api_key+game_code)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "username"    : "123123123",
  "game_code"   : "103",
  "customer_id" : "156378300|8483",
  "sign"        : "148c711ac48519014d2c361b6ebb50c2"
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
  <game_code>103</game_code>
  <customer_id>156378300|8483</customer_id>
  <sign>148c711ac48519014d2c361b6ebb50c2</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Player username | Yes
 status | Double | List of status <br> `1:Success` `2:Failed` | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../../../response-code.md) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "username": "budi",
    "status": 1,
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
  <username>budi</username>
  <status>1</status>
  <message>SUCCESS</message>
  <rc>00</rc>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://prepaid.iak.dev/api/inquiry-game",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "{your username}",
    "game_code": "103",
    "customer_id": "156378300|8483",
    "sign": "{your sign}",
  }
}
```