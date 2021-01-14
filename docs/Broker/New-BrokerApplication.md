
# New-Brokerapplication
Creates a new published application.
## Syntax
```
New-BrokerApplication [-Name] <String> -ApplicationGroup <ApplicationGroup> -CommandLineExecutable <String> [-AdminFolder <AdminFolder>] [-ApplicationType <ApplicationType>] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-LocalLaunchDisabled <Boolean>] [-MaxPerMachineInstances <Int32>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerApplication [-Name] <String> -DesktopGroup <DesktopGroup> -CommandLineExecutable <String> [-Priority <Int32>] [-AdminFolder <AdminFolder>] [-ApplicationType <ApplicationType>] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-LocalLaunchDisabled <Boolean>] [-MaxPerMachineInstances <Int32>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerApplication cmdlet creates a new published application in the site.

New-BrokerApplication creates the application object, and associates it with a desktop group or application group. Application objects have three names that identify them (in addition to their Uid): the Name, BrowserName and the PublishedName. The BrowserName is unique across the entire site, and is primarily used internally. The Name is also unique and is what is seen by the administrator; it contains any prefix for an enclosing admin folder (if any). The PublishedName is not unique and is what is seen by the users.

You can create HostedOnDesktop, InstalledOnClient or PublishedContent applications but the ApplicationType cannot be changed later.

The following special characters are not allowed in the Name, BrowserName or the PublishedName properties: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " '

In addition the \` character is not allowed in the Name property.

See about\_Broker\_Applications for more information.


## Related Commands

* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Get-BrokerApplication](./Get-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Move-BrokerApplication](./Move-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the application (must be unique within folder). | true | true (ByPropertyName) |  |
| CommandLineExecutable | Specifies the name of the executable file to launch. The full path need not be provided if it's already in the path. Environment variables can also be used. | true | true (ByPropertyName) | (required) |
| ApplicationGroup | Specifies which application group this application should be associated with. Associations between applications and desktop groups or application groups can be added or removed using the Add-BrokerApplication and Remove-BrokerApplication cmdlets. | true | true (ByPropertyName) |  |
| DesktopGroup | Specifies which desktop group this application should be associated with. Associations between applications and desktop groups or application groups can be added or removed using the Add-BrokerApplication and Remove-BrokerApplication cmdlets. | true | true (ByPropertyName) |  |
| AdminFolder | The folder in which the new application should reside (if any). | false | true (ByPropertyName) |  |
| ApplicationType | Specifies the type of the application: HostedOnDesktop, InstalledOnClient or PublishedContent. | false | true (ByPropertyName) | (required) |
| BrowserName | Specifies the internal name for this application. It must be unique in the site. | false | true (ByPropertyName) | (same as Name) |
| ClientFolder | Specifies the folder that the application belongs to as the user sees it. This is the application folder that is seen in the Citrix Online Plug-in, in Web Services, and also in the end-user's Start menu. Subdirectories can be specified with '\\' character. The following special characters are not allowed: / \* ? &lt; &gt; | " :. Note that this property cannot be set for applications of type InstalledOnClient. | false | true (ByPropertyName) | null |
| CommandLineArguments | Specifies the command-line arguments to use when launching the executable. Environment variables can be used. This setting is ignored for applications of type PublishedContent. | false | true (ByPropertyName) | null |
| CpuPriorityLevel | Specifies the CPU priority for the launched process. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High. Note that this property cannot be set for applications of type InstalledOnClient. | false | true (ByPropertyName) | Normal |
| Description | Specifies the description of the application. This is only seen by Citrix administrators and is not visible to users. | false | true (ByPropertyName) | null |
| Enabled | Specifies whether or not this application can be launched. | false | true (ByPropertyName) | true |
| HomeZoneOnly | Specifies whether if the preferred zone for launching the application is its home zone but no machine is available from that zone then the launch fails.<br>This can only be set if the application has a home zone preference specified. | false | true (ByPropertyName) | false |
| HomeZoneUid | Specifies any home zone preference used when launching this application. | false | true (ByPropertyName) | null |
| IconFromClient | Specifies if the app icon should be retrieved from the application on the client. This is reserved for possible future use, and all applications of type HostedOnDesktop cannot set or change this value. | false | true (ByPropertyName) | false |
| IconUid | Specifies which icon to use for this application. This icon is visible both to the administrator (in the consoles) and to the user. If no icon is specified, then a generic built-in application icon is used. | false | true (ByPropertyName) | 2 |
| IgnoreUserHomeZone | Specifies that when launching the application and the user has a home zone specified then the user's home zone preference should be ignored.<br>This can only be set if the application does not itself have a home zone preference specified. | false | true (ByPropertyName) | false |
| LocalLaunchDisabled | When launching a published application from within a published desktop, do not launch the application in that desktop session. | false | true (ByPropertyName) | true |
| MaxPerMachineInstances | Specifies the maximum allowed concurrently running instances of the application that an individual machine can have. A value of zero allows unlimited usage subject to any site-wide limit. | false | true (ByPropertyName) | 0 |
| MaxPerUserInstances | Specifies the maximum allowed concurrently running instances of the application that an individual user can have. A value of zero allows unlimited usage subject to any site-wide limit. | false | true (ByPropertyName) | 0 |
| MaxTotalInstances | Specifies the maximum allowed total of concurrently running instances of the application in the site. A value of zero allows unlimited usage. | false | true (ByPropertyName) | 0 |
| PublishedName | The name seen by end users who have access to this application. | false | true (ByPropertyName) | The same value as that supplied for the name of the application. |
| SecureCmdLineArgumentsEnabled | Specifies whether the command-line arguments are secured or not. This is reserved for possible future use, and all applications of type HostedOnDesktop can only have this value set to true. | false | true (ByPropertyName) | true |
| ShortcutAddedToDesktop | Specifies whether or not a shortcut to the application should be placed on the user device. This is valid only for the Citrix Online Plug-in. | false | true (ByPropertyName) | false |
| ShortcutAddedToStartMenu | Specifies whether a shortcut to the application should be placed in the user's start menu on their user device. | false | true (ByPropertyName) | false |
| StartMenuFolder | Specifies the name of the start menu folder that holds the application shortcut (if any). This is valid only for the Citrix Online Plug-in. Subdirectories can be specified with '\\' character. The following special characters are not allowed: / \* ? &lt; &gt; | " :. | false | true (ByPropertyName) | null |
| UserFilterEnabled | Specifies whether the application's user filter is enabled or disabled. Where the user filter is enabled, the application is visible only to users who appear in the filter (either explicitly or by virtue of group membership). | false | true (ByPropertyName) | false |
| UUID | An optional GUID for this application. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| Visible | Specifies whether or not this application is visible to users. Note that it's possible for an application to be disabled and still visible. | false | true (ByPropertyName) | true |
| WaitForPrinterCreation | Specifies whether or not the session waits for the printers to be created before allowing the user to interact with the session. Note that this property cannot be set for applications of type InstalledOnClient. | false | true (ByPropertyName) | false |
| WorkingDirectory | Specifies which working directory the executable is launched from. Environment variables can be used. This setting is ignored for applications of type PublishedContent. | false | true (ByPropertyName) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| Priority | Specifies the priority of the mapping between the application and desktop group. A value of zero has the highest priority, with increasing values indicating lower priorities. | false | true (ByPropertyName) |  |

## Input Type

### Depends On Parameter
Parameters can be piped by property name.
## Return Values

### Citrix.Broker.Admin.Sdk.Application
New-BrokerApplication returns an Application object.
## Notes
Usually only the Name is specified with the New-BrokerApplication cmdlet, and the system chooses a BrowserName and PublishedName for you. By default the BrowserName is the same as the Name, if it is unique in the site. If not, then "-x" is appended to the name, where "x" is a number. For instance, if there is already an application with a BrowserName of "Notepad" and a new application is created with a Name of "Notepad", then the new application gets a BrowserName of "Notepad-1". If another "Notepad" is published, it has a BrowserName of "Notepad-2".<br>    That said, the BrowserName can optionally be specified as well.
## Examples

### Example 1
```
C:\PS> New-BrokerApplication -ApplicationType HostedOnDesktop -Name "Notepad" -CommandLineExecutable "notepad.exe" -DesktopGroup PrivateDG1
```
#### Description
Creates and returns an object for a published application called "Notepad" that launches "notepad.exe".
### Example 2
```
C:\PS> New-BrokerApplication -ApplicationType PublishedContent -Name "Citrix.com" -CommandLineExecutable "https://www.citrix.com/" -DesktopGroup SharedDG1
```
#### Description
Creates and returns an object for a published application called "Citrix.com" that launches the URL https://www.citrix.com/.
### Example 3
```
C:\PS> $dg = Get-BrokerDesktopGroup "SharedDG1"

          C:\PS> $app = New-BrokerApplication -ApplicationType HostedOnDesktop -Name "Notepad" -CommandLineExecutable "notepad.exe" -DesktopGroup $dg

          C:\PS> $group = Get-BrokerDesktopGroup -Name "Shared desktop group"

          C:\PS> Add-BrokerApplication $app -DesktopGroup $group

          C:\PS> $fta = Get-BrokerImportedFTA -ExtensionName ".txt"

          C:\PS> New-BrokerConfiguredFTA -ImportedFTA $fta -ApplicationUid $app.Uid
```
#### Description
This is a much more complete example. It creates an application object to publish Notepad and associates it first with the "SharedDG1" desktop group.&lt;br&gt;Next it adds an additional desktop group (one that can host applications), and publishes the application to that desktop group. It then gets the ImportedFTA object for the .txt file-type extension (this assumes file-type associations have already been imported), and then configures it so that ".txt" is associated with the published application.&lt;br&gt;Note: The appropriate access policy and app assignment/entitlement rules must also be configured to allow access to the application.
