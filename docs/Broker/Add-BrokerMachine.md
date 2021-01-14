
# Add-Brokermachine
Adds one or more machines to a desktop group.
## Syntax
```
Add-BrokerMachine [-InputObject] <Machine[]> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerMachine [-MachineName] <String> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Add-BrokerMachine cmdlet adds specified machines to a desktop group. There are three forms:



* Use the -InputObject parameter to add a single machine instance or array of instances to the group.
* Use the -MachineName parameter to add a single, named machine to the group.
* Use pipelining to pipe machines instances to the command.

The desktop group to which the machines are added can be specified by name, unique identifier (UID), or instance.

For a machine to be used in a site, the machine must be added to a desktop group. The machine and desktop group must be compatible in order for the process to succeed; for example a machine in a single-session catalog cannot be added to a multi-session desktop group.

For more information about machines, see about\_Broker\_Machines.


## Related Commands

* [Add-BrokerMachinesToDesktopGroup](./Add-BrokerMachinesToDesktopGroup/)
* [Remove-BrokerMachine](./Remove-BrokerMachine/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | An array of machines to add to the group. | true | true (ByValue) |  |
| MachineName | The name of the single machine to add (must match the MachineName property of the machine). | true | true (ByPropertyName) |  |
| DesktopGroup | The desktop group to which the machines are added, specified by name, Uid, or instance. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machine
You can pipe in the machines you want to add.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup $desktopGroup

C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup 2

C:\PS> Add-BrokerMachine $machine -DesktopGroup "MyDesktopGroup"
```
#### Description
These examples all add a single machine instance to a desktop group, identifying the group by instance, UID, or name.
### Example 2
```
C:\PS> Add-BrokerMachine -MachineName "MyDomain\MyMachine" -DesktopGroup 2

C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup "MyDesktopGroup"

C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup $desktopGroup
```
#### Description
These examples add the machine called MyMachine to a desktop group.
### Example 3
```
C:\PS> Get-BrokerMachine -Uid 3 | Add-BrokerMachine -DesktopGroup 2

C:\PS> Get-BrokerMachine -CatalogUid 4 | Add-BrokerMachine -DesktopGroup 2
```
#### Description
These examples find specific machines and add them to a desktop group.
