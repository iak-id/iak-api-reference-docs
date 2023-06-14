# Auto Detect Operator

API to top up prepaid products. IAK will automatically detect the operator for each number in **customer_id** field that you send. Change the **product_code** field to one of the code we listed below to activate this feature.

<!-- title: Pulsa Code for Auto Detect Operator -->
Pulsa code | Nominal 
---------|----------
pulsa10000 | 10000
pulsa100000 | 100000
pulsa1000000 | 1000000
pulsa150000 | 150000
pulsa20000 | 20000
pulsa200000 | 200000
pulsa25000 | 25000
pulsa30000 | 30000
pulsa300000 | 300000
pulsa5000 | 5000
pulsa50000 | 50000
pulsa500000 | 500000

<!-- theme: info -->

> Auto detect operator only applied can be applied with **pulsa** product type.
> See details information for product_type in [api pricelist](../price-list.md).

<!-- theme: info -->

> Product code will automatically detect the operator in customer_id field. See operator [prefix list](../../../prefix-list.md) for auto detect operator.

<!-- theme: info -->

> The API request is the same as top up API, you only need to change the pulsa_code value with one of above list. 
> 
> See top up API [here](./top-up.md)


