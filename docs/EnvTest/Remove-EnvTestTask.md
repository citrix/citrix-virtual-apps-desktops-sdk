
# Remove-Envtesttask
Removes from the database completed tasks for the EnvTest Service.
## Syntax
```
Remove-EnvTestTask [-TaskId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-EnvTestTask [-Task <EnvTestTask>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables completed tasks that have run within the EnvTest Service to be removed from the database.


## Related Commands

* [Get-EnvTestDefinition](./Get-EnvTestDefinition/)
* [Get-EnvTestSuiteDefinition](./Get-EnvTestSuiteDefinition/)
* [Get-EnvTestTask](./Get-EnvTestTask/)
* [Start-EnvTestTask](./Start-EnvTestTask/)
* [Switch-EnvTestTask](./Switch-EnvTestTask/)
* [Stop-EnvTestTask](./Stop-EnvTestTask/)
* [Add-EnvTestTaskMetadata](./Add-EnvTestTaskMetadata/)
* [Remove-EnvTestTaskMetadata](./Remove-EnvTestTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier of the task to be removed, retrieveable from the \$task.TaskId property. | false | false |  |
| Task | Specifies the task to be removed. | false | true (ByValue) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
Remove-EnvTestTask
```
#### Description
Removes the current task from the EnvTest service.
### Example 2
```
Remove-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
```
#### Description
Removes a task from the EnvTest service via its id, which is available from an existing task's \$task.TaskId property.
### Example 3
```
$secondTask = $(Get-EnvTestTask -List)[1]

Remove-EnvTestTask -Task $secondTask
```
#### Description
Removes the second task in the list returned by Get-EnvTestTask -List.
