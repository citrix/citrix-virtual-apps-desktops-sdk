
# Get-Applibappdiskappdnarecommendedorder
Sorts the specified AppDisk Uids into a new order that minimises Layer ordering conflicts.
## Syntax
```
Get-AppLibAppDiskAppDNARecommendedOrder [-AppDiskUid] <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sorts the specified AppDisk Uids into a new order that minimises Layer ordering conflicts.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskUid | An array of AppDisk Uids that are intended to run together. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.Guid

## Return Values

### System.Guid

## Examples

### Example 1
```
C:\PS>$Uids = @{"F92EB804-ECB1-4D45-80C0-610AB3FB7DB0", "E7CA2FA1-0DD3-417E-99E7-2BC312E8E359", "FDA1DCF4-8538-4455-9B91-D45E5C668F17"}

            C:\PS>Get-AppLibAppDiskAppDNARecommendedOrder -AppDiskUid $Uids

            F92EB804-ECB1-4D45-80C0-610AB3FB7DB0

            E7CA2FA1-0DD3-417E-99E7-2BC312E8E359

            FDA1DCF4-8538-4455-9B91-D45E5C668F17
```
#### Description
Reorders the specified AppDis Uids to minimise layer ordering conflicts.
### Example 2
```
$DesktopGroup = Get-BrokerDesktopGroup -Name "My Group"

            Get-AppLibAppDiskAppDNARecommendedOrder -AppDiskUid $DesktopGroup.AppDiskUids

            F92EB804-ECB1-4D45-80C0-610AB3FB7DB0

            E7CA2FA1-0DD3-417E-99E7-2BC312E8E359

            FDA1DCF4-8538-4455-9B91-D45E5C668F17
```
#### Description
Finds the disks belonging to the desktop group named "My group" and finds the best order in which to reaply these to minimise layering conflics.
