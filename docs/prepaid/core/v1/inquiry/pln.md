# Inquiry PLN

API to check whether PLN Prepaid Subscriber is valid or invalid.

## Path

Method | Path 
---------|----------
 POST | v1/legacy/index 

## Test Case

Use below test case in **development** environment only. 

<!-- title: Test Case List -->
hp | Response Message 
---------|----------
 12345678901 | SUCCESS
 Other than 12345678901 | INCORRECT DESTINATION NUMBER

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 commands | String | Value: `inquiry_pln` | Yes
 username | String | Your registered phone number | Yes
 hp | String | Customer ID | Yes
 sign | String | Signature. Value: `md5(username+api_key+hp)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "commands" : "inquiry_pln",
  "username" : "123123123",
  "hp"       : "12345678901",
  "sign"     : "6c4bbf2365e7e40423a76b713e3a5f0b"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <commands>inquiry_pln</commands>
  <username>123123123</username>
  <hp>12345678901</hp>
  <sign>6c4bbf2365e7e40423a76b713e3a5f0b</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 status | String | Transaction Status. List of status: <br> `1:SUCCESS` `2:FAILED` | Yes
 hp | String | Customer ID | Yes
 meter_no | String | Meter Number | Yes
 subscriber_id | String | Customer ID information | Yes
 name | String | Customer name | Yes
 segment_power | String | Segment Power | Yes
 message | String | Message | Yes
 rc | String | Response code. See [response code](../../../response-code.md) list | Yes


<!--
type: tab
title: JSON
-->

```json
{
  "data": {
    "status": "1",
    "hp": "12345678901",
    "meter_no": "548933889287",
    "subscriber_id": "12345678901",
    "name": "Sintya Oktaviani",
    "segment_power": "R1 \/000001300",
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
  <status>1</status>
  <hp>12345678901</hp>
  <meter_no>548933889287</meter_no>
  <subscriber_id>12345678901</subscriber_id>
  <name>Sintya Oktaviani</name>
  <segment_power>R1 /000001300</segment_power>
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
    "commands": "inquiry_pln",
    "username": "{your username}",
    "hp": "12345678901",
    "sign": "{your sign}",
  }
}
```

## Tutorial Video
You can see this video for inquiry PLN check code explanation using Laravel.

https://youtu.be/-g2FU_Y5awM

Or you can see this video for inquiry PLN check code explanation using PHP.

https://youtu.be/tt9EjSolQa0