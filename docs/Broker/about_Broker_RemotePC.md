
# about\_Broker\_RemotePC

## Topic
Citrix Broker SDK - RemotePC


## Short Description
Overview of the Remote PC feature.


## Long Description
Remote PC allows automatic publishing of a user's physical desktop within a XenDesktop site, so that it can be accessed remotely. The configuration of Remote PC within the Citrix Broker service specifies the rules and relationships that allow the machine to successfully register with a controller in the site, and be made available for the user to start remote sessions.

When Remote PC is configured, there are two steps required for publishing a machine as a Remote PC desktop.

First a VDA must be installed on the machine and it must be configured such that it registers with a controller in a site.

Second, a user must log on to the machine. When the Citrix Broker service detects an active console session for a user, it assigns the user to the machine and publishes it in a Remote PC desktop group.

Remote PC configuration consists of defining relationships between:


  * Machines and catalogs
  * Catalogs and desktop groups
  * Desktop groups and assignment policy rules
  * Assignment policy rules and users

The Citrix Broker service automates the assignment of Remote PC machines to users in two stages. The first stage automatically imports matching unconfigured machines into the site:


  * Suitable machines are automatically added to a Remote PC catalog.
  * The machines are temporarily configured to be in one of the Remote PC desktop groups associated with the catalog.

When a suitable user logs on to the console of the machine, the second stage of the automatic configuration is performed:


  * The machine is configured to be in the desktop group that is appropriate for the user.
  * The machine is assigned to the user that has logged on.
  * The machine desktop is made available to the user remotely, configured to appear as the machine hostname.

Catalogs and desktop groups can be marked as participating in RemotePC automation with the 'IsRemotePC' property, but this property can only be set to true if various other properties of the catalog or desktop group are appropriate. Catalogs must be single-sessioned and contain physical machines. Desktop Groups must be single session, configured to deliver private assigned machines, delivering desktop sessions only.

Catalogs and desktop groups can have the 'IsRemotePC' property cleared to remove them from the RemotePC automation, but only when all RemotePC associations relating to them through RemotePCAccounts and catalog/group relationships have first been removed.


## Machines And Catalogs
Mappings are defined between machines and Remote PC catalogs through the RemotePCAccount cmdlets.

The machine to catalog mappings support the automated addition of machines to catalogs.


### Properties
RemotePCAccounts expose sets of included and excluded machine name filters specified in DOMAIN\\MACHINE format. A MachinesIncluded or MachinesExcluded entry can include asterisk wildcards to generalize matches.

Each RemotePCAccount can specify the Distinguished Name (DN) of an AD container in addition to the machine name filters, in the RemotePCAccount Organisational Unit (OU) property, and this limits the machines that the account objects act on to those that reside at or below that container in the AD domain hierarchy. An AllowSubfolderMatches setting on the RemotePCAccount indicates whether the computer must exist directly within the container to trigger a match, or whether it can be in a child below the defined container in the AD hierarchy.

Note that the AD container component is optional and a special value of 'any' can be supplied in the OU field to permit the RemotePCAccount to automatically match regardless of the AD machine object location in the AD domain hierarchy. A match is still subject to machine name filtering.

The last component of the RemotePCAccount is the CatalogUid. This indicates which catalog the Remote PC automation should move the machine into when a match is found.


### Constraints
The IsRemotePC setting must be enabled on catalogs before they can be specified in a RemotePCAccount.

There can be any number of RemotePCAccounts configured in the site as long as each specifies a unique OU. There can be only one RemotePCAccount with the 'any' OU.


### Automation
When a machine matching the criteria set up in a RemotePCAccount instance registers with one of the brokers in the site, it is automatically added to the catalog defined by the RemotePCAccount. This can take up to 30 seconds to happen after the machine registers.

When the machine registration occurs, the machine details can match more than one RemotePCAccount instance, but the machine can only be placed into one catalog, so one RemotePCAccount instance is chosen from the list that best matches the machine. This choice is made according to the length in nodes of the DN of the AD container specification associated with the RemotePCAccount, so more specific child OUs override specifications for their parent OUs if both are present. The RemotePCAccount for the 'any' OU is always last and  used only if no other instances match.

A Windows eventlog message is generated when an automated catalog assignment is performed.


### Notes
The AD distinguished name for the container is checked when the RemotePCAccount is created, but if the container is subsequently moved or deleted, the site does not automatically accommodate this, and the RemotePCAccount must be changed or removed manually.


### Related Cmdlets

* [New-BrokerRemotePCAccount](./New-BrokerRemotePCAccount/)
* [Get-BrokerRemotePCAccount](./Get-BrokerRemotePCAccount/)
* [Set-BrokerRemotePCAccount](./Set-BrokerRemotePCAccount/)
* [Remove-BrokerRemotePCAccount](./Remove-BrokerRemotePCAccount/)
* [New-BrokerCatalog \[-IsRemotePC &lt;Boolean&gt;\]](./New-BrokerCatalog/)
* [Set-BrokerCatalog \[-IsRemotePC &lt;Boolean&gt;\]](./Set-BrokerCatalog/)

## Catalogs And Desktop Groups
A Remote PC catalog may be associated with one or more Remote PC desktop groups. The catalog to desktop group associations support automated publishing of machines to users.


### Usage
An association is formed via: Add-BrokerDesktopGroup -RemotePCCatalog &lt;Catalog&gt; \[-Priority &lt;Int32&gt;\]

An association is broken via: Remove-BrokerDesktopGroup -RemotePCCatalog &lt;Catalog&gt;

To find associated desktop groups: Get-BrokerDesktopGroup -RemotePCCatalogUid &lt;Int32&gt;


