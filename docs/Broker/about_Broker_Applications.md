
# about\_Broker\_Applications

## Topic
Citrix Broker SDK - Applications


## Short Description
Describes how to publish and manage hosted applications.


## Long Description
Published applications allow your users to launch applications as if they were installed on their devices when in fact they are hosted remotely. The applications are normally launched in a seamless window, meaning that users see only the application window and not an additional desktop.

Published applications are hosted on either desktop operating systems or server operating systems. Applications are published to users and desktop groups. As such, conceptually they exist "on top" of desktop groups, which are themselves built on top of catalogs. See about\_Broker\_Concepts for more information on catalogs.

There are three types of applications:

* HostedOnDesktop - application runs on a remote machine and is displayed on the local client desktop.
* InstalledOnClient - application is installed and run on the local client machine and has its window overlaid on to a remote desktop.
* PublishedContent - application refers to actual content (using a URL or UNC). File type associations determine what application is run to view the content


### Hosting Applications

There are three main ways of hosting an application: using a private single-session VDI desktop, a shared single-session VDI desktop, and on shared multi-session server operating systems.

An application hosted on a shared single-session VDI desktop, when launched, is hosted on a random machine within the desktop group. An application hosted on a private single-session VDI desktop ensures that when a user launches the application it is always hosted on the same machine. An application hosted on shared multi-session server operating systems ensures that when a user launches the application it is always hosted on one of the least loaded servers in the desktop group.

You control how the application is hosted based on the kind of desktop group that you choose. Shared desktop groups randomly select a machine, and these desktop groups can only be created from catalogs with a Random AllocationType. On the other hand, private desktop groups host the application on the same machine for that user every time, and these desktop group types can only be created from catalogs with a Permanent AllocationType.


### User Access & Assignment
Users are not assigned an application directly, but instead they are required to first have access to the desktop groups on which the applications are published through access policy rules.

With shared desktop groups, access to a published application also needs an application entitlement policy rule. An application entitlement policy rule defines the set of users who are allowed per-session access to desktops in a specified desktop group.

With private desktop groups, access to a published application also needs an application assignment policy rule. An application assignment policy rule defines the set of users who are allowed access to a single application session in a desktop group.

Users are assigned private machines in one of two ways: pre-assigned or assign-on-first-use. Pre-assigned means that individual user accounts have been specified for the machines within that desktop group. A single machine can only have a single user account (not a group account) assigned to it, and likewise a user can only be assigned a single machine within a desktop group.

Assign-on-first-use requires less configuration. Machines are assigned to users the first time they log on. Rather than allocating users directly to machines, instead users are assigned to the private desktop group, either through individual user accounts or through user group accounts. Then, when a user assigned to the desktop group logs on, a machine is automatically allocated to them.


### User Visibility
Users can be further filtered by configuring the visibility filter on top of the application. This restricts the application to a subset of the users that were granted access by the access policy and entitlement/assignment policy rules on the desktop group.


### Multiple Desktop Groups
You can publish an application to multiple desktop groups, which have to be of the same kind. Generally, an application that is published only to private desktop groups is referred to as a "private application". An application that is only published to shared desktop groups is referred to as a "shared application".


### Application Groups
An application group is a group of applications. Applications may be published either by adding them directly to a desktop group, or they may first be assigned to an application group, which may then be added to a desktop group. Adding an application group to a desktop group publishes all of the application group's applications to that desktop group in a single operation. The set of machines on which the application group's applications can be launched may then be restricted further by tagging the desired machines and setting the application group's RestrictToTag property.

Grouping applications together allows for them to be administered as a single unit. For example:

* Moving an application group to a different desktop group has the same effect as moving each of the applications, without the need to move each application individually.
* Disabling an application group disables each application in the group.
* Application groups have a visibility filter that applies to every application within the group (see 'User visibility' above).

