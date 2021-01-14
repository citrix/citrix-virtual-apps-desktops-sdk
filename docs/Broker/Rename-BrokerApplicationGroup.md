
# Rename-Brokerapplicationgroup
Renames an application group.
## Syntax
```
Rename-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerApplicationGroup [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerApplicationGroup cmdlet changes the name of an application group. An application group cannot have the same name as another application group.

Application group names are not visible to end users.


## Related Commands

* [Add-BrokerApplicationGroup](./Add-BrokerApplicationGroup/)
* [Get-BrokerApplicationGroup](./Get-BrokerApplicationGroup/)
* [New-BrokerApplicationGroup](./New-BrokerApplicationGroup/)
* [Remove-BrokerApplicationGroup](./Remove-BrokerApplicationGroup/)
* [Set-BrokerApplicationGroup](./Set-BrokerApplicationGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application group to rename. | true | true (ByValue) | nul |
| Name | Specifies the name of the application group to rename. | true | true (ByPropertyName) | null |
| NewName | Specifies the new name of the application group. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Applicationgroup
You can pipe application groups to Rename-BrokerApplicationGroup.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Applicationgroup
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ApplicationGroup object.
## Examples

### Example 1
```
C:\PS> Rename-BrokerApplicationGroup -Name "Ofice" -NewName "Office"
```
#### Description
Renames the application group with name "Ofice" to "Office".
### Example 2
```
C:\PS> Get-BrokerApplicationGroup -Uid 1 | Rename-BrokerApplicationGroup -NewName "New Name" -PassThru
```
#### Description
Renames application group with the Uid 1 to "New Name", showing the result.
