
# Remove-Sfserverfromcluster
Removes server from the cluster.
## Syntax
```
Remove-SfServerFromCluster -ClusterId <Guid> -ServerName <String> [-StorefrontUrl <Uri>] [-FarmName <String>] [-XmlServices <Uri[]>] [-RunAsynchronously <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Removes server from the cluster and propagates information to other servers. The configuration of the server is wiped out, so the server can be reused.


## Related Commands

* [Get-SfCluster](./Get-SfCluster/)
* [New-SfCluster](./New-SfCluster/)
* [Add-SfServerToCluster](./Add-SfServerToCluster/)
* [Set-SfCluster](./Set-SfCluster/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ClusterId | The if of the cluster to perform operation on. | true | false |  |
| ServerName | The name of the server to remove from cluster. The name must be one of the values returned by Get-SfCluster. | true | false |  |
| StorefrontUrl | The url that will be used by Receivers to contact Storefront. Http or https absolute urls are accepted. | false | false | Server name and http binding. |
| FarmName | Name of the farm that will be used within Store service. Either both FarmName and XmlServices need to be specified or none of them. | false | false |  |
| XmlServices | Collection of the url of xml services that will be used inside a farm. The urls neeed to be http or https, be absolute and share the same schema and port.  Either both FarmName and XmlServices need to be specified or none of them. | false | false |  |
| RunAsynchronously | If set, the command will run asynchronously. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Storefront.Sdk.Task Or Citrix.Storefront.Datamodel.Cluster
Returns cluster description or a task, if ran asynchronously.
## Examples

### Example 1
```
Remove-SfServerFromCluster -ClusterId (Guid) -ServerName BrokenSfServer -RunAsynchronously $true
```
#### Description
Removes Server "BrokenSfServer" from a Cluster with id (Guid).
