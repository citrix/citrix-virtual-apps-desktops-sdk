
# Get-Brokerprivatedesktop
Get private desktops configured for this site.
## Syntax
```
Get-BrokerPrivateDesktop [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerPrivateDesktop [[-MachineName] <String>] [-AgentVersion <String>] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-ColorDepth <ColorDepth>] [-ControllerDNSName <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-DNSName <String>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionUid <Int32>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAssigned <Boolean>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-OSType <String>] [-OSVersion <String>] [-PowerState <PowerState>] [-PublishedName <String>] [-RegistrationState <RegistrationState>] [-SecureIcaRequired <Boolean>] [-SID <String>] [-Tag <String>] [-WillShutdownAfterUse <Boolean>] [-AssignedUserSID <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is deprecated, please use the Get-BrokerMachine cmdlet instead.

Retrieve private desktops matching the specified criteria. If no parameters are specified, this cmdlet enumerates all private desktops.

Get-BrokerPrivateDesktop returns configuration information only for private desktops (a DesktopKind of 'Private'). For more state information about desktops, or other types of desktop, use the Get-BrokerMachine cmdlet instead.

For information about advanced filtering options, see about\_Broker\_Filtering; for more information about desktops, see about\_Broker\_Desktops.


### Brokerprivatedesktop Object
Private desktops are machines that have been configured with a DesktopKind of 'Private'. They are allocated to either a user/users or a client name/address (but cannot be allocated to both).


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the desktop.

  * AssignedClientName (System.String) Client name the desktop has been assigned to.

  * AssignedIPAddress (System.String) IP Address the desktop has been assigned to.

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?) The color depth setting configured on the desktop, possible values are: \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.

  * ControllerDNSName (System.String) The DNS host name of the controller that the desktop is registered to.

  * Description (System.String) Description of the private desktop.

  * DesktopGroupUid (System.Int32) Uid of the desktop group the desktop has been assigned to.

  * DNSName (System.String) The DNS host name of the desktop.

  * HostedMachineId (System.String) Unique ID within the hosting unit of the target managed desktop.

  * HostedMachineName (System.String) The friendly name of a hosted desktop as used by its hypervisor. This is not necessarily the DNS name of the desktop.

  * HostingServerName (System.String) DNS name of the hypervisor that is hosting the desktop if managed.

  * HypervisorConnectionUid (System.Int32?) The UID of the hypervisor connection that the desktop has been assigned to, if managed.

  * IconUid (System.Int32?) The UID of the desktop's icon that is displayed in StoreFront. If this is \$null then the desktop will use the icon specified by the desktop group.

  * InMaintenanceMode (System.Boolean) Denotes whether the desktop is in maintentance mode.

  * IPAddress (System.String) The IP address of the desktop.

  * IsAssigned (System.Boolean) Denotes whether a private desktop has been assigned to a user/users, or a client name/address. Users can be assigned explictitly or by assigning on first use of the desktop.

  * LastDeregistrationReason (Citrix.Broker.Admin.SDK.DeregistrationReason?) The reason for the last deregistration of the desktop with the broker. Possible values are: AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached.

  * LastDeregistrationTime (System.DateTime?) Time of the last deregistration of the desktop from the controller.

  * LastHostingUpdateTime (System.DateTime?) Time of last update to any hosting data for this desktop reported by the hypervisor connection.

  * MachineName (System.String) DNS host name of the machine associated with the desktop.

  * OSType (System.String) A string that can be used to identify the operating system that is running on the desktop.

  * OSVersion (System.String) A string that can be used to identify the version of the operating system running on the desktop, if known.

  * PowerState (Citrix.Broker.Admin.SDK.PowerState) The current power state of the desktop. Possible values are: Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, Resuming.

  * PublishedName (System.String) The name of the desktop that is displayed in StoreFront, if the desktop is published.

  * RegistrationState (Citrix.Broker.Admin.SDK.RegistrationState) Indicates the registration state of the desktop. Possible values are: Unregistered, Initializing, Registered, AgentError.

  * SecureIcaRequired (System.Boolean?) Flag indicating whether SecureICA is required or not when starting a session on the desktop.

  * SID (System.String) Security identifier of the private desktop.

  * Uid (System.Int32) Unique identifier of the private desktop.

  * WillShutdownAfterUse (System.Boolean) Flag indicating whether this desktop is tainted and will be shutdown after all sessions on the desktop have ended. This flag should only ever be true on power managed, single-session desktops. Note: The desktop will not shut down if it is in maintenance mode, but will shut down after the desktop is taken out of maintenance mode.


## Related Commands

* [Set-BrokerPrivateDesktop](./Set-BrokerPrivateDesktop/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets desktops by Uid. | true | false |  |
| MachineName | Gets desktops by machine name (in the form 'domain\\machine'). | false | false |  |
| AgentVersion | Gets desktops with a specific Citrix Virtual Delivery Agent (VDA) version. | false | false |  |
| AssignedClientName | Gets desktops assigned to a specific client name. | false | false |  |
| AssignedIPAddress | Gets desktops assigned to a specific IP address. | false | false |  |
| ColorDepth | Gets desktops configured with a specific color depth.<br>Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| ControllerDNSName | Gets desktops by the DNS name of the controller they are registered with. | false | false |  |
| Description | Gets desktops by description. | false | false |  |
| DesktopGroupUid | Gets desktops from a desktop group with a specific Uid. | false | false |  |
| DNSName | Gets desktops by DNS name. | false | false |  |
| HostedMachineId | Gets desktops by the machine id known to the hypervisor. | false | false |  |
| HostedMachineName | Gets desktops by the machine name known to the hypervisor. | false | false |  |
| HostingServerName | Gets desktops by the name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionUid | Gets desktops by the uid of the hosting hypervisor connection. | false | false |  |
| IconUid | Gets desktops by configured icon. Note that desktops with a \$null IconUid use the icon of the desktop group. | false | false |  |
| InMaintenanceMode | Gets desktops by the InMaintenanceMode setting. | false | false |  |
| IPAddress | Get desktops by their IP address. | false | false |  |
| IsAssigned | Gets desktops depending on whether they are assigned or not. Private desktops can be assigned to either a user/users or client names/addresses. | false | false |  |
| LastDeregistrationReason | Gets desktops whose broker last recorded a specific deregistration reason.<br>Valid values are \$null, AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached. | false | false |  |
| LastDeregistrationTime | Gets desktops by the time that they were last deregistered. | false | false |  |
| LastHostingUpdateTime | Gets desktops by the time that the hosting information was last updated. | false | false |  |
| OSType | Gets desktops by the type of operating system they are running. | false | false |  |
| OSVersion | Gets desktops by the version of the operating system they are running. | false | false |  |
| PowerState | Gets desktops by power state.<br>Valid values are Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| PublishedName | Gets desktops by published name. | false | false |  |
| RegistrationState | Gets desktops by registration state.<br>Valid values are Registered, Unregistered, and AgentError. | false | false |  |
| SecureIcaRequired | Gets desktops configured with a particular SecureIcaRequired setting. Note that the desktop setting of \$null indicates that the desktop group value is used. | false | false |  |
| SID | Gets desktops by machine SID. | false | false |  |
| Tag | Gets desktops tagged with the given tag. | false | false |  |
| WillShutdownAfterUse | Gets desktops depending on whether they will be automatically shut down when the current session ends or not. | false | false |  |
| AssignedUserSID | Gets desktops with the given assigned user (specified by SID). | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Privatedesktop
Get-BrokerPrivateDesktop returns an object for each matching private desktop.
## Notes
To compare dates/times, use -Filter and relative comparisons. See about\_Broker\_Filtering for details.
## Examples

### Example 1
```
C:\PS> $list = 'Unmanaged','On','TurningOn','Resuming'

C:\PS> Get-BrokerPrivateDesktop -Filter { PowerState -in $list } | ft -a DNSName,PowerState
```
#### Description
Get all private desktops that are turned on, or are turning on (assuming unmanaged desktops are powered on).
### Example 2
```
C:\PS> Get-BrokerPrivateDesktop -Tag TestTag
```
#### Description
Retrieve all private desktops tagged with the 'TestTag' tag.
