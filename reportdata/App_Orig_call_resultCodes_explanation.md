# TU App originated call

The meaning of the different values provided in the dashboard are:

* **%Answered_call**: The call was answered normally.
* **%User_Subscription_not_active**: The user has NOT an active subscription in gCOB. If the user is suspended, he should not be able to login any app, so these calls are from users that are misaligned in databases.
* **%B_number_barred**: The number the user dialed is not permitted in this OB. gCOB Barring feature is not allowing the call progress.
* **%Unsuccessful_SIP_code_from_OB**: The OB responded the call with some unsuccessful code. The reason for this can be some problem of the user in Prepay system (no balance), a problem in the OB, user misdialed...
* **%No_Answer_from_OB**: The call timed out without receiving any response from the OB system.
* **%Call_established_more_than_24h**: The call was established for more than 24 hours. It should not happen, and probably is in that state because some signaling problem.
* **%Internal_error**: There was some problem in gCOB with the call.
* **%User_abandoned**: Calling user abandoned the call.
