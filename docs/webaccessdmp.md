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
* Audit Logs
    - keep data for the last 2 months (longest period)
    - export to CSV
* Private Cloud Solution
    - was developed and delivered to a customer

* Delivery Options
    - Public Cloud
    - Hybrid
        - monthly fee 3600 a month (no limits)
        - do not have to pay for infrastructure
    - Private Cloud
        - 50K just to install it
        - flexible on the above price
        - 3600 per quarter for maintenance
        - first 6 months no charge
        - if they choose not to pay maintenance fee, then they would have to pay the 50K over again
* New website => wadmp.advantech.cz
* If they go with the Hybrid version, then they could keep their info in the US or whereever they are
* Roadmap
    - a comprehensive solution for industrial cellular applications
    - WADMP 2.4.3 => H1 2022 => SWH EoL
    - WADMP 2.5 =>  Q3 2022 => Migration from Service, Fabric to KBS, Additional GUI Improvements, AWS Enablement
    - WADMP 2.6 => Q4 2022 => New Sync Engine
    - WADMP 3.0 => 1H 2023 => New WEB, Flexible Dashboard, R-SeeNet Replacement, On-Premises Product, VPN Management
    - WADMP 3.0 => 2023 => New Products Onboarding, ECU-1000, WA/SIM Integration

