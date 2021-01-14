
# Test-Brokercatalognameavailable
Determine whether the proposed Catalog Name is available for use.
## Syntax
```
Test-BrokerCatalogNameAvailable [-Name] <String[]> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet checks whether proposed Catalog Name is available for use. It returns a record for each Name indicating the availability of that Name, with \$true indicating that the Name is unused and available for use, or \$false if it is not available.


## Related Commands

* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [New-BrokerCatalog](./New-BrokerCatalog/)
* [Rename-BrokerCatalog](./Rename-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The Catalog Name to be tested. | true | true (ByValue, ByPropertyName) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### System.String
You can pipe a string that contains the Name to test.
## Return Values

### Citrix.Broker.Admin.Sdk.Nameavailability
The cmdlet returns a result for each Name specified. An availability of "True" indicates the Name is available for use, and "False" if it is not available.
## Examples

### Example 1
```
C:\PS> Test-BrokerCatalogNameAvailable -Name Test1
```
#### Description
Checks whether the Name "Test1" is available.
### Example 2
```
C:\PS> Test-BrokerCatalogNameAvailable @("Test1","Test2","Test3")
```
#### Description
Checks whether each of the specified names is available.
