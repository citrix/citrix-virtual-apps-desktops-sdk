
# Add-Applibisolationgrouppackage
Adds an App-V package to an Isolation Group.
## Syntax
```
Add-AppLibIsolationGroupPackage [-IsolationGroupUid] <Int32> -AppVPackageUid <Int32> -OrderNumber <Int32> [-ExplicitInclusion <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Adds the App-V package to the specified Isolation Group.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group to contain the package. | true | true (ByPropertyName) |  |
| AppVPackageUid | The AppLibrary's internal unique identifier of the App-V package. | true | true (ByPropertyName) |  |
| OrderNumber | The order number within the Isolation Group. | true | true (ByPropertyName) |  |
| ExplicitInclusion | Indicates whether the package is explicitly included in the delivery group. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Isolationgrouppackage
An object representing the IsolationGroupPackage.
## Examples

### Example 1
```
Add-AppLibIsolationGroupPackage -Uid 4 -IsolationGroupUid 15 -ExplicitInclusion True -OrderNumber 1
```
#### Description
Adds the App-V package with the unique identifier to the specified isolation group.
