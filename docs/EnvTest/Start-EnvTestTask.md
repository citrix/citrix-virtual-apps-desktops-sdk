
# Start-Envtesttask
Starts a new test task.
## Syntax
```
Start-EnvTestTask -TestId <String> [-TargetIdType <String>] [-TargetId <String>] [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Start-EnvTestTask -TestSuiteId <String> [-TargetIdType <String>] [-TargetId <String>] [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Start-EnvTestTask -InputObject <PSObject[]> [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Starts a new test task based on a set of criteria provided via parameters or piped input and either waits for the tests to run or returns immediately depending on how it is called.  When running a test suite and providing a target object for that suite, the service will discover related objects by default, but this behavior may be disabled if desired.


## Related Commands

* [Get-EnvTestDefinition](./Get-EnvTestDefinition/)
* [Get-EnvTestSuiteDefinition](./Get-EnvTestSuiteDefinition/)
* [Get-EnvTestTask](./Get-EnvTestTask/)
* [New-EnvTestDiscoveryTargetDefinition](./New-EnvTestDiscoveryTargetDefinition/)
* [Switch-EnvTestTask](./Switch-EnvTestTask/)
* [Stop-EnvTestTask](./Stop-EnvTestTask/)
* [Remove-EnvTestTask](./Remove-EnvTestTask/)
* [Add-EnvTestTaskMetadata](./Add-EnvTestTaskMetadata/)
* [Remove-EnvTestTaskMetadata](./Remove-EnvTestTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TestId | Test identifiers. If specified, do not specify -TestSuiteId. | true | false | Empty |
| TestSuiteId | Test suite identifiers. If specified, do not specify -TestId. | true | false | Empty |
| InputObject | One or more test targets defining the task, see Input Types for details about what kind of objects are permissible.  Any valid object passed to this parameter may also be piped into this cmdlet. | true | true (ByValue) | Empty |
| TargetIdType | Describes the type of corresponding object passed with -TargetId | false | false | Empty |
| TargetId | The Ids that object tests or tests suites will target. By default, other components are queried for objects related to these. | false | false | Empty |
| CultureName | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false | The current user interface culture |
| IgnoreRelatedObjects | Do not ask other components for objects related to a specified target. | false | false | False |
| RunAsynchronously | Do not wait for the test run to complete, return immediately. | false | false | False |
| ExcludeNotRunTests | If set, tests that are not run because no object matching their requirements is found are NOT included in test counts and results. | false | false | False (include Not Run tests) |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Envtest.Sdk.Envtestdiscoverytargetdefinition
A single EnvTestDiscoveryTargetDefinition can be specified to target one test or test suite.
### Citrix.Envtest.Sdk.Envtestdiscoverytargetdefinition\[\]
An array of EnvTestDiscoveryTargetDefinition(s) can be specified to target any combination of tests and/or test suites.
### Pscustomobject
A single PSCustomObject with properties matching the required EnvTestDiscoveryTargetDefinition properties can be specified to target one test or test suite.
### Pscustomobject\[\]
An array of PSCustomObject(s) with properties matching the required EnvTestDiscoveryTargetDefinition properties can be specified to target any combination of tests and/or test suites.
## Return Values

### Ctrix.Envtest.Sdk.Envtesttask
The newly started task.
## Examples

### Example 1
```
$singleSimpleTestTask = Start-EnvTestTask -TestId Monitor_RegisteredWithConfigurationService
```
#### Description
Create and start a task with a single test and no target object.
### Example 2
```
$singleSimpleTestTaskInSpanish = Start-EnvTestTask -TestId Monitor_RegisteredWithConfigurationService -CultureName es-ES
```
#### Description
Create and start a task with a single test and no target object, with localized properties translated into Spanish.
### Example 3
```
$singleSimpleTestSuiteTask = Start-EnvTestTask -TestSuiteId Infrastructure
```
#### Description
Create and start a task with a single test suite and no target object.
### Example 4
```
$singleTestSuiteTask = Start-EnvTestTask -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid
```
#### Description
Create and start a task with a single test suite and a catalog target object.
### Example 5
```
$singleTestSuiteTask = Start-EnvTestTask -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid -RunAsynchronously
```
#### Description
Create and start a task with a single test suite and a catalog target object, and return immediately not waiting for the tests to complete.
### Example 6
```
$adAccountPool = Get-AcctIdentityPool

          $singleTestTaskWithNoObjectDiscovery = StartEnvTestTask -IgnoreRelatedObjects -TestId ADIdentity_IdentityPool_ValidatePoolIsUnlocked -TargetIdType IdentityPool -TargetId $adAccountPool.IdentityPoolUid
```
#### Description
Create and start a task with a single test, a target object for that test, and no object discovery based on that target.
### Example 7
```
$singleSimpleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Infrastructure

          $singleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid

          $inputObjects = @($singleSimpleTestSuiteTaskTarget, $singleTestSuiteTaskTarget)

          Start-EnvTestTask -InputObject $inputObjects
```
#### Description
Create two different discovery target definitions, put them in an array, then start a task based on both via -InputObject.
