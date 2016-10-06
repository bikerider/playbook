The meaning of the different values provided in the dashboard are:

* **%Vanilla_SMS_SIP_OK**: A incoming message was sent to a Vanilla user. The user has some application online and gBE tells gCOB to deliver the message by SIP protocol. TUCore answered with 200 OK to the message, so everything went OK.
* **%Vanilla_SMS_CUE_OK**: A incoming message was sent to a Vanilla user. The user has NOT online applications and gBE tells gCOB NOT to deliver the message by SIP protocol. Message will be included in user timeline via TUCore API.
* **%User_Subscription_not_active**: The user has NOT an active subscription in gCOB. The user could be suspended or it could be misaligned in databases.
* **%UDH_Header_not_supported**: The incoming message to the user contains some UDH header that is not supported.
* **%SIP_TUCore_timeout**: gCOB sent the message towards TUCore but it did not receive any answer in the waiting time.
* **%SIP_TUCore_error**: gCOB sent the message towards TUCore but it did receive an unsuccessful response from TUCore.
* **%Dispatch_timeout**: gCOB did not receive the dispatch for the session on time.
