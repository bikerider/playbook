---
title: Brazil Incoming call flow
keywords: Brazil
summary: "This page contains the relevant information about Incoming call flow in Brazil"
sidebar: opsPB_sidebar
permalink: /BR_incoming_call_intro/
---

**IMPORTANT**: Note that the gCOB runlog files are sent to Splunk once they are completed. This means the data from the last days could be not complete (until the files get to 21Mb in gCOB sites).

## Incoming call CDR result

The following dashboards can be used to monitor the performance of the incoming call in Brazil deployment.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1465921356.64584.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_CDRs_resultcodes){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1465921356.64584.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_CDRs_resultcodes){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_CDRs_resultcodes.html %}

{% markdown Incoming_call_resultCodes_explanation.md %}


## Incoming call gBE delayed dispatchs

The following dashboard can be used to monitor the performance of the dispatchs coming from gBE to gCOB in the incoming call in Brazil deployment.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1465923552.66204.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_Call_delayed_dispatchs){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1465923552.66204.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_Call_delayed_dispatchs){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_Call_delayed_dispatchs.html %}

## Incoming call Voicemail diversion errors

The following dashboard can be used to monitor the performance of the voicemail diversions in Brazil deployment. In this dashboard the evolution of the percentage of errors is shown.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466000536.105914.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_VM_errors){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466000536.105914.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_VM_errors){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_VM_errors.html %}

## Incoming call Voicemail diversion errors per Area

The following dashboard can be used to monitor the performance of the voicemail diversions in Brazil deployment. In this dashboard the  percentage of errors per area for the last 24 hours is shown.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466002080.107849.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_VM_errors_per_area){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466002080.107849.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_VM_errors_per_area){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_VM_errors_per_area.html %}

## Incoming call Domain Transfer failures

The following dashboard can be used to monitor the performance of the domain tranfer failures in Brazil deployment. This dashboard shows the global evolution of the percentage of errors in the last month.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466004194.110585.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466004194.110585.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_Domain_transfer_errors.html %}

## Incoming call Domain Transfer failures per area

The following dashboard can be used to monitor the performance of the domain tranfer failures in Brazil deployment per area. This dashboard shows the percentage of errors in the last 24 hours per Area of the calledParty.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466007331.114326.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors_per_area){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466007331.114326.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_transfer_errors_per_area){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_Domain_transfer_errors_per_area.html %}


## Incoming call RBT MAP query delay Percentile 95

The following dashboard can be used to monitor the performance of the Map query to check RBT status in the HLR. This dashboard shows the percentile 95 of response times for the last month.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466007996.115045.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_RBT_MAP_query_response_time){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466007996.115045.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_RBT_MAP_query_response_time){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_RBT_MAP_query_response_time.html %}

## Incoming call Domain Transfer Delay Percentile 80 per area

The following dashboard can be used to monitor the performance of the domain tranfer delay percentile per area. This dashboard shows the percentile 80 of domain transfer delay for the last day per area.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466008997.116065.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_tranfer_delay_per_area){:target="_blank"} / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466008997.116065.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Incoming_call_Domain_tranfer_delay_per_area){:target="_blank"}

{% include Embed_TEEN_BR_Incoming_call_Domain_tranfer_delay_per_area.html %}
