
# New-Applibisolationgroup
Adds a new isolation group into the library
## Syntax
```
New-AppLibIsolationGroup [-LibraryUid] <Int32> [-Name] <String> [-Description <String>] [-Version <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The isolation group will be added to the library


## Related Commands

* [Remove-AppLibIsolationGroup](./Remove-AppLibIsolationGroup/)
* [Set-AppLibIsolationGroup](./Set-AppLibIsolationGroup/)
* [Set-AppLibIsolationGroupPackage](./Set-AppLibIsolationGroupPackage/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LibraryUid | The unique identifier of the library to which the isolation group will be added | true | true (ByPropertyName) |  |
| Name | The name of the isolation group. | true | false |  |
| Description | The description of the isolation group. | false | false |  |
| Version | The version of the isolation group. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Isolationgroup
An object representing the details of the new isolation group.
## Notes
If supplied, the value of the LibraryUid parameter must be 1. No other values are supported.
## Examples

### Example 1
```
New-AppLibIsolationGroup -LibraryUid 1 -Name "MyIsolationGroup" -Description "Some description here" -Version "1.0.0.1"
```
#### Description
Adds the isolation group to the specified library
