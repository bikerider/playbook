# INCOMING CALL TROUBLESHOOTING PROCEDURE

This document describes the basic operations troubleshooting procedure for the incoming call scenarios.

## MASSIVE ISSUES

### ASR decrease / TUCore incoming calls decrease

The typical problem in incoming call flow is that there is a decrease in the incoming call getting to TUCore.

* Check the gCOB CDR results for incoming call.

 * In BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_CDRs_resultcodes) / [Link based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_CDRs_resultcodes)
 
 * In ARG [Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466086202.183726.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_CDRs_resultcodes) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466086202.183726.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_CDRs_resultcodes) 

The proposed troubleshooting procedure is the following one:

#### STEP 1 -> Check if calls are getting to the OB or not.

Although **unfortunately we don't have 'real-time' gCOB runlogs/CDRs in most of the OBs**, first thing we should check is what is the status of the incoming calls reaching gCOB.

With gBE logs we can ** in real time ** check if calls are notified to gBE ("CalledNumber" event), and gCOB is receiving properly the calls:
[Link based on IP](https://10.253.1.11/en-US/app/tugo/search?earliest=-4h%40m&latest=now&q=search%20%22CalledNumber%22%20sourcetype%3D%22CALL%20-%20Corazones%22%20source%3D%22%2Fvar%2Flog%2Fconnect%2Fcall_control_br.log%22&display.page.search.tab=events&display.general.type=events&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&display.page.search.mode=fast&dispatch.sample_ratio=1&display.visualizations.charting.chart=column&sid=1476352468.1404941.mia-spl-sch02) / [Link based on domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?earliest=-4h%40m&latest=now&q=search%20%22CalledNumber%22%20sourcetype%3D%22CALL%20-%20Corazones%22%20source%3D%22%2Fvar%2Flog%2Fconnect%2Fcall_control_br.log%22&display.page.search.tab=events&display.general.type=events&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&display.page.search.mode=fast&dispatch.sample_ratio=1&display.visualizations.charting.chart=column&sid=1476352468.1404941.mia-spl-sch02)

2 options here:
 * Calls are NOT notified to gBE: **There has to be a problem in gCOB, that is not working fine or the OB has some problem in their network and gCOB is not able to notify the calls to gBE.** In case the deployment in the OB includes rSDP for call notifications, the problem can be in rSDP also (or connectivity between gCOB and gBE/rSDP).
 * Calls are notified to gBE but the calls are not getting to TUCore: see following step.
 
####  Step 2 -> Check why calls are getting to gCOB (and notified to gBE), but they are not getting to TUCore.

The first thing to check in this scenario is the proper status of the actions sent to gCOB:

* Check the gBE actions sent to gCOB for incoming call in BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/search?earliest=-48h%40h&latest=now&q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20stats%20dc(CallSessionId)%20as%20myCount%20by%20myHour%20BEAction%20%7C%20eventstats%20sum(myCount)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(myCount*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20BEAction%20%7C%20rename%20%22totals%3A%20Continue%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&display.page.search.mode=fast&dispatch.sample_ratio=1&display.visualizations.charting.chart=column&sid=1476348782.1402300.mia-spl-sch02) / [Link based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/search?earliest=-48h%40h&latest=now&q=search%20(sourcetype%3D%22CDR-gOB_BR%22%20OR%20sourcetype%3D%22CDR%20-%20gOB_BR%22)%20%22CallType%3D%5C%22incoming%22%20%7C%20rex%20%22(%3F%3CmyResult%3ESuccess%3D%5C%22%5B%5E%5C%22%5D*%5C%22%3BResultCode%3D%5C%22%5Cd*%5C%22)%22%20%7C%20rex%20%22Time%3D%5C%22%5Cd%5Cd%5Cd%5Cd-(%3F%3CmyHour%3E%5B%5ET%5D*T%5Cd%5Cd)%22%20%7C%20stats%20dc(CallSessionId)%20as%20myCount%20by%20myHour%20BEAction%20%7C%20eventstats%20sum(myCount)%20as%20total%20by%20myHour%20%7C%20eval%20%25%3Dround(myCount*100%2Ftotal%2C2)%20%7C%20chart%20values(total)%20as%20totals%20values(%25)%20as%20%25%20over%20myHour%20by%20BEAction%20%7C%20rename%20%22totals%3A%20Continue%22%20as%20Total%20%7C%20table%20myHour%20Total%20%25*%20%7C%20sort%20%2B%20myHour&display.page.search.tab=visualizations&display.general.type=visualizations&display.visualizations.charting.axisTitleY2.text=(%25)&display.visualizations.charting.axisY2.enabled=1&display.visualizations.charting.chart.overlayFields=%22%25%3A%20Continue%22%2C%22%25%3A%20Route%22%2C%22%25%3A%20Route_RouteLeg%22%2C%22%25%3A%20null%22&display.page.search.mode=fast&dispatch.sample_ratio=1&display.visualizations.charting.chart=column&sid=1476348782.1402300.mia-spl-sch02)

This can NOT be checked in splunk in real time, but it can be checked in gCOB.

The reason for the TUCore call decrease can be that gBE is sending a bigger amount(%) of "Continue" actions sent to gCOB. If that is happening the root cause can be related to the registration of the applications in TUCore or the ENUM server not registering those registrations properly.

If the dispatches are getting to gCOB and the amount of "Route SIP" is the correct one, there are some processes that can be causing this error and we should check:

* Check the domain transfer errors:

  * In BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors) / [Link based on domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors)
 
  * In ARG [Link based on IP](https://10.253.1.11/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_transfer_errors) / [Link based on domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_transfer_errors)
 
* Check the domain transfer delays:

  * In BR [Link based on IP](https://10.253.1.11/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_tranfer_delay_per_area) / [Link based on domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_tranfer_delay_per_area)
 
  * In ARG [Link based on IP](https://10.253.1.11/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_tranfer_delay) / [Link based on domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_tranfer_delay)
  
The domain transfer process is the mechanism we used, based on a prefix configured in the OB network, to convert the incoming call from Camel control dialog into SIP (to perform the forking of the call to the GSM network and to the apps). In case the domain transfer procedure is not working (or it's taking too long to happen) there will be no calls sent to TUCore.

Other problems that could be causing the traffic decrease, can be:
* Connectivity problems between gCOB and the SBC in the OB
* Problems in the OB
* Sip peering between the OB SBC and TUCore SBC.

If the calls are getting to TUCore SBC, but can not be answered in the applications, the problem has to be somewhere in TUCore and we should use "Voipmonitor" [Link based on IP](http://10.253.0.169/index.php) / [Link based on domain](http://voipmonitor/index.php) tool to debug.


## OTHER USEFUL LINKS FOR INCOMING CALL TROUBLESHOOTING

When investigating some problem in incoming calls, there's a Splunk report called "Call investigation V2" under *Troubleshoot* section [Link based on IP](https://10.253.1.11/en-US/app/tugo/call_investigations_v2?earliest=-24h%40h&latest=now) / [Link based on Domain](https://mia-splunk.tefcomms.com/en-US/app/tugo/call_investigations_v2?earliest=-24h%40h&latest=now)

The only imput we have to include in the report is the Call-Session-Id generated by gCOB for the call (it can be extracted, for example, from the calledNumber event "call_session_id":"00000059-000202BC-00001000-33610753-1476355568910927-2-72207", or from the Comm-Correlation-Id in the SIP signaling getting to TUCore(if any)).

The report shows us the following sections:
* *Call Summary*: Infomation that summarizes relevant data in the call like start time, a and b numbers, routing case (only GSM, call forking, only to apps), phone rang? and the outcome of the call.
* *Click VPN/10 field to open call in VoipMonitor*: Link to open automagically the call in Voipmonitor tool.
* *User Devices Activity*: Activity of the different devices of the user for this call. Status, model, app version, etc.
* *Event and actions* received in gBE for the call, from gCOB call notification API and from TUCore CC API also.
