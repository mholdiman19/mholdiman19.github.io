# WebAccess/DMP

_Description_: All notes or information on using WebAccess/DMP (WA/DMP).

## Login Information - API

* [WebAccess/DMP API](https://api.wadmp.com)

* Make sure you are logged into your account.

* Click on API Gallery.

* Select SWH API.

* Click on the Authorize button.

* ![Available Authorizations](img/wadmp_available_authorizations.png)

* In the **client_id** field, please enter _swagger_ui_.

* Please be sure to check the box for the following fields: AuthAPI, DeviceAPI, AppStoreAPI and NotificationsAPI.

* Lastly, please click the Authorize button.

## Day 2

* [IoT Academy](https://academy.advantech.com/dashboard)
* Discussion with Martin
    - NAT
    - Transparent Mode
    - Video Tips/Tools

### WADMP Usti Tech Session 2022

#### Gen 2

* [UI](https://wadmp.com/)
* [Documentation](https://docs.wadmp.com/)
* [API](https://api.wadmp.com/)
* [WADMP Status](https://status.wadmp.com/)

__Boris' Preso__

* Customers can add their own router app via API
* Fully automatic billing
* How to upgrade to Premium version?
    - Free => up to 5 devices; no alerts
    - Premium => no limitations
        - starts to get billed $2 a month per device including free 5
        - billed by claim devices
        - any feedback on pricing => 
        - click on crown to upgrade to premium
        - need to know their ERPID (Advantech Billing System - SAP)
    - Trial => do not communicate, trail with no limitations (per case; by request)
* Alerts
    - Endpoints (currently only supporting email, but will eventually do SMS and SNMP)
    - Parameters
    - Rule
        - Period => how often it will check for rule
        - Critical Repition => how many times in a row the rule mut be evaluated as True before the Alert is triggered
        - Cooldown => how long before checking the Alert again
        - Critical Device Count => Number of devices that would need to the match the rule at the same time for the Alert to trigger.

