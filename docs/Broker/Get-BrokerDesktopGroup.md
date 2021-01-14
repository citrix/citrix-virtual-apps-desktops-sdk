
# Get-Brokerdesktopgroup
Gets broker desktop groups configured for this site.
## Syntax
```
Get-BrokerDesktopGroup [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerDesktopGroup [[-Name] <String>] [-AppDisk <Guid>] [-AppDnaAnalysisState <AppDnaAnalysisState>] [-AppDnaCompatibility <AppDnaCompatibility>] [-AppProtectionKeyLoggingRequired <Boolean>] [-AppProtectionScreenCaptureRequired <Boolean>] [-AutomaticPowerOnForAssigned <Boolean>] [-AutomaticPowerOnForAssignedDuringPeak <Boolean>] [-AutoscaleLogOffWarningMessage <String>] [-AutoscaleLogOffWarningTitle <String>] [-AutoscaleMaxSecondsBeforeForcedLogOffDuringOffPeak <Int32>] [-AutoscaleMaxSecondsBeforeForcedLogOffDuringPeak <Int32>] [-AutoscalingEnabled <Boolean>] [-ColorDepth <ColorDepth>] [-DeliveryType <DeliveryType>] [-Description <String>] [-DesktopKind <DesktopKind>] [-Enabled <Boolean>] [-InMaintenanceMode <Boolean>] [-IsRemotePC <Boolean>] [-IsUsedByGpo <Boolean>] [-LicenseModel <LicenseModel>] [-MachineCost <Decimal>] [-MachineLogOnType <MachineLogOnType>] [-Metadata <String>] [-MinimumFunctionalLevel <FunctionalLevel>] [-OffPeakBufferSizePercent <Int32>] [-OffPeakDisconnectAction <SessionChangeHostingAction>] [-OffPeakDisconnectTimeout <Int32>] [-OffPeakExtendedDisconnectAction <SessionChangeHostingAction>] [-OffPeakExtendedDisconnectTimeout <Int32>] [-OffPeakLogOffAction <SessionChangeHostingAction>] [-OffPeakLogOffTimeout <Int32>] [-PeakBufferSizePercent <Int32>] [-PeakDisconnectAction <SessionChangeHostingAction>] [-PeakDisconnectTimeout <Int32>] [-PeakExtendedDisconnectAction <SessionChangeHostingAction>] [-PeakExtendedDisconnectTimeout <Int32>] [-PeakLogOffAction <SessionChangeHostingAction>] [-PeakLogOffTimeout <Int32>] [-PowerOffDelay <Int32>] [-ProductCode <String>] [-PublishedName <String>] [-RestrictAutoscaleTagUid <Int32>] [-ReuseMachinesWithoutShutdownInOutage <Boolean>] [-ScopeId <Guid>] [-ScopeName <String>] [-SecureIcaRequired <Boolean>] [-SessionSupport <SessionSupport>] [-SettlementPeriodBeforeAutoShutdown <TimeSpan>] [-SettlementPeriodBeforeUse <TimeSpan>] [-ShutdownDesktopsAfterUse <Boolean>] [-Tag <String>] [-TenantId <Guid>] [-TimeZone <String>] [-TotalApplicationGroups <Int32>] [-TotalApplications <Int32>] [-TurnOnAddedMachine <Boolean>] [-UUID <Guid>] [-ZonePreference <ZonePreference>] [-ApplicationGroupUid <Int32>] [-ApplicationUid <Int32>] [-TagUid <Int32>] [-PowerTimeSchemeUid <Int32>] [-MachineConfigurationUid <Int32>] [-RemotePCCatalogUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve desktop groups matching the specified criteria. If no parameters are specified this cmdlet enumerates all desktop groups.

Desktop groups represent groups of desktops that are managed together for brokering purposes.


### Brokerdesktopgroup Object
A desktop group object represents a collection of machines that are fully configured in a site that is able to run either a Microsoft Windows desktop environment, individual applications, or both.


  * AppDisks (System.Guid\[\]) The Application Disks used by machines in the desktop group.

  * AppDnaAnalysisState (Citrix.Broker.Admin.SDK.AppDnaAnalysisState?) Specifies the current state of AppDNA Analysis on the desktop group

  * AppDnaCompatibility (Citrix.Broker.Admin.SDK.AppDnaCompatibility?) The compatibility with the application disks attached to the desktop group

  * AppProtectionKeyLoggingRequired (System.Boolean) Specifies whether key logging app protection is required.

  * AppProtectionScreenCaptureRequired (System.Boolean) Specifies whether screen capture app protection is required.

  * AutomaticPowerOnForAssigned (System.Boolean) Specifies whether assigned desktops in the desktop group are automatically started at the start of peak time periods. Only relevant for groups whose DesktopKind is Private.

  * AutomaticPowerOnForAssignedDuringPeak (System.Boolean) Specifies whether assigned desktops in the desktop are automatically started throughout peak time periods. Only relevant for groups whose DesktopKind is Private and which have AutomaticPowerOnForAssigned set to true.

  * AutoscaleLogOffWarningMessage (System.String) Warning message to display to users in active sessions prior to Autoscale issuing a logoff request.

  * AutoscaleLogOffWarningTitle (System.String) Warning message dialog title displayed prior to Autoscale issuing a logoff request.

  * AutoscaleMaxSecondsBeforeForcedLogOffDuringOffPeak (System.Int32) Minimum time that needs to elapse before Autoscale logs off active sessions on a draining machine in the delivery group during off-peak time.

  * AutoscaleMaxSecondsBeforeForcedLogOffDuringPeak (System.Int32) Minimum time that needs to elapse before Autoscale logs off active sessions on a draining machine in the delivery group during peak time.

  * AutoscalingEnabled (System.Boolean) Specifies whether machines in this desktop group can be Autoscaled.

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth) Default color depth of sessions started with machines in the desktop group. Possible values are: FourBit, EightBit, SixteenBit, TwentyFourBit.

  * ConfigurationSlotUids (System.Int32\[\]) Uids of any configuration slots which hold machine configurations associated with the desktop group. The order of slot UIDs in this list correspond with the order of items in the associated MachineConfigurationNames and MachineConfigurationUids list properties, and so the same slot UID can appear more than once.

  * DeliveryType (Citrix.Broker.Admin.SDK.DeliveryType) The type of resources being published. Possible values are: DesktopsOnly, AppsOnly, DesktopsAndApps.

  * Description (System.String) Description of the desktop group.

  * DesktopKind (Citrix.Broker.Admin.SDK.DesktopKind) The kind of the desktops being published, possible values are: Private and Shared.

  * DesktopsAvailable (System.Int32) The number of machines in the desktop group in state Available; this is the number of machines with no sessions present.

  * DesktopsDisconnected (System.Int32) The number of disconnected sessions present on machines in the desktop group.

  * DesktopsFaulted (System.Int32) The number of machines in the desktop group whose FaultState is not None.

  * DesktopsInUse (System.Int32) The number of machines in the desktop group in state InUse; this is the number of machines with at least one session present.

  * DesktopsNeverRegistered (System.Int32) The number of machines in the desktop group that have never registered with the current site.

  * DesktopsPreparing (System.Int32) The number of machines in the desktop group whose PvD disk image is being prepared.

  * DesktopsUnregistered (System.Int32) The number of machines in the desktop group that are currently unregistered.

  * Enabled (System.Boolean) Specifies whether the desktop group is enabled or not; disabled desktop groups do not appear to users.

  * IconUid (System.Int32) The Uid of the icon to be used as a default for desktops in the desktop group. Individual desktop objects can override this default by setting the IconUid parameter on the desktop object.

  * InMaintenanceMode (System.Boolean) Specifies whether the machines in the desktop group are in maintenance mode or not.

  * IsRemotePC (System.Boolean) Specifies whether the desktop group is a Remote PC desktop group.

  * IsUsedByGpo (System.Boolean?) Indicate if the desktop group is used by group policy.

  * LicenseModel (Citrix.Broker.Admin.SDK.LicenseModel?) Specifies the license model for this desktop group. If none is specified, then the site-wide license model is used.

  * MachineConfigurationNames (System.String\[\]) The MachineConfiguration names associated with the desktop group.

  * MachineConfigurationUids (System.Int32\[\]) The MachineConfiguration uids associated with the desktop group.

  * MachineCost (System.Decimal) The per-hour instance cost of machines in this desktop group.

  * MachineLogOnType (Citrix.Broker.Admin.SDK.MachineLogOnType?) Specifies the login type (activedirectory/localmappedaccount) for machines in this desktop group.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata associated with the desktop group.

  * MinimumFunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel) The minimum FunctionalLevel required for the machines in the desktop group to be able to register with the Citrix Broker Service.

  * Name (System.String) Name of the desktop group.

  * OffPeakBufferSizePercent (System.Int32) The percentage of single-session machines that are kept available in an idle state, or for multi-session machines, the percentage of the total load capacity to be kept available outside peak hours.

  * OffPeakDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action that is performed after a configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend or Shutdown.

  * OffPeakDisconnectTimeout (System.Int32) The number of minutes before the configured action is performed after a user session disconnects outside peak hours.

  * OffPeakExtendedDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action performed after a second configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown.

  * OffPeakExtendedDisconnectTimeout (System.Int32) The number of minutes before the second configured action is performed after a user session disconnects outside peak hours.

  * OffPeakLogOffAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action performed after a configurable period of a user session ending outside peak hours. Possible values are Nothing, Suspend, or Shutdown.

  * OffPeakLogOffTimeout (System.Int32) The number of minutes before the configured action is performed after a user session ends outside peak hours.

  * PeakBufferSizePercent (System.Int32) The percentage of single-session machines that are kept available in an idle state, or for multi-session machines, the percentage of the total load capacity to be kept available in peak hours.

  * PeakDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action performed after a configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown.

  * PeakDisconnectTimeout (System.Int32) The number of minutes before the configured action is performed after a user session disconnects in peak hours.

  * PeakExtendedDisconnectAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action performed after a second configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown.

  * PeakExtendedDisconnectTimeout (System.Int32) The number of minutes before the second configured action is performed after a user session disconnects in peak hours.

  * PeakLogOffAction (Citrix.Broker.Admin.SDK.SessionChangeHostingAction) The action performed after a configurable period of a user session ending in peak hours. Possible values are Nothing, Suspend, or Shutdown.

  * PeakLogOffTimeout (System.Int32) The number of minutes before the configured action is performed after a user session ends in peak hours.

  * PowerOffDelay (System.Int32) The number of minutes following a power-on operation that Auto Scale will wait before attemping to power off that same machine. Possible values are in the range 0 - 60.

  * ProductCode (System.String) Specifies the licensing product code for this desktop group. If none is specified, then the site-wide product code is used.

  * ProtocolPriority (System.String\[\]) A list of protocol names in the order in which they are attempted for use during connection.

  * PublishedName (System.String) The name of the desktop group as it is to appear to the user in StoreFront.

  * RestrictAutoscaleTagUid (System.Int32?) If set to a Tag UID, only machines that have this tag will be auto scaled.

  * ReuseMachinesWithoutShutdownInOutage (System.Boolean) Specifies whether desktops should not be shut down after being used during outage mode.

  * Scopes (Citrix.Fma.Sdk.DelegatedAdminInterfaces.ScopeReference\[\]) The list of the delegated admin scopes to which the desktop group belongs.

  * SecureIcaRequired (System.Boolean) Flag that specifies if the SecureICA encryption of the HDX protocol is required for sessions of desktops in the desktop group.

  * Sessions (System.Int32) The total number of user sessions currently running on all of the machines in the desktop group.

  * SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport) Specifies the session support (single/multi) of the machines in the desktop group. Machines with the incorrect session support for the desktop group will be unable to register with the Citrix Broker Service.

  * SettlementPeriodBeforeAutoShutdown (System.TimeSpan) Time after a session ends during which automatic shutdown requests (for example, shutdown after use, idle pool management) are deferred. Any outstanding shutdown request takes effect after the settlement period expires. This is typically used to configure time to allow logoff scripts to complete.

  * SettlementPeriodBeforeUse (System.TimeSpan) Idle period before a machine can be selected to host a new session after registration or the end of a previous session. This is typically used to allow a machine to become idle following processing associated with start-up or logoff actions. A machine may still be selected during the idle period if no other machine is available for immediate use.

  * ShutdownDesktopsAfterUse (System.Boolean) Specifies if the desktops will shut down after they have been used and there are no sessions running on the machine. The machines will not shut down if they are placed into maintenance mode, even if this flag is set to \$true. The machines, however, will shutdown after the machine is taken out of maintenance mode if the flag is still set.

  * Tags (System.String\[\]) Tags associated with the desktop group.

  * TenantId (System.Guid?) Identity of tenant associated with desktop group. Not applicable (always blank) in non-multitenant sites.

  * TimeZone (System.String) The timezone that desktops in the desktop group are in (for power policy purposes).

  * TotalApplicationGroups (System.Int32) Total number of application groups associated with the desktop group.

  * TotalApplications (System.Int32) Total number of applications associated with the desktop group.

  * TotalDesktops (System.Int32) Total number of machines in the desktop group.

  * TurnOnAddedMachine (System.Boolean) Specifies whether the broker should attempt to turn on power-managed machines when they are added to the desktop group.

  * Uid (System.Int32) Uid of the desktop group.

  * UUID (System.Guid) UUID of the desktop group.

  * ZonePreferences (Citrix.Broker.Admin.SDK.ZonePreference\[\]) Ordered list of zone preferences taken into account when launching resources from this desktop group. Possible values for each preference are UserLocation, UserHome, UserHomeOnly and ApplilcationHome.


## Related Commands

* [New-BrokerDesktopGroup](./New-BrokerDesktopGroup/)
* [Set-BrokerDesktopGroup](./Set-BrokerDesktopGroup/)
* [Rename-BrokerDesktopGroup](./Rename-BrokerDesktopGroup/)
* [Remove-BrokerDesktopGroup](./Remove-BrokerDesktopGroup/)
* [Add-BrokerUser](./Add-BrokerUser/)
* [Add-BrokerTag](./Add-BrokerTag/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets desktop groups with the specified value of Uid. | true | false |  |
| Name | Gets desktop groups whose name matches the supplied pattern. | false | false |  |
| AppDisk | Gets only desktop groups using the specified application disk. | false | false |  |
| AppDnaAnalysisState | Gets only desktop groups with specified value of AppDnaAnalysisState | false | false |  |
| AppDnaCompatibility | Gets only desktop groups with specified value of AppDnaCompatibility | false | false |  |
| AppProtectionKeyLoggingRequired | Specifies whether key logging app protection is required. | false | false |  |
| AppProtectionScreenCaptureRequired | Specifies whether screen capture app protection is required. | false | false |  |
| AutomaticPowerOnForAssigned | Gets only desktop groups with the specified value of AutomaticPowerOnForAssigned. | false | false |  |
| AutomaticPowerOnForAssignedDuringPeak | Gets only desktop groups with the specified value of AutomaticPowerOnForAssignedDuringPeak. | false | false |  |
| AutoscaleLogOffWarningMessage | Gets the warning message to display to users in active sessions prior to Autoscale issuing a logoff request. | false | false |  |
| AutoscaleLogOffWarningTitle | Gets the warning message dialog title displayed prior to Autoscale issuing a logoff request. | false | false |  |
| AutoscaleMaxSecondsBeforeForcedLogOffDuringOffPeak | Gets the minimum seconds that need to elapse before Autoscale logs off the active sessions on the draining machines belonging to the delivery group during off-peak time. | false | false |  |
| AutoscaleMaxSecondsBeforeForcedLogOffDuringPeak | Gets the minimum seconds that need to elapse before Autoscale logs off the active sessions on the draining machines belonging to the delivery group during peak time. | false | false |  |
| AutoscalingEnabled | Specifies whether machines in this desktop group can be Autoscaled. | false | false |  |
| ColorDepth | Gets only desktop groups with the specified color depth.<br>Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| DeliveryType | Gets desktop groups according to their delivery type.<br>Valid values are DesktopsOnly, AppsOnly and DesktopsAndApps. | false | false |  |
| Description | Gets desktop groups whose description matches the supplied pattern. | false | false |  |
| DesktopKind | Gets desktops of a particular kind.<br>Valid values are Private and Shared. | false | false |  |
| Enabled | Gets desktop groups with the specified value of Enabled. | false | false |  |
| InMaintenanceMode | Gets desktop groups with the specified value of InMaintenanceMode. | false | false |  |
| IsRemotePC | Gets desktop groups with the specified IsRemotePC value. | false | false |  |
| IsUsedByGpo | Gets desktop groups that are used by group policy. | false | false |  |
| LicenseModel | Gets desktop groups with the specified license model. | false | false |  |
| MachineCost | The per-hour instance cost of machines in this desktop group. | false | false |  |
| MachineLogOnType | Gets desktop groups that have the specified login type. Values can be:<br>o ActiveDirectory - Perform Active Directory login on the machine.<br>o LocalMappedAccount  - Perform local mapped account login on the machine. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| MinimumFunctionalLevel | Gets desktop groups with a specific MinimumFunctionalLevel.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| OffPeakBufferSizePercent | Gets desktop groups with the specified value of OffPeakBufferSizePercent. | false | false |  |
| OffPeakDisconnectAction | Gets desktop groups with the specified value of OffPeakDisconnectAction. | false | false |  |
| OffPeakDisconnectTimeout | Gets desktop groups with the specified value of OffPeakDisconnectTimeout. | false | false |  |
| OffPeakExtendedDisconnectAction | Gets desktop groups with the specified value of OffPeakExtendedDisconnectAction. | false | false |  |
| OffPeakExtendedDisconnectTimeout | Gets desktop groups with the specified value of OffPeakExtendedDisconnectTimeout. | false | false |  |
| OffPeakLogOffAction | Gets desktop groups with the specified value of OffPeakLogOffAction. | false | false |  |
| OffPeakLogOffTimeout | Gets desktop groups with the specified value of OffPeakLogOffTimeout. | false | false |  |
| PeakBufferSizePercent | Gets desktop groups with the specified value of PeakBufferSizePercent. | false | false |  |
| PeakDisconnectAction | Gets desktop groups with the specified value of PeakDisconnectAction. | false | false |  |
| PeakDisconnectTimeout | Gets desktop groups with the specified value of PeakDisconnectTimeout. | false | false |  |
| PeakExtendedDisconnectAction | Gets desktop groups with the specified value of PeakExtendedDisconnectAction. | false | false |  |
| PeakExtendedDisconnectTimeout | Gets desktop groups with the specified value of PeakExtendedDisconnectTimeout. | false | false |  |
| PeakLogOffAction | Gets desktop groups with the specified value of PeakLogOffAction. | false | false |  |
| PeakLogOffTimeout | Gets desktop groups with the specified value of PeakLogOffTimeout. | false | false |  |
| PowerOffDelay | The number of minutes following a power-on operation that Auto Scale will wait before attemping to power off that same machine. Possible values are in the range 0 - 60. | false | false |  |
| ProductCode | Gets desktop groups with the specified licensing product code. | false | false |  |
| PublishedName | Gets desktop groups whose published name matches the supplied pattern. | false | false |  |
| RestrictAutoscaleTagUid | If set to a Tag UID, only machines that have this tag will be auto scaled. | false | false |  |
| ReuseMachinesWithoutShutdownInOutage | Gets only desktop groups that won't shut down machines after they been used during outage. | false | false |  |
| ScopeId | Gets desktop groups that are associated with the given scope identifier. | false | false |  |
| ScopeName | Gets desktop groups that are associated with the given scope name. | false | false |  |
| SecureIcaRequired | Gets desktop groups with the specified value of SecureIcaRequired. | false | false |  |
| SessionSupport | Gets desktop groups that have the specified session capability. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | false | false |  |
| SettlementPeriodBeforeAutoShutdown | Gets desktop groups with the specified value of SettlementPeriodBeforeAutoShutdown. | false | false |  |
| SettlementPeriodBeforeUse | Gets desktop groups with the specified value of SettlementPeriodBeforeUse. | false | false |  |
| ShutdownDesktopsAfterUse | Gets desktop groups with the specified value of ShutdownDesktopsAfterUse. | false | false |  |
| Tag | Gets desktop groups tagged with the specified tag. | false | false |  |
| TenantId | Gets desktop groups associated with the specified tenant identity. | false | false |  |
| TimeZone | Gets desktop groups with the specified value of TimeZone. | false | false |  |
| TotalApplicationGroups | Gets desktop groups that are acting as delivery groups for the specified number of application groups. | false | false |  |
| TotalApplications | Gets desktop groups that are acting as delivery groups for the specified number of applications. | false | false |  |
| TurnOnAddedMachine | Gets desktop groups with the specified value of TurnOnAddedMachine value. | false | false |  |
| UUID | Gets desktop groups with the specified value of UUID. | false | false |  |
| ZonePreference | Gets desktop groups with a zone preference list containing the specified zone preference. | false | false |  |
| ApplicationGroupUid | Gets only desktop groups with which the specified application group has been associated. | false | false |  |
| ApplicationUid | Gets desktop groups that publish the specified application (identified by Uid) | false | false |  |
| TagUid | Gets desktop groups to which the specified tag (identified by its Uid) has been added to help identify it - see Add-BrokerTag for more information. | false | false |  |
| PowerTimeSchemeUid | Gets desktop groups associated with the specified power time scheme (identified by its Uid). | false | false |  |
| MachineConfigurationUid | Gets desktop groups with the specified value of MachineConfiguration. | false | false |  |
| RemotePCCatalogUid | Gets Remote PC desktop groups associated with the specified catalog. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Desktopgroup
Get-BrokerDesktopGroup returns an object for each matching desktop group.
## Notes
To perform greater-than or less-than comparisons, use -Filter. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroup -PublishedName EMEA\*
```
#### Description
Finds all desktop groups with published names starting with "EMEA".
### Example 2
```
C:\PS> Get-BrokerDesktopGroup -InMaintenanceMode $true
```
#### Description
Finds all desktop groups in maintenance mode.
