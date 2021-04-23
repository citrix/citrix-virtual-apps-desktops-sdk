
# New-Brokertag
Creates a new tag.
## Syntax
```
New-BrokerTag [-Name] <String> [-Description <String>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Creates a tag that can be associated with other objects using Add-BrokerTag.


## Related Commands

* [Add-BrokerTag](./Add-BrokerTag/)
* [Get-BrokerTag](./Get-BrokerTag/)
* [Remove-BrokerTag](./Remove-BrokerTag/)
* [Rename-BrokerTag](./Rename-BrokerTag/)
* [Set-BrokerTag](./Set-BrokerTag/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies a name for the new tag. | true | true (ByPropertyName) |  |
| Description | A description for the tag. | false | true (ByPropertyName) |  |
| UUID | Specifies a UUID for the new tag. When not specified, a UUID is automatically assigned. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Tag
Outputs the generated tag.
## Examples

### Example 1
```
C:\PS> New-BrokerTag -Name 'Tag1'
```
#### Description
Creates a new tag with name 'Tag1'.
### Example 2
```
C:\PS> New-BrokerTag 'Tag2' | Add-BrokerTag -Machine DOMAIN\Machine
```
#### Description
Creates a new tag with name 'Tag2' and associates it with machine DOMAIN\\Machine.
