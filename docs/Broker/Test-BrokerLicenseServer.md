
# Test-Brokerlicenseserver
Tests whether or not a license server can be used by the broker.
## Syntax
```
Test-BrokerLicenseServer [-ComputerName] <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [[-Port] <Int32>] [<CommonParameters>]
```
## Detailed Description
Tests whether or not a given license server can be used by the broker.


## Related Commands

* [Get-BrokerSite](./Get-BrokerSite/)
* [Set-BrokerSite](./Set-BrokerSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ComputerName | The name of the license server to test (machine.domain). | true | false | None |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| Port | The port number to use on the server. | false | false | 27000 |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
Test-BrokerLicenseServer returns:<br>o 'Compatible' - the server is a compatible license server that can be used.<br>o 'Incompatible' - the server is an incompatible license server that can't be used.<br>o 'Inaccessible' - the server cannot be accessed. The server may be down, unreachable, or non-existent.<br>o 'InternalError - the server can't be used due to an internal error. A required licensing component on the server may not be installed, configured, or working correctly.
## Examples

### Example 1
```
C:\PS> Test-BrokerLicenseServer -LicenseServerAddress "machine.domain" 1234
```
#### Description
Tests whether or not the license server "machine.domain" with port number 1234 can be used.
### Example 2
```
C:\PS> Test-BrokerLicenseServer -LicenseServerAddress "machine.domain"
```
#### Description
Tests whether or not the license server "machine.domain" with port number 2700 can be used.
