
# Get-Brokershareddesktop
Get shared desktops configured for this site.
## Syntax
```
Get-BrokerSharedDesktop [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerSharedDesktop [[-MachineName] <String>] [-AgentVersion <String>] [-ControllerDNSName <String>] [-DesktopGroupUid <Int32>] [-DNSName <String>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-OSType <String>] [-OSVersion <String>] [-PowerState <PowerState>] [-RegistrationState <RegistrationState>] [-SID <String>] [-Tag <String>] [-WillShutdownAfterUse <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is deprecated, please use the Get-BrokerMachine cmdlet instead.

Retrieve shared desktops matching the specified criteria. If no parameters are specified, all shared desktops are enumerated.

Get-BrokerSharedDesktop returns configuration information only for shared desktops (a DesktopKind of 'Shared').

For information about advanced filtering options, see about\_Broker\_Filtering; for information about desktops, see about\_Broker\_Desktops.


### Brokershareddesktop Object
Shared desktops are desktops that are assigned randomly to users upon connection from a pool of available machines.


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the desktop.

  * ControllerDNSName (System.String) The DNS host name of the controller that the desktop is registered to.

  * DesktopGroupUid (System.Int32) Uid of the desktop group the desktop has been assigned to.

  * DNSName (System.String) The DNS host name of the desktop.

  * HostedMachineId (System.String) Unique ID within the hosting unit of the target managed desktop.

  * HostedMachineName (System.String) The friendly name of a hosted desktop as used by its hypervisor. This is not necessarily the DNS name of the desktop.

  * HostingServerName (System.String) DNS name of the hypervisor that is hosting the desktop if managed.

  * HypervisorConnectionUid (System.Int32?) The UID of the hypervisor connection that the desktop has been assigned to, if managed.

  * InMaintenanceMode (System.Boolean) Denotes whether the desktop is in maintentance mode.

  * IPAddress (System.String) The IP address of the desktop.

  * LastDeregistrationReason (Citrix.Broker.Admin.SDK.DeregistrationReason?) The reason for the last deregistration of the desktop with the broker. Possible values are: AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached.

  * LastDeregistrationTime (System.DateTime?) Time of the last deregistration of the desktop from the controller.

  * LastHostingUpdateTime (System.DateTime?) Time of last update to any hosting data for this desktop reported by the hypervisor connection.

  * MachineName (System.String) DNS host name of the machine associated with the desktop.

  * OSType (System.String) A string that can be used to identify the operating system that is running on the desktop.

  * OSVersion (System.String) A string that can be used to identify the version of the operating system running on the desktop, if known.

  * PowerState (Citrix.Broker.Admin.SDK.PowerState) The current power state of the desktop. Possible values are: Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, resuming.

  * RegistrationState (Citrix.Broker.Admin.SDK.RegistrationState) Indicates the registration state of the desktop. Possible values are: Unregistered, Initializing, Registered, AgentError.

  * SID (System.String) The security identifier of the shared desktop.

  * Uid (System.Int32) The uid of the shared desktop.

  * WillShutdownAfterUse (System.Boolean) Flag indicating whether this desktop is tainted and will be shutdown after all sessions on the desktop have ended. This flag should only ever be true on power managed, single-session desktops. Note: The desktop will not shut down if it is in maintenance mode, but will shut down after the desktop is taken out of maintenance mode.


## Related Commands

* [Set-BrokerSharedDesktop](./Set-BrokerSharedDesktop/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets desktops by Uid. | true | false |  |
| MachineName | Gets desktops by machine name (in the form 'domain\\machine'). | false | false |  |
| AgentVersion | Gets desktops with a specific Virtual Desktop Agent version. | false | false |  |
| ControllerDNSName | Gets desktops by the DNS name of the controller they are registered with. | false | false |  |
| DesktopGroupUid | Gets desktops from a desktop group with a specific Uid. | false | false |  |
| DNSName | Gets desktops by DNS name. | false | false |  |
| HostedMachineId | Gets desktops by the machine id known to the hypervisor. | false | false |  |
| HostedMachineName | Gets desktops by the machine name known to the hypervisor. | false | false |  |
| HostingServerName | Gets desktops by the name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionUid | Gets desktops by the uid of the hosting hypervisor connection. | false | false |  |
| InMaintenanceMode | Gets desktops by the InMaintenanceMode setting. | false | false |  |
| IPAddress | Gets desktops by IP address. | false | false |  |
| LastDeregistrationReason | Gets desktops whose broker last recorded a specific deregistration reason.<br>Valid values are \$null, AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached. | false | false |  |
| LastDeregistrationTime | Gets desktops by the time that they were last deregistered. | false | false |  |
| LastHostingUpdateTime | Gets desktops by the time that the hosting information was last updated. | false | false |  |
| OSType | Gets desktops by the type of operating system they are running. | false | false |  |
| OSVersion | Gets desktops by the version of the operating system they are running. | false | false |  |
| PowerState | Gets desktops by power state.<br>Valid values are Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| RegistrationState | Gets desktops by registration state.<br>Valid values are Registered, Unregistered, and AgentError. | false | false |  |
| SID | Gets desktops by machine SID. | false | false |  |
| Tag | Get desktops tagged with the given tag. | false | false |  |
| WillShutdownAfterUse | Gets desktops depending on whether they shutdown after use or not. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Shareddesktop
Get-BrokerSharedDesktop returns an object for each matching shared desktop.
## Notes
To compare dates/times, use -Filter and relative comparisons. For more information, see about\_Broker\_Filtering.
## Examples

### Example 1
```
C:\PS> Get-BrokerSharedDesktop -HostingServerName BigServer12\*
```
#### Description
Get all shared desktops hosted by the hypervisor server BigServer12.
### Example 2
```
C:\PS> Get-BrokerSharedDesktop -OSType 'Windows XP\*' | ft -a MachineName,OSType,OSVersion
```
#### Description
List all shared desktops running Windows XP, including the machine name and OS details.
