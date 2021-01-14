
# Get-Brokerhostingpoweraction
Gets power actions queued for machines.
## Syntax
```
Get-BrokerHostingPowerAction [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerHostingPowerAction [[-MachineName] <String>] [-Action <PowerManagementAction>] [-ActionCompletionTime <DateTime>] [-ActionStartTime <DateTime>] [-ActualPriority <Int32>] [-BasePriority <Int32>] [-DNSName <String>] [-FailureReason <String>] [-HostedMachineId <String>] [-HostedMachineName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-HypHypervisorConnectionUid <Guid>] [-Metadata <String>] [-Origin <PowerActionPriority>] [-RequestTime <DateTime>] [-Sid <String>] [-State <PowerActionState>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Finds power actions matching the specified search criteria from the queue of all known power actions. These power actions can be waiting to be dealt with or can be part way through being processed by the relevant hypervisor, or they can be recently completed actions. Completed actions are removed from the queue after a configured period, the default being one hour.

If no search criteria are specified all actions in the queue are obtained.

A Hosting Power Action record defines the action that is to be performed or has been performed, the machine that the action is to be applied to, the priority of the action in relation to other actions in the queue, times for points in the life of the action, and any results if the action has completed.

For a detailed description of the queuing mechanism, see 'help about\_Broker\_PowerManagement'.


### Brokerhostingpoweraction Object
The BrokerHostingPowerAction object represents an instance of a power action. It contains the following properties:


  * Action (Citrix.Broker.Admin.SDK.PowerManagementAction) The power action to be performed. Possible values are: TurnOn, TurnOff, Shutdown, Reset, Restart, Suspend, Resume.

  * ActionCompletionTime (System.DateTime?) The time when the power action was completed by the hypervisor connection.

  * ActionStartTime (System.DateTime?) The time when the power action was started to be processed by the hypervisor.

  * ActualPriority (System.Int32) The current priority of the operation after any priority boosting.

  * BasePriority (System.Int32) The starting priority of the operation.

  * DNSName (System.String) The fully qualified DNS name of the machine that the power action applies to.

  * FailureReason (System.String) For failed, lost, canceled or deleted actions, an indication of why the action did not complete.

  * HostedMachineId (System.String) The hypervisor's ID for the machine that the power action applies to.

  * HostedMachineName (System.String) The hypervisor's name for the machine that the power action applies to.

  * HypervisorConnectionUid (System.Int32) The unique identifier of the hypervisor connection that is associated with the target machine.

  * HypHypervisorConnectionUid (System.Guid) The UUID of the hypervisor connection that the machine’s hosting server is accessed through. This is the identifier used by the Host and Provisioning services.

  * MachineName (System.String) The name of the machine that the power action applies to, in the form domain\\machine.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this power action.

  * Origin (Citrix.Broker.Admin.SDK.PowerActionPriority) The origin of the power action.

  * RequestTime (System.DateTime) The timestamp of when the action was created and placed in the queue.

  * Sid (System.String) The SID of the machine to which the power action applies.

  * State (Citrix.Broker.Admin.SDK.PowerActionState) The current state of this power action. Possible values are: Pending, Started, Completed, Failed, Canceled, Deleted, Lost.

  * Uid (System.Int64) The unique identifier of the power action.


## Related Commands

* [New-BrokerHostingPowerAction](./New-BrokerHostingPowerAction/)
* [Set-BrokerHostingPowerAction](./Set-BrokerHostingPowerAction/)
* [Remove-BrokerHostingPowerAction](./Remove-BrokerHostingPowerAction/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the single action record whose ID matches the specified value. | true | false |  |
| MachineName | Gets only the records for actions that are for machines whose name (of the form domain\\machine) matches the specified string. | false | false |  |
| Action | Gets only action records with the specified action type.<br>Valid values are TurnOn, TurnOff, ShutDown, Reset, Restart, Suspend and Resume. | false | false |  |
| ActionCompletionTime | Gets only action records reported as having completed successfully at the specified time. This is useful with advanced filtering; for more information, see about\_Broker\_Filtering. | false | false |  |
| ActionStartTime | Gets only action records reported as starting to be processed by the relevant hypervisor at the specified time. This is useful with advanced filtering; for more information, see about\_Broker\_Filtering. | false | false |  |
| ActualPriority | Gets only the records for actions whose current active priority matches the specified value. | false | false |  |
| BasePriority | Gets only the records for actions whose original priority matches the specified value. | false | false |  |
| DNSName | Gets only the records for actions that are for machines whose DNS name matches the specified string. | false | false |  |
| FailureReason | Gets only actions that did not complete successfully and whose failure reason value matches the specified string. | false | false |  |
| HostedMachineId | Gets only actions for machines whose hosting ID (the ID used by the hypervisor) matches the specified string. | false | false |  |
| HostedMachineName | Gets only actions for machines whose hosting name (the name used by the hypervisor) matches the specified string. | false | false |  |
| HypervisorConnectionName | Gets only the records for actions for machines hosted via a hypervisor connection whose name matches the specified string. | false | false |  |
| HypervisorConnectionUid | Gets only the records for actions for machines hosted via a hypervisor connection whose UID matches the specified value. | false | false |  |
| HypHypervisorConnectionUid | Gets only the records for actions for machines hosted via a hypervisor connection whose UUID matches the specified value. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Origin | Gets only actions whose origin matches the specified string.<br>Valid values are Reset, Pvd, Schedule, Launch, Admin, Untaint, Policy and IdlePool. | false | false |  |
| RequestTime | Gets only the records for actions created and added to the queue at the specified time. This is useful with advanced filtering; for more information, see about\_Broker\_Filtering. | false | false |  |
| Sid | Gets only actions for machines whose SIDs match the specified string. | false | false |  |
| State | Gets only the records for actions with the specified current state.<br>Valid values are Pending, Started, Completed, Failed, Canceled, Deleted and Lost. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Hostingpoweraction
Get-BrokerHostingPowerAction returns all power actions that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerHostingPowerAction
```
#### Description
Fetches records for all known power actions either waiting to be processed, or currently being processed, or which have been processed in the last hour.
### Example 2
```
C:\PS> Get-BrokerHostingPowerAction -State Pending -HypervisorConnectionName 'XenPool5'
```
#### Description
Fetches records for all power actions that are waiting to be processed and where the action is for a virtual machine that is hosted by the hypervisor called 'XenPool5'.
