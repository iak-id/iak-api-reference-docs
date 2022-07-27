---
stoplight-id: 472bd485a6559
---

# Multifinance Object

## General

Below object applied for all finance product except that listed in [special](#special) section.

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

## Special

This object applied for certain product as stated below.

### AIA
This object applied for AIA pulsa_code: `AIA.PREMICONVEN`, `AIA.PREMISYARIAH`, `AIA.NONPREMICONVEN`, `AIA.NONPREMISYARIAH`

Attributes | Type | Description | Mandatory
---------|----------|---------|----------
insured | String | Number of member insured | Yes
policy_status | String |  Policy Status | Yes
due_date | String | Last day to pay bill | Yes

### Mega Finance
This object applied for pulsa_code `FNMF`

Attributes | Type | Description | Mandatory
---------|----------|---------|----------
installment | Double | Installment fee | Yes
penalty_bill | Double | Penalty fee | Yes
