
# Test-Brokermachinenameavailable
Determine whether the proposed Machine MachineName is available for use.
## Syntax
```
Test-BrokerMachineNameAvailable [-MachineName] <String[]> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet checks whether proposed Machine MachineName is available for use. It returns a record for each MachineName indicating the availability of that MachineName, with \$true indicating that the MachineName is unused and available for use, or \$false if it is not available.


## Related Commands

* [Get-BrokerMachine](./Get-BrokerMachine/)
* [New-BrokerMachine](./New-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| MachineName | The Machine MachineName to be tested. | true | true (ByValue, ByPropertyName) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### System.String
You can pipe a string that contains the MachineName to test.
## Return Values

### Citrix.Broker.Admin.Sdk.Nameavailability
The cmdlet returns a result for each MachineName specified. An availability of "True" indicates the MachineName is available for use, and "False" if it is not available.
## Examples

### Example 1
```
C:\PS> Test-BrokerMachineNameAvailable -MachineName Test1
```
#### Description
Checks whether the MachineName "Test1" is available.
### Example 2
```
C:\PS> Test-BrokerMachineNameAvailable @("Test1","Test2","Test3")
```
#### Description
Checks whether each of the specified names is available.
