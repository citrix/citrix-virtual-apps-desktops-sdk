
# Revoke-Trustpreviousservicekey
This cmdlet removes the older public key from the service key
## Syntax
```
Revoke-TrustPreviousServiceKey -ServiceName <String> [-InstanceId <String>] [-PassThru] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Revoke-TrustPreviousServiceKey -ServiceKey <ServiceKey> [-PassThru] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet removes the older public key from the service key


## Related Commands

* [Register-TrustServiceKey](./Register-TrustServiceKey/)
* [Set-TrustServiceKeyRotation](./Set-TrustServiceKeyRotation/)
* [Get-TrustServiceKey](./Get-TrustServiceKey/)
* [Unregister-TrustServiceKey](./Unregister-TrustServiceKey/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceName | The Name of the service being effected | true | false |  |
| ServiceKey | An existing Service key.  Usually the results piped from another command. | true | true (ByValue) |  |
| InstanceId | The instance ID of the service.  This is usually the FQDN of the machine the service is running on. | false | false | \$null |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Trust.Sdk.Servicekey
You can pipe the service keys to be updated into this command.
## Return Values

### None Or Citrix.Trust.Sdk.Servicekey
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a ServiceKey object.
## Examples

### Example 1
```
Revoke-TrustPreviousServiceKey -ServiceName ConnectorProxy -InstanceId DCCHN-Proxy.xd.local
```
#### Description
Revoke the previous public key for the DCCHN-Proxy.xd.local ConnectorProxy service.
### Example 2
```
Get-TrustServiceKey -Filter "LastUpdated -gt '10-20-2016'" | Revoke-TrustPreviousServiceKey
```
#### Description
Revoke the previous public key of all service keys that were updated after October 20, 2016.
