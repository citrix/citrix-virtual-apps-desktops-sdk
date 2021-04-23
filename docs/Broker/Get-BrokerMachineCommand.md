
# Get-Brokermachinecommand
Get the list of commands queued for delivery to a desktop.
## Syntax
```
Get-BrokerMachineCommand -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerMachineCommand [-Category <String>] [-CommandName <String>] [-CompletionTime <DateTime>] [-MachineName <String>] [-MachineUid <Int32>] [-Metadata <String>] [-RequestTime <DateTime>] [-SendDeadline <TimeSpan>] [-SendDeadlineTime <DateTime>] [-SendTrigger <MachineCommandTrigger>] [-SessionUid <Int64>] [-State <MachineCommandState>] [-User <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Get the list of commands queued for delivery to a desktop.  Commands are batched and can be configured to be delivered at various times during a desktop session's lifetime.  Normally commands are sent within a few minutes of being queued, but it is also possible to queue a command for a user who is not currently logged on or a desktop that is currently switched off.

See about\_Broker\_Filtering for information about advanced filtering options.


### Brokermachinecommand Object
The command object returned represents a command handled by a specific service on a desktop as determined by the Category property.


  * Category (System.String) Category of the command.

  * CommandData (System.Byte\[\]) Additional binary data included when the command is sent.

  * CommandName (System.String) Name of the command.

  * CompletionTime (System.DateTime?) Time at which the command was sent, expired or canceled.

  * DesktopGroupNames (System.String\[\]) List of desktop group names that the command was restricted to.

  * MachineName (System.String) Name of the machine this command is targeted at.

  * MachineUid (System.Int32?) Unique ID of the machine this command is targeted at.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this command.

  * RequestTime (System.DateTime) Time at which this command was created.

  * SendDeadline (System.TimeSpan) Duration after which this command expires if it has not been sent yet.

  * SendDeadlineTime (System.DateTime?) Time at which this command expires if it has not been sent yet.

  * SendTrigger (Citrix.Broker.Admin.SDK.MachineCommandTrigger?) Event that triggers the sending of the command. Valid values are NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect.

  * SessionUid (System.Int64?) Unique ID of the session this command is targeted at.

  * State (Citrix.Broker.Admin.SDK.MachineCommandState) Indicates whether the command is pending, sent, expired or canceled.

  * Synchronous (System.Boolean) Flag that indicates if this is a synchronous command.

  * Uid (System.Int64) Unique identifier of this machine command.

  * User (System.String) Name of the user this command is targeted at.


## Related Commands

* [New-BrokerMachineCommand](./New-BrokerMachineCommand/)
* [Remove-BrokerMachineCommand](./Remove-BrokerMachineCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get only the command with the specified unique identifier. | true | false |  |
| Category | Get only commands targeted to the specified service category. | false | false |  |
| CommandName | Get only commands with the specified command name. | false | false |  |
| CompletionTime | Get only commands that entered the Sent, Failed, Canceled or Expired state at the specified time. | false | false |  |
| MachineName | Get only commands targeted to the specified machine. | false | false |  |
| MachineUid | Get only commands targeted to the specified machine. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| RequestTime | Get only commands that were requested at the specified time. | false | false |  |
| SendDeadline | Get only commands that expire after the specified time span. | false | false |  |
| SendDeadlineTime | Get only commands that have the specified deadline time. | false | false |  |
| SendTrigger | Get only commands that are due to be sent when the specified trigger occurs. Valid values are  NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect. | false | false |  |
| SessionUid | Get only commands targeted to the specified session. | false | false |  |
| State | Get only commands in the specified state. Valid values are Pending, Sent, Failed, Canceled and Expired. | false | false |  |
| User | Get only commands targeted to the specified user. | false | false |  |
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
No parameter is accepted from the input pipeline.
## Return Values

### Citrix.Broker.Admin.Sdk.Machinecommand
Returns Command objects matching all specified selection criteria.
## Examples

### Example 1
```
Get-BrokerMachineCommand
```
#### Description
Returns all pending, canceled, expired and sent commands.
### Example 2
```
Get-BrokerMachineCommand -State Pending
```
#### Description
Returns all queued commands.
