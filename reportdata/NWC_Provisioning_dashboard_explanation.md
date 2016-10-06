Meaning of the panels shown in the dashboard:

* **API requests from AAA** shows the APIs consumed by AAA component from gCOB (for EAP-AKA and IMS-AKA) and from gBE(EAP-AKA).
* **API requests from AAA (by IMSI)** shows the information of AAA APIs but summarized by IMSI.
* **Log types** are the most common logs shown by AAA servers.
* **AAA activity vs Prov in gBE** crosses the information of the AAA server with the provision events logged by gBE. It has the following categories:
   * **A. NWC register in gBE became ACTIVE**: NWC regitration attempt that got active in gBE shown per delay in getting to active status.
   * **B. no NWC register in gBE (no GC2003) but became ACTIVE** users that became active but don't have GC2003 in the time period.
   * **C. always failing (no GC1005, some GC1006)** users whose provisioning process is always failing.
   * **D. NWC register but no GC1005 or GC1006** users that don't have an activation but are able to register (already provisioned).
   * **E. no NWC register but AAA activity** 
* **gOB Auth** shows some data about gCOB authorization API:
   * **distinct_imsi** the number of distinc IMSIs accessing the API.
   * **n_requests** is the number of requests in the API.
   * **avg_req_imsi** is the average of requests per IMSI.
* **gCOB Auth TPS by code** is a graph showing the evolution of the response codes in the API sent from gCOB.
* **IMSI to MSISDN** some statistics of the IMSI to MSISDN mapping made in gCOB.
