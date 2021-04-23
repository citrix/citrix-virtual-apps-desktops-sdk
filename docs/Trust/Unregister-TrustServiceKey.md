
# Unregister-Trustservicekey
Unregister and Revoke the service keys for a specified service from the site.
## Syntax
```
Unregister-TrustServiceKey -ServiceName <String> [-InstanceId <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Unregister-TrustServiceKey -ServiceKey <ServiceKey> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Unregister and Revoke the service keys for a specified service. If this is a service key with the ServiceName of "ConnectorProxy", it will also result in the removal of the corresponding Edge Server.


## Related Commands

* [Register-TrustServiceKey](./Register-TrustServiceKey/)
* [Get-TrustServiceKey](./Get-TrustServiceKey/)
* [Set-TrustServiceKeyRotation](./Set-TrustServiceKeyRotation/)
* [Revoke-TrustPreviousServiceKey](./Revoke-TrustPreviousServiceKey/)
* [Get-ConfigEdgeServer](./Get-ConfigEdgeServer/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceName | The Name of the Service being effected | true | false |  |
| ServiceKey | An existing Service key.  Usually the results piped from another command. | true | true (ByValue) |  |
| InstanceId | The instance ID of the service.  This is usually the FQDN of the machine the service is running on. | false | false | \$null |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Trust.Sdk.Servicekey
You can pipe the service keys to be updated into this command.
## Return Values

### None

## Examples

### Example 1
```
Unregister-TrustServiceKey -ServiceName ConnectorProxy -InstanceId DCCHN-Proxy.xd.local
```
#### Description
Remove the service key for the ConnectorProxy DCCHN-Proxy.xd.local
### Example 2
```
Get-TrustServiceKey -InstanceId DCCHN-DDC1.xd.local | Unregister-TrustServiceKey
```
#### Description
Unregister all the service keys associated with DCCHN-DDC1.xd.local
