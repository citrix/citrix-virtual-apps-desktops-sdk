
# Add-Brokeruser
Creates an association between a user and another broker object
## Syntax
```
Add-BrokerUser [-InputObject] <User[]> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerUser [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-Application <Application>] [-SessionLinger <SessionLinger>] [-SessionPreLaunch <SessionPreLaunch>] [-Machine <Machine>] [-PrivateDesktop <PrivateDesktop>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Add-BrokerUser cmdlet adds broker user objects to another specified object, such as a broker private desktop. This depends on the target object type:

* Machine - assign the broker machine to the specified user(s); when the machine is subsequently added to a desktop group, the desktop is also assigned to the same user(s).
* PrivateDesktop - assign the desktop to the specified user(s).
* Application - assign the application to the specified user(s).
* Application group - assign the applications in the application group to the specified user(s).


## Related Commands

* [Get-BrokerUser](./Get-BrokerUser/)
* [Remove-BrokerUser](./Remove-BrokerUser/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The user objects to add. | true | true (ByValue) | null |
| Name | The name of the user or users to be added. | true | true (ByPropertyName) | null |
| ApplicationGroup | The application group to which the user is to be assigned. | false | true (ByValue) |  |
| Application | The application to which the user is to be assigned. | false | true (ByValue) |  |
| SessionLinger | The session linger setting to which the user is to be assigned. | false | true (ByValue) | null |
| SessionPreLaunch | The session pre-launch setting to which the user is to be assigned. | false | true (ByValue) | null |
| Machine | The machine to which the user is to be assigned | false | true (ByValue) | null |
| PrivateDesktop | The desktop to which the user is to be assigned | false | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.User
You can pipe the users to be added to Add-BrokerUser.
## Return Values

### None

## Notes
Specify one of the -Machine or -PrivateDesktop or -Application parameters only.
## Examples

### Example 1
```
Add-BrokerUser "DOMAIN\UserName" -PrivateDesktop "DOMAIN\MachineName"
```
#### Description
Assign the specified private desktop to the specified user.
### Example 2
```
Add-BrokerUser "DOMAIN\UserName" -Application "ApplicationName"
```
#### Description
Assign the specified application to the specified user.
