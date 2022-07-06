# Response Code

Below is all of response code for prepaid transaction.

Response code | Description | Status
---------|----------|---------
 00 | SUCCESS | Success
 06 | TRANSACTION NOT FOUND | Failed
 07 | FAILED | Failed
 10 | REACH TOP UP LIMIT USING SAME DESTINATION NUMBER IN 1 DAY | Failed
 12 | BALANCE MAXIMUM LIMIT EXCEEDED | Failed
 13 | CUSTOMER NUMBER BLOCKED | Failed
 14 |	INCORRECT DESTINATION NUMBER | Failed
 16 | NUMBER NOT MATCH WITH OPERATOR | Failed
 17 | INSUFFICIENT DEPOSIT | Failed
 20 | CODE NOT FOUND | Failed
 39 | PROCESS | Pending
 102 | INVALID IP ADDRESS | Failed
 106 | PRODUCT IS TEMPORARILY OUT OF SERVICE | Failed
 107 | ERROR IN XML FORMAT | Failed
 117 | PAGE NOT FOUND | Failed
 121 | MONTHLY TOP UP LIMIT EXCEEDED | Failed
 131 | TOP UP REGION BLOCKED FOR PLAYER | Failed
 201 | UNDEFINED RESPONSE CODE | Pending
 202 | MAXIMUM 1 NUMBER 1 TIME IN 1 DAY | Failed
 203 | NUMBER IS TOO LONG | Failed
 204 | WRONG AUTHENTICATION | Failed
 205 | WRONG COMMAND | Failed
 206 | THIS DESTINATION NUMBER HAS BEEN BLOCKED | Failed
 207 | 	MAXIMUM 1 NUMBER WITH ANY CODE 1 TIME IN 1 DAY | Failed

## Game

Below is additional response code that applied for inquiry game section only.

Response code | Description | Status | Description
---------|----------|---------|---------
 143 | INQUIRY NOT NEEDED | Failed | The inputted operator is a voucher type therefore it doesn't need the player id validation
