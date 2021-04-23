
# Remove-Brokeruser
Remove broker user objects from another broker object
## Syntax
```
Remove-BrokerUser [-InputObject] <User[]> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerUser [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerUser cmdlet removes broker user objects from another specified object, such as a broker private desktop, to which the user had previously been added.


## Related Commands

* [Add-BrokerUser](./Add-BrokerUser/)
* [Get-BrokerUser](./Get-BrokerUser/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the user objects to remove. | true | true (ByValue) |  |
| Name | Specifies the user objects to remove, based on their Name property. | true | true (ByPropertyName) | null |
| ApplicationGroup | The application group from which to remove the user | false | true (ByValue) |  |
| Application | The application from which to remove the user | false | true (ByValue) |  |
| SessionLinger | The desktop group session linger setting from which to remove the user. | false | true (ByValue) | null |
| SessionPreLaunch | The desktop group session pre-launch setting from which to remove the user. | false | true (ByValue) | null |
| Machine | The machine from which to remove the user | false | true (ByValue) | null |
| PrivateDesktop | The desktop from which to remove the user | false | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.User
You can pipe the users to be removed to Remove-BrokerUser.
## Return Values

### None

## Notes
Specify one of the -Machine or -PrivateDesktop parameters only.
## Examples

### Example 1
```
Remove-BrokerUser "DOMAIN\UserName" -PrivateDesktop "DOMAIN\MachineName"
```
#### Description
Remove the assignment of the specified private desktop to the specified user.
