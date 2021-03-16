# Download Receipt

API to download receipt after paying the bill. 

## Path

Method | Path 
---------|----------
 GET | api/v1/download/:tr_id

### Path Parameters

<!-- title: Path Parameters -->
Attributes | Type | Description | Mandatory
---------|----------|---------|----------
 tr_id | Integer | Inquiry ID (payment must be done first) | Yes

```json
BASE_URL/api/v1/download/123
```

## Response

The response will be receipt in pdf format.