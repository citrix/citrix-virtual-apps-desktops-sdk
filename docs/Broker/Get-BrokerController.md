
# Get-Brokercontroller
Gets Controllers running broker services in the site.
## Syntax
```
Get-BrokerController [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerController [[-MachineName] <String>] [-ControllerVersion <String>] [-DesktopsRegistered <Int32>] [-DNSName <String>] [-LastActivityTime <DateTime>] [-LastLicensingServerEvent <LicensingServerEvent>] [-LastLicensingServerEventTime <DateTime>] [-LastStartTime <DateTime>] [-LicensingGraceState <LicensingGraceState>] [-LicensingServerState <LicensingServerState>] [-Metadata <String>] [-OSType <String>] [-OSVersion <String>] [-SID <String>] [-State <ControllerState>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets Controllers from the current site that match the specified search criteria.

Controllers are server machines running instances of the broker service. The broker service is responsible for the brokering of user sessions to desktops or applications, and for power management of the underlying machines. An operational site must contain at least one Controller.

If no search criteria are specified, all Controllers in the site are obtained.


### Brokercontroller Object
The BrokerController object represents a single controller running an instance of the Broker service. It contains the following properties:


  * ActiveSiteServices (System.String\[\]) The Broker site services active on the controller.

  * AssociatedHypervisorConnectionUids (System.Int32\[\]) The UIDs of the hypervisor connections being managed by the Broker service on the controller.

  * ControllerVersion (System.String) The version of the Broker service on the controller.

  * DesktopsRegistered (System.Int32) The number of VDA machines registered with the Broker service on the controller.

  * DNSName (System.String) The DNS name of the controller.

  * LastActivityTime (System.DateTime?) The last reported activity time of the Broker service on the controller.

  * LastLicensingServerEvent (Citrix.Broker.Admin.SDK.LicensingServerEvent?) Last significant licensing server event reported by the Broker service on the controller.

  * LastLicensingServerEventDetails (System.String\[\]) Additional details associated with the last significant licensing server event.

  * LastLicensingServerEventTime (System.DateTime?) Time at which the last significant licensing server event was reported.

  * LastStartTime (System.DateTime?) The last start-up time of the Broker service on the controller.

  * LicensingGracePeriodReasons (Citrix.Broker.Admin.SDK.LicensingGracePeriodReason\[\]) Current active or expired licensing grace periods in effect on the controller.

  * LicensingGracePeriodTimesRemaining (System.TimeSpan\[\]) Times remaining in currently active or expired licensing grace periods in effect on the controller. Expired grace periods are indicated by zero remaining time. The number and order of entries in this list matches that in the LicensingGracePeriodReasons list.

  * LicensingGraceState (Citrix.Broker.Admin.SDK.LicensingGraceState) The licensing grace state currently in effect in the Broker service on the controller.

  * LicensingServerState (Citrix.Broker.Admin.SDK.LicensingServerState) The licensing server state currently in effect in the Broker service on the controller.

  * MachineName (System.String) The Windows name of the controller.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) The metadata for the controller.

  * OSType (System.String) The Operating System type of the controller.

  * OSVersion (System.String) The Operating System version of the controller.

  * SID (System.String) The SID of the controller.

  * State (Citrix.Broker.Admin.SDK.ControllerState) The state of the Broker service on the controller.

  * Uid (System.Int32) The UID of the controller instance.

  * UUID (System.Guid) A globally unique identifier of the controller instance.


## Related Commands

* [Get-BrokerDesktop](./Get-BrokerDesktop/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only Controller with the specified unique ID. | true | false |  |
| MachineName | Gets only Controllers with the specified Windows name. ('domain\\machine') | false | false |  |
| ControllerVersion | Gets only Controllers running the specified version of the broker service. | false | false |  |
| DesktopsRegistered | Gets only Controllers that have the specified number of desktops currently registered. This parameter is mainly of use with advanced filtering; see about\_Broker\_Filtering. | false | false |  |
| DNSName | Gets only Controllers with the specified DNS name ('machine.domain') | false | false |  |
| LastActivityTime | Gets only Controllers last reported as active at the specified time. This parameter is mainly of use with advanced filtering; see about\_Broker\_Filtering. | false | false |  |
| LastLicensingServerEvent | Gets only Controllers with the specified last license server event recorded. | false | false |  |
| LastLicensingServerEventTime | Gets only Controllers with its last recorded licensing server event at the specified time. This parameter is mainly of use with advanced filtering; see about\_Broker\_Filtering. | false | false |  |
| LastStartTime | Gets only Controllers that last started-up at the specified time. This parameter is mainly of use with advanced filtering; see about\_Broker\_Filtering. | false | false |  |
| LicensingGraceState | Gets only Controllers in the specified licensing grace state.<br>Valid values are: NotActive, InOutOfBoxGracePeriod, InSupplementalGracePeriod, InEmergencyGracePeriod and GracePeriodExpired. | false | false |  |
| LicensingServerState | Gets only Controllers in the specified licensing server state. Valid values are: ServerNotSpecified, NotConnected, OK, LicenseNotInstalled, LicenseExpired, Incompatible and Failed. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| OSType | Gets only Controllers running the specified Operating System type. | false | false |  |
| OSVersion | Gets only Controllers running the specified Operating System version. | false | false |  |
| SID | Gets only Controllers with the specified SID. | false | false |  |
| State | Gets only Controllers currently in the specified state.<br>Valid values are: Failed, Off, On, and Active. | false | false |  |
| UUID | Gets only the Controller with the specified GUID. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Controller
Returns Controllers matching all specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerController -State Active
```
#### Description
Gets all Controllers in the site that are currently active (powered on and fully operational).
### Example 2
```
C:\PS> Get-BrokerController -Filter 'LastStartTime -gt "-30:00"'
```
#### Description
Gets all Controllers in the site that started-up in the last 30 minutes.
