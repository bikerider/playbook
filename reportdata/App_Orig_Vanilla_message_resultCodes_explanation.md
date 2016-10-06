The meaning of the different values provided in the dashboard are:

* **%Fragmented_message_OK**: A message sent from the app that required fragmentation was successfully delivered (all framents).
* **%Message_OK**: A message sent from the app that did NOT require fragmentation was successfully delivered.
* **%User_Subscription_not_active**: The user has NOT an active subscription in gCOB. If the user is suspended, he should not be able to login any app, so these messages are from users that are misaligned in databases.
* **%SMPP_Error**: There was some error in SMPP protocol between gCOB and the SMSC. Message failed.
* **%SMPP_Timeout**: There was some timeout in SMPP protocol between gCOB and the SMSC. Message could have failed.
* **%B_number_barred**: The dialed number is not permitted in the OB. gCOB Barring feature stopped the message.
* **%Internal_error**: Internal error in gCOB. Message was not progressed.
