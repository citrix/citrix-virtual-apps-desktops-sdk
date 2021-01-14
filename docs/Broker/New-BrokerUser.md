
# New-Brokeruser
Creates a new broker user object
## Syntax
```
New-BrokerUser [-SID] <SecurityIdentifier> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerUser [-Name] <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerUser cmdlet creates a new broker object to represent a user identity (or the identity of a group of users). The object is created local to the PowerShell environment in which the cmdlet is run; no new user object is created in the broker configuration, unless the object is added to another broker object, such as a machine or a desktop. For details, see Add-BrokerUser.

The identity of the user or group must be specified using either the Name or SID parameter


## Related Commands

* [Add-BrokerUser](./Add-BrokerUser/)
* [Get-BrokerUser](./Get-BrokerUser/)
* [Remove-BrokerUser](./Remove-BrokerUser/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SID | The SID of the user or group | true | false | null |
| Name | The name of the user or group | true | false | null |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.User
The broker user object
## Notes
Typically, broker user objects are created implicitly using the Add-BrokerUser cmdlet with a user name or SID.
## Examples

### Example 1
```
$user = New-BrokerUser DOMAIN\UserName
```
#### Description
Create a broker user object for the specified user.
### Example 2
```
$user = New-BrokerUser -SID S-1-5-23-1763203430-193137401-908696819-3450
```
#### Description
Create a broker user object for the specified user.
