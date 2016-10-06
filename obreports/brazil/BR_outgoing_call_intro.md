# TU App originated call flow, Brazil

## App Originated Call Evolution in Brazil

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=andresp__andresp__tugo__search3_1465487491.1181709.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_Outgoing_conversion_BRA) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=andresp__andresp__tugo__search3_1465487491.1181709.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_Outgoing_conversion_BRA)

{% include Embed_TEEN_Outgoing_conversion_BRA.html %}
{% markdown App_originated_call_conversion_explanation.md %}

## App Originated Call in Brazil

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/br__outgoing_call_by_area?earliest=-1d%40d&latest=%40d&form.code_digits=\d) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/br__outgoing_call_by_area?earliest=-1d%40d&latest=%40d&form.code_digits=\d)

It is important to note that in Brazil the areas are **very relevant** for network performance. Areas are the 2 digits after the *CountryCode*. Relevant areas are:

* **11**: Sao Paulo.
* **21**: Rio de Janeiro
* **31**: Minas Gerais

Historical areas with problems are "8X and 9X" ('remote' areas with bad satellite connections, big delays, etc.)

*Parameters to review:*

* **4. Outbound leg Answered** should be
    * Area 1X and 2X:  between 50% and 60%
    * Areas 3X, 4X, 5X, 6X, 7X: Higher than 45%
    * Areas 8X and 9X (remote areas): Around 40%
* **Ringing rate** should be > 90% (depending on the area)
* **4b Outbound leg 480** should be < 15-20% (users not reachable).
* **4a , 4c, 4d, 4e** should be < 3-5%
* **4g Outbound leg cancel** should be < 25-30% (for NWC it's higher because the client has smaller timeout: around 30-35%)

*Parameters of the dashboard:*

* The data for each value (categories explained before) is shown as percentage. The data for 'regular' apps and NWC are shown in different categories.
* The area code can be analyzed with 1 or 2 digits.
* The value between parenthesis '()' is the number of distinc users in the period. This has to be taken in to account because there are areas with small traffic (where percentages could be misleading).

## gCOB CDRs for App Originated calls in Brazil

[Link to dashboard based on IP](https://10.253.1.11/en-US/app/tugo/report?sid=1465567692.1238236.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Outgoing_call_CDRs) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1465567692.1238236.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Outgoing_call_CDRs)

{% include Embed_TEEN_BR_Outgoing_call_CDRs.html %}

{% markdown App_Orig_call_resultCodes_explanation.md %}


## gCOB CDRs for App Originated calls in Brazil PER AREA

[Link to dashboard based on IP](
https://10.253.1.11/en-US/app/tugo/report?sid=1465568521.1238823.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BRA_CDRs_Outgoing_Call_per_area) / [Link to dashboard based on URL](https://mia-splunk.tefcomms.com/en-US/app/tugo/report?sid=1465568521.1238823.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BRA_CDRs_Outgoing_Call_per_areaen-US/app/tugo/report?sid=1465567692.1238236.mia-spl-sch02&s=%2FservicesNS%2Fnobody%2Ftugo%2Fsaved%2Fsearches%2FTEEN_BR_Outgoing_call_CDRs)

{% include Embed_TEEN_BRA_CDRs_Outgoing_Call_per_area.html %}
As we've explained, there's a difference in Brazil for the different areas and the data has to be examined per Area basis.
