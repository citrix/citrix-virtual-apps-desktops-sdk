
# Get-Brokermachine
Gets machines belonging to this site.
## Syntax
```
Get-BrokerMachine [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerMachine [[-MachineName] <String>] [-AgentVersion <String>] [-AllocationType <AllocationType>] [-ApplicationInUse <String>] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-AssignedUserSID <String>] [-AssociatedTenantId <Guid>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserSID <String>] [-AssociatedUserUPN <String>] [-BrowserName <String>] [-CatalogName <String>] [-CatalogUid <Int32>] [-CatalogUUID <Guid>] [-CbpVersion <CBPVersion>] [-ColorDepth <ColorDepth>] [-ControllerDNSName <String>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopCondition <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-DesktopGroupUUID <Guid>] [-DesktopKind <DesktopKind>] [-DesktopUid <Int32>] [-DNSName <String>] [-DrainingUntilShutdown <Boolean>] [-FaultState <MachineFaultState>] [-FunctionalLevel <FunctionalLevel>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HostingServerName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-HypHypervisorConnectionUid <Guid>] [-IconUid <Int32>] [-ImageOutOfDate <Boolean>] [-InMaintenanceMode <Boolean>] [-IPAddress <String>] [-IsAssigned <Boolean>] [-IsPhysical <Boolean>] [-IsReserved <Boolean>] [-LastConnectionFailure <ConnectionFailureReason>] [-LastConnectionTime <DateTime>] [-LastConnectionUser <String>] [-LastDeregistrationReason <DeregistrationReason>] [-LastDeregistrationTime <DateTime>] [-LastErrorReason <String>] [-LastErrorTime <DateTime>] [-LastHostingUpdateTime <DateTime>] [-LastPvdErrorReason <String>] [-LastPvdErrorTime <DateTime>] [-LastRegistrationTime <DateTime>] [-LoadIndex <Int32>] [-MacAddress <String>] [-MachineInternalState <MachineInternalState>] [-MaintenanceModeReason <MaintenanceModeReason>] [-Metadata <String>] [-OSType <String>] [-OSVersion <String>] [-PersistUserChanges <PersistUserChanges>] [-PowerActionPending <Boolean>] [-PowerState <PowerState>] [-ProvisioningType <ProvisioningType>] [-PublishedApplication <String>] [-PublishedName <String>] [-PvdEstimatedCompletionTime <DateTime>] [-PvdPercentDone <Int32>] [-PvdStage <PvdStage>] [-PvdUpdateStartTime <DateTime>] [-RegistrationState <RegistrationState>] [-ScheduledReboot <ScheduledReboot>] [-SecureIcaRequired <Boolean>] [-SessionAutonomouslyBrokered <Boolean>] [-SessionClientAddress <String>] [-SessionClientName <String>] [-SessionClientVersion <String>] [-SessionConnectedViaHostName <String>] [-SessionConnectedViaIP <String>] [-SessionCount <Int32>] [-SessionDeviceId <String>] [-SessionHardwareId <String>] [-SessionHidden <Boolean>] [-SessionKey <Guid>] [-SessionLaunchedViaHostName <String>] [-SessionLaunchedViaIP <String>] [-SessionProtocol <String>] [-SessionSecureIcaActive <Boolean>] [-SessionsEstablished <Int32>] [-SessionSmartAccessTag <String>] [-SessionsPending <Int32>] [-SessionStartTime <DateTime>] [-SessionState <SessionState>] [-SessionStateChangeTime <DateTime>] [-SessionSupport <SessionSupport>] [-SessionType <SessionType>] [-SessionUid <Int64>] [-SessionUserName <String>] [-SessionUserSID <String>] [-SID <String>] [-SummaryState <DesktopSummaryState>] [-SupportedPowerActions <String[]>] [-Tag <String>] [-UUID <Guid>] [-VMToolsState <VMToolsState>] [-WillShutdownAfterUse <Boolean>] [-WillShutdownAfterUseReason <WillShutdownAfterUseReason>] [-WindowsConnectionSetting <WindowsConnectionSetting>] [-ZoneName <String>] [-ZoneUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves machines matching the specified criteria. If no parameters are specified, this cmdlet enumerates all machines.

Get-BrokerMachine returns objects that combine machine configuration and state information.

For single-session machines, session information is displayed if present. If "fast user switching" is enabled, more than one session may be present on single-session machines. Because this cmdlet returns information only for a single session, if two sessions are present it will return information about the brokered session (rather than, for example, an unbrokered direct RDP session). If there is no session running, session-related fields return \$null.

For multi-session machines, no session information about single sessions is displayed by this cmdlet, and so are always \$null. Get-BrokerSession can be used to get information about sessions on both multi-session and single-session machines.

To count machines, rather than retrieve full details of each machine, use Group-BrokerMachine instead.

See about\_Broker\_Filtering for information about advanced filtering options, and about\_Broker\_Machines for background information about machines.


### Brokermachine Object
The machine object returned represents a physical or virtual machine, which has been configured in the site.


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the machine.

  * AllocationType (Citrix.Broker.Admin.SDK.AllocationType) Describes how the machine is allocated to the user, can be Permanent or Random.

  * ApplicationsInUse (System.String\[\]) List of applications in use on the machine (in the form of browser name).

  * AssignedClientName (System.String) The name of the endpoint client device that the machine has been assigned to.

  * AssignedIPAddress (System.String) The IP address of the endpoint client device that the machine has been assigned to.

  * AssignedUserSIDs (System.String\[\]) The SIDs of the users that have been assigned to the machine (private machines only).

  * AssociatedTenantId (System.Guid?) Tenant associated with the machine. Once a tenant is associated with a machine it can only host sessions for that tenant and no other. Tenant associations are transient and are cleared when the machine's image is reset.

  * AssociatedUserFullNames (System.String\[\]) Full names of the users that have been associated with the machine (usually in the form "Firstname Lastname"). Associated users are the current user(s) for shared machines and the assigned users for private machines.

  * AssociatedUserNames (System.String\[\]) Usernames of the users that have been associated with the machine (in the form "domain\\user"). Associated users are the current user(s) for shared machines and the assigned users for private machines.

  * AssociatedUserSIDs (System.String\[\]) The SIDs of the users that have been associated with the machine. Associated users are the current user(s) for shared machines and the assigned users for private machines.

  * AssociatedUserUPNs (System.String\[\]) The User Principal Names of the users associated with the machine (in the form user@domain). Associated users are the current user(s) for shared machines and the assigned users for private machines.

  * BrowserName (System.String) Site-wide unique name identifying associated desktop to other components (for example StoreFront). This is typically non-null only for machines backing assigned private desktops.

  * Capabilities (System.String\[\]) List of the capabilities that the machine supports. Valid capabilities are:
    * MultiSession: Indicates an RDS- (Terminal Services-) based machine, which supports multiple active sessions from different users.
    * CBP1\_5: Indicates the machine can use the CBP 1.5 protocol for communication.

  * CatalogName (System.String) Name of the catalog the machine is a member of.

  * CatalogUid (System.Int32) UID of the catalog the machine is a member of.

  * CatalogUUID (System.Guid) UUID of the catalog the machine is a member of.

  * CbpVersion (Citrix.Broker.Admin.SDK.CBPVersion?) The version of CBP that the VDA is currently registered with. This will be null when the VDA is not registered.

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?) The color depth setting configured on the machine, possible values are: \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.

  * ControllerDNSName (System.String) The DNS host name of the controller that the machine is registered to.

  * DeliveryType (Citrix.Broker.Admin.SDK.DeliveryType?) Denotes whether the machine delivers desktops only, apps only or both.

  * Description (System.String) Description of the machine.

  * DesktopConditions (System.String\[\]) List of outstanding desktop conditions for the machine.

  * DesktopGroupName (System.String) Name of the desktop group the machine is a member of.

  * DesktopGroupUid (System.Int32?) UID of the desktop group the machine is a member of.

  * DesktopGroupUUID (System.Guid?) UUID of the desktop group the machine is a member of.

  * DesktopKind (Citrix.Broker.Admin.SDK.DesktopKind?) Deprecated. Denotes whether the machine is private or shared. Use AllocationType instead.

  * DesktopUid (System.Int32?) The UID of the associated desktop object.

  * DNSName (System.String) The DNS host name of the machine.

  * DrainingUntilShutdown (System.Boolean) Flag indicating if this machine is draining and will be shut down after all sessions on the machine have ended. This flag is only ever true on power-managed, multi-session machines. Note: The machine will not shut down if it is in maintenance mode; it will shut down only after it is taken out of maintenance mode.

  * FaultState (Citrix.Broker.Admin.SDK.MachineFaultState) Summary state of any current fault state of the machine. Can be one of the following:
    * None - No fault; machine is healthy.
    * FailedToStart - Last power-on operation for machine failed.
    * StuckOnBoot - Machine does not seem to have booted following power on.
    * Unregistered - Machine has failed to register within expected period, or its registration has been rejected.
    * MaxCapacity - Machine is reporting itself at maximum capacity.

  * FunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?) Functional level of the machine, if known.

  * HostedMachineId (System.String) Unique ID within the hosting unit of the target managed machine.

  * HostedMachineName (System.String) The friendly name of a hosted machine as used by its hypervisor. This is not necessarily the DNS name of the machine.

  * HostingServerName (System.String) DNS name of the hypervisor that is hosting the machine if managed.

  * HypervisorConnectionName (System.String) The name of the hypervisor connection that the machine has been assigned to, if managed.

  * HypervisorConnectionUid (System.Int32?) The UID of the hypervisor connection that the machine’s hosting server is accessed through.

  * HypHypervisorConnectionUid (System.Guid?) The UUID of the hypervisor connection that the machine’s hosting server is accessed through

  * IconUid (System.Int32?) The UID of the machine's icon that is displayed in StoreFront.

  * ImageOutOfDate (System.Boolean?) Denotes if the VM image for a hosted machine is out of date.

  * InMaintenanceMode (System.Boolean) Denotes if the machine is in maintenance mode.

  * IPAddress (System.String) The IP address of the machine.

  * IsAssigned (System.Boolean) Denotes whether a private desktop has been assigned to a user/users, or a client name/address. Users can be assigned explicitly or by assigning on first use of the machine.

  * IsPhysical (System.Boolean) This value is true if the machine is physical (ie not power managed by the Citrix Broker service, and false otherwise.

  * IsReserved (System.Boolean) Indicates if machine is reserved for special use, for example for AppDisk preparation. A reserved machine cannot be a member of a desktop group.

  * LastConnectionFailure (Citrix.Broker.Admin.SDK.ConnectionFailureReason) The reason for the last failed connection between a client and the machine.

  * LastConnectionTime (System.DateTime?) Time of the last detected connection attempt that either failed or succeeded.

  * LastConnectionUser (System.String) The SAM name (in the form DOMAIN\\user) of the user that last attempted a connection with the machine. If the SAM name is not available, the SID is used.

  * LastDeregistrationReason (Citrix.Broker.Admin.SDK.DeregistrationReason?) The reason for the last deregistration of the machine with the broker. Possible values are: AgentShutdown, AgentSuspended, AgentRequested, IncompatibleVersion, AgentAddressResolutionFailed, AgentNotContactable, AgentWrongActiveDirectoryOU, EmptyRegistrationRequest, MissingRegistrationCapabilities, MissingAgentVersion, InconsistentRegistrationCapabilities, NotLicensedForFeature, UnsupportedCredentialSecurityVersion, InvalidRegistrationRequest, SingleMultiSessionMismatch, FunctionalLevelTooLowForCatalog, FunctionalLevelTooLowForDesktopGroup, PowerOff, DesktopRestart, DesktopRemoved, AgentRejectedSettingsUpdate, SendSettingsFailure, SessionAuditFailure, SessionPrepareFailure, ContactLost, SettingsCreationFailure, UnknownError and BrokerRegistrationLimitReached.

  * LastDeregistrationTime (System.DateTime?) Time of the last deregistration of the machine from the controller.

  * LastErrorReason (System.String) The reason for the last error detected in the machine.

  * LastErrorTime (System.DateTime?) The time of the last detected error.

  * LastHostingUpdateTime (System.DateTime?) Time of last update to any hosting data (such as power states) for this machine reported by the hypervisor connection.

  * LastPvdErrorReason (System.String) The error text from the most recent failure of the Personal vDisk preparation process for this machine (if any).

  * LastPvdErrorTime (System.DateTime?) The time of the most recent failure of the Personal vDisk preparation process for this machine (if any).

  * LastRegistrationTime (System.DateTime?) Time of last registration of the machine with the controller.

  * LoadIndex (System.Int32?) Gives current effective load index for multi-session machines.

  * LoadIndexes (System.String\[\]) Gives the last reported individual load indexes that were used in the calculation of the LoadIndex value. Note that the LoadIndex value may have been subsequently adjusted due to session brokering operations. This value is only set for multi-session machines.

  * MacAddress (System.String) A string representing the physical address of the network interface corresponding to the IP Address this machine uses to communicate with the Broker.

  * MachineInternalState (Citrix.Broker.Admin.SDK.MachineInternalState) The internal state of the machine; reported while the machine is registered to a controller, plus some private Citrix Broker Service states while the machine is not registered.

  * MachineName (System.String) DNS host name of the machine.

  * MaintenanceModeReason (Citrix.Broker.Admin.SDK.MaintenanceModeReason) The reason why the machine was placed in maintenance mode (if it is in maintenance mode). Possible values are:

    * None - Machine is not in maintenance mode.
    * Administrator - Machine was manually placed in maintenance mode by an administrator.
    * MaxFailedRegistrations - Machine was automatically placed in maintenance mode due to reaching the maximum failed registration limit.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Any metadata that is associated with the machine.

  * OSType (System.String) A string that can be used to identify the operating system that is running on the machine.

  * OSVersion (System.String) A string that can be used to identify the version of the operating system running on the machine, if known.

  * PersistUserChanges (Citrix.Broker.Admin.SDK.PersistUserChanges) Describes if and how user changes are persisted. Possible values are:
    * OnLocal - Persist the user changes on the local disk of the machine.
    * Discard - Discard user changes.
    * OnPvd - Persist user changes on the Citrix Personal vDisk.

  * PowerActionPending (System.Boolean) Indicates if there are any pending power actions for the machine.

  * PowerState (Citrix.Broker.Admin.SDK.PowerState) The current power state of the machine. Possible values are: Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, resuming.

  * ProvisioningType (Citrix.Broker.Admin.SDK.ProvisioningType) Describes how the machine was provisioned, possible values are:
    * Manual: No automated provisioning.
    * PVS: Machine provisioned by PVS (may be physical, blade, VM,...)
    * MCS: Machine provisioned by MCS (machine must be VM)

  * PublishedApplications (System.String\[\]) List of applications published by the machine (displayed as browser names).

  * PublishedName (System.String) The name of the machine that is displayed in StoreFront, if the machine has been published.

  * PvdEstimatedCompletionTime (System.DateTime?) If preparation of the Personal vDisk is currently in progress for this machine, this reports an estimation of the time at which the process will be complete.

  * PvdPercentDone (System.Int32?) If preparation of the Personal vDisk is currently in progress for this machine, this reports how far the process has got as a percentage. This value will be zero if preparation is not in progress.

  * PvdStage (Citrix.Broker.Admin.SDK.PvdStage) For a machine supporting Personal vDisk technology (PvD), indicates the stage of the PvD image preparation.

  * PvdUpdateStartTime (System.DateTime?) If preparation of the Personal vDisk is currently in progress for this machine, this reports when the update process began.

  * RegistrationState (Citrix.Broker.Admin.SDK.RegistrationState) Indicates the registration state of the machine. Possible values are: Unregistered, Initializing, Registered, AgentError.

  * ScheduledReboot (Citrix.Broker.Admin.SDK.ScheduledReboot) Indicates the state of any scheduled reboot operation for a machine. Possible values:
    * None: No reboot is scheduled.
    * Pending: Machine is awaiting reboot but is available for use.
    * Draining: Machine is awaiting reboot and is unavailable for new sessions; reconnections to existing connections are still allowed, however.
    * InProgress: Machine is actively undergoing a scheduled reboot. o Natural: Natural reboot in progress. Machine is awaiting a restart.

  * SecureIcaRequired (System.Boolean?) Flag indicating whether SecureICA is required or not when starting a session on the machine.

  * SessionAutonomouslyBrokered (System.Boolean?) Session property indicating if the current session is an HDX session established by direct connection without being brokered. Session properties are always null for multi-session machines.

  * SessionClientAddress (System.String) Session property indicating the IP address of the client connected to the machine. Session properties are always null for multi-session machines.

  * SessionClientName (System.String) Session property indicating the host name of the client connected to the machine. Session properties are always null for multi-session machines.

  * SessionClientVersion (System.String) Session property indicating the version of the Citrix Receiver on the connected client. Session properties are always null for multi-session machines.

  * SessionConnectedViaHostName (System.String) Session property indicating the host name of the connection gateway, router or client. Session properties are always null for multi-session machines.

  * SessionConnectedViaIP (System.String) Session property indicating the IP address of the connection gateway, router or client. Session properties are always null for multi-session machines.

  * SessionCount (System.Int32) Count of number of sessions on the machine.

  * SessionDeviceId (System.String) Session property indicating a unique identifier for the client device that has most recently been associated with the current session. Session properties are always null for multi-session machines.

  * SessionHardwareId (System.String) Session property indicating a unique identifier for the client hardware that has been most recently associated with the current session. Session properties are always null for multi-session machines.

  * SessionHidden (System.Boolean?) Session property that indicates if a session is hidden. Session properties are always null for multi-session machines.

  * SessionKey (System.Guid?) Session property indicating the key of the current session. Session properties are always null for multi-session machines.

  * SessionLaunchedViaHostName (System.String) Session property that denotes the host name of the StoreFront server used to launch the current brokered session. Session properties are always null for multi-session machines.

  * SessionLaunchedViaIP (System.String) Session property that denotes the IP address of the StoreFront server used to launch the current brokered session. Session properties are always null for multi-session machines.

  * SessionProtocol (System.String) Session property that denotes the protocol that the current session is using, can be either HDX, RDP or Console. Console sessions on XenDesktop 5 VDAs appear with a blank protocol. Session properties are always null for multi-session machines.

  * SessionSecureIcaActive (System.Boolean?) Session property that indicates whether SecureICA is active on the current session or not. Session properties are always null for multi-session machines.

  * SessionsEstablished (System.Int32) Number of established sessions on this machine. For multi-session machines this excludes established sessions which have not yet completed their logon processing.

  * SessionSmartAccessTags (System.String\[\]) Session property that indicates the Smart Access tags for the current session. Session properties are always null on multi-session machines.

  * SessionsPending (System.Int32) Number of pending (brokered but not yet established) sessions on this machine. For multi-session machines this also includes established sessions which have not yet completed their logon processing.

  * SessionStartTime (System.DateTime?) Session property that indicates the start time of the current session. Session properties are always null on multi-session machines.

  * SessionState (Citrix.Broker.Admin.SDK.SessionState?) Session property indicating the state of the current session, possible values are: Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession and Unknown. Session properties are always null for multi-session machines.

  * SessionStateChangeTime (System.DateTime?) Session property indicating the time of the last state change of the current session. Session properties are always null for multi-session machines.

  * SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport) Indicates the session support of the machine. Possible values:
    * SingleSession: Single-session only machine.
    * MultiSession: Multi-session capable machine.

  * SessionType (Citrix.Broker.Admin.SDK.SessionType?) Session property indicating the type of the current session. Session properties are always null for multi-session machines.

  * SessionUid (System.Int64?) Session property indicating the UID of the current session. Session properties are always null for multi-session machines.

  * SessionUserName (System.String) Session property indicates the name of the current session's user (in the form DOMAIN\\user). Session properties are always null for multi-session machines.

  * SessionUserSID (System.String) Session property indicates the SID of the current session's user. Session properties are always null for multi-session machines.

  * SID (System.String) The SID of the machine.

  * SummaryState (Citrix.Broker.Admin.SDK.DesktopSummaryState) Indicates the overall state of the desktop associated with the machine. The overall state is a result of other more specific states such as session state, registration state and power state. Possible values: Off, Unregistered, Available, Disconnected, InUse, Preparing.

  * SupportedPowerActions (System.String\[\]) A list of power actions supported by this machine.

  * Tags (System.String\[\]) A list of tags associated with the machine.

  * Uid (System.Int32) UID of the machine object.

  * UUID (System.Guid) UUID of the machine object.

  * VMToolsState (Citrix.Broker.Admin.SDK.VMToolsState) State of the hypervisor tools present on the VM (if any). Possible values are: NotPresent, Unknown, NotStarted, Running.

  * WillShutdownAfterUse (System.Boolean) Flag indicating if this machine is tainted and will be shut down after all sessions on the machine have ended. This flag is only ever true on power-managed, single-session machines. Note: The machine will not shut down if it is in maintenance mode; it will shut down only after it is taken out of maintenance mode.

  * WillShutdownAfterUseReason (Citrix.Broker.Admin.SDK.WillShutdownAfterUseReason) The reason why the machine will shutdown after use (if it will shutdown after use). Possible values are:

    * None - Machine will not shutdown after use.
    * ResetDiskImage - Machine will shutdown after use to reset its disk image.
    * ScheduledNaturalReboot - Machine will shutdown after use as part of the scheduled natural reboot process.
    * OnDemandNaturalReboot - Machine will shutdown after use as part of an on-demand natural reboot process.

  * WindowsConnectionSetting (Citrix.Broker.Admin.SDK.WindowsConnectionSetting?) The logon mode reported by Windows itself (multi-session machines only). For single-session machines the value is always hardwired to LogonEnabled. Possible values are: LogonEnabled, Draining, DrainingUntilRestart and LogonDisabled.

  * ZoneName (System.String) The name of the zone in which the machine is located.

  * ZoneUid (System.Guid) The UID of the zone in which the machine is located.


## Related Commands

* [Group-BrokerMachine](./Group-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets a machine with a specific UID. | true | false |  |
| MachineName | Gets machines with a specific machine name (in the form domain\\machine). | false | false |  |
| AgentVersion | Gets machines with a specific Citrix Virtual Delivery Agent version. | false | false |  |
| AllocationType | Gets machines from catalogs with the specified allocation type. | false | false |  |
| ApplicationInUse | Gets machines running a specified published application (identified by browser name).<br>String comparisons are case-insensitive. | false | false |  |
| AssignedClientName | Gets machines that have been assigned to the specific client name. | false | false |  |
| AssignedIPAddress | Gets machines that have been assigned to the specific IP address. | false | false |  |
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
| ControllerDNSName | Gets machines with a specific DNS name of the controller they are registered with. | false | false |  |
| DeliveryType | Gets machines of a particular delivery type.<br>Valid values are AppsOnly, DesktopsOnly, DesktopsAndApps | false | false |  |
| Description | Gets machines with a specific description. | false | false |  |
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
| LastConnectionFailure | Gets machines with a specific reason for the last recorded connection failure. This value is None if the last connection was successful or if there has been no attempt to connect to the desktop yet.<br>Valid values are None, SessionPreparation, RegistrationTimeout, ConnectionTimeout, Licensing, Ticketing, and Other. | false | false |  |
| LastConnectionTime | Gets machines on which a user session connection occurred at a specific time. This is the time at which the broker detected that the connection attempt either succeeded or failed. | false | false |  |
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
| PersistUserChanges | Gets machines by the location where the user changes are persisted.<br>o OnLocal - User changes are persisted locally.<br>o Discard - User changes are discarded.<br>o OnPvd - User changes are persisted on the Pvd. | false | false |  |
| PowerActionPending | Gets machines depending on whether a power action is pending or not.<br>Valid values are \$true or \$false. | false | false |  |
| PowerState | Gets machines with a specific power state.<br>Valid values are Unmanaged, Unknown, Unavailable, Off, On, Suspended, TurningOn, TurningOff, Suspending, and Resuming. | false | false |  |
| ProvisioningType | Gets machines that are in a catalog with a particular provisioning type. Values can be:<br>o Manual - No provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | false | false |  |
| PublishedApplication | Gets machines with a specific application published to them (identified by its browser name). | false | false |  |
| PublishedName | Gets desktops with a specific published name. | false | false |  |
| PvdEstimatedCompletionTime | If preparation of the Personal vDisk is currently in progress for this machine, this reports an estimation of the time at which the process will be complete. | false | false |  |
| PvdPercentDone | Gets machines a specific percentage through the Personal vDisk preparation process.<br>This property is typically used with advanced filtering; see about\_Broker\_Filtering. | false | false |  |
| PvdStage | Gets machines at a specific personal vDisk stage.<br>Valid values are None, Requested, Starting, Working and Failed. | false | false |  |
| PvdUpdateStartTime | If preparation of the Personal vDisk is currently in progress for this machine, this reports when the update process began. | false | false |  |
| RegistrationState | Gets machines in a specific registration state.<br>Valid values are Unregistered, Initializing, Registered, and AgentError. | false | false |  |
| ScheduledReboot | Gets machines according to their current status with respect to any scheduled reboots (for either scheduled desktop group reboots or image rollout purposes). Valid values are:<br>o None - No reboot currently scheduled.<br>o Pending - Reboot scheduled but machine still available for use.<br>o Draining - Reboot scheduled. New logons are disabled, but reconnections to existing sessions are allowed.<br>o InProgress - Machine is actively being rebooted.<br>o Natural - Natural reboot in progress. Machine is awaiting a restart. | false | false |  |
| SecureIcaRequired | Gets machines configured with a particular SecureIcaRequired setting. Note that the machine setting of \$null indicates that the desktop group value is used. | false | false |  |
| SessionAutonomouslyBrokered | Gets machines according to whether their current session is autonomously brokered or not. Autonomously brokered sessions are HDX sessions established by direct connection without being brokered.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionClientAddress | Gets machines with a specific client IP address. | false | false |  |
| SessionClientName | Gets machines with a specific client name. | false | false |  |
| SessionClientVersion | Gets machines with a specific client version. | false | false |  |
| SessionConnectedViaHostName | Gets machines with a specific incoming connection host name. This is usually a proxy or Citrix Access Gateway server.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionConnectedViaIP | Gets machines with a specific incoming connection IP address.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionCount | Gets machines according to the total number of both pending and established user sessions on the machine. | false | false |  |
| SessionDeviceId | Gets machines with a specific client device ID. | false | false |  |
| SessionHardwareId | Gets machines with a specific client hardware ID. | false | false |  |
| SessionHidden | Gets machines depending on whether their sessions are hidden or not. Hidden sessions are treated as though they do not exist when launching sessions using XenDesktop; a hidden session cannot be reconnected to, but a new session may be launched using the same entitlement. | false | false |  |
| SessionKey | Gets machine running the session with a specified unique key.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionLaunchedViaHostName | Gets machines with a specific host name of the StoreFront server from which the user launched the session.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionLaunchedViaIP | Gets machines with a specific IP address of the StoreFront server from which the user launched the session.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionProtocol | Gets machines with connections using a specific protocol, for example HDX, RDP, or Console. | false | false |  |
| SessionSecureIcaActive | Gets machines depending on whether the current session uses SecureICA or not.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionsEstablished | Gets machines according to the number of established user sessions present on the machine. | false | false |  |
| SessionSmartAccessTag | Gets machines where the session has the specific SmartAccess tag.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionsPending | Get machines according to the number of pending user sessions for the machine. | false | false |  |
| SessionStartTime | Gets machines with a specific session start time.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionState | Gets machines with a specific session state.<br>Valid values are \$null, Other, PreparingSession, Connected, Active, Disconnected, Reconnecting, NonBrokeredSession, and Unknown.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionStateChangeTime | Gets machines whose sessions last changed state at a specific time.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionSupport | Gets machines that have the specified session capability. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession - Multi-session capable machine. | false | false |  |
| SessionType | Gets machines with a specific session state.<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUid | Gets machines with a specific session UID (\$null for no session).<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUserName | Gets machines with a specific user name for the current session (in the form 'domain\\user').<br>Session properties are always null for multi-session machines. | false | false |  |
| SessionUserSID | Gets machines with a specific SID of the current session user.<br>Session properties are always null for multi-session machines. | false | false |  |
| SID | Gets machines with a specific machine SID.<br>Session properties are always null for multi-session machines. | false | false |  |
| SummaryState | Gets machines with a specific summary state.<br>Valid values are Off, Unregistered, Available, Disconnected, and InUse. | false | false |  |
| SupportedPowerActions | A list of power actions supported by this machine. | false | false |  |
| Tag | Gets machines associated with the specified tag. | false | false |  |
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
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Machine
Get-BrokerMachine returns an object for each matching desktop.
## Notes
It is generally better to compare dates and times using -Filter and relative comparisons. See about\_Broker\_Filtering and the examples in this topic for more information.
## Examples

### Example 1
```
C:\PS> Get-BrokerMachine -PowerState Suspended

C:\PS> Get-BrokerMachine -Filter { PowerState -eq 'Suspended' }
```
#### Description
These commands return all suspended machines. The second form uses advanced filtering (see about\_Broker\_Filtering).
### Example 2
```
C:\PS> Get-BrokerMachine -DNSName '\*.mydomain.mycompany.com'
```
#### Description
This command returns all machines belonging to the DNS domain mydomain.mycompany.com.
### Example 3
```
C:\PS> Get-BrokerMachine -Filter { RegistrationState -eq 'Registered' -and HypervisorConnectionUid -eq 5 }
```
#### Description
This command returns all registered machines running on the specified hypervisor connection.
### Example 4
```
C:\PS> Get-BrokerMachine -MachineName 'MyDomain\X\*' | Remove-BrokerDesktopGroup 2
```
#### Description
This command finds all of the machines in MyDomain with names beginning with X and removes them from the specified desktop group.
### Example 5
```
C:\PS> Get-BrokerMachine -Filter { DesktopGroupUid -ne $null }
```
#### Description
This command gets all desktops in a site. Use this instead of the deprecated Get-BrokerDesktop command.
