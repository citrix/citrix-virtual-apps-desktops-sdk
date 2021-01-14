
# Group-Brokersession
Groups and counts sessions with the same value for a specified property.
## Syntax
```
Group-BrokerSession [-Uid] <Int64> -Property <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Group-BrokerSession -Property <String> [[-SessionKey] <Guid>] [-AgentVersion <String>] [-AnonymousUserId <String>] [-ApplicationInUse <String>] [-AppState <SessionAppState>] [-AppStateLastChangeTime <DateTime>] [-AutonomouslyBrokered <Boolean>] [-BrokeringDuration <Int32>] [-BrokeringTime <DateTime>] [-BrokeringUserName <String>] [-BrokeringUserSID <String>] [-CatalogName <String>] [-CbpVersion <CBPVersion>] [-ClientAddress <String>] [-ClientName <String>] [-ClientPlatform <String>] [-ClientProductId <Int32>] [-ClientVersion <String>] [-ConnectedViaHostName <String>] [-ConnectedViaIP <String>] [-ConnectionMode <ConnectionMode>] [-ControllerDNSName <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopKind <DesktopKind>] [-DesktopSID <String>] [-DesktopUid <Int32>] [-DeviceId <String>] [-DNSName <String>] [-EntitlementPolicyRuleUid <Int32>] [-EstablishmentDuration <Int32>] [-EstablishmentTime <DateTime>] [-HardwareId <String>] [-Hidden <Boolean>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-IdleDuration <TimeSpan>] [-IdleSince <DateTime>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAnonymousUser <Boolean>] [-IsPhysical <Boolean>] [-LaunchedViaHostName <String>] [-LaunchedViaIP <String>] [-LaunchedViaPublishedName <String>] [-LogoffInProgress <Boolean>] [-LogonInProgress <Boolean>] [-MachineName <String>] [-MachineSummaryState <DesktopSummaryState>] [-MachineUid <Int32>] [-Metadata <String>] [-OSType <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerState <PowerState>] [-PreferredZoneName <String>] [-PreferredZoneUid <Guid>] [-Protocol <String>] [-ProvisioningType <ProvisioningType>] [-ReceiverIPAddress <String>] [-ReceiverName <String>] [-SecureIcaActive <Boolean>] [-SessionId <Int32>] [-SessionReconnection <SessionReconnection>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionSupport <SessionSupport>] [-SessionType <SessionType>] [-StartTime <DateTime>] [-TenantId <Guid>] [-UntrustedUserName <String>] [-UserFullName <String>] [-UserName <String>] [-UserSID <String>] [-UserUPN <String>] [-ZoneName <String>] [-ZoneUid <Guid>] [-ApplicationUid <Int32>] [-SharedDesktopUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Filters sessions using the specified criteria, then groups and counts matching sessions with the same value for a particular property. The number of sessions in the group, and the property value for the group, is output. For example:


```
C:\PS> Group-BrokerSession -Property SessionState  

