
# Group-Brokermachine
Groups and counts machines with the same value for a specified property.
## Syntax
```
Group-BrokerMachine [-Uid] <Int32> -Property <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Group-BrokerMachine -Property <String> [[-MachineName] <String>] [-AgentVersion <String>] [-AllocationType <AllocationType>] [-ApplicationInUse <String>] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-AssignedUserSID <String>] [-AssociatedTenantId <Guid>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserSID <String>] [-AssociatedUserUPN <String>] [-BrowserName <String>] [-CatalogName <String>] [-CatalogUid <Int32>] [-CatalogUUID <Guid>] [-CbpVersion <CBPVersion>] [-ColorDepth <ColorDepth>] [-ControllerDNSName <String>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopCondition <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopGroupUUID <Guid>] [-DesktopKind <DesktopKind>] [-DesktopUid <Int32>] [-DNSName <String>] [-DrainingUntilShutdown <Boolean>] [-FaultState <MachineFaultState>] [-FunctionalLevel <FunctionalLevel>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-HypHypervisorConnectionUid <Guid>] [-IconUid <Int32>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAssigned <Boolean>] [-IsPhysical <Boolean>] [-IsReserved <Boolean>] [-LastConnectionFailure <ConnectionFailureReason>] [-LastConnectionTime <DateTime>] [-LastConnectionUser <String>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastErrorReason <String>] [-LastErrorTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-LastPvdErrorReason <String>] [-LastPvdErrorTime <DateTime>] [-LastRegistrationTime <DateTime>] [-LoadIndex <Int32>] [-MacAddress <String>] [-MachineInternalState <MachineInternalState>] [-MaintenanceModeReason <MaintenanceModeReason>] [-Metadata <String>] [-OSType <String>] [-OSVersion <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerActionPending <Boolean>] [-PowerState <PowerState>] [-ProvisioningType <ProvisioningType>] [-PublishedApplication <String>] [-PublishedName <String>] [-PvdEstimatedCompletionTime <DateTime>] [-PvdPercentDone <Int32>] [-PvdStage <PvdStage>] [-PvdUpdateStartTime <DateTime>] [-RegistrationState <RegistrationState>] [-ScheduledReboot <ScheduledReboot>] [-SecureIcaRequired <Boolean>] [-SessionAutonomouslyBrokered <Boolean>] [-SessionClientAddress <String>] [-SessionClientName <String>] [-SessionClientVersion <String>] [-SessionConnectedViaHostName <String>] [-SessionConnectedViaIP <String>] [-SessionCount <Int32>] [-SessionDeviceId <String>] [-SessionHardwareId <String>] [-SessionHidden <Boolean>] [-SessionKey <Guid>] [-SessionLaunchedViaHostName <String>] [-SessionLaunchedViaIP <String>] [-SessionProtocol <String>] [-SessionSecureIcaActive <Boolean>] [-SessionsEstablished <Int32>] [-SessionSmartAccessTag <String>] [-SessionsPending <Int32>] [-SessionStartTime <DateTime>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionSupport <SessionSupport>] [-SessionType <SessionType>] [-SessionUid <Int64>] [-SessionUserName <String>] [-SessionUserSID <String>] [-SID <String>] [-SummaryState <DesktopSummaryState>] [-SupportedPowerActions <String[]>] [-Tag <String>] [-UUID <Guid>] [-VMToolsState <VMToolsState>] [-WillShutdownAfterUse <Boolean>] [-WillShutdownAfterUseReason <WillShutdownAfterUseReason>] [-WindowsConnectionSetting <WindowsConnectionSetting>] [-ZoneName <String>] [-ZoneUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Filters machines using the specified criteria, then groups and counts matching machines with the same value for a particular property. The number of machines in the group, and the property value for the group, is output. For example:


```
C:\PS> Group-BrokerMachine -Property SummaryState  

