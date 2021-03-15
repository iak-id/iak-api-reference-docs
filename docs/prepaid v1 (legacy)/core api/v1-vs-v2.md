# Different Between Version 1 and Version 2

IAK prepaid API have 2 version. Actually the flow and process behind is still the same. The difference is in version 2, its more clear about the endpoint path, request body and response body format. In version 1, each service is defined by its request body meanwhile the version 2 is in each path already defined the service. The request body and response body is more clearly in version 2. Below is the summary of difference between version 1 and version 2.

 | - |Version 1 | Version 2 |
 ---------|---------|----------
  Endpoint path | v1/legacy/index | api/{service-name}
 Request & response body field | hp | customer_id
 Request & response body field | all of pulsa keyword | product
 Request & response body field (in [pricelist api](./price-list.md) only) | pulsa_op | product_description
 Request & response body field (in [pricelist api](./price-list.md) only) | masaaktif | active_period
