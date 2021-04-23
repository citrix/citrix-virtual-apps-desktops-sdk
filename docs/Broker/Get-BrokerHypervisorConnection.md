
# Get-Brokerhypervisorconnection
Gets hypervisor connections matching the specified criteria.
## Syntax
```
Get-BrokerHypervisorConnection [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerHypervisorConnection [[-Name] <String>] [-ExplicitPreferredController <Boolean>] [-ExtraSpinUpTimeSecs <Int32>] [-HypHypervisorConnectionUid <Guid>] [-HypHypervisorType <String>] [-IsReady <Boolean>] [-MachineCount <Int32>] [-MaxAbsoluteActiveActions <Int32>] [-MaxAbsoluteNewActionsPerMinute <Int32>] [-MaxAbsolutePvdPowerActions <Int32>] [-MaxPercentageActiveActions <Int32>] [-MaxPvdPowerActionsPercentageOfDesktops <Int32>] [-Metadata <String>] [-PreferredController <String>] [-State <HypervisorConnectionState>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerHypervisorConnection cmdlet gets hypervisor connections matching the specified criteria. If no parameters are specified this cmdlet enumerates all hypervisor connections.


### Brokerhypervisorconnection Object
The BrokerHypervisorConnection represents hypervisor connection object. It contains the following properties:


  * Capabilities (System.String\[\]) The set of capabilities as reported by the hypervisor.

  * ExplicitPreferredController (System.Boolean?) Whether the PreferredController property was explicity set through the SDK or automatically chosen.

  * ExtraSpinUpTimeSecs (System.Int32?) The extra time a VM is allowed to start before it is marked as failed on session launch

  * HypHypervisorConnectionUid (System.Guid) The Guid that identifies the hypervisor connection.

  * HypHypervisorType (System.String) The type of hypervisor connected to.

  * IsReady (System.Boolean) Indicates that the connection is ready to be used in the configuration of managed machines.

  * MachineCount (System.Int32) Count of machines associated with this hypervisor connection.

  * MaxAbsoluteActiveActions (System.Int32?) Maximum number of active power actions allowed at any one time (defined in the metadata named 'Citrix\_Broker\_MaxAbsoluteActiveActions' on the hypervisor connection in the Citrix Hosting Service).

  * MaxAbsoluteNewActionsPerMinute (System.Int32?) Maximum number of new actions that can be fired off to the hypervisor in any one minute (defined in the metadata named 'Citrix\_Broker\_MaxAbsoluteNewActionsPerMinute' on the hypervisor connection in the Citrix Hosting Service).

  * MaxAbsolutePvdPowerActions (System.Int32?) Maximum number of active PvD power actions allowed at any one time (defined in the metadata named 'Citrix\_Broker\_MaxAbsolutePvdPowerActions' on the hypervisor connection in the Citrix Hosting Service).

  * MaxPercentageActiveActions (System.Int32?) Maximum percentage of machines on the connection that can have active power actions at any one time (defined in the metadata named 'Citrix\_Broker\_MaxPowerActionsPercentageOfDesktops' on the hypervisor connection in the Citrix Hosting Service).

  * MaxPvdPowerActionsPercentageOfDesktops (System.Int32?) Maximum percentage of machines on the connection that can be in personal VDisk image preparation mode at any one time (defined in the metadata named 'Citrix\_Broker\_MaxPvdPowerActionsPercentageOfDesktops' on the hypervisor connection in the Citrix Hosting Service).

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Collection of all the metadata associated to the hypervisor connection.

  * Name (System.String) The display name of the hypervisor connection.

  * PreferredController (System.String) The name of the controller which is preferred to be used, when available, to perform all communication to the hypervisor. The name is in DOMAIN\\machine form. A preferred controller may have been automatically chosen when the hypervisor connection was created.

  * State (Citrix.Broker.Admin.SDK.HypervisorConnectionState) The state of the hypervisor connection.

  * Uid (System.Int32) Unique internal identifier of hypervisor connection.


## Related Commands

* [New-BrokerHypervisorConnection](./New-BrokerHypervisorConnection/)
* [Remove-BrokerHypervisorConnection](./Remove-BrokerHypervisorConnection/)
* [Set-BrokerHypervisorConnection](./Set-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the hypervisor connection with the specified internal id. | true | false |  |
| Name | Gets hypervisor connections with the specified name. | false | false |  |
| ExplicitPreferredController | Gets hypervisor connections based on whether their preferred controller was explicitly specified or not | false | false |  |
| ExtraSpinUpTimeSecs | Gets the extra time a VM is allowed to start before it is marked as failed on session launch | false | false |  |
| HypHypervisorConnectionUid | Gets hypervisor connections with the specified Guid. | false | false |  |
| HypHypervisorType | Gets hypervisor connections with the specified value of the hypervisor type. | false | false |  |
| IsReady | Gets hypervisor connections with the specified value of the IsReady flag. | false | false |  |
| MachineCount | Gets hypervisor connections with the specified machine count. | false | false |  |
| MaxAbsoluteActiveActions | Gets hypervisor connections with the specified MaxAbsoluteActiveActions value. | false | false |  |
| MaxAbsoluteNewActionsPerMinute | Gets hypervisor connections with the specified MaxAbsoluteNewActionsPerMinute value. | false | false |  |
| MaxAbsolutePvdPowerActions | Gets hypervisor connections with the specified MaxAbsolutePvdPowerActions value. | false | false |  |
| MaxPercentageActiveActions | Gets hypervisor connections with the specified MaxPercentageActiveActions value. | false | false |  |
| MaxPvdPowerActionsPercentageOfDesktops | Gets hypervisor connections with the specified MaxPvdPowerActionsPercentageOfDesktops value. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| PreferredController | Gets hypervisor connections with the specified preferred controller. Specify the SAM name of the controller. | false | false |  |
| State | Gets hypervisor connections with the specified connection state. Values can be can be:<br>o Unavailable - The broker is unable to contact the hypervisor.<br>o InMaintenanceMode - The hosting server is in maintenance mode.<br>o On - The broker is in contact with the hypervisor. | false | false |  |
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

## Return Values

### Citrix.Broker.Admin.Sdk.Hypervisorconnection
Get-BrokerHypervisorConnection returns an object for each matching hypervisor connection.
## Examples

### Example 1
```
c:\PS> $hvConn = Get-BrokerHypervisorConnection -Name "hvConnectionName"
```
#### Description
Gets a hypervisor connection by name.
### Example 2
```
c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "domainName\controllerName"
```
#### Description
Gets hypervisor connections by preferred controller.
### Example 3
```
c:\PS> $machine = Get-BrokerMachine -Uid $machineUid

c:\PS> $hvConn = Get-BrokerHypervisorConnection -Uid $machine.HypervisorConnectionUid
```
#### Description
Gets hypervisor connection used by a (power managed) machine.
