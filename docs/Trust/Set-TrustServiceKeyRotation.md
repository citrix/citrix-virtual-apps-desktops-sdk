
# Set-Trustservicekeyrotation
Mark a service key as needing to be rotated
## Syntax
```
Set-TrustServiceKeyRotation -ServiceName <String> [-InstanceId <String>] [-PassThru] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-TrustServiceKeyRotation -ServiceKey <ServiceKey> [-PassThru] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Mark a service key as needing to be rotated. Key rotation will not happen immediately.  Typically, it should take about an hour for the keys to be rotated but it can take longer if the service that owns the key is down or unable to contact the Trust Service.

Use Get-TrustServiceKey and look at the "LastUpdated" and "RotationNeeded" fields to determine when it was last rotated and if the Service Key has already been marked for Rotation.


## Related Commands

* [Register-TrustServiceKey](./Register-TrustServiceKey/)
* [Get-TrustServiceKey](./Get-TrustServiceKey/)
* [Unregister-TrustServiceKey](./Unregister-TrustServiceKey/)
* [Revoke-TrustPreviousServiceKey](./Revoke-TrustPreviousServiceKey/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceName | The Name of the Service being effected | true | false |  |
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
Set-TrustServiceKeyRotation -ServiceName ConnectorProxy -InstanceId DCCHN-Proxy.xd.local
```
#### Description
Mark the Service Key for the DCCHN-Proxy.xd.local ConnectorProxy to be rotated.
### Example 2
```
Get-TrustServiceKey -Filter "LastUpdated -lt '10-20-2015'" | Set-TrustServiceKeyRotation
```
#### Description
Mark all the Service Keys that were last updated before October 20, 2015 to rotate their public keys.
