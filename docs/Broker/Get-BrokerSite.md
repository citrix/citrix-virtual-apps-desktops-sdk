
# Get-Brokersite
Gets the current XenDesktop broker site.
## Syntax
```
Get-BrokerSite [-ReuseMachinesWithoutShutdownInOutageAllowed <Boolean>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerSite cmdlet gets the current broker site.

The broker site is a top-level, logical representation of the XenDesktop site, from the perspective of the brokering services running within the site. It defines various site-wide default attributes used by the brokering services.

A XenDesktop installation has only a single broker site instance.


### Brokersite Object
The BrokerSite object represents logical representation of the XenDesktop site. It contains the following properties:


  * BaseOU (System.Guid?) The objectGUID property identifying the base OU in Active Directory used for desktop registrations.

  * BrokerServiceGroupUid (System.Guid) The Uid for the Broker Service Group.

  * BypassAuthForCachedResources (System.Boolean) Allows client to display cached resources without authentication.

  * CloudSiteLicense (System.String) Configures the single cloud license chosen to be used as the default one for the site.

  * CloudValidLicenses (System.String) The valid cloud license SKUs.

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth) The default color depth for new desktop groups.

  * ConfigLastChangeTime (System.DateTime) The time the broker configuration was changed.

  * ConfigurationServiceGroupUid (System.Guid?) The Uid for the Configuration Service Group.

  * ConnectionLeasingEnabled (System.Boolean?) Always false. Connection leasing is no longer supported.

  * CredentialForwardingToCloudAllowed (System.Boolean) The indicator that whether the Connector is allowed to forward user credentials to cloud.

  * DefaultMinimumFunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?) The default minimum functional level used for new catalogs and desktop groups when no explicit value is provided.

  * DefaultReuseMachinesWithoutShutdownInOutage (System.Boolean) The default ReuseMachinesWithoutShutdownInOutage used for new desktop groups when no explicit value is provided.

  * DeleteResourceLeasesOnLogOff (System.Boolean) Forces client to delete all leases on explicit logoff.

  * DesktopGroupIconUid (System.Int32) The default desktop icon used for new desktop groups.

  * DnsResolutionEnabled (System.Boolean) The setting to configure whether numeric IP address or the DNS name to be present in the ICA file.

  * IsSecondaryBroker (System.Boolean) Reserved for internal use.

  * LicensedSessionsActive (System.Int32?) The count of active licensed session.

  * LicenseEdition (System.String) The license edition for session brokering.

  * LicenseGraceSessionsRemaining (System.Int32?) The count of Concurrent License Grace Sessions Remaining

  * LicenseModel (Citrix.Broker.Admin.SDK.LicenseModel?) The licensing model in use. Values can be 'Concurrent' or 'UserDevice'

  * LicenseServerName (System.String) The DNS for License Server Name

  * LicenseServerPort (System.Int32) The port for the License Server

  * LicensingBurnIn (System.String) The date for the license to end in yyyy.MMdd format

  * LicensingBurnInDate (System.DateTime?) The date for the license to end

  * LicensingGraceHoursLeft (System.Int32?) The number of grace hours left after license expiry

  * LicensingGracePeriodActive (System.Boolean?) The indicator for licensing grace period active

  * LicensingOutOfBoxGracePeriodActive (System.Boolean?) The indicator for licensing out of the box grace period active

  * LocalHostCacheEnabled (System.Boolean) The indicator that the Local Host Cache feature is switched on

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) The metadata for this command.

  * Name (System.String) The name of the site

  * PeakConcurrentLicensedDevices (System.Int32?) The peak number of concurrent devices

  * PeakConcurrentLicenseUsers (System.Int32?) The peak number of concurrent license users

  * RequireXmlServiceKeyForNFuse (System.Boolean) Determines if the NFuse, MCP, and Admin interfaces require authentication with a service key.

  * RequireXmlServiceKeyForSta (System.Boolean) Determines if the StA interface requires authentication with a service key.

  * ResourceLeaseValidityPeriodInDays (System.Int32) Validity period for a lease.

  * ResourceLeasingEnabled (System.Boolean) Enables lease syncing on client.

  * ReuseMachinesWithoutShutdownInOutageAllowed (System.Boolean) Specifies whether or not power cycle behavior during outage can be overriden on a delivery group level.

  * SecureIcaRequired (System.Boolean) The default SecureICA usage requirements for new desktop groups.

  * TelemetryHeadlessLaunchEnabled (System.Boolean) Enables client to perform headless telemetry launches.

  * TelemetryLaunchMinTimeIntervalMins (System.Int32) Configures minimum time interval (in minutes) between headless telemetry launches.

  * TelemetryLaunchShadowDelayMins (System.Int32) Configures delay (in minutes) between ICA-HDX launch and headless telemetry launch.

  * TotalUniqueLicenseUsers (System.Int32?) The total count of license users

  * TrustManagedAnonymousXmlServiceRequests (System.Boolean) The XML Service managed anonymous settings.

  * TrustRequestsSentToTheXmlServicePort (System.Boolean) The XML Service trust settings.

  * UseVerticalScalingForRdsLaunches (System.Boolean) Use vertical scaling when finding an RDS machine for a session launch.

  * XmlServiceKey1 (System.String) The first XML Service Key

  * XmlServiceKey2 (System.String) The second XML Service Key


## Related Commands

* [Set-BrokerSite](./Set-BrokerSite/)
* [Get-BrokerIcon](./Get-BrokerIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ReuseMachinesWithoutShutdownInOutageAllowed | Specifies whether or not power cycle behavior during outage can be overriden on a delivery group level. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Site
Get-BrokerSite returns the single broker site instance.
## Examples

### Example 1
```
C:\PS> Get-BrokerSite
```
#### Description
Gets the current broker site.
