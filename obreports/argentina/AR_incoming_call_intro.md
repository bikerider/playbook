
# TU Incoming call flow, Argentina

**IMPORTANT**: Note that the gCOB runlog files are sent to Splunk once they are completed. This means the data from the last days could be not complete (until the files get to 21Mb in gCOB sites).

## Incoming call CDR result

The following dashboards can be used to monitor the performance of the incoming call in Argentina deployment.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466086202.183726.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_CDRs_resultcodes) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466086202.183726.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_CDRs_resultcodes)

Example:

See also Incoming_call_resultCodes_explanation.md

## Incoming call gBE delayed dispatchs

The following dashboard can be used to monitor the performance of the dispatchs coming from gBE to gCOB in the incoming call in Argentina deployment.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466592172.629500.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_Call_delayed_dispatchs) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466592172.629500.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_Call_delayed_dispatchs)

{% include Embed_TEEN_AR_Incoming_Call_delayed_dispatchs.html %}
<iframe height="461" style="width: 100%; border: none" src="https://10.253.1.11/en-US/embed?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_Call_delayed_dispatchs&oid=Md1K9LqLckJKpW1Ds1dgSB5DJ4I8tFUC883deNhq5FQR2fCEZt5WA%5EnGDMbbWS0hSMeLRwCQbJHBvWNWckY6l9WGsUydY%5EPdZeobPcarjjryzgBg2tnOma0ShINo4TdaaJZKTvGXSEGrTmNAgpn5PhrldpNWT%5Enf2K%5EW4rv9"></iframe>

## Incoming call Voicemail diversion errors

The following dashboard can be used to monitor the performance of the voicemail diversions in Argentina deployment. In this dashboard the evolution of the percentage of errors is shown.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466595047.631627.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_VM_errors) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466595047.631627.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_VM_errors)

{% include Embed_TEEN_AR_Incoming_call_VM_errors.html %}
<iframe height="461" style="width: 100%; border: none" src="https://10.253.1.11/en-US/embed?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_VM_errors&oid=8BeF25MvJTVKfRjNxDIvfVgBgptYngxzFFBNOZKWgJ2SYAHiBgxHayUFOoGHb2J9CUk6kTfP9riWv8D8qVVndx7FFFal8STElzb4h8gvhwva6DBjHIA5DbyR5e5LNiqZ9qXdzFENg9IZ_kkltYJz_rnrk5gf9C"></iframe>

## Incoming call Domain Transfer failures

The following dashboard can be used to monitor the performance of the domain tranfer failures in Brazil deployment. This dashboard shows the global evolution of the percentage of errors in the last month.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466595319.631800.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_transfer_errors) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466595319.631800.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_transfer_errors)

{% include Embed_TEEN_AR_Incoming_call_Domain_transfer_errors.html %}
<iframe height="461" style="width: 100%; border: none" src="https://10.253.1.11/en-US/embed?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_transfer_errors&oid=LWXXjpggpWTzJmINg2vQg6ZAVULtqS_P3GCEiY21mWQ4ivM3EQhws5_T3b%5EK66sD3xixzHVYI6XUot3h8ylFRGrbhZW32Jpig_WTiuTyZqXRXy2arTPoToqsMkVv_ich5U8TmrZkAcJtGdmcaDCbrudQDc__UI83elpMLZ4TfPkpcAs7RUhpsKY"></iframe>

## Incoming call Domain Transfer Delay Percentile 80

The following dashboard can be used to monitor the performance of the domain tranfer delay percentile per area. This dashboard shows the percentile 80 of domain transfer delay for the last day per area.

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1466612233.643981.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_tranfer_delay) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1466612233.643981.mia-spl-sch01&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_tranfer_delay)

{% include Embed_TEEN_AR_Incoming_call_Domain_tranfer_delay.html %}
<iframe height="461" style="width: 100%; border: none" src="https://10.253.1.11/en-US/embed?s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_AR_Incoming_call_Domain_tranfer_delay&oid=qK7UL7DWKjMqwSH0fl2_Up9Y86cTm2kbejSmt%5EhpH97b7_wZw78uML77fy_nHPHtAOvga_wn7dx3AVxpOiH5q4fuZ6ddhS0F3XioDzm%5EMQ6G0VIVEtkqRvmco3sIXY9ROSSPq3V4ONvp1pciZlIg1Lod3B%5E1NC6UXjYQviOqfohBwc1tOWiO"></iframe>
