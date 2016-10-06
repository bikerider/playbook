# TU MO originated message, Brazil

This flow is one of the simplest ones we have in the service, the user writes some SMS from the native client in his phone, and the message gets to gCOB for it to notify the message to gBE in order to include it in the timeline.

## gConnectOB runlogs and CDRs dashboards

Query for CDR for GSM MO result in Brazil for all the areas (there's no need  to differentiate in this flow per area):

   [Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1465564854.1236240.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_GSM_MO_CDR_result) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1465564854.1236240.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_GSM_MO_CDR_result)

{% include Embed_TEEN_BR_GSM_MO_CDR_result.html %}

{% markdown GSM_MO_message_resultCodes_explanation.md %}
