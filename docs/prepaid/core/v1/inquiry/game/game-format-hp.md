---
stoplight-id: a3c75e05a75d3
---

# Inquiry Game Format hp

API to check format player id. This format player id is used for **hp** field in [topup](../../transaction/top-up.md)

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index 

## Test Case

Use below test case in **development** environment only. 

<!-- title: Test Case List -->
game_code | Response Message | Description
---------|----------|---------
 103 | SUCCESS | [userid]\|[zoneid]
 135 | SUCCESS | [userid]
 140 | SUCCESS | [rolename]\|[userid]\|[zoneid]
 127 | SUCCESS | [userid]\|[serverId]
 142 | SUCCESS | [rolename]\|[serverId]
 104 | INQUIRY NOT NEEDED |
 1234 | CODE NOT FOUND |

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `game-format-id` | Yes
 username | String | Your registered phone number | Yes
 game_code | String | Game Code. See [here](../../../../game-format.md#format-hp) for game_code list | Yes
 sign | String | Signature. Value: `md5(username+api_key+game_code)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands"   : "game-format-id",
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
  <commands>game-format-id</commands>
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
 formatGameId | String | Player id format | Yes
 status | Double | List of status <br> `1:Success` `2:Failed` | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../../../../response-code.md#game) list | Yes

<!--
type: tab
title: JSON
-->

```json
{
	"data": {
		"formatGameId": "[userid]",
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
  <formatGameId>[userid]</formatGameId>
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
  "url": "https://testprepaid.mobilepulsa.net/v1/legacy/index",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "commands": "game-format-id",
    "username": "{your username}",
    "game_code": "103",
    "sign": "{your sign}",
  }
}
```