Application groups may be configured to allow or disallow session sharing with applications published by other application groups. For example, you may have a particular set of applications that do not interoperate well with certain other applications that are installed on the same machines - for example, two different versions of the same software suite, or two different versions of the same web browser. You may prefer not to allow the user to launch both versions in the same session.

In such a case, an application group can be created for each version of the software suite, and the applications for each version of the software suite added to the corresponding application group. If session sharing is disabled for each of the application groups, then the user will be able to run applications of the same version in the same session, and can still run other applications at the same time - but not in the same session. If the user launches one of the different-versioned applications, which are in a different application group, or launches any application that is not contained in an application group, then that application is launched in a new session.

IMPORTANT. The session sharing feature of application groups is not intended to be a security sandboxing feature. In addition to not being foolproof, it cannot prevent users from launching applications into their sessions through other means (e.g. through Windows Explorer).

An application may be a member of more than one application group. In that case, it inherits settings from all of the application groups of which it is a member. For example, an application is only disabled if all of the application groups to which it is assigned are disabled, or if the application itself is disabled.

However, if application or application group visiblity filters are used, then it is recommended that each application be a member of at most one application group, and that visibility filters are used either on applications, or on application groups, but not both. This is because it is not generally possible for the system to combine multiple visibility filters in such as way that they can consistently be enforced.

An application may also be a member of both an application group and a desktop group at the same time. However, this is not recommended, because the additional complexity can make it harder for the administrator to predict how machines are allocated to users. It is recommended that each application be published either via application groups, or via desktop groups, but not both.

Application groups may not be published via private desktop groups.

Application groups are purely an administrative concept. They are not visible to end users.


### Licensing
Hosted applications need the appropriate licenses to exist on the license server to be functional.


### Naming
Applications have three names that identify them: the Name, BrowserName and the PublishedName. The Name is unique for each application, is not visible to the user, and is primarily used for administrative purpose. The BrowserName is unique across the entire site, and is primarily used internally. The PublishedName is not unique and is the name seen by end users who have access to this application.

When creating an application, you only need to specify the Name. If no BrowserName is specified one is automatically generated. If no PublishedName is specified by default it is the same as the Name.

The following special characters are not allowed in the Name, BrowserName or the PublishedName properties: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " '

In addition the \` character is not allowed in the Name property.

To change the PublishedName or BrowserName of an application you must use the Set-BrokerApplication cmdlet.

To change the Name of an application you must use the Rename-BrokerApplication cmdlet.


### Optional
You can configure file-type associations for applications, so that if a user double-clicks a document icon on their device, a published application automatically starts. For more information, see the help for New-BrokerConfiguredFTA.

You can apply tags to applications as another convenient way to further organize (and search for) applications. For more information, see the help for New-BrokerTag.


### Cmdlets
New-BrokerApplication Creates an application for publishing after the needed desktop groups, access policy and entitlement/assignment policy rules have been created.

Add-BrokerApplication Adds one or more applications to a desktop group.

Get-BrokerApplication Gets one or more applications.

Remove-BrokerApplication Deletes one or more applications or it can be used to delete just the association of an application to a desktop group.

Rename-BrokerApplication Changes the Name of an application.

Set-BrokerApplication Changes the settings of application objects, except their names.


## Examples


### Shared Application (Singlesession)
You have created a catalog with a Random AllocationType and SingleSession SessionSupport. It contains two machines called worker1 and worker2, both in the ACME domain. You publish an application with shared hosting as follows:


```
    C:\PS> Write-Host "Create a desktop group, and add machines to it" 
    C:\PS> $dg = New-BrokerDesktopGroup "Shared Application Group" 
    -DesktopKind Shared -DeliveryType AppsOnly -SessionSupport 'SingleSession' 
    C:\PS> $m1 = Get-BrokerMachine -MachineName "ACME\worker1" 
    C:\PS> $m2 = Get-BrokerMachine -MachineName "ACME\worker2" 
    C:\PS> Add-BrokerMachine $m1 -DesktopGroup $dg 
    C:\PS> Add-BrokerMachine $m2 -DesktopGroup $dg 
    C:\PS> Write-Host "Create access policy rule for desktop group" 
    C:\PS> New-BrokerAccessPolicyRule -Name "Shared Application Group - Allow Everyone Access" 
    -Enabled $true -DesktopGroupUid $dg.Uid -IncludedUserFilterEnabled $true 
    -AllowedProtocols @("HDX") -AllowedUsers AnyAuthenticated 
    C:\PS> Write-Host "Create application entitlement policy for desktop group" 
    C:\PS> New-BrokerAppEntitlementPolicyRule -Name "Shared Application Group - App Entitlement" 
    -IncludedUsers 'ACME\Domain Users' -DesktopGroupUid $dg.Uid -Enabled $true 
    C:\PS> Write-Host "Create an application" 
    C:\PS> New-BrokerApplication -Name "Notepad" -PublishedName "Notepad" 
    -CommandLineExecutable "notepad.exe" -DesktopGroup $dg.Uid 

