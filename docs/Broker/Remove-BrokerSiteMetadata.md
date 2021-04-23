
# Remove-Brokersitemetadata
Deletes Site Metadata from the Site objects
## Syntax
```
Remove-BrokerSiteMetadata -Name <String> [[-InputObject] <Site[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerSiteMetadata cmdlet deletes Metadata from the Site objects.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the Metadata to be deleted | true | false |  |
| InputObject | Specifies the Site object's instance whose Metadata is to be deleted. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Brokersite
You can pipe the Site to delete the metadata.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerSiteMetadata -Name "MyMetadataName"
```
#### Description
This command deletes the Metadata "MyMetadataName" key-value pair for the Site
