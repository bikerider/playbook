# TU NWC App originated call dashboard

The meaning of the different values provided in the dashboard are:

* **%Message_OK**: A message sent from the app that did NOT require fragmentation was successfully delivered.
* **%User_Subscription_not_active**: The user has NOT an active subscription in gCOB. If the user is suspended, he should not be able to login any app, so these messages are from users that are misaligned in databases.
* **%Error_TL_extraction_gCOB**: There was some error in gCOB when trying to extract the information of the 3gpp encapsulated message sent by the iPhone.
* **%NOT_Supported_UDH**: Some UDH header included in the message is not supported in gCOB. Message NOT progressed to the network(by gCOB).
* **%NOT_supported_encoding**: The encoding sent by the iPhone is NOT supported by gCOB. Message NOT progressed to the network (by gCOB).
* **SMPP_Timeout**: There was a timeout between gCOB and the SMSC in the SMPP Protocol. Message could have been lost.
* **SMPP_Error**: There was an error between gCOB and the SMSC in the SMPP Protocol. Message was not progressed to the network.
* **%gOB_Internal_error**: There was some error in gCOB processing. Message was not progressed to the network.
