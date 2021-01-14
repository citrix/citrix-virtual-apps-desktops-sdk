
# Register-Trustservicekey
Creates a new trusted Service Key
## Syntax
```
Register-TrustServiceKey -ServiceName <String> -PublicKey <String> [-InstanceId <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Creates a new trusted Service Key. If this is a Service Key with the ServiceName of "ConnectorProxy", it will also result in adding of the corresponding Edge Server.


## Related Commands

* [Get-TrustServiceKey](./Get-TrustServiceKey/)
* [Set-TrustServiceKeyRotation](./Set-TrustServiceKeyRotation/)
* [Unregister-TrustServiceKey](./Unregister-TrustServiceKey/)
* [Revoke-TrustPreviousServiceKey](./Revoke-TrustPreviousServiceKey/)
* [Get-ConfigEdgeServer](./Get-ConfigEdgeServer/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceName | The Name of the Service being effected | true | false |  |
| PublicKey | The primary public key being registered. | true | false |  |
| InstanceId | The instance ID of the service.  This is usually the FQDN of the machine the service is running on. | false | false | \$null |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Trust.Sdk.Servicekey
The newly created Service Key.
## Notes
This command should only be needed to register a ConnectorProxy that cannot do so using the installer and repair tool.
## Examples

### Example 1
```
Register-TrustServiceKey -ServiceName ConnectorProxy -InstanceId DCCHN-Proxy.xd.local -PublicKey PFJTQUtleVZhbHVlPjxNb2R1bHVzPnU2b0lCaFR2NXl...
```
#### Description
Register DCCHN-Proxy.xd.local ConnectorProxy with the Trust Service using the specified Public Key
