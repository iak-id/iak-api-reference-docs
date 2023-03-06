# Response Code

Below is all of response code for postpaid transaction.

Response code | Description | Status | Solution
---------|----------|---------|---------
00 | PAYMENT / INQUIRY SUCCESS | Success | Your inquiry or payment is successfully processed.
01 | INVOICE HAS BEEN PAID | Failed | The invoice with your inputted data has already been paid. You don’t need to pay it again, or you can check for your inputted customer_id.
02 | BILL UNPAID | Failed | Your bill is unpaid, only reaching inquiry status. Please finish your payment first.
03 | INVALID REF ID | Failed | Your inputted ref_id isn’t valid. Please follow the correct format for ref_id (alpha_num only without space). Try again with a valid ref_id.
04 | BILLING ID EXPIRED | Failed | Your reference ID (ref_id) is expired. Please retry your inquiry request with a different reference ID (ref_id).
05 | UNDEFINED ERROR | Pending | Your transaction failed because of an undefined error. Please try again later.
06 | INQUIRY ID NOT FOUND | Failed | The inquiry ID (tr_id) that you’ve inputted is not found, there is no inquiry with that ID. You can check the inquiry ID (tr_id) field for any typos, or try using another inquiry ID.
07 | TRANSACTION FAILED | Failed | Your transaction has failed. Please try again.
08 | BILLING ID BLOCKED | Failed | The customer ID for your inputted product code is blocked by IAK. Please contact our Customer Service.
09 | INQUIRY FAILED | Failed | Your inquiry process failed. Please try to do the inquiry again.
10 | BILL IS NOT AVAILABLE | Failed | The bill isn’t available yet. Please try again when the bill is already added/available.
11 | DUPLICATE REF ID | Failed | The ref_id that you’ve inputted is already been inputted, try again with another ref_id.
13 | CUSTOMER NUMBER BLOCKED | Failed | Your custom number (customer_id) has been blocked by Indobest Artha Kreasi. You can change your customer number (customer_id) or ask IAK’s Customer Service.
14 | INCORRECT DESTINATION NUMBER | Failed | The customer/destination number that you’ve inputted is incorrect. Try checking your customer/destination number for typos or try with another customer/destination number.
15 | NUMBER THAT YOU ENTERED IS NOT SUPPORTED | Failed | Customer number that you’ve inputted isn’t supported by your inputted product_code. Try again with another customer number or product_code.
16 | NUMBER DOESN'T MATCH THE OPERATOR | Failed | Your customer number (customer_id) that you’ve inputted doesn’t match with your desired operator (product_code). Please check again your customer number or change your operator.
17 | BALANCE NOT ENOUGH | Failed | Your current balance is lower than the product price you want to buy. You can add more money into your deposit by doing top up on iak.id deposit menu, or if you are in development mode, you can add your development deposit by clicking the + (plus) sign on development deposit menu (https://developer.iak.id/sandbox-report).
20 | PRODUCT UNREGISTERED | Failed | Your inputted product_code isn’t in the database. Check again your product_code, you can check product_code list by using pricelist API (https://api.iak.id/docs/reference/ad7437ff00ecc-price-list).
30 | PAYMENT HAVE TO BE DONE VIA COUNTER / PDAM | Failed | Your inputted payment has to be done at the counter. Please do your transaction at the counter.
31 | TRANSACTION REJECTED DUE TO EXCEEDING MAXIMAL TOTAL BILL ALLOWED | Failed | Your current transaction is exceeding the maximal total bill allowed. Please try to reduce your transaction.
32 | TRANSACTION FAILED, PLEASE PAY BILL OF ALL PERIOD | Failed | Your current transaction isn’t covering all periods. Please try again to pay with all periods.
33 | TRANSACTION CAN'T BE PROCESS, PLEASE TRY AGAIN LATER | Failed | There is an error on your body field. Please check again your product code for typos, or retry with other product code.
34 | BILL HAS BEEN PAID | Failed | Your bill for your current transaction has been paid. Please try again for another transaction.
35 | TRANSACTION REJECTED DUE TO ANOTHER UNPAID ARREAR | Failed | Your transaction id failed. Please pay for your other arrear first, then try again your transaction.
36 | EXCEEDING DUE DATE, PLEASE PAY IN THE COUNTER / PDAM | Failed | Your current transaction is exceeding the due date. Please pay the transaction at the counter.
37 | PAYMENT FAILED | Failed | Your payment failed, please try again later.
38 | PAYMENT FAILED, PLEASE DO ANOTHER REQUEST | Failed | Your payment failed, please try again with a new request.
39 | PENDING / TRANSACTION IN PROCESS | Pending | Your transaction is still being processed. Please wait for further status updates.
40 | TRANSACTION REJECTED DUE TO ALL OR ONE OF THE ARREAR/INVOICE HAS BEEN PAID | Failed | Your transaction has already been paid. You can try again with another transaction.
41 | CAN'T BE PAID IN COUNTER, PLEASE PAY TO THE CORRESPONDING COMPANY | Failed | Your current transaction cannot be paid in the counter. You can pay your transaction to the corresponding company.
42 | PAYMENT REQUEST HAVEN'T BEEN RECEIEVED | Failed | Your current transaction is still in the inquiry process. Please continue your payment process first.
91 | DATABASE CONNECTION ERROR | Failed | There is an error on the database connection. Please try again later.
92 | GENERAL ERROR | Failed | The received response code is undefined yet. Please contact our Customer Service.
93 | INVALID AMOUNT | Failed | The amount inputted isn’t valid or identical with the amount from the supplier. Please check again your inputted amount.
94 | SERVICE HAS EXPIRED | Failed | -
100 | INVALID SIGNATURE | Failed | Your sign (signature) field doesn’t contain the right key for your current request. Please check again your sign value.
101 | INVALID COMMAND | Failed | The command that you’ve inputted is not a valid command, try checking your commands field for typos or try another command.
102 | INVALID IP ADDRESS | Failed | Your IP address isn’t allowed to make a transaction. You can add your IP address to your allowed IP address list in https://developer.iak.id/prod-setting.
103 | TIMEOUT | Failed | Your current request exceeds the timeout limit. You can try to request it again.
105 | MISC ERROR / BILLER SYSTEM ERROR | Failed | There is an error from the supplier. Please try again later.
106 | PRODUCT IS TEMPORARILY OUT OF SERVICE | Failed | The product_code that you pick is in non-active status. You can retry your transaction with another product_code that has active status.
107 | XML FORMAT ERROR | Failed | The body format of your request isn’t correct or there is an error in your body (required, ajax error, etc). Please use the correct JSON or XML format corresponding to your request to API. You can see the required body request for each request in the API Documentation (https://api.iak.id/docs/reference).
108 | SORRY, YOUR ID CAN'T BE USED FOR THIS PRODUCT TRANSACTION | Failed | The customer ID that you’ve inputted can’t be used for this product transaction. Please try again with another customer ID or another product.
109 | SYSTEM CUT OFF | Failed | PLN product code cannot receive a request at 11PM until 1AM (GMT +7). Please try again when the service is available.
110 | SYSTEM UNDER MAINTENANCE | Failed | The system is currently under maintenance, you can try again later.
117 | PAGE NOT FOUND | Failed | The API URL that you want to hit is not found. Try checking your request URL for any typos or try other API URLs.
201 | UNDEFINED RESPONSE CODE | Pending | The received response code is undefined yet. Please contact our Customer Service.
