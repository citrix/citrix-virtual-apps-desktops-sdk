
# Get-Hyplocalizedstring
Obtains human-readable and locale-aware status messages from a hosting connection.
## Syntax
```
Get-HypLocalizedString [-LiteralPath] <String> [-Locale] <String> [-Category] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [[-LookupKey] <String>] [<CommonParameters>]
```
## Detailed Description
TODO


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hypervisor connection whose strings are being queried. The path must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;ConnectionName&gt; or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;} | true | true (ByValue) |  |
| Locale | The requested locale for the message, such as "en-US". | true | false |  |
| Category | The category of the localized string. | true | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |
| LookupKey | The lookup key or message ID. | false | false |  |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Get-Hyplocalizedstring (Literalpath Parameter).

## Return Values

### Citrix.Host.Sdk.Hypervisorstring
Get-HypLocalizedString returns zero or more instances of the HypervisorString object, each of which contain the following properties:<br>Category &lt;string&gt; Specifies the category of the string, such as "Exception". LookupKey &lt;string&gt; Specifies the unique lookup key or message ID within the category. DisplayText &lt;string&gt; Specifies the locale-aware and human-readable text.
## Notes
In the case of failure, the following errors can be produced.<br>    Error Codes<br>    -----------<br>    ConnectionsPathInvalid<br>    The path provided is not to an item in the Connections subdirectory of the host service provider.<br>    HypervisorConnectionObjectNotFound<br>    The path provided could not be resolved to an existing hypervisor connection. The name or GUID is invalid.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-HypLocalizedString -LiteralPath XDHyp:\Connections\MyCloud -Category Exception -Locale "en-US" -LookupKey "MyCloud.InsufficientFreeIpSpace"

          Category             : Exception

          LookupKey            : MyCloud.InsufficientFreeIpSpace

          DisplayText          : There are not enough free IP addresses on the network {0}
```
#### Description
This command illustrates how a single error/exception message can be obtained for a hosting operation that failed (such as a provisioning operation). The caller specifies that they need to display the message in the en-US locale. They also specify a lookup key or message ID for the message, which will have been obtained as an exception code from the failed operation. The locale and key/ID are traded for a readable message, which also includes substitutions.
