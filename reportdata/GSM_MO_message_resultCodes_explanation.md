The meaning of the different values provided in the dashboard are:

* **%Messages_OK**: Messages with the expected flow.
* **%Late_Dispatch**: The dispatch operation sent by gBE was not received on time (2s). In this flow it has not impact for the user, but an increase in this value means there is some problem in gBE or rSDP that is delaying the dispatchs.
* **%NOT_Supported_UDH**: Message with NOT supported UDH was received in gCOB. In gCOB we only support some UDH headers (mainly fragmentation ones), so probably these messages are NOT 'regular text' messages but some other kind of messages not intended for the user (messages to special apps, binary messages, etc.)
* **%NOT_supported_encoding**: Message received in gCOB with different encoding that supported ones (chinese, japanese, arabic, etc.)
