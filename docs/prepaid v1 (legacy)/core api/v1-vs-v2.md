# Different Between V1 and V2

IAK prepaid API have 2 version. Actually the flow and process behind is still the same. The difference is in version 2, its more clear about the endpoint path, request body and response body format. In version 1, each service is defined by its request body meanwhile the version 2 is in each path already defined the service. The request body and response body is more clearly in version 2. Below is the summary of difference between version 1 and version 2.

 | - |V1 | V2 |
 ---------|---------|----------
  Endpoint path | v1/legacy/index | api/{service-name}
 Request body | Can be seen in each docs segment | Can be seen in each docs segment
 Response body | Can be seen in each docs segment | Can be seen in each docs segment

 
<!-- theme: info -->

> It is recomended to use version 2 
