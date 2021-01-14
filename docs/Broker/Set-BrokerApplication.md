
# Set-Brokerapplication
Changes the settings of an application to the value specified in the command.
## Syntax
```
Set-BrokerApplication [-InputObject] <Application[]> [-PassThru] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CommandLineExecutable <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-LocalLaunchDisabled <Boolean>] [-MaxPerMachineInstances <Int32>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-UserFilterEnabled <Boolean>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerApplication [-Name] <String> [-PassThru] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CommandLineExecutable <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-LocalLaunchDisabled <Boolean>] [-MaxPerMachineInstances <Int32>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-UserFilterEnabled <Boolean>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerApplication cmdlet changes the value of one or more properties of an application, such as its CpuPriorityLevel or its CommandLineArguments, to the value specified in the command.

This cmdlet lets you change only the settings of the Application object, and not the relationships to other objects. For instance, it does not let you change which users can access this application, or change which desktop groups this application is published to. To do this, you need to remove the existing association, and then add a new association. The following example shows how to change the desktop group that an application is associated with from \$group1 to \$group2: Remove-BrokerApplication -DesktopGroup \$group1 Add-RemoveApplication -DesktopGroup \$group2

You can change properties of HostedOnDesktop, InstalledOnClient and PublishedContent applications but it is not possible to change the ApplicationType. Also, the Name cannot be changed using this cmdlet; to do this, use the Rename-BrokerApplication cmdlet.


## Related Commands

* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Get-BrokerApplication](./Get-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Move-BrokerApplication](./Move-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application to modify. The Uid of the application can also be substituted for the object. | true | true (ByValue) |  |
| Name | Specifies the name of the application to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| BrowserName | Specifies the BrowserName of the application. | false | false |  |
| ClientFolder | Specifies the folder that the application belongs to as the user sees it. This is the application folder displayed in the Citrix Online Plug-in, in Web Services, and also in the user's start menu. Subdirectories can be specified with '\\' character. The following special characters are not allowed: / \* ? &lt; &gt; | " :. Note that this property cannot be set for applications of type InstalledOnClient. | false | false |  |
| CommandLineArguments | Specifies the command-line arguments to use when launching the executable.  This setting is ignored for applications of type PublishedContent. | false | false |  |
| CommandLineExecutable | Specifies the name of the executable file to launch. | false | false |  |
| CpuPriorityLevel | Specifies the CPU priority for the launched executable. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High. Note that this property cannot be set for applications of type InstalledOnClient. | false | false |  |
| Description | Specifies the description of the application. | false | false |  |
| Enabled | Specifies whether or not this application can be launched. | false | false |  |
| HomeZoneOnly | Specifies whether if the preferred zone for launching the application is its home zone but no machine is available from that zone then the launch fails.<br>This can only be set if the application has a home zone preference specified. | false | false |  |
| HomeZoneUid | Specifies any home zone preference used when launching this application. | false | false |  |
| IconFromClient | Specifies if the app icon should be retrieved from the application on the client. This is reserved for possible future use, and all applications of type HostedOnDesktop cannot set or change this value. | false | false |  |
| IconUid | Specifies which icon to use for this application. This application is visible both to the administrator (in the consoles) and also to the user. If no icon is specified, then a generic built-in application icon is used. | false | false |  |
| IgnoreUserHomeZone | Specifies that when launching the application and the user has a home zone specified then the user's home zone preference should be ignored.<br>This can only be set if the application does not itself have a home zone preference specified. | false | false |  |
| LocalLaunchDisabled | When launching a published application from within a published desktop, do not launch the application in that desktop session. | false | false |  |
| MaxPerMachineInstances | Specifies the maximum allowed concurrently running instances of the application that an individual machine can have. A value of zero allows unlimited usage subject to any site-wide limit.<br>Reducing the limit below the currently running number of instances does not cause any of those to be stopped. | false | false |  |
| MaxPerUserInstances | Specifies the maximum allowed concurrently running instances of the application that an individual user can have. A value of zero allows unlimited usage subject to any site-wide limit.<br>Reducing the limit below the currently running number of instances does not cause any of those to be stopped. | false | false |  |
| MaxTotalInstances | Specifies the maximum allowed total of concurrently running instances of the application in the site. A value of zero allows unlimited usage.<br>Reducing the limit below the currently running number of instances does not cause any of those to be stopped. | false | false |  |
| PublishedName | Specifies the name seen by end users who have access to this application. | false | false |  |
| SecureCmdLineArgumentsEnabled | Specifies whether the command-line arguments should be secured. This is reserved for possible future use, and all applications of type HostedOnDesktop can only have this value set to true. | false | false |  |
| ShortcutAddedToDesktop | Specifies whether or not a shortcut to the application should be placed on the user device. | false | false |  |
| ShortcutAddedToStartMenu | Specifies whether a shortcut to the application should be placed in the user's start menu on their user device. | false | false |  |
| StartMenuFolder | Specifies the name of the start menu folder that holds the application shortcut (if any). This is valid only for the Citrix Online Plug-in. Subdirectories can be specified with '\\' character. The following special characters are not allowed: / \* ? &lt; &gt; | " :. | false | false |  |
| UserFilterEnabled | Specifies whether the application's user filter is enabled or disabled. Where the user filter is enabled, the application is only visible to users who appear in the filter (either explicitly or by virtue of group membership). | false | false |  |
| Visible | Specifies whether or not this application is visible to users. Note that it's possible for an application to be disabled and still visible. | false | false |  |
| WaitForPrinterCreation | Specifies whether or not the session waits for the printers to be created before allowing the end-user to interact with the session. Note that this property cannot be set for applications of type InstalledOnClient. | false | false |  |
| WorkingDirectory | Specifies from which working directory the executable is launched from. This setting is ignored for applications of type PublishedContent. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Application, Or Depends On Parameter
You can pipe the application to be added to Set-BrokerApplication. You can also pipe some of the other parameters by name.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Application
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Application object.
## Examples

### Example 1
```
C:\PS> Set-BrokerApplication -Name "Notepad" -Description 'Windows Notepad'
```
#### Description
Modifies the application that has a Name of "Notepad" so that its description reads Windows Notepad.
### Example 2
```
C:\PS> $app = Get-BrokerApplication -BrowserName "Calculator"

          C:\PS> Set-BrokerApplication -InputObject $app -Enabled $false
```
#### Description
First gets the application with a BrowserName of "Calculator", then modifies that application (by supplying the application object in the first position) so that it is disabled for users.
