
# Get-Envtestsuitedefinition
Gets one or more test suite definitions.
## Syntax
```
Get-EnvTestSuiteDefinition [-TestSuiteId <String[]>] [-CultureName <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of test suite definitions that are available from currently running components.


## Related Commands

* [Get-EnvTestDefinition](./Get-EnvTestDefinition/)
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
| TestSuiteId | The id of one or more test suites. | false | true (ByValue) |  |
| CultureName | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String
A test suite id.
### System.String\[\]
An array of test suite ids.
## Return Values

### Citrix.Envtest.Sdk.Envtestsuitedefinition
The definition of a test suite
## Examples

### Example 1
```
$allTestSuiteDefinitions = Get-EnvTestSuiteDefinition
```
#### Description
Retrieve all test suites.
### Example 2
```
$allTestSuiteDefinitionsTranslatedIntoSpanish = Get-EnvTestSuiteDefinition -CultureName es-ES
```
#### Description
Retrieve all test suites with localized properties returned in Spanish.
### Example 3
```
$infrastructureSuiteDefinition = Get-EnvTestSuiteDefinition -TestSuiteId Infrastructure
```
#### Description
Retrieve the definition of the 'Infrastructure' test suite.