```
Count Name ----- ---- 43 Active 17 NonBrokeredSession 3 Disconnected

Filtering supports the same options as the Get-BrokerSession cmdlet, and allows filtering on both machine and session properties.

Group-BrokerSession is similar to the standard PowerShell Group-Object, but is faster than piping the output of Get-BrokerSession into Group-Object when working with many machines.

Note that the MaxRecordCount, ReturnTotalRecordCount, Skip, and SortBy parameters apply to GroupInfo records output rather than the filtered sessions.


## Related Commands

* [Get-BrokerSession](./Get-BrokerSession/)
* [Group-Object](./Group-Object/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets session by its Uid. | true | false |  |
| Property | Selects the property by which matching sessions are grouped. | true | false |  |
| SessionKey | Gets session having the specified unique key. | false | false |  |
| AgentVersion | Gets sessions with a specific Virtual Desktop Agent version. | false | false |  |
| AnonymousUserId | Gets sessions associated with the specified user ID. | false | false |  |
| ApplicationInUse | Gets sessions running specific applications (identified by their SDK Name property). | false | false |  |
| AppState | Gets sessions by their app state.<br>Valid values are PreLogon, PreLaunched, Active, Desktop, Lingering and NoApps. | false | false |  |
| AppStateLastChangeTime | Get sessions by their app state change time. | false | false |  |
| AutonomouslyBrokered | Gets sessions according to whether they are autonomously brokered or not. Autonomously brokered sessions are HDX sessions established by direct connection without being brokered. | false | false |  |
| BrokeringDuration | Gets session with a specific time taken to broker. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| BrokeringTime | Get sessions brokered at a specific time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| BrokeringUserName | Get sessions by brokering user. | false | false |  |
| BrokeringUserSID | Get sessions by brokering user SID. | false | false |  |
| CatalogName | Gets sessions on machines from a specific catalog name. | false | false |  |
| CbpVersion | The version of CBP that the VDA is currently registered with. This will be null when the VDA is not registered. | false | false |  |
| ClientAddress | Get sessions by client IP address. | false | false |  |
| ClientName | Get sessions by client name. | false | false |  |
| ClientPlatform | Get sessions by client platform. | false | false |  |
| ClientProductId | Get sessions by client product ID. | false | false |  |
| ClientVersion | Get sessions by client version. | false | false |  |
| ConnectedViaHostName | Get sessions by host name of the incoming connection. This is usually a proxy or Citrix Access Gateway server. | false | false |  |
| ConnectedViaIP | Get sessions by IP address of the incoming connection. | false | false |  |
| ConnectionMode | Gets sessions by the way in which the most recent connection to the session was established.<br>Valid modes are Brokered, Unbrokered, LeasedConnection, VdaHighAvailabilityMode, ThirdPartyBroker, and ThirdPartyBrokerWithLicensing. | false | false |  |
| ControllerDNSName | Gets sessions that are hosted on machines which are registered with a specific controller. | false | false |  |
| DesktopGroupName | Gets sessions from a desktop group with the specified name. | false | false |  |
| DesktopGroupUid | Gets sessions from a desktop group with the specified UID. | false | false |  |
| DesktopKind | Gets sessions on a desktop of a particular kind.<br>Valid values are Private and Shared. | false | false |  |
| DesktopSID | Get sessions by desktop SID. | false | false |  |
| DesktopUid | Get sessions by desktop Uid. | false | false |  |
| DeviceId | Get sessions by client device id. | false | false |  |
| DNSName | Gets sessions by their machine's DNS name. | false | false |  |
| EntitlementPolicyRuleUid | Gets sessions where the user was granted the entitlement to launch the session from the specified entitlement policy rule. | false | false |  |
| EstablishmentDuration | Gets sessions which took a specific time to establish. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| EstablishmentTime | Gets sessions which became established at a particular time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| HardwareId | Get sessions by client hardware id. | false | false |  |
| Hidden | Get sessions by whether they are hidden or not. Hidden sessions are treated as though they do not exist when brokering sessions; a hidden session cannot be reconnected to, but a new session may be launched using the same entitlement. | false | false |  |
| HostedMachineName | Gets sessions by their machine's name as known to its hypervisor. | false | false |  |
| HostingServerName | Gets sessions hosted by a machine with a specific name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionName | Gets sessions hosted by a machine with a specific name of the hosting hypervisor connection. | false | false |  |
| IdleDuration | Gets sessions that have been idle for the specified period | false | false |  |
| IdleSince | Time at which session went idle | false | false |  |
| ImageOutOfDate | Gets sessions hosted by a machine with a specific ImageOutOfDate setting. | false | false |  |
| InMaintenanceMode | Gets sessions hosted by a machine with a specific InMaintenanceMode setting. | false | false |  |
| IPAddress | Gets sessions hosted by a machine with a specific IP address. | false | false |  |
| IsAnonymousUser | Gets sessions depending on whether they were established anonymously (\$true) or not (\$false). An anonymous session is established without user credentials and a temporary local user account is used. | false | false |  |
| IsPhysical | Gets sessions hosted on machines where the flag indicating if the machine can be power managed by the Citrix Broker Service matches the requested value. Where the power state of the machine cannot be controlled, specify \$true, otherwise \$false. | false | false |  |
| LaunchedViaHostName | Get sessions by the host name of the StoreFront server from which a user launches a session. | false | false |  |
| LaunchedViaIP | Get sessions by the IP address of the StoreFront server from which a user launches a session. | false | false |  |
| LaunchedViaPublishedName | Gets sessions originally launched using a resource having a name matching the specified published name. | false | false |  |
| LogoffInProgress | Gets sessions by whether they are in the process of being logged off or not. | false | false |  |
| LogonInProgress | Gets sessions by whether they are still executing user logon processing or not. | false | false |  |
| MachineName | Gets sessions by their machine name (in the form DOMAIN\\machine). | false | false |  |
| MachineSummaryState | Gets sessions on a machine with a specific summary state.<br>Valid values are Off, Unregistered, Available, Disconnected, Preparing, and InUse. | false | false |  |
| MachineUid | Gets sessions on a machine with the specified UID. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| OSType | Gets sessions with a specific type of operating system. | false | false |  |
| PersistUserChanges | Gets sessions where the user changes are persisted in a particular manner. Values can be:<br>o OnLocal - User changes are persisted locally.<br>o Discard - User changes are discarded.<br>o OnPvd - User changes are persisted on the Pvd. | false | false |  |
| PowerState | Gets sessions on machines in the specified power state.<br>Valid values are Unmanaged, Unknown, Unavailable, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| PreferredZoneName | Gets sessions originally launched with the specified preferred zone name. | false | false |  |
| PreferredZoneUid | Gets sessions originally launched with the specified preferred zone Uid. | false | false |  |
| Protocol | Get sessions by connection protocol. Valid values are HDX, RDP and Console. | false | false |  |
| ProvisioningType | Gets sessions hosted on machines provisioned in a particular manner. Values can be:<br>o Manual - No automated provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| ReceiverIPAddress | Gets sessions with the specified client IP address supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected. | false | false |  |
| ReceiverName | Gets sessions with the specified client name supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected. | false | false |  |
| SecureIcaActive | Get sessions by their use of SecureICA. | false | false |  |
| SessionId | Deprecated.<br>Gets sessions by session ID, a unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine. | false | false |  |
| SessionReconnection | Get sessions by their session reconnection (roaming) behavior. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
| SessionState | Get sessions by their state.<br>Valid values are Other, PreparingNewSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown. | false | false |  |
| SessionStateChangeTime | Get sessions by their last state change time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| SessionSupport | Gets sessions hosted on machines which support the required pattern of sessions. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | false | false |  |
| SessionType | Gets sessions by their type.<br>Valid values are Application and Desktop. | false | false |  |
| StartTime | Gets sessions by their start time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| TenantId | Gets sessions associated with the specified tenant. | false | false |  |
| UntrustedUserName | Gets sessions by the untrusted user name reported directly from the machine (in the form DOMAIN\\user). | false | false |  |
| UserFullName | Gets sessions by user's full name (usually 'first-name last-name'). | false | false |  |
| UserName | Get sessions by user name (in the form DOMAIN\\user). | false | false |  |
| UserSID | Get sessions by user's Windows SID. | false | false |  |
| UserUPN | Gets sessions by user's User Principal Name (in the form user@domain). | false | false |  |
| ZoneName | Gets sessions hosted by machines located in the zone with the specified name. | false | false |  |
| ZoneUid | Gets sessions hosted by machines located in the zone with the specified UID. | false | false |  |
| ApplicationUid | Gets sessions running the application with the specified Uid. | false | false |  |
| SharedDesktopUid | Gets sessions by SharedDesktop Uid. | false | false |  |
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
Each GroupInfo object represents one group, and contains the following properties:<br>-- Count: The count of sessions in this group.<br>-- Name: The value of the property the sessions were grouped by (as a string).<br>If you do not specify -SortBy, groups are sorted with the largest count first.
## Notes
To compare dates or times, use -Filter and relative comparisons. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Group-BrokerSession -Property SessionState -DesktopGroupName dg1
```
#### Description
Group sessions on machines from the dg1 group by session state.
### Example 2
```
C:\PS> Group-BrokerSession -Property ClientName -ClientName 'ThinClient\*' -SortBy Name
```
#### Description
List alphabetically the names of the clients connected to the site, but only show clients whose names starts with 'ThinClient'.
