
# New-Sfcluster
Creates new Storefront cluster with default set of services.
## Syntax
```
New-SfCluster -ServerName <String> -FarmName <String> -XmlServices <Uri[]> [-StorefrontUrl <Uri>] [-RunAsynchronously <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The server will have a default set of services containing fully-functionaly Storefront server with Authentication, Store, Receiver for Web and Desktop Appliance.


## Related Commands

* [Get-SfCluster](./Get-SfCluster/)
* [Add-SfServerToCluster](./Add-SfServerToCluster/)
* [Remove-SfServerFromCluster](./Remove-SfServerFromCluster/)
* [Set-SfCluster](./Set-SfCluster/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServerName | The name of the server to build a cluster on. The name must be one of the values returned by Get-SfCluster | true | false |  |
| FarmName | Name of the farm that will be used within Store service. | true | false |  |
| XmlServices | Collection of the url of xml services that will be used inside a farm. The urls neeed to be http or https, be absolute and share the same schema and port. | true | false |  |
| StorefrontUrl | The url that will be used by Receivers to contact Storefront. Http or https absolute urls are accepted. | false | false | Server name and http binding. |
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
New-SfCluster -FarmName "XdSiteName" -XmlServices http://farm1,http://farm2 -ServerName SfServer -RunAsynchronously $true
```
#### Description
Creates a new cluster on server "SfServer". The server will have a default set of services containing fully-functionaly Storefront server with Authentication, Store, Receiver for Web, Desktop Appliance site and the required infrastructure. The Store service will have a farm named "XdSiteName" that will contain servers farm1 and farm2, whose will be contacted using http on default port 80.
