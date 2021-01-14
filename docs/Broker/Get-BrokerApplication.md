
# Get-Brokerapplication
Get the applications published on this site.
## Syntax
```
Get-BrokerApplication [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerApplication [[-Name] <String>] [-AdminFolderName <String>] [-AdminFolderUid <Int32>] [-AllAssociatedDesktopGroupUid <Int32>] [-AllAssociatedDesktopGroupUUID <Guid>] [-ApplicationName <String>] [-ApplicationType <ApplicationType>] [-AssociatedApplicationGroupUid <Int32>] [-AssociatedApplicationGroupUUID <Guid>] [-AssociatedDesktopGroupPriority <Int32>] [-AssociatedDesktopGroupUid <Int32>] [-AssociatedDesktopGroupUUID <Guid>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserSID <String>] [-AssociatedUserUPN <String>] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CommandLineExecutable <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneName <String>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-LocalLaunchDisabled <Boolean>] [-MaxPerMachineInstances <Int32>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-MetadataKey <String>] [-Metadata <String>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-Tag <String>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-DesktopUid <Int32>] [-ApplicationGroupUid <Int32>] [-SessionUid <Int64>] [-UserSID <String>] [-DesktopGroupUid <Int32>] [-MachineConfigurationUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerApplication cmdlet gets the published applications that are hosted on this site.

Without parameters, Get-BrokerApplication gets all the applications that have been published, regardless of whether they are visible to users or not. You can also use the parameters of Get-BrokerApplication to filter the results to just the applications you're interested in. You can also identify applications by their UIDs or their BrowserNames.

For more information about applications, see about\_Broker\_Applications.


### Brokerapplication Object
The BrokerApplication object represents a published application in the site. It contains the following properties:


  * AdminFolderName (System.String) The name of the admin folder the application is in (including trailing backslash), or the empty string if the application is at the root level

  * AdminFolderUid (System.Int32) The Uid of the admin folder the application is in (if any)

  * AllAssociatedDesktopGroupUids (System.Int32\[\]) List of associated desktop group uids, including desktop groups that are indirectly associated with the application by virtue of being associated with an application group of which this application is a member.

  * AllAssociatedDesktopGroupUUIDs (System.Guid\[\]) List of associated desktop group UUIDs, including desktop groups that are indirectly associated with the application by virtue of being associated with an application group of which this application is a member.

  * ApplicationName (System.String) The simple name of the application within its parent admin folder (if any)

  * ApplicationType (Citrix.Broker.Admin.SDK.ApplicationType) The type of the application, whether HostedOnDesktop, InstalledOnClient or PublishedContent.

  * AssociatedApplicationGroupUids (System.Int32\[\]) List of associated application group uids.

  * AssociatedApplicationGroupUUIDs (System.Guid\[\]) List of associated application group UUIDs.

  * AssociatedDesktopGroupPriorities (System.Int32\[\]) List of directly associated desktop group priorities. Associated desktop groups is the list of desktop groups on which the application is published. When launching an application an available machine from one of the associated groups is selected. Desktop groups are searched for available machines in order of their priority.

  * AssociatedDesktopGroupUids (System.Int32\[\]) List of directly associated desktop group uids. Associated desktop groups is the list of desktop groups on which the application is published. The list is sorted by priority, with the highest priority group first.

  * AssociatedDesktopGroupUUIDs (System.Guid\[\]) List of directly associated desktop group UUIDs. Associated desktop groups is the list of desktop groups on which the application is published. The list is sorted by priority, with the highest priority group first.

  * AssociatedUserFullNames (System.String\[\]) List of associated users (full names). Associated users is the list of users who are given access using the application/user mapping filter.

  * AssociatedUserNames (System.String\[\]) List of associated users (SAM names). Associated users is the list of users who are given access using the application/user mapping filter.

  * AssociatedUserSIDs (System.String\[\]) List of associated users (SIDs). Associated users is the list of users who are given access using the application/user mapping filter.

  * AssociatedUserUPNs (System.String\[\]) List of associated users (user principle names). Associated users is the list of users who are given access using the application/user mapping filter.

  * BrowserName (System.String) Unique browser name used to identify this application to other components in the site. This value is not visible to the end users.

  * ClientFolder (System.String) The folder that the application belongs to as the user sees it.

  * CommandLineArguments (System.String) The command-line arguments to use when launching the executable.

  * CommandLineExecutable (System.String) The name including the full path of the executable file to launch.

  * ConfigurationSlotUids (System.Int32\[\]) Uids of any configuration slots which hold machine configurations associated with the application. The order of slot UIDs in this list correspond with the order of items in the associated MachineConfigurationNames and MachineConfigurationUids list properties, and so the same slot UID can appear more than once.

  * CpuPriorityLevel (Citrix.Broker.Admin.SDK.CpuPriorityLevel) The CPU priority of the launched process. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High.

  * Description (System.String) Optional application description. This description is visible to the end users.

  * Enabled (System.Boolean) Specifies whether or not this application can be launched.

  * HomeZoneName (System.String) Name of optional preferred home zone for launching the application.

  * HomeZoneOnly (System.Boolean) Indicates that if the preferred zone for launching the application is its home zone but no machine is available from that zone then the launch fails.

  * HomeZoneUid (System.Guid?) Optional preferred home zone for launching the application.

  * IconFromClient (System.Boolean) Specifies if the app icon should be retrieved from the application on the client. This is reserved for possible future use, and all applications of type HostedOnDesktop cannot set or change this value.

  * IconUid (System.Int32?) The icon UID used for this application. If not specified a generic icon is used.

  * IgnoreUserHomeZone (System.Boolean) Indicates that when launching the application and the user has a home zone specified then the user's home zone preference should be ignored.

  * LocalLaunchDisabled (System.Boolean) When launching a published application from within a published desktop, do not launch the application in that desktop session.

  * MachineConfigurationNames (System.String\[\]) The MachineConfiguration names associated with the application.

  * MachineConfigurationUids (System.Int32\[\]) The MachineConfiguration uids associated with the application.

  * MaxPerMachineInstances (System.Int32) Maximum allowed concurrently running instances of the application that an individual machine can have. A value of zero allows unlimited usage subject to any site-wide limit.

  * MaxPerUserInstances (System.Int32) Maximum allowed concurrently running instances of the application that an individual user can have. A value of zero allows unlimited usage subject to any site-wide limit.

  * MaxTotalInstances (System.Int32) Maximum allowed total of concurrently running instances of the application in the site. A value of zero allows unlimited usage.

  * MetadataKeys (System.String\[\]) All key names of metadata items associated with this application.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this application.

  * Name (System.String) Unique administrative name of application; this will include any parent admin folder hierarchy separated by backslash characters.

  * PublishedName (System.String) Published name of application as seen by end user. If not specified value used defaults to the administrative name.

  * SecureCmdLineArgumentsEnabled (System.Boolean) Specifies whether the command-line arguments should be secured.

  * ShortcutAddedToDesktop (System.Boolean) Specifies whether a shortcut to the application should be placed on the user device.

  * ShortcutAddedToStartMenu (System.Boolean) Specifies whether a shortcut to the application should be placed in the user's Start menu on their user device.

  * StartMenuFolder (System.String) The name of the Start menu folder that holds the application shortcut.

  * Tags (System.String\[\]) A list of tags associated with the application.

  * Uid (System.Int32) A unique identifier of the application.

  * UserFilterEnabled (System.Boolean) Indicates if application-specific user filter is enabled.

  * UUID (System.Guid) UUID of the application.

  * Visible (System.Boolean) Specifies if the application is visible to users.

  * WaitForPrinterCreation (System.Boolean) Specifies whether the VDA delays starting the app until printers are set up or not.

  * WorkingDirectory (System.String) The working directory the executable is launched from.


## Related Commands

* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Move-BrokerApplication](./Move-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the application with the specified unique identifier. | true | false |  |
| Name | Gets only the applications matching the specified name (including any parent admin folder hierarchy. | false | false |  |
| AdminFolderName | Gets applications that are in admin folders matching the specified name. | false | false |  |
| AdminFolderUid | Gets applications that are in the specified admin folder. | false | false |  |
| AllAssociatedDesktopGroupUid | Gets applications associated with the desktop group identified by the uid.<br>The application may be either published directly on the desktop group or published indirectly on the desktop group as part of an application group. | false | false |  |
| AllAssociatedDesktopGroupUUID | Gets applications associated with the desktop group identified by the UUID.<br>The application may be either published directly on the desktop group or published indirectly on the desktop group as part of an application group. | false | false |  |
| ApplicationName | Gets applications that match the specified simple name. | false | false |  |
| ApplicationType | Gets applications that match the type specified: HostedOnDesktop, InstalledOnClient or PublishedContent. | false | false |  |
| AssociatedApplicationGroupUid | Gets applications that are members of the application group identified by the uid. | false | false |  |
| AssociatedApplicationGroupUUID | Gets applications that are members of the application group identified by the UUID. | false | false |  |
| AssociatedDesktopGroupPriority | Gets applications with an associated desktop group identified by priority assigned to the pairing between an application and desktop group.<br>Associated desktop group is a desktop group on which the application is published. | false | false |  |
| AssociatedDesktopGroupUid | Gets applications directly associated with the desktop group identified by the uid.<br>The application must be published directly on the desktop group. To search for applications that may be published indirectly on the desktop group as part of an application group, use the AllAssociatedDesktopGroupUid filter instead. | false | false |  |
| AssociatedDesktopGroupUUID | Gets applications directly associated with the desktop group identified by the UUID.<br>The application must be published directly on the desktop group. To search for applications that may be published indirectly on the desktop group as part of an application group, use the AllAssociatedDesktopGroupUid filter instead. | false | false |  |
| AssociatedUserFullName | Gets applications with an associated user identified by their full name (usually 'first-name last-name').<br>If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserName | Gets applications with an associated user identified by their user name (in the form 'domain\\user'). If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserSID | Gets applications with an associated user identified by their Windows SID. If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserUPN | Gets applications with an associated user identified by their user principle name (in the form 'user@domain'). If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| BrowserName | Gets only the applications that match the supplied name. The BrowserName is usually an internal name for the application and is unique in the site. | false | false |  |
| ClientFolder | Gets only the applications that match the specified value for the folder the application belongs to as seen by the end-user. This folder can be seen in the Citrix Online Plug-in, in Web Services, and also potentially in the user's start menu. | false | false |  |
| CommandLineArguments | Gets only the applications that match the supplied arguments to the command-line executable. | false | false |  |
| CommandLineExecutable | Gets only the applications that match the supplied command-line executable. | false | false |  |
| CpuPriorityLevel | Gets only the applications that have the specified value for the CPU priority level of the launched executable. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High. | false | false |  |
| Description | Gets only the applications that match the supplied description. | false | false |  |
| Enabled | Gets only the applications that have the specified value for whether the application is enabled. Disabled applications are still visible to users (that is controlled by the Visible setting) but cannot be launched. | false | false |  |
| HomeZoneName | Gets only applications with a home zone preference matching the specified name. | false | false |  |
| HomeZoneOnly | Gets only applications that have the specified behaviour with respect to forcing use of their home zone during launch. | false | false |  |
| HomeZoneUid | Gets only applications with a home zone preference matching the specified UID. | false | false |  |
| IconFromClient | Gets only the applications that have the specified value for whether the application icon should be retrieved from the user device. | false | false |  |
| IconUid | Gets only the applications that use the specified icon (identified by its Uid). | false | false |  |
| IgnoreUserHomeZone | Gets only applications that have the specified behaviour with respect to ignoring user home zones during launch. | false | false |  |
| LocalLaunchDisabled | Gets only applications that have the specified local launch behaviour | false | false |  |
| MaxPerMachineInstances | Gets only applications with the specified maximum allowed concurrently running instances that an individual machine can have. | false | false |  |
| MaxPerUserInstances | Gets only applications with the specified maximum allowed concurrently running instances that an individual user can have. | false | false |  |
| MaxTotalInstances | Gets only applications with the specified maximum allowed total of concurrently running instances in the site. | false | false |  |
| MetadataKey | Gets only applications whose associated metadata contains key names matching the specified value. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| PublishedName | Gets applications whose published name matches the supplied pattern. | false | false |  |
| SecureCmdLineArgumentsEnabled | Gets only the applications that have the specified value for whether the command-line arguments should be secured. This is reserved for possible future use, and all applications of type HostedOnDesktop can only have this value set to true. | false | false |  |
| ShortcutAddedToDesktop | Gets only the applications that match depending on whether a shortcut for the application has been added to the user device or not. | false | false |  |
| ShortcutAddedToStartMenu | Gets only the applications that match depending on whether a shortcut for the application has been added to Start Menu of the user device or not. | false | false |  |
| StartMenuFolder | Gets only the applications that match the specified name for the start menu folder that holds the application shortcut. This is valid only for the Citrix Online Plug-in. | false | false |  |
| Tag | Gets applications associated with the specified tag. | false | false |  |
| UserFilterEnabled | Gets only applications whose user filter is in the specified state. | false | false |  |
| UUID | Gets applications with the specified value of UUID. | false | false |  |
| Visible | Gets only the applications that have the specified value for whether it is visible to the users. | false | false |  |
| WaitForPrinterCreation | Gets only the applications that match depending on whether the VDA delays starting the application until printers are set up. | false | false |  |
| WorkingDirectory | Gets only the applications that match the specified working directory. | false | false |  |
| DesktopUid | Gets only the applications that have been associated (using a desktop group) to the specified desktop (identified by its Uid). Note that an application is not directly associated with a desktop, but only indirectly by which desktop group it has been published to. | false | false |  |
| ApplicationGroupUid | Gets applications that are members of the application group identified by the uid. | false | false |  |
| SessionUid | Gets only the applications that are running in the specified session (identified by its Uid). | false | false |  |
| UserSID | Gets only applications with their accessibility restricted to include the specified user. | false | false |  |
| DesktopGroupUid | Gets only the applications that have been published to the specified desktop group (identified by its Uid). | false | false |  |
| MachineConfigurationUid | Gets only applications which have an associated machine configuration identified by the given Uid. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Application
Get-BrokerApplication returns an object for each application it gets.
## Notes
Get-BrokerApplication returns just the application object, and as such is not a complete picture. The returned objects do not tell you what File-Type Associations are configured for this application, etc.<br>    Use the following cmdlets to gather data related to applications (shown with examples of syntax):<br>    Get-BrokerConfiguredFTA -ApplicationUid \$app.Uid<br>    Get-BrokerTag -ApplicationUid \$app.Uid<br>    Get-BrokerDesktopGroup -ApplicationUid \$app.Uid<br>    Get-BrokerDesktop -PublishedApplication \$app<br>    Get-BrokerSession -ApplicationUid \$app.Uid<br>    Get-BrokerApplicationInstance -ApplicationUid \$app.Uid
## Examples

### Example 1
```
C:\PS> Get-BrokerApplication Notepad
```
#### Description
Returns the application with the Name of "Notepad".
### Example 2
```
C:\PS> Get-BrokerApplication -PublishedName Note\* -Enabled $true
```
#### Description
Returns the applications that have a PublishedName starting with "Note" and that are enabled.
