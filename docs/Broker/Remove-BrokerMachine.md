
# Remove-Brokermachine
Removes one or more machines from its desktop group or catalog.
## Syntax
```
Remove-BrokerMachine [-InputObject] <Machine[]> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerMachine [-MachineName] <String> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerMachine cmdlet removes one or more machines from their desktop group or catalog. There are three forms:


* Use the -InputObject parameter to remove a single machine instance or array of instances from their desktop group or catalog.
* Use the -MachineName parameter to remove the single named machine from its group or catalog.
* Use pipelining to pipe machine instances to the command.

To remove machines from their desktop group use the -DesktopGroup parameter; the specified group must be the one that contains the machines. If more than one machine is being removed from its group they must all be members of the same group.

If the -DesktopGroup parameter is not used then the machines are removed from their catalog. Removing a machine from its catalog deletes the record of the machine from the Citrix Broker Service.

Machines cannot be removed from their catalog while they are members of a desktop group.


## Related Commands

* [Add-BrokerMachine](./Add-BrokerMachine/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | An array of machines to be removed from their desktop group or catalog. | true | true (ByValue) |  |
| MachineName | The name of the single machine to remove (must match the MachineName property of the machine). | true | true (ByPropertyName) |  |
| Force | Forces removal of machine from a desktop group even if it is still in use (that is, there are user sessions running on the machine). Forcing removal of a machine does not disconnect or logoff the user sessions. | false | false |  |
| DesktopGroup | The desktop group from which the machines are to be removed, specified by name, UID, or instance. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machine
You can pipe in the machines to be removed.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerMachine -InputObject $machine -DesktopGroup $desktopGroup

C:\PS> Remove-BrokerMachine -InputObject $machine -DesktopGroup 2

C:\PS> Remove-BrokerMachine $machine -DesktopGroup "MyDesktopGroup"
```
#### Description
These all remove a single machine from a desktop group, identifying the group by instance, UID, or name.
### Example 2
```
C:\PS> Remove-BrokerMachine -MachineName "DOMAIN\MyMachine" -DesktopGroup 2

C:\PS> Remove-BrokerMachine DOMAIN\MyMachine -DesktopGroup "MyDesktopGroup"

C:\PS> Remove-BrokerMachine DOMAIN\MyMachine -DesktopGroup $desktopGroup
```
#### Description
These remove the machine called "DOMAIN\\MyMachine" from its desktop group.
### Example 3
```
C:\PS> Remove-BrokerMachine -MachineName DOMAIN\MyMachine

C:\PS> Remove-BrokerMachine "DOMAIN\MyMachine"

C:\PS> Remove-BrokerMachine $machine
```
#### Description
These all remove a machine from its catalog.
### Example 4
```
C:\PS> Get-BrokerMachine -Uid 3 | Remove-BrokerMachine -DesktopGroup $dg

C:\PS> Get-BrokerMachine -CatalogUid 4 | Remove-BrokerMachine
```
#### Description
These find specific machines and remove them from their desktop group or catalog.
