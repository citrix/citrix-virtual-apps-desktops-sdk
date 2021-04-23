
# Reset-Brokerhypervisorconnection
Reset the hypervisor connection
## Syntax
```
Reset-BrokerHypervisorConnection [[-HypervisorConnectionUid] <Int32>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Reset-BrokerHypervisorConnection [-InputObject] <HypervisorConnection> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Requests the hypervisor connection to be reset. The connection is dropped, details including credentials refreshed and the connection reestablished. The reset request is asynchronous and may take a moment to occur


## Related Commands

* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [Remove-BrokerHypervisorConnection](./Remove-BrokerHypervisorConnection/)
* [Set-BrokerHypervisorConnection](./Set-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the hypervisor connection object to remove. | true | true (ByValue) |  |
| HypervisorConnectionUid | Specifies the hypervisor connection Uid | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Hypervisorconnection
You can pipe the hypervisor connection to be reset to Reset-BrokerHypervisorConnection.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Reset-BrokerHypervisorConnection -HypervisorConnectionUid 2
```
#### Description
This command resets the specified Hypervisor connection by internal Uid
### Example 2
```
C:\PS> Get-HypervisorConnection | Reset-BrokerHypervisorConnection
```
#### Description
This command resets the piped in hypervisor connection
