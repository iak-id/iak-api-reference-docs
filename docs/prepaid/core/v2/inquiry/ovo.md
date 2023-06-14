# Inquiry OVO

API to check whether OVO number is valid or invalid.

## Path

Method | Path 
---------|----------
 POST | api/inquiry-ovo

 ## Test Case

Use below test case in **development** environment only. 

<!-- title: Test Case List -->
customer_id | Response Message 
---------|----------
 082179374708 | SUCCESS
 Other than 082179374708 | INCORRECT DESTINATION NUMBER

## Request Body

<!-- title: Request Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 username | String | Your registered phone number | Yes
 customer_id | String | Customer ID | Yes
 sign | String | Signature. Value: `md5(username+api_key+customer_id)` | Yes

<!--
type: tab
title: JSON
-->

```json
{
  "username"    : "123123123",
  "customer_id" : "082179374708",
  "sign"        : "df1f2be3585597a5ec102b792555adc9"
}
```

<!--
type: tab
title: XML
-->

```json
<?xml version="1.0"?>
<mp>
  <username>123123123</username>
  <customer_id>082179374708</customer_id>
  <sign>df1f2be3585597a5ec102b792555adc9</sign>
</mp>
```
<!-- type: tab-end -->

## Response

<!-- title: Response Attributes -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 status | String | Transaction Status. List of status: <br> `1:SUCCESS` `2:FAILED` | Yes
 customer_id | String | Customer ID | Yes
 name | String | Customer name | Yes
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
    "customer_id": "082179374708",
    "name": "OVO shXXXy",
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
  <customer_id>082179374708</customer_id>
  <name>OVO shXXXy</name>
  <message>SUCCESS</message>
  <rc>00</rc>
</mp>
```
<!-- type: tab-end -->

## Live Testing

```json http
{
  "method": "POST",
  "url": "https://prepaid.iak.dev/api/inquiry-ovo",
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "username": "{your username}",
    "customer_id": "{your customer_id}",
    "sign": "{your sign}",
  }
}
```

## Tutorial Video
You can see this video for inquiry OVO check code explanation using Laravel.

https://youtu.be/-g2FU_Y5awM

Or you can see this video for inquiry OVO check code explanation using PHP.

https://youtu.be/tt9EjSolQa0