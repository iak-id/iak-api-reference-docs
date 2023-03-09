# Response Code

Below is all of response code for prepaid transaction.

Response code | Description | Status | Solution
---------|----------|---------|---------
 00 | SUCCESS | Success | Transaction success.
 06 | TRANSACTION NOT FOUND | Failed | There is no transaction with your inputted ref_id. Please check again your inputted ref_id to find your transaction.
 07 | FAILED | Failed | Your current transaction has failed. Please try again.
 10 | REACH TOP UP LIMIT USING SAME DESTINATION NUMBER IN 1 DAY | Failed | Your current destination number top up request is reaching the limit on that day. Please try again tomorrow.
 12 | BALANCE MAXIMUM LIMIT EXCEEDED | Failed | -
 13 | CUSTOMER NUMBER BLOCKED | Failed | Your customer number (customer_id) has been blocked. You can change your customer number (customer_id) or contact our Customer Service.
 14 |	INCORRECT DESTINATION NUMBER | Failed | Your customer_id that you’ve inputted isn’t a valid phone number. Please check again your customer_id. 
 16 | NUMBER NOT MATCH WITH OPERATOR | Failed | Your phone number (customer_id) that you’ve inputted doesn’t match with your desired operator (product_code). Please check again your phone number or change your operator. 
 17 | INSUFFICIENT DEPOSIT | Failed | Your current deposit is lower than the product_price you want to buy. You can add more money into your deposit by doing top up on iak.id deposit menu, or if you are in development mode, you can add your development deposit by clicking the + (plus) sign on development deposit menu (https://developer.iak.id/sandbox-report). 
 20 | CODE NOT FOUND | Failed | Your inputted product_code isn’t in the database. Check again your product_code, you can check product_code list by using pricelist API (https://api.iak.id/docs/reference/ZG9jOjEyNjIwNjQy-price-list). 
 39 | PROCESS | Pending | Your current transaction is being processed, please wait until your transaction is fully processed. You can check the status by using check-status API or by receiving a callback (if you use callback).
 102 | INVALID IP ADDRESS | Failed | Your IP address isn’t allowed to make a transaction. You can add your IP address to your allowed IP address list in https://developer.iak.id/prod-setting. 
 106 | PRODUCT IS TEMPORARILY OUT OF SERVICE | Failed | The product_code that you pick is in non-active status. You can retry your transaction with another product_code that has active status.
 107 | ERROR IN XML FORMAT | Failed | The body format of your request isn’t correct or there is an error in your body (required, ajax error, etc). Please use the correct JSON or XML format corresponding to your request to API. You can see the required body request for each request in the API Documentation (https://api.iak.id/docs/reference).
 110 | SYSTEM UNDER MAINTENANCE | Failed | The system is currently under maintenance, you can try again later.
 117 | PAGE NOT FOUND | Failed | The API URL that you want to hit is not found. Try checking your request URL for any typos or try other API URLs.
 121 | MONTHLY TOP UP LIMIT EXCEEDED | Failed | -
 131 | TOP UP REGION BLOCKED FOR PLAYER | Failed | Your current destination number top up request is blocked in that region. Please try again with a different destination number.
 141 | INVALID USER ID / ZONE ID / SERVER ID / ROLENAME | Failed | Your inputted user ID / Zone ID / Server ID / Role name isn’t valid. Please try again with another user ID / Zone ID / Server ID / Role name.
 142 | INVALID USER ID | Failed | Your current destination number (user id) top up request is invalid. Please try again with a different destination number or try checking for typos in your field.
 201 | UNDEFINED RESPONSE CODE | Pending | The received response code is undefined yet. Please contact our Customer Service.
 202 | MAXIMUM 1 NUMBER 1 TIME IN 1 DAY | Failed | You can only top up to a phone number once in a day (based on your developer setting). If you want to allow more than one top up to a phone number, you can go to https://developer.iak.id/ then choose API Setting menu, you can turn on “Allow multiple transactions for the same number” in development or production settings.
 203 | NUMBER IS TOO LONG | Failed | Your inputted customer ID is too long. Please check again your customer ID.
 204 | WRONG AUTHENTICATION | Failed | Your sign (signature) field doesn’t contain the right key for your current request. Please check again your sign value.
 205 | WRONG COMMAND | Failed | The command that you’ve inputted is not a valid command, try check your commands field for typos or try another command.
 206 | THIS DESTINATION NUMBER HAS BEEN BLOCKED | Failed | The customer_id that you inputted is blocked. You can unblock it by remove customer number blacklist in API Security menu on developer.iak.id (https://developer.iak.id/end-user-blacklist). 
 207 | 	MAXIMUM 1 NUMBER WITH ANY CODE 1 TIME IN 1 DAY | Failed | You’ve already done a transaction today. Please do another transaction tomorrow, or disable the high restriction setting in https://developer.iak.id/prod-setting. 

## Game

Below is additional response code that applied for inquiry game section only.

Response code | Description | Status | Description
---------|----------|---------|---------
 143 | INQUIRY NOT NEEDED | Failed | The inputted operator is a voucher type therefore it doesn't need the player id validation. You don’t need to hit inquiry on voucher purchase. (https://api.iak.id/docs/reference/ec804704ff306-inquiry-game-server)
