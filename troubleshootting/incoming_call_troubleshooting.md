# Incoming Call troubleshooting procedure

This document describes the basic operations troubleshooting procedure for the incoming call scenarios.

## Massive problems in incoming call flow

### ASR decrease / TUCore incoming calls decrease

The typical problem in incoming call flow is that there is a decrease in the incoming call getting to TUCore.

The proposed troubleshooting procedure is the following one:

#### IC_MassiveTroubleshooting_step_1 Check if calls are getting to gCOB or not.

Although **unfortunately we don't have 'real-time' gCOB runlogs/CDRs in most of the OBs**, first thing we should check is what is the status of the incoming calls reaching gCOB. Depending on the OB, we can do the following Splunk search for the last days:

  * Check the gCOB CDR results for incoming call in BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/search?q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20source!%3D%22*.gz%22%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20lookup%20%20TEEN_gCOB_CDRs_resultcodes%20resultCode%20as%20myResult%20OUTPUT%20text%20as%20myResult2%20%7C%20stats%20c%20by%20myHour%20myResult2%20%7C%20eventstats%20sum(c)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(c*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20myResult2%20%7C%0Arename%20%22totals%3A%20Answered_call%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&earliest=-48h%40h&latest=now&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Answered_call%22%2C%22%25%3A%20Call_abandoned%22%2C%22%25%3A%20Call_forwarded%22%2C%22%25%3A%20Call_not_established_no_errors%22%2C%22%25%3A%20Unsuccessful_Call%22%2C%22%25%3A%20User_Subscription_not_active%22%2C%22%25%3A%20gCOB_Internal_error%22%2C%22%25%3A%20User_abandoned%22&sid=1467371934.1233674.mia-spl-sch01) / [Link based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20source!%3D%22*.gz%22%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20lookup%20%20TEEN_gCOB_CDRs_resultcodes%20resultCode%20as%20myResult%20OUTPUT%20text%20as%20myResult2%20%7C%20stats%20c%20by%20myHour%20myResult2%20%7C%20eventstats%20sum(c)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(c*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20myResult2%20%7C%0Arename%20%22totals%3A%20Answered_call%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&earliest=-48h%40h&latest=now&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Answered_call%22%2C%22%25%3A%20Call_abandoned%22%2C%22%25%3A%20Call_forwarded%22%2C%22%25%3A%20Call_not_established_no_errors%22%2C%22%25%3A%20Unsuccessful_Call%22%2C%22%25%3A%20User_Subscription_not_active%22%2C%22%25%3A%20gCOB_Internal_error%22%2C%22%25%3A%20User_abandoned%22&sid=1467371934.1233674.mia-spl-sch01)

  * Check the gBE actions sent to gCOB for incoming call in BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/search?earliest=-48h%40h&latest=now&q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20source!%3D%22*.gz%22%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20stats%20dc(CallSessionId)%20as%20myCount%20by%20myHour%20BEAction%20%7C%20eventstats%20sum(myCount)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(myCount*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20BEAction%20%7C%20rename%20%22totals%3A%20Continue%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&sid=1467385972.1242511.mia-spl-sch01) / [Link based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?earliest=-48h%40h&latest=now&q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20source!%3D%22*.gz%22%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20stats%20dc(CallSessionId)%20as%20myCount%20by%20myHour%20BEAction%20%7C%20eventstats%20sum(myCount)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(myCount*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20BEAction%20%7C%20rename%20%22totals%3A%20Continue%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&sid=1467385972.1242511.mia-spl-sch01)

With those queries we can checñ

* [UK dashboard based on IP](https://10.253.0.167/en-US/app/tugo/outgoing_call_conversion?earliest=0&latest=).
* [UK dashboard based on URL](https://ldn-splunk.tefcomms.com/en-US/app/tugo/outgoing_call_conversion?earliest=0&latest=).

If the **2. Outbound leg from TU Core** parameter is high *(>98-99%)* or not:

* **If the percentage of Outbound leg is low for that  OB** this means that *there's probably a problem bewteen the Freeswitchs in TUCore and gBE*.
* **If the percentage of Outbound leg is high** this discards problems in gBE and TUCore's Freeswitchs. In this case we will have to check deeper in Voipmonitor statistics which error code increased and analyze some samples.
   * If the calls are not getting to the OB, there has to be a problem in TUCore platform (BES) or in some SBC (routing problem?).
   * If the calls are getting to the OB, go to [next step](#aoc_ts_2-check-why-calls-are-failing-in-the-ob).

#### AOC_MassiveTroubleshooting_step_2 Check why calls are failing in the OB

In case calls are failing in the OB, we have 2 sources of data to analyze what is going on:

1. **gConnectOB runlogs and CDRs**: we can try to analyze what has changed querying in splunk for gCOB data:

   * Query for CDR result for outgoing calls in Brazil for all the areas [IP Based link](https://10.253.1.11/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464361705.273182.mia-spl-sch01) / [URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464361705.273182.mia-spl-sch01)

   * Query for CDR result in Brazil for an specific area (54 in the example) [IP Based link](https://10.253.1.11/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20where%20calling_area%3D54%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464361705.273182.mia-spl-sch01) / [URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20where%20calling_area%3D54%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464361705.273182.mia-spl-sch01)

   * Query for CDR result codes in whole Brazil [IP Based link](https://10.253.1.11/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20%20timechart%20span%3D1h%20count%20by%20myResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362657.274131.mia-spl-sch01) / [URL Based link ](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20%20timechart%20span%3D1h%20count%20by%20myResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362657.274131.mia-spl-sch01)

   * Query for CDR result codes in some area (54 in the example) Brazil [IP Based link](https://10.253.1.11/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20where%20calling_area%3D54%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20%20timechart%20span%3D1h%20count%20by%20myResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362785.274320.mia-spl-sch01) / [URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?q=search%20sourcetype%3D%22CDR%20-%20gOB_BR%22%20%22CallType%3D\%22outgoing%22%20%7C%20%20rex%20%22CallingParty%3D\%220055%28%3F%3Ccalling_area%3E\d\d%29\d*%22%20%7C%20where%20calling_area%3D54%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20%20timechart%20span%3D1h%20count%20by%20myResult&earliest=-30d%40d&latest=now&display.page.search.mode=fast&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362785.274320.mia-spl-sch01)

   * Query for CDR result in Argentina [IP Based link](https://10.253.1.11/en-US/app/tugo/search?earliest=-7d%40d&latest=now&q=search%20sourcetype%3D%22CDR%20-%20gOB_AR%22%20%22CallType%3D\%22outgoing%22%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362151.273731.mia-spl-sch01) / [URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?earliest=-7d%40d&latest=now&q=search%20sourcetype%3D%22CDR%20-%20gOB_AR%22%20%22CallType%3D\%22outgoing%22%20%7C%20timechart%20span%3D1h%20count%20by%20CallResult&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362151.273731.mia-spl-sch01)

   * Query for CDR result codes in Argentina [IP Based link](https://10.253.1.11/en-US/app/tugo/search?earliest=-7d%40d&latest=now&q=search%20sourcetype%3D%22CDR%20-%20gOB_AR%22%20%22CallType%3D\%22outgoing%22%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20timechart%20span%3D1h%20count%20by%20myResult&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362444.274001.mia-spl-sch01) / [URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?earliest=-7d%40d&latest=now&q=search%20sourcetype%3D%22CDR%20-%20gOB_AR%22%20%22CallType%3D\%22outgoing%22%20%7C%20rex%20%22%28%3F%3CmyResult%3ESuccess%3D\%22[^\%22]*\%22%3BResultCode%3D\%22\d*\%22%29%22%20%7C%20timechart%20span%3D1h%20count%20by%20myResult&display.page.search.tab=visualizations&display.general.type=visualizations&sid=1464362444.274001.mia-spl-sch01)

2. **Comm-reason header in SIP responses**:

   **Pending how to get that information from Splunk or Voipmonitor**

## Single call/user investigations

 When troubleshooting specific calls, these are the steps that can be followed:

#### AOC_SingleUserTroubleshooting_step_1

For the app originated flow, the first place to review the call is Voipmonitor [IP Based link](http://10.253.0.169/index.php) / [URL Based link](http://voipmonitor/index.php).

A basic manual for this tool can be found [here]({{site.baseurl}}/Voipmonitor_tutorial_intro/).

It should be checked:

* The format of the number in the different headers is the appropriate for the specific country:
   * _Request URI_: The format of the number should be suitable for the OB
   * _To header_: The number in the To header should be the E.164 normalized version of the dialed number (for the platform to include the communication record in the appropriate timeline of the user).
* The INVITE gets to the SIP endpoint provided by the OB.

  From gConnectOB version 1.2.7.1 on , we included the service to put a Comm-Reason header in the unsuccessful response from gCOB towards TUCore. In case the call received some unsuccessful response in the OB, that Comm-Reason header will contain the sip response that the OB equipment replied and the information provided by the OB in the Reason header.

  NOTE: If there is no SIP Reason header received from the OB, Comm-Reason header will contain just the cause parameter.


  The format of the Comm-Reason header is the following (this is an example):

   If the Reason received in the OB unsuccessful response is:

>  Reason: Q.850;cause=127;text="Interworking, unspecified"

 The Comm-Reason will have the following format

> Comm-Reason: OB;cause=xxx;text="Interworking, unspecified"; rcvdCause="127";rcvdProtocol="Q.850";

  where:

   * *cause=* will be XXX, where XXX is the sip response code received by gCOB.
   * *text=* will contain the value of the the "text" field in Reason if present.
   * *rcvdCause=* will contain the value of the cause field in original Reason
   * *rcvdProtocol=* will contain the protocol value after the Reason header.

   The format of the reason header in SIP can be checked [here](https://tools.ietf.org/html/rfc3326).


#### AOC_SingleUserTroubleshooting_step_2


In case the call is getting to the OB and we can't identify the reason, you can check the **Call investigations v2** dashboard [Latam IP Based link](https://10.253.1.11/en-US/app/tugo/call_investigations_v2?earliest=-24h%40h&latest=now) / [Latam URL Based link](https://mia-splunk.tefcomms.com/en-US/app/tugo/call_investigations_v2?earliest=-24h%40h&latest=now) / [UK IP Based link](https://10.253.0.167/en-US/app/tugo/call_investigations?earliest=-24h%40h&latest=now) / [UK URL Based link](https://ldn-splunk.tefcomms.com/en-US/app/tugo/call_investigations?earliest=-24h%40h&latest=now)

{% markdown Call_investigation_dashboard_explanation.md %}
