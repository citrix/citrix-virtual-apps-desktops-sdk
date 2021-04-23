
# Get-Brokermachinestartmenushortcuticon
Retrieves a Start Menu Shortcut icon from the specified machine.
## Syntax
```
Get-BrokerMachineStartMenuShortcutIcon [-MachineName] <String> [-Path] <String> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves the icon associated with a particular shortcut on a particular machine. This icon is usually used to help create a published application to access the shortcut.


## Related Commands

* [Get-BrokerMachine](./Get-BrokerMachine/)
* [New-BrokerIcon](./New-BrokerIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| MachineName | Specify the name of the machine to use for icon retrieval for the specified shortcut path. The machine can be identified by DNS name, short name, SID, or name of the form domain\\machine. | true | true (ByValue) |  |
| Path | The location of the shortcut in the specified machine whose icon is being fetched. | true | true (ByValue) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
Get-BrokerMachineStartMenuShortcutIcon generates a Base64 encoded string containing the icon for the specified shortcut. This can be used as input to New-BrokerIcon cmdlet.
## Examples

### Example 1
```
C:\PS> $shortcuts =  Get-BrokerMachineStartMenuShortcuts -MachineName 'MyDomain\MyMachine'

C:\PS> $encodedIconData =  Get-BrokerMachineStartMenuShortcutIcon -MachineName 'MyDomain\MyMachine' -Path $shortcuts[0].ShortcutPath

C:\PS> $brokerIcon = New-BrokerIcon -EncodedIconData $encodedIconData

C:\PS> Set-BrokerApplication 'Notepad' -IconUid $brokerIcon.Uid
```
#### Description
This example retrieves all Start Menu Shortcuts from 'MyDomain\\MyMachine', and then the icon for the first shortcut from the returned list. The icon is then associated with a published application called 'Notepad'.
