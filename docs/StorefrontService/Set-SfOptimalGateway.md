
# Set-Sfoptimalgateway
Set the farms and the optimal gateway to use for launch.
## Syntax
```
Set-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> -HostNames <String[]> -StaUrls <String[]> -Farm <String> [-StasBypassDuration <TimeSpan>] [-StasUseLoadBalancing] [-EnableSessionReliability] [-UseTwoTickets] [-EnabledOnDirectAccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Set the farms and the optimal gateway to use for launch.


## Related Commands

* [Get-SfOptimalGatewayCommand](./Get-SfOptimalGatewayCommand/)
* [Remove-SfOptimalGatewayCommand](./Remove-SfOptimalGatewayCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SiteId | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default. | true | true (ByPropertyName) |  |
| ResourcesVirtualPath | Path to the store that is to be configured to have a farm to optimal gateway mapping.<br>Example: “/Citrix/Store” | true | true (ByPropertyName) |  |
| HostNames | Specifies the fully qualified domain name (FQDN) and port of the optimal NetScaler Gateway appliance.<br>Example1 for standard vServer port 443: gateway.example.com<br>Example2 for nonstandard vServer port 500: gateway.example.com:500 | true | false |  |
| StaUrls | Specifies the URLs for XenDesktop, XenApp, and VDI-in-a-Box servers running the Secure Ticket Authority (STA). If using multiple farms, list the STA servers on each using a comma separated list:<br>Example: "http://xenapp-a.ptd.com/scripts/ctxsta.dll","http://xendesktop-a.ptd.com/scripts/ctxsta.dll" | true | false |  |
| Farm | Specificies the set of delivery controllers, as named when they were configured with StoreFront. | true | false |  |
| StasBypassDuration | Set the time period, in hours, minutes, and seconds, for which an STA is considered unavailable after a failed request. | false | false |  |
| StasUseLoadBalancing | Set to true: randomly obtains session tickets from all STAs, evenly distributing requests across all the STAs.<br>Set to false: users are connected to the first available STA in the order in which they are listed in the configuration, minimizing the number of STAs in use at any given time. | false | false |  |
| EnableSessionReliability | Set to true: keeps disconnected sessions open while Receiver attempts to reconnect automatically. If you configured multiple STAs and want to ensure that session reliability is always available, set the value of the UseTwoTickets attribute to true to obtain session tickets from two different STAs in case one STA becomes unavailable during the session. | false | false |  |
| UseTwoTickets | Set to true: obtains session tickets from two different STAs in case one STA becomes unavailable during the session.<br>Set to false: uses only a single STA server. | false | false |  |
| EnabledOnDirectAccess | Set to true: ensures that when local users on the internal network log on to StoreFront directly, connections to their resources are still routed through the optimal appliance defined for the farm.<br>Set to false: connections to resources are not routed through the optimal appliance for the farm unless users access StoreFront through a NetScaler Gateway. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None

## Return Values

### None

## Examples

### Example 1
```
C:\PS>Set-DSOptimalGatewayForFarms -SiteId 1 -ResourcesVirtualPath /Citrix/Store -Hostnames @("gateway1.citrix.com:2222") -StaUrls @("https://server1.citrix.com/staurl") -StasBypassDuration "00.02:00:00" -EnabledOnDirectAccess
```
#### Description

