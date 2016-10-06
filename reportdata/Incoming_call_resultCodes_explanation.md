The meaning of the different values provided in the dashboard are:

* **%Answered_call**: The incoming call was answered by the user or by the voicemail.
* **%Call_abandoned**: The call was abandoned by the calling party.
* **%Call_forwarded**: The call was forwarded by the called party. These calls are not sent to the apps.
* **%Call_not_established_no_errors**: The call was not established because the called party was not available (and voicemail was disabled).No error in call execution.
* **%Unsuccessful_call**: The call was not able to be completed due to some error.
* **%User_Subscription_not_active**: The user has NOT an active subscription in gCOB. If the user is suspended, he should not be able to login any app, so these messages are from users that are misaligned in databases.
* **%gCOB_Internal_error**: The call failed due to some internal error in gCOB. Typically the error is caused by the SB/MSC dropping ungracefully the TCAP dialog in the Camel/CS1+ control dialog.
