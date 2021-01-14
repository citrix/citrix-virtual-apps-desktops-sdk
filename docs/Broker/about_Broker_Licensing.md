
# about\_Broker\_Licensing

## Topic
Citrix Broker - Licensing


## Short Description
Overview of broker licensing configuration.


## Long Description
As part of the licensing setup for a site, the types of product licenses used by the broker when creating connections to virtual desktops or applications can be configured using the Central Configuration Service SDK.

The following licensing related properties can be specified using the Set-ConfigSite cmdlet:


* LicensingModel  - Sets the licensing model to use. Values can be 'Concurrent' or 'UserDevice'.
* ProductCode - Specifies which product license is supported by the site. Values can be ‘MPS’ for XenApp licenses or ‘XDT’ for XenDesktop licenses.
* ProductEdition - Sets the licensing edition to use.

A license matching the specified model, product code, and edition must be available within the site's license server in order for the broker to grant licenses.

These properties are part of the site object returned by the Get-ConfigSite cmdlet.


## Concurrent License Model
A concurrent license is tied to a XenDesktop session. When a user launches a session, a license is checked out to that session. When a user logs off from a session, the license is checked back in again, making it available for another session.


## User Device License Model
With user device licensing, the license server automatically assigns licenses to users or devices based on usage:


* User licensing allows users to access their desktops and applications from multiple devices.
* Device licensing allows multiple users to access their desktops and applications from a single device.

When users or devices connect to an application or desktop, they consume a license for a 90-day license assignment period. The assignment period begins when a connection is made, is renewed to the full 90 days during the life of the connection, and expires (allowing reassignment) 90 days after the last connection terminates. A license assignment can be manually ended before the 90-day period elapses using the udadmin command line installed on the license server.


## Licensing State
The broker site contains the following properties related to licensing state:


* LicensingGracePeriodActive - Reports if the broker is in licensing grace period.
* LicensingOutOfBoxGracePeriodActive - Reports if the broker is in out-of-box grace period.
* LicensingGraceHoursLeft - The number of grace hours remaining, if the broker is in grace period, else it is null.
* LicensedSessionsActive - The number of active, licensed sessions.
* LicenseGraceSessionsRemaining - The number of concurrent grace sessions available for the site Product Code, if the broker is in licensing grace period, else it is null.

These properties are part of the site object returned by the Get-BrokerSite cmdlet.


## License Server Test
The broker SDK cmdlet Test-BrokerLicenseServer checks whether or not a given server can be used as a license server by the broker.


## Resetting License Server Connection
The broker SDK cmdlet Reset-BrokerLicensingConnection resets the broker's connection to the license server.


## License Burn-In Date
The version of the product that is supported within the site is denoted by a licensing burn-in date. This date can be accessed through the LicensingBurnInDate field of the site object returned by the Get-ConfigSite cmdlet.


## See Also

* [about\_Broker\_Site](./about_Broker_Site/)
* [Test-BrokerLicenseServer](./Test-BrokerLicenseServer/)
* [Reset-BrokerLicensingConnection](./Reset-BrokerLicensingConnection/)
* [Get-BrokerController](./Get-BrokerController/)
* [Set-ConfigSite](./Set-ConfigSite/)
* [Get-ConfigSite](./Get-ConfigSite/)
* [Get-BrokerSite](./Get-BrokerSite/)

