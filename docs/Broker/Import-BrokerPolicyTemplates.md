
# Import-Brokerpolicytemplates
Sets the site wide Citrix Group Policy templates for the site.
## Syntax
```
Import-BrokerPolicyTemplates [-Templates] <Byte[]> [-Version] <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [[-Force]] [<CommonParameters>]
```
## Detailed Description
Import-BrokerPolicyTemplates sets the site wide Citrix Group Policy templates. A read of the policy templates data using the Export-BrokerPolicyTemplates command should have been executed prior to issuing this command. That command returns a version number that indicates the version of the data stored in the database. If the version number is specified and the number does not match the number stored in the database, it means another import has been executed. In this case, this import will overwrite the changes made by the other import.


## Related Commands

* [Export-BrokerPolicyTemplates](./Export-BrokerPolicyTemplates/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Templates | The configuration data containing the Citrix Group Policy templates. | true | true (ByValue) |  |
| Version | The current version of the group policy templates data. This number should be obtained from a previous Export-BrokerPolicyTemplates. This number is used to ensure that the data stored in the database has not changed between the last time the data was read and this import. If -Force is not specified, the import will be rejected if the version does not match the version in the database. If -Force is specified, the data stored in the database will be overwritten with the templates provided. The version number always increases by 1 for each write, even when the data is overwritten. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| Force | The current version of the group policy templates data. This number should be obtained from a previous Export-BrokerPolicyTemplates. This number is used to ensure that the data stored in the database has not changed between the last time the data was read and this import. If this parameter is not specified, the templates stored in the database is replaced regardless if there has been another import since the last time the data was exported. | false | false |  |

## Input Type

### System.Byte\[\]
The configuration data as an opaque binary blob.
### System.Int
The current version of the group policy templates data.
## Return Values

### None

## Notes
Import-BrokerPolicyTemplates performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation be performed via the Citrix Studio.
## Examples

### Example 1
```
C:\PS> Import-BrokerPolicyTemplates $templatesData 100
```
#### Description
This command sets the Citrix Group Policy templates in the site.
### Example 2
```
C:\PS> Import-BrokerPolicyTemplates $templatesData 100 -Force
```
#### Description
This command sets the Citrix Group Policy templates in the site even if the data in the database is not at version 100.
