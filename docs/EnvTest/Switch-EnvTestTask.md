
# Switch-Envtesttask
Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.
## Syntax
```
Switch-EnvTestTask [-TaskId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Switch-EnvTestTask [-Task <EnvTestTask>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.


## Related Commands

* [Get-EnvTestDefinition](./Get-EnvTestDefinition/)
* [Get-EnvTestSuiteDefinition](./Get-EnvTestSuiteDefinition/)
* [Get-EnvTestTask](./Get-EnvTestTask/)
* [New-EnvTestTask](./New-EnvTestTask/)
* [Start-EnvTestTask](./Start-EnvTestTask/)
* [Stop-EnvTestTask](./Stop-EnvTestTask/)
* [Remove-EnvTestTask](./Remove-EnvTestTask/)
* [Add-EnvTestTaskMetadata](./Add-EnvTestTaskMetadata/)
* [Remove-EnvTestTaskMetadata](./Remove-EnvTestTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier of the task to be made current. | false | false |  |
| Task | The task object to be made current, retrieveable from the \$task.TaskId property. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.Management.Automation.Psobject
Objects containing the TaskId parameter can be piped to the Remove-EnvTestTask command.
## Return Values

### 

## Examples

### Example 1
```
Switch-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
```
#### Description
Switches the current task to another via its id, which is available from an existing task's \$task.TaskId property.
### Example 2
```
$secondTask = $(Get-EnvTestTask -List)[1]

Switch-EnvTestTask -Task $switchTask
```
#### Description
Switches the current task to the second in the list returned by Get-EnvTestTask -List.
