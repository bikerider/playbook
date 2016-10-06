The meaning of the different values provided in the dashboard are:

* **%NWC_SMS_SIP_OK**: A incoming message was sent to a NWC user. The user has some application online and gBE tells gCOB to deliver the message by SIP protocol. TUCore answered with 200 OK to the message, so everything went OK.
* **%NWC_SIP_TUCore_timeout**: gCOB sent the message towards TUCore but it did not receive any answer in the waiting time.
* **%SIP_TUCore_error**: gCOB sent the message towards TUCore but it did receive an unsuccessful response from TUCore.
