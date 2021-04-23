
# Group-Brokerdesktop
Groups and counts desktops with the same value for a specified property.
## Syntax
```
Group-BrokerDesktop [-Uid] <Int32> -Property <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Group-BrokerDesktop -Property <String> [[-MachineName] <String>] [-AgentVersion <String>] [-ApplicationInUse <String>] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserUPN <String>] [-AutonomouslyBrokered <Boolean>] [-CatalogName <String>] [-CatalogUid <Int32>] [-ClientAddress <String>] [-ClientName <String>] [-ClientVersion <String>] [-ColorDepth <ColorDepth>] [-ConnectedViaHostName <String>] [-ConnectedViaIP <String>] [-ControllerDNSName <String>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopCondition <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopKind <DesktopKind>] [-DeviceId <String>] [-DNSName <String>] [-FunctionalLevel <FunctionalLevel>] [-HardwareId <String>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-IconUid <Int32>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAssigned <Boolean>] [-IsPhysical <Boolean>] [-LastConnectionFailure <ConnectionFailureReason>] [-LastConnectionTime <DateTime>] [-LastConnectionUser <String>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastErrorReason <String>] [-LastErrorTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-LaunchedViaHostName <String>] [-LaunchedViaIP <String>] [-MachineInternalState <MachineInternalState>] [-MachineUid <Int32>] [-OSType <String>] [-OSVersion <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerActionPending <Boolean>] [-PowerState <PowerState>] [-Protocol <String>] [-ProvisioningType <ProvisioningType>] [-PublishedApplication <String>] [-PublishedName <String>] [-PvdStage <PvdStage>] [-RegistrationState <RegistrationState>] [-SecureIcaActive <Boolean>] [-SecureIcaRequired <Boolean>] [-SessionHidden <Boolean>] [-SessionId <Int32>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionUid <Int64>] [-SessionUserName <String>] [-SessionUserSID <String>] [-SID <String>] [-SmartAccessTag <String>] [-StartTime <DateTime>] [-SummaryState <DesktopSummaryState>] [-Tag <String>] [-WillShutdownAfterUse <Boolean>] [-ApplicationUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is now deprecated, please use Group-BrokerMachine.

Filters desktops using the specified criteria, then groups and counts matching desktops with the same value for a particular property. The number of desktops in the group, and the property value for the group, is output. For example:


```
C:\PS> Group-BrokerDesktop -Property SummaryState  

