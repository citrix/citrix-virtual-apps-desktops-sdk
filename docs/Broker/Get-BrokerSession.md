
# Get-Brokersession
Gets a list of sessions.
## Syntax
```
Get-BrokerSession [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerSession [[-SessionKey] <Guid>] [-AgentVersion <String>] [-AnonymousUserId <String>] [-ApplicationInUse <String>] [-AppState <SessionAppState>] [-AppStateLastChangeTime <DateTime>] [-AutonomouslyBrokered <Boolean>] [-BrokeringDuration <Int32>] [-BrokeringTime <DateTime>] [-BrokeringUserName <String>] [-BrokeringUserSID <String>] [-CatalogName <String>] [-CbpVersion <CBPVersion>] [-ClientAddress <String>] [-ClientName <String>] [-ClientPlatform <String>] [-ClientProductId <Int32>] [-ClientVersion <String>] [-ConnectedViaHostName <String>] [-ConnectedViaIP <String>] [-ConnectionMode <ConnectionMode>] [-ControllerDNSName <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopKind <DesktopKind>] [-DesktopSID <String>] [-DesktopUid <Int32>] [-DeviceId <String>] [-DNSName <String>] [-EntitlementPolicyRuleUid <Int32>] [-EstablishmentDuration <Int32>] [-EstablishmentTime <DateTime>] [-HardwareId <String>] [-Hidden <Boolean>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-IdleDuration <TimeSpan>] [-IdleSince <DateTime>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAnonymousUser <Boolean>] [-IsPhysical <Boolean>] [-LaunchedViaHostName <String>] [-LaunchedViaIP <String>] [-LaunchedViaPublishedName <String>] [-LogoffInProgress <Boolean>] [-LogonInProgress <Boolean>] [-MachineName <String>] [-MachineSummaryState <DesktopSummaryState>] [-MachineUid <Int32>] [-Metadata <String>] [-OSType <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerState <PowerState>] [-PreferredZoneName <String>] [-PreferredZoneUid <Guid>] [-Protocol <String>] [-ProvisioningType <ProvisioningType>] [-ReceiverIPAddress <String>] [-ReceiverName <String>] [-SecureIcaActive <Boolean>] [-SessionId <Int32>] [-SessionReconnection <SessionReconnection>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionSupport <SessionSupport>] [-SessionType <SessionType>] [-StartTime <DateTime>] [-TenantId <Guid>] [-UntrustedUserName <String>] [-UserFullName <String>] [-UserName <String>] [-UserSID <String>] [-UserUPN <String>] [-ZoneName <String>] [-ZoneUid <Guid>] [-ApplicationUid <Int32>] [-SharedDesktopUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves sessions matching all the specified criteria. If no parameters are specified this cmdlet enumerates all sessions.


### Brokersession Object
The session object returned represents a session on a machine in the site. The session could be for a desktop or application


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the machine.

  * AnonymousUserId (System.String) User ID associated with an anonymous session. This is a non-Windows identity and does not relate to the user account under which the session is running. Not all anonymous sessions have associated user IDs.

  * ApplicationsInUse (System.String\[\]) List of applications in use in the session. Applications are identified by their administrative name.

  * AppState (Citrix.Broker.Admin.SDK.SessionAppState) The app state of the session. Valid values are PreLogon, PreLaunched, Active, Desktop, Lingering and NoApps.

  * AppStateLastChangeTime (System.DateTime?) The time when the session entered the current app state.

  * AutonomouslyBrokered (System.Boolean) Indicates whether this is an HDX session established by direct connection without being brokered.

  * BrokeringDuration (System.Int32?) Time taken to broker the session (in milliseconds).

  * BrokeringTime (System.DateTime?) Time at which the session was brokered.

  * BrokeringUserName (System.String) The user name of the brokering user.

  * BrokeringUserSID (System.String) The SID of the brokering user.

  * CatalogName (System.String) The name of the catalog that the machine hosting the session is assigned to.

  * CbpVersion (Citrix.Broker.Admin.SDK.CBPVersion?) The version of CBP that the VDA is currently registered with. This will be null when the VDA is not registered.

  * ClientAddress (System.String) The IP address of the client connected to the session.

  * ClientName (System.String) The host name of the client connected to the session.

  * ClientPlatform (System.String) The name of client platform, as indicated by client product ID.

  * ClientProductId (System.Int32?) The product ID of the client connected to the session.

  * ClientVersion (System.String) The version of the Citrix Receiver running on the client connected to the session.

  * ConnectedViaHostName (System.String) The host name of the incoming connection. This is usually a gateway, router or client.

  * ConnectedViaIP (System.String) The IP address of the incoming connection This is usually a gateway, router or client.

  * ConnectionMode (Citrix.Broker.Admin.SDK.ConnectionMode?) The way in which the most recent connection to the session was established. Valid modes are:
    * Brokered: established through the XenDesktop Broker (for example, using StoreFront).
    * Unbrokered: direct connection (for example, using the console or direct RDP/HDX).
    * LeasedConnection: established through the XenDesktop Broker using a connection lease.
    * VdaHighAvailabilityMode: direct connection while VDA in high-availability mode.
    * ThirdPartyBroker: established through a third-party Broker.
    * ThirdPartyBrokerWithLicensing: established and licensed through a third-party Broker.

  * ControllerDNSName (System.String) The DNS host name of the controller that the session's hosting machine is registered with.

  * DesktopGroupName (System.String) Name of the desktop group of the machine the session is on.

  * DesktopGroupUid (System.Int32) UID of the desktop group of the machine the session is on.

  * DesktopKind (Citrix.Broker.Admin.SDK.DesktopKind) Indicates if the session is shared or private.

  * DesktopSID (System.String) The Windows SID of the machine the session is on.

  * DesktopUid (System.Int32) For a desktop session, the unique identifier of the desktop.

  * DeviceId (System.String) Unique identifier for the client device that has most recently been associated with the session.

  * DNSName (System.String) The DNS host name of the machine hosting the session.

  * EntitlementPolicyRuleUid (System.Int32?) The entitlement policy rule that granted the user the entitlement to launch the session. Only present for shared resources.

  * EstablishmentDuration (System.Int32?) Duration that it took to establish the session.

  * EstablishmentTime (System.DateTime?) Time at which the session was established.

  * HardwareId (System.String) Unique identifier for the client hardware that has been most recently associated with the session.

  * Hidden (System.Boolean) Flag to indicate if the session is currently hidden from the user and not to be reconnected to.

  * HostedMachineName (System.String) The friendly name of a hosted machine running the session, as used by its hypervisor. This does not necessarily match either the DNS or AD name of the machine.

  * HostingServerName (System.String) DNS name of the hypervisor that is hosting the machine hosting the session.

  * HypervisorConnectionName (System.String) The name of the hypervisor connection that the machine hosting the session has been assigned to.

  * IdleDuration (System.TimeSpan?) Period for which session has been idle, or null if it is not considered idle.

  * IdleSince (System.DateTime?) Time at which session went idle

  * ImageOutOfDate (System.Boolean?) Denotes whether the VM image for a hosted machine is out of date and due to be updated to a new master image when the machine next reboots.

  * InMaintenanceMode (System.Boolean) Denotes whether the machine hosting the session is in maintentance mode.

  * IPAddress (System.String) The IP address of the machine hosting the session.

  * IsAnonymousUser (System.Boolean) Indicates whether the session was established anonymously (without user credentials), in this case a temporary local user account on the machine is used.

  * IsPhysical (System.Boolean) This value is false if the machine hosting the session can be power managed, and true otherwise

  * LaunchedViaHostName (System.String) The host name of the StoreFront server used to launch the session.

  * LaunchedViaIP (System.String) The IP address of the StoreFront server used to launch the session.

  * LaunchedViaPublishedName (System.String) The published name of the resource originally used to launch the session. This is the name selected by the user in Receiver. For application sessions this is the name of the first application launched into the session even if that application has since terminated. The name here does not change if the resource is later renamed or removed.
    Only present for shared resources.

  * LogoffInProgress (System.Boolean) Indicates whether the session is in the process of being logged off.

  * LogonInProgress (System.Boolean) Indicates whether the session is still executing user logon processing or not.

  * MachineName (System.String) DNS host name of the machine hosting the session.

  * MachineSummaryState (Citrix.Broker.Admin.SDK.DesktopSummaryState) The summary state of the machine (will be Unregistered, Disconnected, or InUse)

  * MachineUid (System.Int32) UID of the machine hosting the session.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Map of metadata for this session.

  * OSType (System.String) A string that can be used to identify the operating system that is running on the machine hosting the session.

  * PersistUserChanges (Citrix.Broker.Admin.SDK.PersistUserChanges) Describes whether/how the user changes are persisted. Possible values are:
    * OnLocal - Persist the user changes locally.
    * Discard - Discard user changes.
    * OnPvd - Persist user changes on the Citrix Personal vDisk.

  * PowerState (Citrix.Broker.Admin.SDK.PowerState) The current power state of the machine hosting the session. Possible values are: Unmanaged, Unknown, Unavailable, On, Suspended, TurningOn, TurningOff, Suspending and Resuming.

  * PreferredZoneName (System.String) The name of preferred zone used for the original session launch. This may differ from the actual ZoneName if no resources were available in the preferred zone at launch time.

  * PreferredZoneUid (System.Guid?) The UID of preferred zone used for the original session launch. This may differ from the actual ZoneUid if no resources were available in the preferred zone at launch time.

  * Protocol (System.String) The protocol that the session is using, can be HDX, RDP, or Console. Console sessions on XenDesktop 5 VDAs appear with a blank protocol.

  * ProvisioningType (Citrix.Broker.Admin.SDK.ProvisioningType) Describes how the machine hosting the session was provisioned, possible values are:
    * Manual: No provisioning.
    * PVS: Machine provisioned by PVS (may be physical, blade, VM,...)
    * MCS: Machine provisioned by MCS (machine must be VM)

  * ReceiverIPAddress (System.String) The IP address of the client as supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected.

  * ReceiverName (System.String) The name of the client as supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected.

  * SecureIcaActive (System.Boolean?) Indicates whether SecureICA is active on the session.

  * SessionId (System.Int32) Deprecated. A unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine.

  * SessionKey (System.Guid) GUID that provides a unique identifier for this session.

  * SessionReconnection (Citrix.Broker.Admin.SDK.SessionReconnection?) Describes the session reconnection (roaming) behavior for this session. Possible values are: Always, DisconnectedOnly, and SameEndpointOnly.

  * SessionState (Citrix.Broker.Admin.SDK.SessionState) The state of the session. Valid values are Connected, Active or Disconnected.
    For a session on a machine with functional level below L7, the additional states PreparingSession, Reconnecting, NonBrokeredSession, Other, and Unknown can also occur.

  * SessionStateChangeTime (System.DateTime) The time of the most recent state change for the session.

  * SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport) Indicates if the machine hosting the session supports multiple or single sessions.

  * SessionType (Citrix.Broker.Admin.SDK.SessionType) Indicates if this is an Application or Desktop session.

  * SmartAccessTags (System.String\[\]) The Smart Access tags for this session.

  * StartTime (System.DateTime?) Indicates when the session was started.

  * TenantId (System.Guid?) The tenant associated with the session.

  * Uid (System.Int64) Unique identifier of this session.

  * UntrustedUserName (System.String) The name of the logged-on user reported directly from the machine (in the form DOMAIN\\user). This may be useful where the user is logged in to a non-domain account, however the name cannot be verified and must therefore be considered untrusted.

  * UserFullName (System.String) The full name of the user.

  * UserName (System.String) The name of the user.

  * UserSID (System.String) The user's Windows SID.

  * UserUPN (System.String) The user's User Principal Name

  * ZoneName (System.String) The name of zone in which the machine hosting the session is located.

  * ZoneUid (System.Guid) The UID of the zone in which the machine hosting the session is located.


## Related Commands

* [Disconnect-BrokerSession](./Disconnect-BrokerSession/)
* [Stop-BrokerSession](./Stop-BrokerSession/)
* [Get-BrokerDesktop](./Get-BrokerDesktop/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get session by its Uid. | true | false |  |
| SessionKey | Gets session having the specified unique key. | false | false |  |
| AgentVersion | Gets sessions with a specific Virtual Desktop Agent version. | false | false |  |
| AnonymousUserId | Gets anonymous session associated with the specified user ID. | false | false |  |
| ApplicationInUse | Gets sessions running specific applications (identified by their SDK Name property). | false | false |  |
| AppState | Get sessions by their app state.<br>Valid values are PreLogon, PreLaunched, Active, Desktop, Lingering and NoApps. | false | false |  |
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
| Protocol | Get sessions by connection protocol. Valid values are HDX, RDP, or Console. | false | false |  |
| ProvisioningType | Gets sessions hosted on machines provisioned in a particular manner. Values can be:<br>o Manual - No automated provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| ReceiverIPAddress | Gets sessions with the specified client IP address supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected. | false | false |  |
| ReceiverName | Gets sessions with the specified client name supplied by Receiver (for example, StoreFront) when the session was launched, or reconnected. | false | false |  |
| SecureIcaActive | Get sessions by their use of SecureICA. | false | false |  |
| SessionId | Deprecated.<br>Gets sessions by session ID, a unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine. | false | false |  |
| SessionReconnection | Get sessions by their session reconnection (roaming) behavior. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
| SessionState | Get sessions by their state.<br>Valid values are Other, PreparingNewSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown. | false | false |  |
| SessionStateChangeTime | Get sessions by their last state change time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| SessionSupport | Gets sessions hosted on machines which support the required pattern of sessions. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | false | false |  |
| SessionType | Get sessions by their type.<br>Valid values are Application and Desktop. | false | false |  |
| StartTime | Get sessions by their start time. In general, Citrix recommends using -Filter and relative comparisons. | false | false |  |
| TenantId | Gets sessions associated with the specified tenant. | false | false |  |
| UntrustedUserName | Gets sessions by the untrusted user name reported directly from the machine (in the form DOMAIN\\user). | false | false |  |
| UserFullName | Gets sessions by user's full name (usually 'first-name last-name'). | false | false |  |
| UserName | Get sessions by user name (in the form DOMAIN\\user). | false | false |  |
| UserSID | Get sessions by user's Windows SID. | false | false |  |
| UserUPN | Gets sessions by user's User Principal Name (in the form user@domain). | false | false |  |
| ZoneName | Gets sessions hosted on machines located in the zone with the specified name. | false | false |  |
| ZoneUid | Gets sessions hosted on machines located in the zone with the specified UID. | false | false |  |
| ApplicationUid | Get sessions running the application with the specified Uid. | false | false |  |
| SharedDesktopUid | Get sessions by SharedDesktop Uid. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Session
Returns sessions matching the specified criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerSession
```
#### Description
Enumerate all sessions.
### Example 2
```
C:\PS> Get-BrokerSession -UserName MyDomain\MyAccount -SessionState Disconnected
```
#### Description
Get all disconnected sessions for a specific user.
