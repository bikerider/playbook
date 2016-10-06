Meaning of the parameters shown in the dashboard:

* **%_users_succeeded** shows the percenage of the users that where successfully provisioned in the time period.
* **n_users_succeeded** is the number of different users successfully provisioned in the time period.

The following parameters are defined in the tables:

* **1. User from another OB, no OTAC**: The query made to the OB to check if the number belongs to the OB failed. The user is from other operation.
* **2. User did not try OTAC validation**: User passed over step 1, but did not even try to validate the PIN sent by OTAC.
* **3. User failed OTAC validation**: Users that failed to get OTAC validation.
* **4. User passed OTAC but failed activation**: 	User that passed OTAC validation, but the activation failed.
* **4b. User validated but failed activation (NWC)**: NWC calling for whom the activation process failed (they have GC2003 in the period and later GC1006).
* **4c. User failed activation (No validation)**: These are users that in the period don't have validation via OTAC. These are users that are reattempted automatically (they have GC1006 but dont have GC1003/GC2003).
* **5. User completed activation**: Percentage of Vanilla users that were successfully activated.
* **5b. User completed activation (NWC)**: Percentage of NWC users that were successfully activated.
* **6. User not eligible**: Percentage of Vanilla users that are not eligible in the OB for TU.
* **6b. User not eligible (NWC)**: Percentage of Vanilla users that are not eligible in the OB for TU.
* **7. User still Pending**: Vanilla users that are still in pending status.
* **7b. User still Pending (NWC)**: NWC users that are still in pending status.
* **------------ TOTAL USERS** : Total number of provisioning attempts in the time period.

Addittionaly to the percentages, the number of distinct users in each category is shown between *()*.

About the failure reasons, it is shown the number of cases of each reason and the amount of different users for each day.