```
In turn, this set of commands: creates a shared single session desktop group for applications delivery; adds two machines (from a catalog with a Random AllocationType and SingleSession SessionSupport) to the desktop group; creates access policy and application entitlement policy rules; creates an application; specifies its name, the executable, and links the application to the desktop group that will host it.


### Shared Application (Multisession)
You have created a catalog with a Random AllocationType and MultiSession SessionSupport. It contains one machine called worker1 in the ACME domain. You publish an application with shared hosting as follows:


```
    C:\PS> Write-Host "Create a desktop group, and add machines to it" 
    C:\PS> $dg = New-BrokerDesktopGroup "Shared Application Group" 
    -DesktopKind Shared -DeliveryType AppsOnly -SessionSupport 'MultiSession' 
    C:\PS> $m1 = Get-BrokerMachine -MachineName "ACME\worker1" 
    C:\PS> Add-BrokerMachine $m1 -DesktopGroup $dg 
    C:\PS> Write-Host "Create access policy rule for desktop group" 
    C:\PS> New-BrokerAccessPolicyRule -Name "Shared Application Group - Allow Everyone Access" 
    -Enabled $true -DesktopGroupUid $dg.Uid -IncludedUserFilterEnabled $true 
    -AllowedProtocols @("HDX") -AllowedUsers AnyAuthenticated 
    C:\PS> Write-Host "Create application entitlement policy for desktop group" 
    C:\PS> New-BrokerAppEntitlementPolicyRule -Name "Shared Application Group - App Entitlement" 
    -IncludedUsers 'ACME\Domain Users' -DesktopGroupUid $dg.Uid -Enabled $true 
    C:\PS> Write-Host "Create an application" 
    C:\PS> New-BrokerApplication -Name "Notepad" -PublishedName "Notepad" 
    -CommandLineExecutable "notepad.exe" -DesktopGroup $dg.Uid 

```
In turn, this set of commands: creates a shared multi session desktop group for applications delivery; adds one machine (from a catalog with a Random AllocationType and MultiSession SessionSupport) to the desktop group; creates access policy and application entitlement policy rules; creates an application; specifies its name, the executable, and links the application to the desktop group that will host it.


### Private Pre-Assigned Application
You have a catalog with a Permanent AllocationType and SingleSession SessionSupport. It contains two machines called worker1 and worker2, both in the ACME domain. You publish an application with private hosting using pre-assigned machines as follows:


```
    C:\PS> Write-Host "Create a desktop group, and add machines to it" 
    C:\PS> $dg = New-BrokerDesktopGroup "Private App G1" -DesktopKind Private 
    -DeliveryType AppsOnly -SessionSupport 'SingleSession' 
    C:\PS> $m1 = Get-BrokerMachine -MachineName "ACME\worker1" 
    C:\PS> $m2 = Get-BrokerMachine -MachineName "ACME\worker2" 
    C:\PS> Add-BrokerMachine $m1 -DesktopGroup $dg 
    C:\PS> Add-BrokerMachine $m2 -DesktopGroup $dg 
    C:\PS> Write-Host "Setting access policy rule for desktop group" 
    C:\PS> New-BrokerAccessPolicyRule -Name "Private App G1 - Allow Everyone Access" 
    -Enabled $true -DesktopGroupUid $dg.Uid -IncludedUserFilterEnabled $true 
    -AllowedProtocols @("HDX") -AllowedUsers AnyAuthenticated 
    C:\PS> Write-Host "Pre-Assign users to the machines" 
    C:\PS> Add-BrokerUser "ACME\user1" -Machine $m1 
    C:\PS> Add-BrokerUser "ACME\user2" -Machine $m2 
    C:\PS> Write-Host "Create an application" 
    C:\PS> New-BrokerApplication -Name "Notepad" -PublishedName "Notepad" 
    -CommandLineExecutable "notepad.exe" -DesktopGroup $dg.Uid 

