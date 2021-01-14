
# Update-Brokerscopecache
Synchronise the scope information with the Delegated Administration service
## Syntax
```
Update-BrokerScopeCache [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Force an immediate synchronisation of the scope information held by the Delegated Administration service with the cached copy held by the Broker service. The scope data would be eventually synchronised anyway, but this cmdlet can be used when the synchronisation is needed immediately.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### None

## Examples

### Example 1
```
C:\PS> New-AdminScope -Name 'NewScopeName'

            C:\PS> Update-BrokerScopeCache
```
#### Description
Ensures the broker cache is up to date after a change to the scopes configured in the site
