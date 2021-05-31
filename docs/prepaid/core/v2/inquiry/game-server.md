# Inquiry Game Server

API to check game server.

## Path

Method | Path 
---------|----------
 POST | api/inquiry-game-server

## Test Case

Use below test case in **development** environment only. 

<!-- title: Test Case List -->
game_code | Response Message | Description
---------|----------|---------
 103 | SUCCESS | Servers list return [], means that user have to fill the server value on their own
 142 | SUCCESS | Fill server value accord to field value in the response
 100 | CODE NOT FOUND | Wrong code, check the code list above

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Your registered phone number | Yes
 game_code | String | Game Code. See [here](../../../game-format.md#inquiry-game-server) for game_code list | Yes
 sign | String | Signature. Value: `md5(username+api_key+game_code)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "username"   : "123123123",
  "game_code"  : "103",
  "sign"       : "148c711ac48519014d2c361b6ebb50c2"
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
  <sign>148c711ac48519014d2c361b6ebb50c2</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 servers | Array | Player username | Yes
 servers.**name** | String | Server Name | Yes
 servers.**value** | String | Server ID | Yes
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
    "servers": [
      {
        "name": "Test 1",
        "value": "90001"
      },
      {
        "name": "Test 2",
        "value": "90002"
      }
    ],
    "status": 1,
    "message": "SUCCESS",
    "rc": "00",
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
  <servers>
      <name>Test 1</name>
      <value>90001</value>
  </servers>
  <servers>
      <name>Test 2</name>
      <value>90002</value>
  </servers>
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
  "url": "https://prepaid.iak.dev/api/inquiry-game-server",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "{your username}",
    "game_code": "103",
    "sign": "{your sign}",
  }
}
```