```
In turn, this set of commands: creates a private desktop group for applications delivery; adds two machines (from a catalog with a Permanent AllocationType and SingleSession SessionSupport) to the desktop group; creates access policy; creates two user objects; pre-assigns a user to each machine; creates the application; assigns users to it; and links the application to the desktop group that will host it.


### Private, Assign-On-First-Use Application
You have a catalog created with a Permanent AllocationType and SingleSession SessionSupport. It contains two machines called worker1 and worker2, both in the ACME domain. You publish an application with private hosting using assign-on-first-use machines as follows:


```
    C:\PS> Write-Host "Create a desktop group, and add machines to it" 
    C:\PS> $dg = New-BrokerDesktopGroup "Private App G2" -DesktopKind Private 
    -DeliveryType AppsOnly -SessionSupport 'SingleSession' 
    C:\PS> $m1 = Get-BrokerMachine -MachineName "ACME\worker1" 
    C:\PS> $m2 = Get-BrokerMachine -MachineName "ACME\worker2" 
    C:\PS> Add-BrokerMachine $m1 -DesktopGroup $dg 
    C:\PS> Add-BrokerMachine $m2 -DesktopGroup $dg 
    C:\PS> Write-Host "Setting access policy rule for desktop group" 
    C:\PS> New-BrokerAccessPolicyRule -Name "Private App G1 - Allow Everyone Access" 
    -Enabled $true -DesktopGroupUid $dg.Uid -IncludedUserFilterEnabled $true 
    -AllowedProtocols @("HDX") -AllowedUsers AnyAuthenticated 
    C:\PS> Write-Host "Create application assignment policy for desktop group" 
    C:\PS> New-BrokerAppAssignmentPolicyRule -Name "Private App G2 - App Assignment" 
    -IncludedUsers 'ACME\Domain Users' -DesktopGroupUid $dg.Uid -Enabled $true 
    C:\PS> Write-Host "Create an application" 
    C:\PS> New-BrokerApplication -Name "Notepad" -PublishedName "Notepad" 
    -CommandLineExecutable "notepad.exe" -DesktopGroup $dg.Uid 

```
In turn, this set of commands: creates a private single session desktop group for applications delivery; adds two machines (from a catalog with a Permanent AllocationType and SingleSession SessionSupport) to the desktop group; creates access policy and application assignment policy rules; creates the application, and links the application to the desktop group that will host it.


## See Also

* [about\_Broker\_Concepts](./about_Broker_Concepts/)
* [about\_Broker\_Desktops](./about_Broker_Desktops/)
* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [Remove-BrokerAppAssignmentPolicyRule](./Remove-BrokerAppAssignmentPolicyRule/)
* [Set-BrokerAppAssignmentPolicyRule](./Set-BrokerAppAssignmentPolicyRule/)
* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [Remove-BrokerAppEntitlementPolicyRule](./Remove-BrokerAppEntitlementPolicyRule/)
* [Set-BrokerAppEntitlementPolicyRule](./Set-BrokerAppEntitlementPolicyRule/)

