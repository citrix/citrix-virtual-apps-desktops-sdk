
# Test-Brokerremotepcaccountnameavailable
Determine whether the proposed RemotePCAccount OU is available for use.
## Syntax
```
Test-BrokerRemotePCAccountNameAvailable [-OU] <String[]> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet checks whether proposed RemotePCAccount OU is available for use. It returns a record for each OU indicating the availability of that OU, with \$true indicating that the OU is unused and available for use, or \$false if it is not available.


## Related Commands

* [Get-BrokerRemotePCAccount](./Get-BrokerRemotePCAccount/)
* [New-BrokerRemotePCAccount](./New-BrokerRemotePCAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| OU | The RemotePCAccount OU to be tested. | true | true (ByValue, ByPropertyName) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### System.String
You can pipe a string that contains the OU to test.
## Return Values

### Citrix.Broker.Admin.Sdk.Nameavailability
The cmdlet returns a result for each OU specified. An availability of "True" indicates the OU is available for use, and "False" if it is not available.
## Examples

### Example 1
```
C:\PS> Test-BrokerRemotePCAccountNameAvailable -OU Test1
```
#### Description
Checks whether the OU "Test1" is available.
### Example 2
```
C:\PS> Test-BrokerRemotePCAccountNameAvailable @("Test1","Test2","Test3")
```
#### Description
Checks whether each of the specified names is available.