### Automation
When a machine in a Remote PC catalog is not already assigned to a user, Remote PC automation temporarily places the machine in one of the desktop groups associated with the catalog. The temporary placing of the machine in a group will be adjusted as needed when the machine assignment to a user is first made.

The desktop group chosen as the temporary home for a machine is according to the priority value supplied when making the association between the group and the catalog. The group with the highest priority (lowest numerical priority value) is chosen.

A Windows eventlog message is generated when an automated machine assignment is performed.


### Priority
Each desktop group to catalog association has a priority value that can be specified when the association is made or defaults to lower than the lowest existing association priority (highest numerical value) or zero if no other association exists yet. The lower the priority numerical value, the higher the priority level. The priority value for the association is used to choose the temporary desktop group to place a new RemotePC machine in when it first registers. It is also used to decide which group to finally place the machine in when the user that the machine is being assigned to is appropriate for more than one of the associated desktop groups, usually because the desktop groups are using AD security groups for the user associations with the desktop groups.

The priority values for each association between a desktop group and a catalog are automatically maintained as unique for each catalog, and priorities can be adjusted up or down accordingly by the system. The last association created without a specified priority is always arranged to have the least priority (the highest numerical priority value).


### Notes
The temporary placement of the machines in a desktop group is not re-evaluated if settings change after the automatic placement.


### Related Cmdlets

* [Add-BrokerDesktopGroup -RemotePCCatalog &lt;Catalog&gt;](./Add-BrokerDesktopGroup/)
* [Remove-BrokerDesktopGroup \[-RemotePCCatalog &lt;Catalog&gt;\]](./Remove-BrokerDesktopGroup/)
* [Get-BrokerDesktopGroup \[-RemotePCCatalogUid &lt;Int32&gt;\]](./Get-BrokerDesktopGroup/)
* [New-BrokerCatalog \[-IsRemotePC &lt;Boolean&gt;\]](./New-BrokerCatalog/)
* [Set-BrokerCatalog \[-IsRemotePC &lt;Boolean&gt;\]](./Set-BrokerCatalog/)
* [New-BrokerDesktopGroup \[-IsRemotePC &lt;Boolean&gt;\]](./New-BrokerDesktopGroup/)
* [Set-BrokerDesktopGroup \[-IsRemotePC &lt;Boolean&gt;\]](./Set-BrokerDesktopGroup/)

## Desktop Groups, Assignment Policy Rules, And Users
Assignment policy rules are used to define sets of users allowed to be assigned to machines by Remote PC automation, and to determine which desktop group the machine is placed in when the user assignment is made.


### Automation
A machine is automatically assigned to a user when the Citrix Broker service sees that the user has logged on to a RemotePC machine, and the user is amongst those configured in the desktop group assignment policy rule. If this is the first assignment of a user to a machine, all the assignment policy rules for all groups associated with the machine are checked, and the machine can be moved to a different, more appropriate desktop group if needed.

A Windows eventlog message is generated when an automated assignment of a machine to a user is made.


### Multiple Assignments
By default, multiple automatic assignments of users to the same machine can be established if multiple users log on to the RemotePC machine, but this can be disabled if desired using a registry setting (see CTX137805).


### Notes
User to machine assignments can still be made and removed manually through the Powershell SDK for machines in Remote PC catalogs and desktop groups.

The automatic placement of a machine in an appropriate desktop group happens when the first automatic assignment of a user to the machine is made, and this placement will not be automatically updated if the configuration subsequently changes.

Only a single assignment policy rule is allowed for each RemotePC desktop group.


### Related Cmdlets

* [New-BrokerUser](./New-BrokerUser/)
* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [Set-BrokerAssignmentPolicyRule](./Set-BrokerAssignmentPolicyRule/)

## Example
The following example creates a simple configuration that allows any user and machine in the current AD domain to participate in RemotePC.


```
    # Create a Remote PC catalog 
    $catalog = New-BrokerCatalog -IsRemotePC $true 
                                 -SessionSupport SingleSession 
                                 -MachinesArePhysical $true 
                                 -AllocationType Static 
                                 -PersistUserChanges OnLocal 
                                 -ProvisioningType Manual 
                                 -Name RemotePCCatalog 

```

```
    # Create a Remote PC desktop group 
    $dg = New-BrokerDesktopGroup -IsRemotePC $true 
                                 -SessionSupport SingleSession 
                                 -DeliveryType DesktopsOnly 
                                 -DesktopKind Private 
                                 -Name RemotePCDesktopGroup 

```

```
    # Create an assignment policy rule for that desktop group allowing any 
    # domain user to match. 
    New-BrokerAssignmentPolicyRule -DesktopGroupUid $dg.Uid 
                                   -IncludedUsers 'domain users' 
                                   -Name RemotePCAPR 

```

```
    # Create a RemotePCAccount matching any unconfigured machine, causing the 
    # machines to be added to the catalog by Remote PC automation. 
    New-BrokerRemotePCAccount -OU 'any' 
                              -CatalogUid $catalog.Uid 

```

```
    # Associate the desktop group and catalog to permit domain users to be 
    # automatically assigned to machines in that catalog 
    Add-BrokerDesktopGroup $dg -RemotePCCatalog $catalog 

```

```
    # Create an access policy rule, allowing access to the users to the 
    # Remote PC desktop group. 
    New-BrokerAccessPolicyRule -IncludedUsers 'domain users' 
                               -DesktopGroupUid $dg.Uid 
                               -IncludedUserFilterEnabled $true 
                               -Name RemotePCAccessPolicyRule 

```

