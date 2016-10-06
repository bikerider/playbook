Parameters to review:

* **ASR** should be, as general between 50% and 60%.
* **Ringing rate** should be > 90% - 95% (depending on the OB)
* **Outbound leg from TU Core** should be > 99%.

The dashboards show the following parameters per OB, in the graph:

* **ASR (Answer Seizure Ratio)**: Percentage of answered calls.
    * *Reference value*: 50 < value < 60 is 'normal behavior'.
* **Ring_rate**: Percentage of calls that get to '*ringing*' state.
    * *Reference value*: It depends on the OB (having 'fake ringing' or not), but the value should be *high* (>90-95%).
* **n_calls**: Total number of calls.
* **n_answer**: Total number of answered calls.     

The following parameters are defined in the tables:

* **1. Outgoing call to gBE**: Total number of outgoing calls reported to gBE.
* **2. Outbound leg from TU Core**: Outbound leg created from gBE. Ideally it should be **100%**.
* **3. Outbound leg ringing**: Percetage of legs that got to ringing status.
* **4. Outbound leg answered**: Percentage of calls that are answered.
* **4a. Outbound leg 486**: Percentage of calls that are replied as 'Busy' from the OB.
* **4b. Outbound leg 480**: Percentage of calls that are replied as 'Not reachable' from the OB.
* **4c. Outbound leg 404**: Percentage of calls that are replied as 'Not reachable' from the OB.
* **4d. Outbound leg other 4xx**: Percentage of calls that are replied as 'Not reachable' from the OB.
* **4e. Outbound leg 5xx**: Percentage of calls that are replied as 'Error' from the OB.
* **4f. Outbound leg 6xx**: Percentage of calls that are replied as 'Rejection' from the OB.
* **4g. Outbound leg cancel**: Percentage of calls that are abandoned by the calling party.