```
Count Name ----- ---- 43 Available 17 InUse 3 Disconnected

Filtering supports the same options as the Get-BrokerDesktop cmdlet, and allows filtering on both desktop and session properties.

Group-BrokerDesktop is similar to the standard PowerShell Group-Object, but is faster than piping the output of Get-BrokerDesktop into Group-Object when working with many desktops.

Note that all session information properties for multi-session desktops is always \$null, this means that is is not possible to group these desktops by session information using this command. Use Get-BrokerSession to get information on all current sessions.

Also note that the MaxRecordCount, ReturnTotalRecordCount, Skip, and SortBy parameters apply to GroupInfo records output rather than the filtered desktops.


## Related Commands

* [Get-BrokerDesktop](./Get-BrokerDesktop/)
* [Group-Object](./Group-Object/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets desktops with a specific UID. | true | false |  |
| Property | Selects the property by which matching desktops are grouped. | true | false |  |
| MachineName | Gets desktops with a specific machine name (in the form 'domain\\machine'). | false | false |  |
| AgentVersion | Gets desktops with a specific Citrix Virtual Delivery Agent version. | false | false |  |
| ApplicationInUse | Gets desktops running a specified published application (identified by browser name).<br>String comparisons are case-insensitive. | false | false |  |
| AssignedClientName | Gets desktops assigned to a specific client name. | false | false |  |
| AssignedIPAddress | Gets desktops assigned to a specific IP address.q | false | false |  |
| AssociatedUserFullName | Gets desktops with an associated user identified by their full name (usually in the form 'first-name last-name').<br>Associated users are the current user for shared desktops, and the assigned users for private desktops. | false | false |  |
| AssociatedUserName | Gets desktops with an associated user identified by their user name (in the form 'domain\\user').<br>Associated users are the current user for shared desktops, and the assigned users for private desktops. | false | false |  |
| AssociatedUserUPN | Gets desktops with an associated user identified by their User Principle Name (in the form 'user@domain').<br>Associated users are the current user for shared desktops, and the assigned users for private desktops. | false | false |  |
| AutonomouslyBrokered | Gets desktops according to whether their current session is autonomously brokered or not. Autonomously brokered sessions are HDX sessions established by direct connection without being brokered.<br>Session properties are always null for multi-session desktops. | false | false |  |
| CatalogName | Gets desktops from the catalog with the specific name. | false | false |  |
| CatalogUid | Gets desktops from a catalog with a specific UID. | false | false |  |
| ClientAddress | Gets desktops with a specific client IP address. | false | false |  |
| ClientName | Gets desktops with a specific client name. | false | false |  |
| ClientVersion | Gets desktops with a specific client version. | false | false |  |
| ColorDepth | Gets desktops configured with a specific color depth.<br>Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| ConnectedViaHostName | Gets desktops with a specific host name of the incoming connection. This is usually a proxy or Citrix Access Gateway server. | false | false |  |
| ConnectedViaIP | Gets desktops with a specific IP address of the incoming connection. | false | false |  |
| ControllerDNSName | Gets desktops with a specific DNS name of the controller they are registered with. | false | false |  |
| DeliveryType | Gets desktops of a particular delivery type.<br>Valid values are AppsOnly, DesktopsOnly, DesktopsAndApps | false | false |  |
| Description | Get desktops with a specific description. | false | false |  |
| DesktopCondition | Gets desktop with an outstanding desktop condition condition.<br>Valid values are:<br>o CPU: Indicates the machine has high CPU usage<br>o ICALatency: Indicates the network latency is high<br>o UPMLogonTime: Indicates that the profile load time was high | false | false |  |
| DesktopGroupName | Gets desktops from a desktop group with the specified name. | false | false |  |
| DesktopGroupUid | Gets desktops from a desktop group with the specified UID. | false | false |  |
| DesktopKind | Deprecated: Use AllocationType parameter.<br>Gets desktops of a particular kind.<br>Valid values are Private, Shared. | false | false |  |
| DeviceId | Gets desktops with a specific client device ID. | false | false |  |
| DNSName | Get desktops with a specific DNS name. | false | false |  |
| FunctionalLevel | Gets desktops with a specific FunctionalLevel.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| HardwareId | Gets desktops with a specific client hardware ID. | false | false |  |
| HostedMachineId | Gets desktops with a specific machine ID known to the hypervisor. | false | false |  |
| HostedMachineName | Gets desktops with a specific machine name known to the hypervisor. | false | false |  |
| HostingServerName | Gets desktops with a specific name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionName | Gets desktops with a specific name of the hosting hypervisor connection. | false | false |  |
| HypervisorConnectionUid | Gets desktops with a specific UID of the hosting hypervisor connection. | false | false |  |
| IconUid | Gets desktops with a specific configured icon. Note that desktops with a null IconUid use the icon of the desktop group. | false | false |  |
| ImageOutOfDate | Gets desktops if they have an ImageOutOfDate flag. | false | false |  |
| InMaintenanceMode | Gets desktops with a specific InMaintenanceMode setting. | false | false |  |
| IPAddress | Gets desktops with a specific IP address. | false | false |  |
| IsAssigned | Gets desktops according to whether they are assigned or not. Desktops may be assigned to one or more users or groups, a client IP address or a client endpoint name. | false | false |  |
| IsPhysical | Specifies if machines in the catalog can be power managed by the Citrix Broker Service. Where the power state of the machine cannot be controlled, specify \$true, otherwise \$false. Can only be specified together with a provisioning type of Pvs or Manual, or if used with the deprecated CatalogKind parameter only with Pvs or PvsPvd catalog kinds. | false | false |  |
| LastConnectionFailure | Gets desktops with a specific reason for the last recorded connection failure. This value is None if the last connection was successful or if there has been no attempt to connect to the desktop yet.<br>Valid values are None, SessionPreparation, RegistrationTimeout, ConnectionTimeout, Licensing, Ticketing, and Other. | false | false |  |
| LastConnectionTime | Gets desktops that last connected at a specific time. This is the time that the broker detected that the connection attempt either succeeded or failed. | false | false |  |
| LastConnectionUser | Gets desktops where a specific user name last attempted a connection (in the form 'domain\\user'). | false | false |  |
| LastDeregistrationReason | Gets desktops whose broker last recorded a specific deregistration reason.<br>Valid values are \$null, AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached. | false | false |  |
| LastDeregistrationTime | Gets desktops that were last deregistered by a specific time. | false | false |  |
| LastErrorReason | Gets desktops with the specified last error reason. | false | false |  |
| LastErrorTime | Gets desktops with the specified last error time. | false | false |  |
| LastHostingUpdateTime | Gets desktops with a specific time that the hosting information was last updated. | false | false |  |
| LaunchedViaHostName | Gets desktops with a specific host name of the StoreFront server from which the user launched the session.<br>Session properties are always null for multi-session desktops. | false | false |  |
| LaunchedViaIP | Gets desktops with a specific IP address of the StoreFront server from which the user launched the session.<br>Session properties are always null for multi-session desktops. | false | false |  |
| MachineInternalState | Gets desktops with the specified internal machine state. | false | false |  |
| MachineUid | Gets desktops with a specific machine UID. | false | false |  |
| OSType | Gets desktops by the type of operating system they are running. | false | false |  |
| OSVersion | Gets desktops by the version of the operating system they are running. | false | false |  |
| PersistUserChanges | Gets desktops by the location where the user changes are persisted.<br>o OnLocal - User changes are persisted locally.<br>o Discard - User changes are discarded.<br>o OnPvd - User changes are persisted on the Pvd. | false | false |  |
| PowerActionPending | Gets desktops with a specific power action pending state.<br>Valid values are \$true or \$false. | false | false |  |
| PowerState | Gets desktops with a specific power state.<br>Valid values are Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| Protocol | Gets desktops with connections using a specific protocol, for example HDX, RDP, or Console. | false | false |  |
| ProvisioningType | Specifies the provisioning type for the catalog. Values can be:<br>o Manual - No provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| PublishedApplication | Gets desktops with a specific application published on them (identified by its browser name). | false | false |  |
| PublishedName | Gets desktops with a specific published name. | false | false |  |
| PvdStage | Gets machines with a specific personal vDisk stage.<br>Valid values are None, Requested, Starting, Working and Failed. | false | false |  |
| RegistrationState | Gets desktops with a specific registration state.<br>Valid values are Unregistered, Initializing, Registered and AgentError. | false | false |  |
| SecureIcaActive | Gets desktops depending on whether the current session uses SecureICA or not.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SecureIcaRequired | Gets desktops configured with a particular SecureIcaRequired setting. Note that the desktop setting of \$null indicates that the desktop group value is used.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionHidden | Gets desktops by whether their sessions are hidden or not. Hidden sessions are treated as though they do not exist when launching sessions; a hidden session cannot be reconnected to, but a new session may be launched using the same entitlement.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionId | Deprecated.<br>Gets desktops by session ID, a unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine. | false | false |  |
| SessionState | Gets desktops with a specific session state.<br>Valid values are \$null, Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionStateChangeTime | Gets desktops whose sessions last changed state at a specific time.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUid | Gets desktops with a specific session UID (\$null for no session).<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUserName | Gets desktops with a specific user name for the current session (in the form 'domain\\user').<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUserSID | Gets desktops with a specific SID of the current session user.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SID | Gets desktops with a specific machine SID. | false | false |  |
| SmartAccessTag | Gets desktops where the session has the specific SmartAccess tag.<br>Session properties are always null for multi-session desktops. | false | false |  |
| StartTime | Gets desktops with a specific session start time.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SummaryState | Gets desktops with a specific summary state.<br>Valid values are Off, Unregistered, Available, Disconnected, and InUse. | false | false |  |
| Tag | Gets desktops with a specific tag. | false | false |  |
| WillShutdownAfterUse | Gets desktops depending on whether they shut down after use or not. | false | false |  |
| ApplicationUid | Gets desktops with a specific published application (identified by its UID). | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Groupinfo
Each GroupInfo object represents one group, and contains the following properties:<br>-- Count: The count of desktops in this group.<br>-- Name: The value of the property the desktops were grouped by (as a string).<br>If you do not specify -SortBy, groups are sorted with the largest count first.
## Notes
To compare dates or times, use -Filter and relative comparisons. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Group-BrokerDesktop -Property SummaryState -DesktopGroupName dg1
```
#### Description
Group desktops from the dg1 group by summary state.
### Example 2
```
C:\PS> Group-BrokerDesktop -Property LastConnectionFailure -Filter { LastConnectionFailure -ne "None" -and LastConnectionTime -ge '-7' } -MaxRecordCount 1
```
#### Description
For desktops where the last connection attempt failed, list the most common reason for failure, ignoring connections that failed over a week ago.
### Example 3
```
C:\PS> Group-BrokerDesktop -Property HostingServerName -DesktopCondition ICALatency -SortBy Name
```
#### Description
List alphabetically the hypervisor servers hosting desktops that are currently experiencing high network latency.
