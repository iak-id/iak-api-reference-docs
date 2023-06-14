# Introduction

IAK API use **RESTful API** as interface to communicate. Our API has predictable, resource oriented URL, and use HTTPS. 

- We wrap every API response in JSON or XML
- Set the Content-Type as application/xml for XML or application/json for JSON
- Follow the request method ( **POST** or **GET** ) which you can find in each function
- Term **PULSA** means "Mobile Topup / Recharge"
- We'd suggest to set the time out to 30 seconds for postpaid transaction

You can use IAK API in sandbox or production environment. In sandbox environment is just simulation and will not interact with biller. The URL you use to call API will determine whether the transaction is in sandbox or production environment.

You can visit [IAK's youtube channel](https://www.youtube.com/@iak_id) for IAK API tutorials.