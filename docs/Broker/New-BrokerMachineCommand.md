
# New-Brokermachinecommand
Creates a new command to deliver to a desktop.
## Syntax
```
New-BrokerMachineCommand -User <String> -Category <String> -CommandName <String> [-DesktopGroups <DesktopGroup[]>] [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerMachineCommand -MachineUid <Int32> -Category <String> -CommandName <String> [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerMachineCommand -SessionUid <Int64> -Category <String> -CommandName <String> [-SendTrigger <MachineCommandTrigger>] [-SendDeadline <TimeSpan>] [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerMachineCommand -Synchronous -MachineUid <Int32> -Category <String> -CommandName <String> [-CommandData <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Create a new command queued for delivery to a desktop.  Commands are sent to a specific handler installed on the desktop using the Category parameter. Each handler has its own list of commands identified by the CommandName parameter.  Optional command data can be provided using the CommandData parameter in a format specified by the handler.

Commands are targeted at a specific user, session or machine. Commands targeted at a user can be further be restricted to one or more desktop groups.

The SendTrigger is used to restrict the command to a specific event related to the target. For example, when the target machine registers or when the target user reconnects to a session. The command will be sent to the machine when the SendTrigger occurs for the target.

If the Synchronous switch is provided, the target must be a machine and no SendTrigger can be specified. The command is sent immediately to the machine if it is currently registered and fails if the machine is not registered.

Note that the combined length of the Category and CommandName is limited to 64 characters. The Category and CommandName must both be entirely alphanumeric and not include any white space.


## Related Commands

* [Get-BrokerMachineCommand](./Get-BrokerMachineCommand/)
* [Remove-BrokerMachineCommand](./Remove-BrokerMachineCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Category | The service on the desktop to send the command to. | true | true (ByPropertyName) |  |
| CommandName | The name of the command to send (as defined by the service). | true | true (ByPropertyName) |  |
| User | User whose desktop or session should receive the command. | true | true (ByPropertyName) | Any user. |
| MachineUid | Specific machine that should receive the command. | true | true (ByPropertyName) |  |
| SessionUid | Currently logged on user session that should receive the command. | true | true (ByPropertyName) | Any session. |
| Synchronous | Send the command immediately and block while waiting for the reply. | true | false | false |
| CommandData | Optional additional data to include with the command. | false | true (ByPropertyName) | None |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| DesktopGroups | Further restrict the command targeted at a user to machines in these desktop groups. | false | true (ByPropertyName) | No restriction by desktop group. |
| SendTrigger | Queue command for delivery until this particular event occurs. Valid values are  NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect. | false | true (ByPropertyName) | Default value is 'NextContact' so the command is sent during the next communication with the desktop. |
| SendDeadline | Automatically cancel the command if it not delivered before the specified time span passes. | false | true (ByPropertyName) | Command expires after 24 hours. |

## Input Type

### None
No parameter is accepted from the input pipeline.
## Return Values

### Citrix.Broker.Admin.Sdk.Machinecommand
New command that was added to the command queue.
### Citrix.Broker.Admin.Sdk.Machinesynchronouscommandresponse
When the Synchronous option is used, the command is immediately sent to the specified machine and processed. The SDK object returned describes the command and the result of this command processing.
## Notes
Commands are subject to delegated administration restrictions based on the desktop group, category and command name.
## Examples

### Example 1
```
New-BrokerMachineCommand -Category UserProfileManager -CommandName "ResetUpmProfile" -DesktopGroups 1 -CommandData $byteArray -SendTrigger logon -user domain1\user1
```
#### Description
Instruct the User Profile Manager service to execute the "ResetUpmProfile" command using the encoded \$byteArray command data when user domain1\\user1 logs on to any machine in desktop group 1
### Example 2
```
New-BrokerMachineCommand -Synchronous -Category "MonitorService" -CommandName "EnableLogging" -MachineUid 13
```
#### Description
Instruct the monitor service to immediately execute the "EnableLogging" command on the machine having Uid 13.
