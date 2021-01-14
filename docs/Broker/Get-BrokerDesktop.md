
# Get-Brokerdesktop
Gets desktops configured for this site.
## Syntax
```
Get-BrokerDesktop [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerDesktop [[-MachineName] <String>] [-AgentVersion <String>] [-ApplicationInUse <String>] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserUPN <String>] [-AutonomouslyBrokered <Boolean>] [-CatalogName <String>] [-CatalogUid <Int32>] [-ClientAddress <String>] [-ClientName <String>] [-ClientVersion <String>] [-ColorDepth <ColorDepth>] [-ConnectedViaHostName <String>] [-ConnectedViaIP <String>] [-ControllerDNSName <String>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopCondition <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopKind <DesktopKind>] [-DeviceId <String>] [-DNSName <String>] [-FunctionalLevel <FunctionalLevel>] [-HardwareId <String>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-IconUid <Int32>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAssigned <Boolean>] [-IsPhysical <Boolean>] [-LastConnectionFailure <ConnectionFailureReason>] [-LastConnectionTime <DateTime>] [-LastConnectionUser <String>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastErrorReason <String>] [-LastErrorTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-LaunchedViaHostName <String>] [-LaunchedViaIP <String>] [-MachineInternalState <MachineInternalState>] [-MachineUid <Int32>] [-OSType <String>] [-OSVersion <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerActionPending <Boolean>] [-PowerState <PowerState>] [-Protocol <String>] [-ProvisioningType <ProvisioningType>] [-PublishedApplication <String>] [-PublishedName <String>] [-PvdStage <PvdStage>] [-RegistrationState <RegistrationState>] [-SecureIcaActive <Boolean>] [-SecureIcaRequired <Boolean>] [-SessionHidden <Boolean>] [-SessionId <Int32>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionUid <Int64>] [-SessionUserName <String>] [-SessionUserSID <String>] [-SID <String>] [-SmartAccessTag <String>] [-StartTime <DateTime>] [-SummaryState <DesktopSummaryState>] [-Tag <String>] [-WillShutdownAfterUse <Boolean>] [-ApplicationUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is now deprecated, please use Get-BrokerMachine.

Retrieves desktops matching the specified criteria. If no parameters are specified this cmdlet enumerates all desktops.

Get-BrokerDesktop returns objects that combine desktop configuration and state information.

For single-session desktops, session information is displayed if present. It is possible that there are more than one sessions present on single-session desktops if 'fast user switching' is enabled, this cmdlet will prefer to return information about brokered sessions (rather than, for example, unbrokered direct RDP sessions). If there is no session running, session related fields return \$null.

For multi-session desktops, no session information is ever displayed by this cmdlet, so session related fields always return \$null. Get-BrokerSession can be used to get information about sessions on both multi-session and single-session desktops.

To count desktops, rather than retrieve full details of each desktop, use Group-BrokerDesktop instead.

For information about advanced filtering options, see about\_Broker\_Filtering; for information about desktops, see about\_Broker\_Desktops.


### Brokerdesktop Object
The desktop object returned represents a physical or virtual machine configured in the site that is able to run either a Microsoft Windows desktop environment, individual applications, or both.


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the desktop.

  * ApplicationsInUse (System.String\[\]) List of applications in use on the desktop (in the form of browser name).

  * AssignedClientName (System.String) The name of the endpoint client device that the desktop has been assigned to.

  * AssignedIPAddress (System.String) The IP address of the endpoint client device that the desktop has been assigned to.

  * AssociatedUserFullNames (System.String\[\]) Full names of the users that have been associated with the desktop (in the form "Firstname Lastname"). Associated users are the current user(s) for shared desktops and the assigned users for private desktops.

  * AssociatedUserNames (System.String\[\]) Usernames of the users that have been associated with the desktop (usually in the form "domain\\user"). Associated users are the current user(s) for shared desktops and the assigned users for private desktops.

  * AssociatedUserUPNs (System.String\[\]) The user principal names of the users that have been associated with the desktop (in the form user@upndomain.com). Associated users are the current user(s) for shared desktops and the assigned users for private desktops.

  * AutonomouslyBrokered (System.Boolean?) Session property indicating if the current session is an HDX session established by direct connection without being brokered. Session properties are always null for multi-session desktops.

  * CatalogName (System.String) Name of the catalog the desktop is a member of.

  * CatalogUid (System.Int32) UID of the catalog the desktop is a member of.

  * ClientAddress (System.String) Session property indicating the IP address of the client connected to the desktop. Session properties are always null for multi-session desktops.

  * ClientName (System.String) Session property indicating the host name of the client connected to the desktop. Session properties are always null for multi-session desktops.

  * ClientVersion (System.String) Session property indicating the version of the Citrix Receiver running on the connected client. Session properties are always null for multi-session desktops.

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?) The color depth setting configured on the desktop, possible values are: \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.

  * ConnectedViaHostName (System.String) Session property indicating the host name of the connection gateway, router or client. Session properties are always null for multi-session desktops.

  * ConnectedViaIP (System.String) Session property indicating the IP address of the connection gateway, router or client. Session properties are always null for multi-session desktops.

  * ControllerDNSName (System.String) The DNS host name of the controller that the desktop is registered to.

  * DeliveryType (Citrix.Broker.Admin.SDK.DeliveryType) Denotes whether the desktop delivers desktops only, apps only or both.

  * Description (System.String) Description of the desktop.

  * DesktopConditions (System.String\[\]) List of outstanding desktop conditions for the desktop.

  * DesktopGroupName (System.String) Name of the desktop group the desktop has been assigned to.

  * DesktopGroupUid (System.Int32) Uid of the desktop group the desktop has been assigned to.

  * DesktopKind (Citrix.Broker.Admin.SDK.DesktopKind) Deprecated. Denotes whether the desktop is private or shared. AllocationType should be used instead.

  * DeviceId (System.String) Session property indicating a unique identifier for the client device that has most recently been associated with the current session. Session properties are always null for multi-session desktops.

  * DNSName (System.String) The DNS host name of the desktop.

  * FunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?) The functional level of the desktop, if known.

  * HardwareId (System.String) Session property indicating a unique identifier for the client hardware that has been most recently associated with the current session. Session properties are always null for multi-sesison desktops.

  * HostedMachineId (System.String) Unique ID within the hosting unit of the target managed desktop.

  * HostedMachineName (System.String) The friendly name of a hosted desktop as used by its hypervisor. This is not necessarily the DNS name of the desktop.

  * HostingServerName (System.String) DNS name of the hypervisor that is hosting the desktop if managed.

  * HypervisorConnectionName (System.String) The name of the hypervisor connection that the desktop's hosting server is accessed through, if managed.

  * HypervisorConnectionUid (System.Int32?) The UID of the hypervisor connection that the desktop's hosting server is accessed through, if managed.

  * IconUid (System.Int32?) The UID of the desktop's icon that is displayed in StoreFront.

  * ImageOutOfDate (System.Boolean?) Denotes whether the VM image for a hosted desktop is out of date.

  * InMaintenanceMode (System.Boolean) Denotes whether the desktop is in maintenance mode.

  * IPAddress (System.String) The IP address of the desktop.

  * IsAssigned (System.Boolean) Denotes whether a private desktop has been assigned to a user/users, or a client name/address. Users can be assigned explicitly or by assigning on first use of the desktop.

  * IsPhysical (System.Boolean) This value is true if the desktop is physical(ie not power managed by the Citrix Broker Service), and false otherwise.

  * LastConnectionFailure (Citrix.Broker.Admin.SDK.ConnectionFailureReason) The reason for the last failed connection between a client and the desktop.

  * LastConnectionTime (System.DateTime?) Time of the last detected connection attempt that either failed or succeeded.

  * LastConnectionUser (System.String) The SAM name (in the form DOMAIN\\user) of the user that last attempted a connection with the desktop. If the SAM name is not available, the SID is used.

  * LastDeregistrationReason (Citrix.Broker.Admin.SDK.DeregistrationReason?) The reason for the last deregistration of the desktop with the broker. Possible values are: AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached.

  * LastDeregistrationTime (System.DateTime?) Time of the last deregistration of the desktop from the controller.

  * LastErrorReason (System.String) The reason for the last error detected in the desktop.

  * LastErrorTime (System.DateTime?) The time of the last detected error.

  * LastHostingUpdateTime (System.DateTime?) Time of last update to any hosting data (such as power state) for this desktop reported by the hypervisor connection.

  * LaunchedViaHostName (System.String) Session property that denotes the host name of the StoreFront server used to launch the current brokered session. Session properties are always null for multi-session desktops.

  * LaunchedViaIP (System.String) Session property that denotes the IP address of the StoreFront server used to launch the current brokered session. Session properties are always null for multi-session desktops.

  * MachineInternalState (Citrix.Broker.Admin.SDK.MachineInternalState) The internal state of the machine associated with the desktop; reported while the desktop is registered to a controller, plus some private Citrix Broker Service states while the machine is not registered.

  * MachineName (System.String) DNS host name of the machine associated with the desktop.

  * MachineUid (System.Int32) Uid of the associated machine.

  * OSType (System.String) A string that can be used to identify the operating system that is running on the desktop.

  * OSVersion (System.String) A string that can be used to identify the version of the operating system running on the desktop, if known

  * PersistUserChanges (Citrix.Broker.Admin.SDK.PersistUserChanges) Describes whether/how the user changes are persisted. Possible values are:
    * OnLocal - Persist the user changes on the local disk of the desktop.
    * Discard - Discard user changes.
    * OnPvd - Persist user changes on the Citrix Personal vDisk.

  * PowerActionPending (System.Boolean) Property indicating whether there are any pending power actions for the desktop.

  * PowerState (Citrix.Broker.Admin.SDK.PowerState) The current power state of the desktop. Possible values are: Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, resuming.

  * Protocol (System.String) Session property that denotes the protocol that the current session is using, can be either HDX, RDP or Console. Console sessions on XenDesktop 5 VDAs appear with a blank protocol. Session properties are always null for multi-session desktops.

  * ProvisioningType (Citrix.Broker.Admin.SDK.ProvisioningType) Describes how the machine associated with the desktop was provisioned, possible values are:
    * Manual: No automated provisioning.
    * PVS: Machine provisioned by PVS (may be physical, blade, VM,...)
    * MCS: Machine provisioned by MCS (machine must be VM)

  * PublishedApplications (System.String\[\]) List of applications published by the desktop (displayed as browser names).

  * PublishedName (System.String) The name of the desktop that is displayed in StoreFront, if the desktop is published.

  * PvdStage (Citrix.Broker.Admin.SDK.PvdStage) For a desktop supporting Personal vDisk technology (PvD), indicates the stage of the PvD image preparation.

  * RegistrationState (Citrix.Broker.Admin.SDK.RegistrationState) Indicates the registration state of the desktop. Possible values are: Unregistered, Initializing, Registered, AgentError.

  * SecureIcaActive (System.Boolean?) Session property that indicates whether SecureICA is active on the current session. Session properties are always null for multi-session desktops.

  * SecureIcaRequired (System.Boolean?) Flag indicating whether SecureICA is required or not when starting a session on the desktop.

  * SessionHidden (System.Boolean?) Session property that indicates if a session is hidden. Session properties are always null for multi-session desktops.

  * SessionId (System.Int32?) Deprecated. A unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine and only unique at any one particular time.

  * SessionState (Citrix.Broker.Admin.SDK.SessionState?) Session property indicating the state of the current session. Session properties are always null for multi-session desktops, possible values are: Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession and Unknown.

  * SessionStateChangeTime (System.DateTime?) Session property indicating the time of the last state change of the current session. Session properties are always null for multi-session desktops.

  * SessionUid (System.Int64?) Session property indicating the UID of the current session. Session properties are always null for multi-session desktops.

  * SessionUserName (System.String) Session property indicates the name of the current sessions' user (in the form DOMAIN\\user). Session properties are always null for multi-session desktops.

  * SessionUserSID (System.String) Session property indicates the SID of the current sessions' user. Session properties are always null for multi-session desktops.

  * SID (System.String) The SID of the desktop.

  * SmartAccessTags (System.String\[\]) Session property that indicates the Smart Access tags for the current session. Session properties are always null on multi-session desktops.

  * StartTime (System.DateTime?) Session property that indicates the start time of the current session. Session properties are always null on multi-session desktops.

  * SummaryState (Citrix.Broker.Admin.SDK.DesktopSummaryState) Indicates the overall state of the desktop. The overall state is a result of other more specific states such as session state, registration state and power state. Possible values: Off, Unregistered, Available, Disconnected, InUse, Preparing.

  * Tags (System.String\[\]) A list of tags for the desktop.

  * Uid (System.Int32) UID of the desktop object.

  * WillShutdownAfterUse (System.Boolean) Flag indicating whether this desktop is tainted and will be shut down after all sessions on the desktop have ended. This flag should only ever be true on power managed, single-session desktops. Note: The desktop will not shut down if it is in maintenance mode, but will shut down after the desktop is taken out of maintenance mode.


## Related Commands

* [Group-BrokerMachine](./Group-BrokerMachine/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets desktops with a specific UID. | true | false |  |
| MachineName | Gets desktops with a specific machine name (in the form 'domain\\machine'). | false | false |  |
| AgentVersion | Gets desktops with a specific Citrix Virtual Delivery Agent version. | false | false |  |
| ApplicationInUse | Gets desktops running a specified published application (identified by browser name).<br>String comparisons are case-insensitive. | false | false |  |
| AssignedClientName | Gets desktops assigned to a specific client name. | false | false |  |
| AssignedIPAddress | Gets desktops assigned to a specific client IP address. | false | false |  |
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
| Description | Gets desktops with a specific description. | false | false |  |
| DesktopCondition | Gets desktop with an outstanding desktop condition condition.<br>Valid values are:<br>o CPU: Indicates the machine has high CPU usage<br>o ICALatency: Indicates the network latency is high<br>o UPMLogonTime: Indicates that the profile load time was high | false | false |  |
| DesktopGroupName | Gets desktops from a desktop group with the specified name. | false | false |  |
| DesktopGroupUid | Gets desktops from a desktop group with the specified UID. | false | false |  |
| DesktopKind | Deprecated: Use AllocationType parameter.<br>Gets desktops of a particular kind.<br>Valid values are Private, Shared. | false | false |  |
| DeviceId | Gets desktops with a specific client device ID. | false | false |  |
| DNSName | Gets desktops with a specific DNS name. | false | false |  |
| FunctionalLevel | Gets desktops with a specific FunctionalLevel.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| HardwareId | Gets desktops with a specific client hardware ID. | false | false |  |
| HostedMachineId | Gets desktops with a specific machine ID known to the hypervisor. | false | false |  |
| HostedMachineName | Gets desktops with a specific machine name known to the hypervisor. | false | false |  |
| HostingServerName | Gets desktops with a specific name of the hosting hypervisor server. | false | false |  |
| HypervisorConnectionName | Gets desktops with a specific name of the hosting hypervisor connection. | false | false |  |
| HypervisorConnectionUid | Gets desktops with a specific UID of the hosting hypervisor connection. | false | false |  |
| IconUid | Gets desktops with a specific configured icon. Note that desktops with a null IconUid use the icon of the desktop group. | false | false |  |
| ImageOutOfDate | Gets desktops by whether their disk image is out of date (for machines provisioned using MCS only). | false | false |  |
| InMaintenanceMode | Gets desktops with a specific InMaintenanceMode setting. | false | false |  |
| IPAddress | Gets desktops with a specific IP address. | false | false |  |
| IsAssigned | Gets desktops according to whether they are assigned or not. Desktops may be assigned to one or more users or groups, a client IP address or a client endpoint name. | false | false |  |
| IsPhysical | Specifies if machines in the catalog can be power managed by the Citrix Broker Service. Where the power state of the machine cannot be controlled, specify \$true, otherwise \$false. Can only be specified together with a provisioning type of Pvs or Manual, or if used with the deprecated CatalogKind parameter only with Pvs or PvsPvd catalog kinds. | false | false |  |
| LastConnectionFailure | Gets desktops with a specific reason for the last recorded connection failure. This value is None if the last connection was successful or if there has been no attempt to connect to the desktop yet.<br>Valid values are None, SessionPreparation, RegistrationTimeout, ConnectionTimeout, Licensing, Ticketing, and Other. | false | false |  |
| LastConnectionTime | Gets desktops that last connected at a specific time. This is the time that the broker detected that the connection attempt either succeeded or failed. | false | false |  |
| LastConnectionUser | Gets desktops where a specific user name last attempted a connection (in the form 'domain\\user'). | false | false |  |
| LastDeregistrationReason | Gets desktops whose broker last recorded a specific deregistration reason.<br>Valid values are \$null, AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached. | false | false |  |
| LastDeregistrationTime | Gets desktops by the time that they were last deregistered. | false | false |  |
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
| ProvisioningType | Gets desktops that are in a catalog with a particular provisioning type. Values can be:<br>o Manual - No provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| PublishedApplication | Gets desktops with a specific application published to them. | false | false |  |
| PublishedName | Gets desktops with a specific published name. | false | false |  |
| PvdStage | Gets desktops with a specific personal vDisk stage.<br>Valid values are None, Requested, Starting, Working and Failed. | false | false |  |
| RegistrationState | Gets desktops with a specific registration state.<br>Valid values are Unregistered, Initializing, Registered and AgentError. | false | false |  |
| SecureIcaActive | Gets desktops depending on whether the current session uses SecureICA or not.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SecureIcaRequired | Gets desktops configured with a particular SecureIcaRequired setting. Note that the desktop setting of \$null indicates that the desktop group value is used.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionHidden | Gets desktops by whether their sessions are hidden or not. Hidden sessions are treated as though they do not exist when launching sessions; a hidden session cannot be reconnected to, but a new session may be launched using the same entitlement.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionId | Deprecated.<br>Gets desktops by session ID, a unique identifier that Remote Desktop Services uses to track the session but it is only unique on that machine. | false | false |  |
| SessionState | Gets desktops with a specific session state.<br>Valid values are \$null, Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionStateChangeTime | Gets desktops whose sessions last changed state at a specific time.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUid | Gets single-session desktops with a specific session UID (\$null for no session).<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUserName | Gets desktops with a specific user name for the current session (in the form 'domain\\user').<br>Session properties are always null for multi-session desktops. | false | false |  |
| SessionUserSID | Gets desktops with a specific SID of the current session user.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SID | Gets desktops with a specific machine SID. | false | false |  |
| SmartAccessTag | Gets session desktops where the session has the specific SmartAccess tag.<br>Session properties are always null for multi-session desktops. | false | false |  |
| StartTime | Gets desktops with a specific session start time.<br>Session properties are always null for multi-session desktops. | false | false |  |
| SummaryState | Gets desktops with a specific summary state.<br>Valid values are Off, Unregistered, Available, Disconnected, InUse and Preparing. | false | false |  |
| Tag | Gets desktops with a specific tag. | false | false |  |
| WillShutdownAfterUse | Gets desktops depending on whether they shut down after use or not. | false | false |  |
| ApplicationUid | Gets desktops with a specific published application (identified by its UID). | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Desktop
Get-BrokerDesktop returns an object for each matching desktop.
## Notes
To compare dates or times, use -Filter and relative comparisons. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktop -RegistrationState Unregistered

C:\PS> Get-BrokerDesktop -Filter { RegistrationState -ne 'Registered' }
```
#### Description
Both commands retrieve desktops that are unregistered. The second command also includes desktops with a registration state of AgentError.
### Example 2
```
C:\PS> Get-BrokerDesktop -SessionUid $null | ft -a DNSName,SummaryState
```
#### Description
Gets desktops without sessions, listing the DNS name and current state.
### Example 3
```
C:\PS> Get-BrokerDesktop -Filter { OSType -like "Windows XP\*" -and ImageOutOfDate }
```
#### Description
Finds all Windows XP desktops with an out-of-date image.
### Example 4
```
C:\PS> Get-BrokerDesktop -ApplicationInUse '\*powerpoint\*'
```
#### Description
Gets desktops running a published PowerPoint application. It matches any application browser name containing the word 'powerpoint'. String comparisons are case-insensitive.
### Example 5
```
C:\PS> Get-BrokerDesktop -DesktopCondition \* DNSName,SessionUserName,DesktopConditions
```
#### Description
Finds all desktops with an outstanding desktop condition, listing the affected desktop and user.
### Example 6
```
C:\PS> $d = (Get-Date).AddDays(-1)

C:\PS> Get-BrokerDesktop -Filter { StartTime -le $d } | ft MachineName,SessionUserName,StartTime,@{Label='Duration'; Expression={(Get-Date) - $_.StartTime}}
```
#### Description
Finds users who have been logged on for more than a day, and outputs the machine name, start time, and duration the session has been logged on.