```
Count Name ----- ---- 43 Available 17 InUse 3 Disconnected

Filtering supports the same options as the Get-BrokerMachine cmdlet, and allows filtering on both machine and session properties.

Group-BrokerMachine is similar to the standard PowerShell Group-Object, but is faster than piping the output of Get-BrokerMachine into Group-Object when working with many machines.

Note that the MaxRecordCount, ReturnTotalRecordCount, Skip, and SortBy parameters apply to GroupInfo records output rather than the filtered machines.


## Related Commands

* [Get-BrokerMachine](./Get-BrokerMachine/)
* [Group-Object](./Group-Object/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets a machine with a specific UID. | true | false |  |
| Property | Selects the property by which matching machines are grouped. | true | false |  |
| MachineName | Gets machines with a specific machine name (in the form domain\\machine). | false | false |  |
| AgentVersion | Gets machines with a specific Virtual Delivery Agent version. | false | false |  |
| AllocationType | Gets machines from catalogs with the specified allocation type. | false | false |  |
| ApplicationInUse | Gets machines running a specified published application. String comparisons are case-insensitive. | false | false |  |
| AssignedClientName | Gets machines that have been assigned to the specific client name. | false | false |  |
| AssignedIPAddress | Gets machines that have been assigned to the specific client IP address. | false | false |  |
| AssignedUserSID | Gets machines with the specific SID of the user to whom the desktop is assigned. | false | false |  |
| AssociatedTenantId | Gets machines associated with the specified tenant. | false | false |  |
| AssociatedUserFullName | Gets machines with an associated user identified by their full name (usually 'first-name last-name').<br>Associated users are all current users of a desktop, plus the assigned users for private desktops. | false | false |  |
| AssociatedUserName | Gets machines with an associated user identified by their user name (in the form 'domain\\user').<br>Associated users are all current users of a desktop, plus the assigned users for private desktops. | false | false |  |
| AssociatedUserSID | Gets machines with an associated user identified by their Windows SID.<br>Associated users are all current users of a desktop, plus the assigned users for private desktops. | false | false |  |
| AssociatedUserUPN | Gets machines with an associated user identified by their User Principle Name (in the form 'user@domain').<br>Associated users are all current users of a desktop, plus the assigned users for private desktops. | false | false |  |
| BrowserName | Gets assigned machines backing desktop resources that have browser names matching the specified name. | false | false |  |
| CatalogName | Gets machines from the catalog with the specific name. | false | false |  |
| CatalogUid | Gets machines from the catalog with the specific UID. | false | false |  |
| CatalogUUID | Gets machines from the catalog with the specific UUID. | false | false |  |
| CbpVersion | The version of CBP that the VDA is currently registered with. This will be null when the VDA is not registered. | false | false |  |
| ColorDepth | Gets machines configured with a specific color depth.<br>Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| ControllerDNSName | Gets machines by the DNS name of the controller they are registered with. | false | false |  |
| DeliveryType | Gets machines of a particular delivery type.<br>Valid values are AppsOnly, DesktopsOnly, DesktopsAndApps | false | false |  |
| Description | Get machines by description. | false | false |  |
| DesktopCondition | Gets machines with an outstanding desktop condition.<br>Valid values are:<br>o CPU: Indicates the machine has high CPU usage<br>o ICALatency: Indicates the network latency is high<br>o UPMLogonTime: Indicates that the profile load time was high | false | false |  |
| DesktopGroupName | Gets machines from a desktop group with the specified name. | false | false |  |
| DesktopGroupUid | Gets machines from a desktop group with a specific UID. | false | false |  |
| DesktopGroupUUID | Gets machines from a desktop group with a specific UUID. | false | false |  |
| DesktopKind | Deprecated: Use AllocationType parameter.<br>Gets machines of a particular kind.<br>Valid values are Private, Shared. | false | false |  |
| DesktopUid | Gets the machine that corresponds to the desktop with the specific UID. | false | false |  |
| DNSName | Gets machines with the specific DNS name. | false | false |  |
| DrainingUntilShutdown | Gets machines depending on whether they are draining until shutdown or not. | false | false |  |
| FaultState | Gets machines currently in the specified fault state. | false | false |  |
| FunctionalLevel | Gets machines with a specific FunctionalLevel.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| HostedMachineId | Gets machines with the specific machine ID known to the hypervisor. | false | false |  |
| HostedMachineName | Gets machines with the specific machine name known to the hypervisor. | false | false |  |
| HostingServerName | Gets machines by the name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionName | Gets machines with the specific name of the hypervisor connection hosting them. | false | false |  |
| HypervisorConnectionUid | Gets machines with the specific UID of the hypervisor connection hosting them. | false | false |  |
| HypHypervisorConnectionUid | Gets machines with the specific UUID of the hypervisor connection hosting them. | false | false |  |
| IconUid | Gets machines by configured icon. Note that machines with a null IconUid use the icon of the desktop group. | false | false |  |
| ImageOutOfDate | Gets machines depending on whether their disk image is out of date or not (for machines provisioned using MCS only). | false | false |  |
| InMaintenanceMode | Gets machines by whether they are in maintenance mode or not. | false | false |  |
| IPAddress | Gets machines with a specific IP address. | false | false |  |
| IsAssigned | Gets machines according to whether they are assigned or not. Machines may be assigned to one or more users or groups, a client IP address or a client endpoint name. | false | false |  |
| IsPhysical | Gets machines according to whether they can be power managed by XenDesktop or not. | false | false |  |
| IsReserved | Gets machines that are reserved for special use, for example, for AppDisk preparation. | false | false |  |
| LastConnectionFailure | Gets machines with a specific reason for the last recorded connection failure. This value is None if the last connection was successful or if there has been no attempt to connect to the machine yet.<br>Valid values are None, SessionPreparation, RegistrationTimeout, ConnectionTimeout, Licensing, Ticketing, and Other. | false | false |  |
| LastConnectionTime | Gets machines to which a user session connection occurred at a specific time. This is the time that the broker detected that the connection attempt either succeeded or failed. | false | false |  |
| LastConnectionUser | Gets machines where a specific user name last attempted a connection (in the form 'domain\\user'). | false | false |  |
| LastDeregistrationReason | Gets machines whose broker last recorded a specific deregistration reason.<br>Valid values are \$null, AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached. | false | false |  |
| LastDeregistrationTime | Gets machines by the time that they were last deregistered. | false | false |  |
| LastErrorReason | Gets machines with the specified last error reason. | false | false |  |
| LastErrorTime | Gets machines with the specified last error time. | false | false |  |
| LastHostingUpdateTime | Gets machines with a specific time that the hosting information was last updated. | false | false |  |
| LastPvdErrorReason | Gets machines with the specified last Personal vDisk preparation error reason. | false | false |  |
| LastPvdErrorTime | Gets machines with the specified last Personal vDisk preparation error time. | false | false |  |
| LastRegistrationTime | Gets machines by the time that they last registered. | false | false |  |
| LoadIndex | Gets machines by their current load index. | false | false |  |
| MacAddress | Gets machines with a specific MAC address. | false | false |  |
| MachineInternalState | Gets machines with the specified internal state. | false | false |  |
| MaintenanceModeReason | Gets machines by the maintenance mode reason. Valid values are:<br>o None - Machine is not in maintenance mode.<br>o Administrator - Machine was manually placed in maintenance mode by an administrator.<br>o MaxFailedRegistrations - Machine was automatically placed in maintenance mode due to reaching the maximum failed registration limit. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| OSType | Gets machines by the type of operating system they are running. | false | false |  |
| OSVersion | Gets machines by the version of the operating system they are running. | false | false |  |
| PersistUserChanges | Gets machines according to the location where user changes are persisted. Values can be:<br>o OnLocal - User changes are persisted locally.<br>o Discard - User changes are discarded.<br>o OnPvd - User changes are persisted on the Pvd. | false | false |  |
| PowerActionPending | Gets machines depending on whether a power action is pending or not.<br>Valid values are \$true or \$false. | false | false |  |
| PowerState | Gets machines with a specific power state.<br>Valid values are Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| ProvisioningType | Specifies the provisioning type for the catalog. Values can be:<br>o Manual - No provisioning.<br>o PVS - Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| PublishedApplication | Gets machines with a specific application published to them (identified by its browser name). | false | false |  |
| PublishedName | Gets desktops with a specific published name. | false | false |  |
| PvdEstimatedCompletionTime | If preparation of the Personal vDisk is currently in progress for this machine, this reports an estimation of the time at which the process will be complete. | false | false |  |
| PvdPercentDone | Gets machines a specific percentage through the Personal vDisk preparation process. | false | false |  |
| PvdStage | Gets machines at a specific personal vDisk stage.<br>Valid values are None, Requested, Starting, Working and Failed. | false | false |  |
| PvdUpdateStartTime | If preparation of the Personal vDisk is currently in progress for this machine, this reports when the update process began. | false | false |  |
| RegistrationState | Gets machines in a specific registration state.<br>Valid values are Unregistered, Initializing, Registered, and AgentError. | false | false |  |
| ScheduledReboot | Gets machines according to their current status with respect to any scheduled reboots (for either scheduled desktop group reboots or image rollout purposes). Valid values are:<br>o None - No reboot currently scheduled.<br>o Pending - Reboot scheduled but machine still available for use.<br>o Draining - Reboot scheduled. New logons are disabled, but reconnections to existing sessions are allowed.<br>o InProgress - Machine is actively being rebooted.<br>o Natural - Natural reboot in progress. Machine is awaiting a restart. | false | false |  |
| SecureIcaRequired | Gets machines configured with a particular SecureIcaRequired setting. Note that the machine setting of \$null indicates that the desktop group value is used. | false | false |  |
| SessionAutonomouslyBrokered | Gets machines according to whether their current session is autonomously brokered or not. Autonomously brokered sessions are HDX sessions established by direct connection without being brokered.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionClientAddress | Gets machines with a specific client IP address. | false | false |  |
| SessionClientName | Gets machines with a specific client name. | false | false |  |
| SessionClientVersion | Gets machines with a specific client version. | false | false |  |
| SessionConnectedViaHostName | Gets machines with a specific host name of the incoming connection. This is usually a proxy or Citrix Access Gateway server.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionConnectedViaIP | Gets machines with a specific IP address of the incoming connection.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionCount | Gets machines according to the total number of both pending and established user sessions on the machine. | false | false |  |
| SessionDeviceId | Gets machines with a specific client device ID. | false | false |  |
| SessionHardwareId | Gets machines with a specific client hardware ID. | false | false |  |
| SessionHidden | Gets machines by whether their sessions are hidden or not. Hidden sessions are treated as though they do not exist when launching sessions using XenDesktop; a hidden session cannot be reconnected to, but a new session may be launched using the same entitlement. | false | false |  |
| SessionKey | Gets machine running the session with the specified unique key.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionLaunchedViaHostName | Gets machines with a specific host name of the Web Interface server from which the user launched the session.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionLaunchedViaIP | Gets machines with a specific IP address of the Web Interface server from which the user launched the session.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionProtocol | Gets machines with connections using a specific protocol, for example HDX, RDP, or Console. | false | false |  |
| SessionSecureIcaActive | Gets machines depending on whether the current session uses SecureICA or not.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionsEstablished | Gets machines according to the number of established user sessions present on the machine. | false | false |  |
| SessionSmartAccessTag | Gets session machines where the session has the specific SmartAccess tag.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionsPending | Get machines according to the number of pending user sessions for the machine. | false | false |  |
| SessionStartTime | Gets machines with a specific session start time.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionState | Gets machines with a specific session state.<br>Valid values are \$null, Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionStateChangeTime | Gets machines whose sessions last changed state at a specific time.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionSupport | Gets machines that have the specified session capability. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession - Multi-session capable machine. | false | false |  |
| SessionType | Gets machines with a specific session state.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUid | Gets single-session machines with a specific session UID (\$null for no session).<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUserName | Gets machines with a specific user name for the current session (in the form 'domain\\user').<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUserSID | Gets machines with a specific SID of the current session user.<br>Session properties are always null for multi-session machines. | false | false |  |
| SID | Gets machines with a specific machine SID. | false | false |  |
| SummaryState | Gets machines with a specific summary state.<br>Valid values are Off, Unregistered, Available, Disconnected, and InUse. | false | false |  |
| SupportedPowerActions | A list of power actions supported by this machine. | false | false |  |
| Tag | Gets machines where the session has the given SmartAccess tag. | false | false |  |
| UUID | Gets machines with the specified value of UUID. | false | false |  |
| VMToolsState | Gets machines with a specific VM tools state.<br>Valid values are NotPresent, Unknown, NotStarted, and Running. | false | false |  |
| WillShutdownAfterUse | Gets machines depending on whether they shut down after use or not. | false | false |  |
| WillShutdownAfterUseReason | Gets machines by the will shutdown after use reason. Valid values are:<br>o None - Machine will not shutdown after use.<br>o ResetDiskImage - Machine will shutdown after use to reset its disk image.<br>o ScheduledNaturalReboot - Machine will shutdown after use as part of the scheduled natural reboot process.<br>o OnDemandNaturalReboot - Machine will shutdown after use as part of an on-demand natural reboot process. | false | false |  |
| WindowsConnectionSetting | Gets machines according to their current Windows connection setting (logon mode). Valid values are:<br>o LogonEnabled - All logons are enabled.<br>o Draining - New logons are disabled, but reconnections to existing sessions are allowed.<br>o DrainingUntilRestart - Same as Draining, but setting reverts to LogonEnabled when machine next restarts.<br>o LogonDisabled - All logons and reconnections are disabled.<br>This is a Windows setting and is not controlled by XenDesktop. It applies only to multi-session machines; for single-session machines its value is always LogonEnabled. | false | false |  |
| ZoneName | Gets machines located in the zone with the specified name. | false | false |  |
| ZoneUid | Gets machines located in the zone with the specified UID. | false | false |  |
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
Each GroupInfo object represents one group, and contains the following properties:<br>-- Count: The count of machines in this group.<br>-- Name: The value of the property the machines were grouped by (as a string).<br>If you do not specify -SortBy, groups are sorted with the largest count first.
## Notes
To compare dates or times, use -Filter and relative comparisons. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Group-BrokerMachine -Property SummaryState -DesktopGroupName dg1
```
#### Description
Group machines from the dg1 group by summary state.
### Example 2
```
C:\PS> Group-BrokerMachine -Property LastConnectionFailure -Filter { LastConnectionFailure -ne "None" -and LastConnectionTime -ge '-7' } -MaxRecordCount 1
```
#### Description
For machines where the last connection attempt failed, list the most common reason for failure, ignoring connections that failed over a week ago.
### Example 3
```
C:\PS> Group-BrokerMachine -Property HostingServerName -DesktopCondition ICALatency -SortBy Name
```
#### Description
List alphabetically the hypervisor servers hosting machines that are currently experiencing high network latency.
