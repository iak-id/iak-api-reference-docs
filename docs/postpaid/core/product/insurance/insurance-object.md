# Insurance Object

## General

Below object applied for all insurance product except that listed in [specific](#specific) section.

Attributes | Type | Description | Mandatory
---------|----------|---------|----------
insured | String | Number of member insured | Yes
policy_status | String |  Policy Status | Yes
due_date | String | Last day to pay bill | Yes
footer | String | Biller message | Yes

## Specific

This object applied for certain product as stated below.

### TASPEN
This object applied for pulsa_code: `TASPEN.ASURANSI`

Attributes | Type | Description | Mandatory
---------|----------|---------|----------
misc_fee | Double | Other fee | No
item_name | String | Item name | No
no_rangka | String | Chassis number | No
no_pol | String | Police number | No
tenor | String | Tenor | No
installment | Double | Installment fee | No
penalty_bill | Double | Penalty fee | No
max_payment | Double | Max payment | No
last_paid_due_date | String | Last paid due date | No
id_ref | String | Finance reff number | No
