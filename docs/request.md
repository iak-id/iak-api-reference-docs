# Request

To make request into IAK API, it is the same way as make request to other **RESTful API**.

## Base URL

IAK provide different base url for prepaid and postpaid product. Below is listed IAK base URL for each version.

<!--
type: tab
title: Prepaid
-->

Environment | Base URL 
----------|---------
Development | Old: `https://testprepaid.mobilepulsa.net` <br> New: `https://prepaid.iak.dev`
Production | Old: `https://api.mobilepulsa.net` <br> New: `https://prepaid.iak.id`

<!--
type: tab
title: Postpaid
-->

Environment | Base URL 
----------|---------
Development | `https://testpostpaid.mobilepulsa.net`
Production | `https://mobilepulsa.net`

<!-- type: tab-end -->

## Schema

IAK provide 2 request schema to make API request: **JSON** and **XML**. The request header must appropriate based on the request schema.


<!--
type: tab
title: JSON
-->

Content-Type: application/json

<!--
type: tab
title: XML
-->

Content-Type: application/xml

<!-- type: tab-end -->

## Authentication

IAK API use **md5** hash to authenticate the requests. You need to put the **sign** key as request body and combination of md5 hash as value. The combination include username, [api key](developer-documentation/docs/integration/api-key.md), and additional.

```javascript
sign: md5({username}+{api_key}+{additional})
```

**`additional`** : Based on the request commands. The additional will be explained in each api call later.

