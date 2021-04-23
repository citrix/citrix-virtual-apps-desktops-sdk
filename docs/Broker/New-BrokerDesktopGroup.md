
# New-Brokerdesktopgroup
Create a new desktop group for managing the brokering of groups of desktops.
## Syntax
```
New-BrokerDesktopGroup [-Name] <String> -DesktopKind <DesktopKind> [-AppDisks <Guid[]>] [-AppProtectionKeyLoggingRequired <Boolean>] [-AppProtectionScreenCaptureRequired <Boolean>] [-AutomaticPowerOnForAssigned <Boolean>] [-AutomaticPowerOnForAssignedDuringPeak <Boolean>] [-AutoscaleLogOffWarningMessage <String>] [-AutoscaleLogOffWarningTitle <String>] [-AutoscaleMaxSecondsBeforeForcedLogOffDuringOffPeak <Int32>] [-AutoscaleMaxSecondsBeforeForcedLogOffDuringPeak <Int32>] [-AutoscalingEnabled <Boolean>] [-ColorDepth <ColorDepth>] [-DeliveryType <DeliveryType>] [-Description <String>] [-Enabled <Boolean>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsRemotePC <Boolean>] [-LicenseModel <LicenseModel>] [-MachineCost <Decimal>] [-MachineLogOnType <MachineLogOnType>] [-MinimumFunctionalLevel <FunctionalLevel>] [-OffPeakBufferSizePercent <Int32>] [-OffPeakDisconnectAction <SessionChangeHostingAction>] [-OffPeakDisconnectTimeout <Int32>] [-OffPeakExtendedDisconnectAction <SessionChangeHostingAction>] [-OffPeakExtendedDisconnectTimeout <Int32>] [-OffPeakLogOffAction <SessionChangeHostingAction>] [-OffPeakLogOffTimeout <Int32>] [-PeakBufferSizePercent <Int32>] [-PeakDisconnectAction <SessionChangeHostingAction>] [-PeakDisconnectTimeout <Int32>] [-PeakExtendedDisconnectAction <SessionChangeHostingAction>] [-PeakExtendedDisconnectTimeout <Int32>] [-PeakLogOffAction <SessionChangeHostingAction>] [-PeakLogOffTimeout <Int32>] [-PowerOffDelay <Int32>] [-ProductCode <String>] [-ProtocolPriority <String[]>] [-PublishedName <String>] [-RestrictAutoscaleTagUid <Int32>] [-ReuseMachinesWithoutShutdownInOutage <Boolean>] [-Scope <String[]>] [-SecureIcaRequired <Boolean>] [-SessionSupport <SessionSupport>] [-SettlementPeriodBeforeAutoShutdown <TimeSpan>] [-SettlementPeriodBeforeUse <TimeSpan>] [-ShutdownDesktopsAfterUse <Boolean>] [-TenantId <Guid>] [-TimeZone <String>] [-TurnOnAddedMachine <Boolean>] [-UUID <Guid>] [-ZonePreferences <ZonePreference[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerDesktopGroup cmdlet creates a new broker desktop group that can then be used to manage the brokering settings of all desktops within that desktop group. Once the desktop group has been created, you can create desktops in it by adding the appropriate broker machines to it using the Add-BrokerMachine or Add-BrokerMachinesToDesktopGroup cmdlets.

Desktop groups hold settings that apply to all desktops they contain.

For any automatic power management settings of a desktop group to take effect, the group's TimeZone property must be specified. Automatic power management operations include pool management (power time schemes), reboot schedules, session disconnect and logoff actions, and powering on assigned machines etc.


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
* [Set-BrokerDesktopGroup](./Set-BrokerDesktopGroup/)
* [Rename-BrokerDesktopGroup](./Rename-BrokerDesktopGroup/)
* [Remove-BrokerDesktopGroup](./Remove-BrokerDesktopGroup/)
* [Add-BrokerMachine](./Add-BrokerMachine/)
* [Add-BrokerMachinesToDesktopGroup](./Add-BrokerMachinesToDesktopGroup/)
* [Get-BrokerSite](./Get-BrokerSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The name of the new broker desktop group. | true | true (ByPropertyName) |  |
| DesktopKind | The kind of desktops this group will hold. Valid values are Private and Shared. | true | true (ByPropertyName) |  |
| AppDisks | Specifies the application disks to be used by machines in the desktop group. | false | true (ByPropertyName) | None |
| AppProtectionKeyLoggingRequired | Specifies whether key logging app protection is required. | false | true (ByPropertyName) |  |
| AppProtectionScreenCaptureRequired | Specifies whether screen capture app protection is required. | false | true (ByPropertyName) |  |
| AutomaticPowerOnForAssigned | Specifies whether assigned desktops in the desktop group should be automatically started at the start of peak time periods. Only relevant for groups whose DesktopKind is Private. | false | true (ByPropertyName) | true |
| AutomaticPowerOnForAssignedDuringPeak | Specifies whether assigned desktops in the desktop group should be automatically started throughout peak time periods. Only relevant for groups whose DesktopKind is Private and which have AutomaticPowerOnForAssigned set to true. | false | true (ByPropertyName) | false |
| AutoscaleLogOffWarningMessage | Specifies the warning message to display to users in active sessions prior to Autoscale issuing a logoff request. | false | true (ByPropertyName) |  |
| AutoscaleLogOffWarningTitle | Specifies the warning message dialog title displayed prior to Autoscale issuing a logoff request. | false | true (ByPropertyName) |  |
| AutoscaleMaxSecondsBeforeForcedLogOffDuringOffPeak | Specifies the minimum seconds that need to elapse before Autoscale logs off the active sessions on the draining machines belonging to the delivery group during off-peak time. | false | true (ByPropertyName) | 0 |
| AutoscaleMaxSecondsBeforeForcedLogOffDuringPeak | Specifies the minimum seconds that need to elapse before Autoscale logs off the active sessions on the draining machines belonging to the delivery group during peak time. | false | true (ByPropertyName) | 0 |
| AutoscalingEnabled | Specifies whether machines in this desktop group can be Autoscaled. | false | true (ByPropertyName) |  |
| ColorDepth | Specifies the color depth that the ICA session should use for desktops in this group.  Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | true (ByPropertyName) | TwentyFourBit |
| DeliveryType | Specifies whether desktops, applications, or both, can be delivered from machines contained within the new desktop group. Desktop groups with a DesktopKind of Private cannot be used to deliver both desktops and applications. Defaults to DesktopsOnly if not specified.<br>Valid values are DesktopsOnly, AppsOnly, and DesktopsAndApps. | false | true (ByPropertyName) | DesktopsOnly |
| Description | A description for this desktop group useful for administrators of the site. | false | true (ByPropertyName) | null |
| Enabled | Whether the desktop group should be in the enabled state; disabled desktop groups do not appear to users. | false | true (ByPropertyName) | true |
| IconUid | The UID of the broker icon to be displayed to users for their desktop(s) in this desktop group. | false | true (ByPropertyName) | The Uid of the default desktop icon in this site - use the Get-BrokerSite cmdlet to find this value. |
| InMaintenanceMode | Whether the desktop should be created in maintenance mode; a desktop group in maintenance mode will not allow users to connect or reconnect to their desktops. | false | true (ByPropertyName) | false |
| IsRemotePC | Specifies whether this is to be a Remote PC desktop group.<br>IsRemotePC can only be enabled when:<br>o SessionSupport is SingleSession<br>o DeliveryType is DesktopsOnly<br>o DesktopKind is Private | false | true (ByPropertyName) | false |
| LicenseModel | The license model for this desktop group. If none is specified, then the site-wide license model is used. | false | true (ByPropertyName) | null |
| MachineCost | The per-hour instance cost of machines in this desktop group. | false | true (ByPropertyName) |  |
| MachineLogOnType | Specifies the login type for the desktop group. Values can be:<br>o ActiveDirectory - Perform Active Directory login on the machine.<br>o LocalMappedAccount  - Perform local mapped account login on the machine. | false | true (ByPropertyName) |  |
| MinimumFunctionalLevel | The minimum FunctionalLevel required for machines to work successfully in the desktop group.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | true (ByPropertyName) | The FunctionalLevel of the current release (L7\_6); by default no machines with less than the most current FunctionalLevel will be functional. |
| OffPeakBufferSizePercent | The percentage of single-session machines that are kept available in an idle state, or for multi-session machines, the percentage of the total load capacity to be kept available outside peak hours. | false | true (ByPropertyName) | 0 |
| OffPeakDisconnectAction | The action to be performed after a configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown | false | true (ByPropertyName) | Nothing |
| OffPeakDisconnectTimeout | The number of minutes before the configured action should be performed after a user session disconnects outside peak hours. | false | true (ByPropertyName) | 0 |
| OffPeakExtendedDisconnectAction | The action to be performed after a second configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | true (ByPropertyName) | Nothing |
| OffPeakExtendedDisconnectTimeout | The number of minutes before the second configured action should be performed after a user session disconnects outside peak hours. | false | true (ByPropertyName) | 0 |
| OffPeakLogOffAction | The action to be performed after a configurable period of a user session ending outside peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | true (ByPropertyName) | Nothing |
| OffPeakLogOffTimeout | The number of minutes before the configured action should be performed after a user session ends outside peak hours. | false | true (ByPropertyName) | 0 |
| PeakBufferSizePercent | The percentage of single-session machines that are kept available in an idle state, or for multi-session machines, the percentage of the total load capacity to be kept available in peak hours. | false | true (ByPropertyName) | 0 |
| PeakDisconnectAction | The action to be performed after a configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | true (ByPropertyName) | Nothing |
| PeakDisconnectTimeout | The number of minutes before the configured action should be performed after a user session disconnects in peak hours. | false | true (ByPropertyName) | 0 |
| PeakExtendedDisconnectAction | The action to be performed after a second configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | true (ByPropertyName) | Nothing |
| PeakExtendedDisconnectTimeout | The number of minutes before the second configured action should be performed after a user session disconnects in peak hours. | false | true (ByPropertyName) | 0 |
| PeakLogOffAction | The action to be performed after a configurable period of a user session ending in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | true (ByPropertyName) | Nothing |
| PeakLogOffTimeout | The number of minutes before the configured action should be performed after a user session ends in peak hours. | false | true (ByPropertyName) | 0 |
| PowerOffDelay | The number of minutes following a power-on operation that Auto Scale will wait before attemping to power off that same machine. Possible values in the range 0 - 60. | false | true (ByPropertyName) | 30 |
| ProductCode | The licensing product code for this desktop group. If none is specified, then the site-wide product code is used. | false | true (ByPropertyName) | null |
| ProtocolPriority | A list of protocol names in the order in which they should be attempted for use during connection. | false | true (ByPropertyName) | null |
| PublishedName | The name that will be displayed to users for their desktop(s) in this desktop group. | false | true (ByPropertyName) | The same value as that supplied for the name of the desktop group. |
| RestrictAutoscaleTagUid | If set to a Tag UID, only machines that have this tag will be auto scaled. | false | true (ByPropertyName) |  |
| ReuseMachinesWithoutShutdownInOutage | Specifies whether power cycle operations are required during outage for pooled machines. | false | true (ByPropertyName) | false |
| Scope | Specifies the name of the delegated administration scope to which the desktop group should belong. | false | true (ByPropertyName) |  |
| SecureIcaRequired | Whether HDX connections to desktops in the new desktop group require the use of a secure protocol. | false | true (ByPropertyName) | false |
| SessionSupport | Specifies whether machines in the desktop group are single or multi-session capable. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | false | true (ByPropertyName) |  |
| SettlementPeriodBeforeAutoShutdown | Time after a session ends during which automatic shutdown requests (for example, shutdown after use, idle pool management) are deferred. Any outstanding shutdown request takes effect after the settlement period expires. This is typically used to configure time to allow logoff scripts to complete. | false | true (ByPropertyName) | 0 |
| SettlementPeriodBeforeUse | Idle period before a machine can be selected to host a new session after registration or the end of a previous session. This is typically used to allow a machine to become idle following processing associated with start-up or logoff actions. A machine may still be selected during the idle period if no other machine is available for immediate use. | false | true (ByPropertyName) | 0 |
| ShutdownDesktopsAfterUse | Whether desktops in this desktop group should be automatically shut down when each user session completes (only relevant to power-managed desktops). | false | true (ByPropertyName) | false |
| TenantId | Specifies identity of tenant associated with desktop group. Must always be specified in multitenant sites, must not be specified otherwise. | false | true (ByPropertyName) |  |
| TimeZone | The time zone in which this desktop group's machines reside.<br>The time zone must be specified for any of the group's automatic power management settings to take effect. Automatic power management operations include pool management (power time schemes), reboot schedules, session disconnect and logoff actions, and powering on assigned machines etc. | false | true (ByPropertyName) | null |
| TurnOnAddedMachine | This flag specifies whether the Broker Service should attempt to power on machines when they are added to the desktop group. | false | true (ByPropertyName) | \$false for single session machines and \$true for multi-session machines. |
| UUID | An optional GUID for this desktop group. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| ZonePreferences | Ordered list of zone preferences to be applied when launching resources from this desktop group. Valid zone preference values are UserLocation, UserHome, UserHomeOnly and ApplicationHome.<br>The list can have zero or more entries subject to the following restrictions: Zone preferences can only be applied to groups having a DesktopKind of Shared; the same zone preference value cannot occur in the list more than once; the UserHome and UserHomeOnly values are mutually exclusive and cannot both appear in the list. | false | true (ByPropertyName) | For shared groups the default preference list is ApplicationHome, UserHome, then UserLocation. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Desktopgroup
The newly created desktop group.
## Notes
Once a new desktop group is created, you can create desktops in it by adding the appropriate broker machines to it using the Add-BrokerMachine or Add-BrokerMachinesToDesktopGroup cmdlets.
## Examples

### Example 1
```
C:\PS> New-BrokerDesktopGroup "Assigned Desktops" -PublishedName "MyDesktop" -DesktopKind Private
```
#### Description
Create a desktop group to manage the brokering of private desktops, which will appear to users with the name "MyDesktop".
