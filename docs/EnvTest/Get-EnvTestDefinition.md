
# Get-Envtestdefinition
Gets the one or more test definitions
## Syntax
```
Get-EnvTestDefinition [-TestId <String[]>] [-CultureName <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of test definitions that are available from currently running components.


## Related Commands

* [Get-EnvTestSuiteDefinition](./Get-EnvTestSuiteDefinition/)
* [Get-EnvTestTask](./Get-EnvTestTask/)
* [Start-EnvTestTask](./Start-EnvTestTask/)
* [Switch-EnvTestTask](./Switch-EnvTestTask/)
* [Stop-EnvTestTask](./Stop-EnvTestTask/)
* [Remove-EnvTestTask](./Remove-EnvTestTask/)
* [Add-EnvTestTaskMetadata](./Add-EnvTestTaskMetadata/)
* [Remove-EnvTestTaskMetadata](./Remove-EnvTestTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TestId | The id of one or more tests. | false | true (ByValue) |  |
| CultureName | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String
A test id.
### System.String\[\]
An array of test ids.
## Return Values

### Citrix.Envtest.Sdk.Envtestdefinition
One or more test definitions.
## Examples

### Example 1
```
$allTestDefinitions = Get-EnvTestDefinition
```
#### Description
Retrieve all tests.
### Example 2
```
$allTestDefinitionsTranslatedIntoSpanish = Get-EnvTestDefinition -CultureName es-ES
```
#### Description
Retrieve all tests with localized properties returned in Spanish.
### Example 3
```
$monitorConfigServiceRegistrationDefinition = Get-EnvTestDefinition -TestId Monitor_RegisteredWithConfigurationService
```
#### Description
Retrieve the definition of the 'Monitor\_RegisteredWithConfigurationService' test.
