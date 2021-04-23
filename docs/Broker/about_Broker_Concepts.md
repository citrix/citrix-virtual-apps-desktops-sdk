
# about\_Broker\_Concepts

## Topic
Citrix Broker - Concepts


## Short Description
Overview of the Citrix Broker.


## Long Description
The Citrix Broker is a Microsoft Windows service running on a delivery controller that responds to desktop/application launch requests from users through StoreFront by selecting a suitable machine, powering it up if necessary, and then returning the address of the selected machine to the user's endpoint system so that a session connection can be made. If required for resilience or scale, additional instances of the Broker may be installed to run on additional delivery controllers in the same delivery site.

In addition to handling launch requests, the Broker also has background responsibilities in the delivery site; these include: maintaining appropriate numbers of unused, powered-up machines to avoid unnecessary delays to users launching desktops/applications; maintaining periodic contact with powered-up machines; and monitoring the state of machines and user sessions.

The Citrix.Broker.Admin PowerShell snap-in provides the cmdlets needed to administer and monitor the behaviour of the Broker service, either on the local system (by default) or on another system (by use of the -AdminAddress command-line parameter).

The cmdlets in the broker SDK manage objects in the following broad functional areas:


### Provisioning Configuration
The Broker must be informed of the machines which are at its disposal. In order to do this, machines are organized in catalogs, created with the New-BrokerCatalog cmdlet; machines are introduced into the system through the use of the New-BrokerMachine cmdlet.

Catalogs define the nature of the machines contained within them, such as the allocation type (that is, static or random), how the machines are actually provisioned (that is, by MCS, PVS or manually), whether they are physical or virtual machines, whether they are single-session or multi-session, etc.

Typically, machines configured from a provisioning standpoint are not associated with specific users (though they may need to be, for example if the machine's disk image was captured from a specific user's physical desktop using a P2V tool); this is normally done when configuring how resources are brokered to users, below.

It is also possible for a catalog to be configured to be populated automatically with end users’ existing physical machines using the RemotePC feature. The about\_Broker\_RemotePC topic gives more detail.

Provisioning configuration involves the following SDK objects:

  * BrokerHypervisorConnection
  * BrokerCatalog
  * BrokerMachine
  * BrokerRemotePCAccount
  * BrokerUser

    For more information, see: 

* [about\_Broker\_Machines](./about_Broker_Machines/)
* [about\_Broker\_RemotePC](./about_Broker_RemotePC/)
* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
* [Get-BrokerUser](./Get-BrokerUser/)

### Brokering Configuration

In order that resources (that is, desktops and applications) can be used in user sessions, the Broker must be configured to connect incoming user launch requests through StoreFront with the correct machine. This is achieved by adding machines to desktop groups. The grouping of machines in desktop groups need not necessarily match the grouping of the machines within the catalogs that were used for the configuration of provisioning. It is through the desktop group that the configuration of which users can use which machine resources is achieved.

Configuration of the mapping between resources and end users is achieved through a combination of machine assignment and entitlement rules. In addition, access to those resources must also be configured (for example, some resources could be configured only to be accessible to users when they are not connecting remotely through Access Gateway.) The about\_Broker\_Policies topic gives more detail of the rich configuration options available.

It is also possible for a desktop group to be configured to be populated automatically with end users’ existing physical machines using the RemotePC feature. The about\_Broker\_RemotePC topic gives more detail.

When machines are virtual, the broker can be configured to minimize power usage by switching them off when they are not expected to be in use while still maintaining good response times for end-user launch requests. This is achieved through power policy for desktop groups. This allows separate configuration for peak compared to off-peak times of the week of the number of machines nominally to be powered up, the number of machines to be powered up and idling, in addition to those in use to be used as a "buffer" to ensure prompt servicing of user launch requests, and the behavior required for virtual machines when users disconnect from their sessions for extended periods of time.

It is also possible to issue explicit power commands to machines. The about\_Broker\_PowerManagement topic gives more detail.

Configuration of Brokering involves the following SDK objects:

  * BrokerDesktopGroup
  * BrokerPrivateDesktop
  * BrokerSharedDesktop
  * BrokerRemotePCAccount
  * BrokerPowerTimeScheme
  * BrokerUser
  * BrokerTag
  * BrokerAccessPolicyRule
  * BrokerAssignmentPolicyRule
  * BrokerEntitlementPolicyRule
  * BrokerApplication
  * BrokerApplicationGroup
  * BrokerApplicationInstance
  * BrokerAppAssignmentPolicyRule
  * BrokerAppEntitlementPolicyRule
  * BrokerConfiguredFTA
  * BrokerImportedFTA

    For more information, see: 

* [about\_Broker\_Desktops](./about_Broker_Desktops/)
* [about\_Broker\_Policies](./about_Broker_Policies/)
* [about\_Broker\_Applications](./about_Broker_Applications/)
* [about\_Broker\_RemotePC](./about_Broker_RemotePC/)
* [Get-BrokerPrivateDesktop](./Get-BrokerPrivateDesktop/)
* [Get-BrokerSharedDesktop](./Get-BrokerSharedDesktop/)
* [Get-BrokerPowerTimeScheme](./Get-BrokerPowerTimeScheme/)
* [Get-BrokerUser](./Get-BrokerUser/)
* [Get-BrokerTag](./Get-BrokerTag/)
* [Get-BrokerAccessPolicyRule](./Get-BrokerAccessPolicyRule/)
* [Get-BrokerAssignmentPolicyRule](./Get-BrokerAssignmentPolicyRule/)
* [Get-BrokerEntitlementPolicyRule](./Get-BrokerEntitlementPolicyRule/)

### Monitoring And Administration

After you have provisioned and configured machines for brokering, use the broker SDK to monitor and administer user sessions and other aspects of the delivery site.

Monitoring and administration involve the following SDK objects:

  * BrokerServiceStatus
  * BrokerHypervisorAlert
  * BrokerDesktop
  * BrokerDesktopUsage
  * BrokerHostingPowerAction
  * BrokerSession
  * BrokerSessionMessage

    For more information, see: 

* [about\_Broker\_Desktops](./about_Broker_Desktops/)
* [Get-BrokerServiceStatus](./Get-BrokerServiceStatus/)
* [Get-BrokerHypervisorAlert](./Get-BrokerHypervisorAlert/)
* [Get-BrokerDesktop](./Get-BrokerDesktop/)
* [Get-BrokerDesktopUsage](./Get-BrokerDesktopUsage/)
* [Get-BrokerHostingPowerAction](./Get-BrokerHostingPowerAction/)
* [Get-BrokerSession](./Get-BrokerSession/)
* [Send-BrokerSessionMessage](./Send-BrokerSessionMessage/)

### Site Management

The broker must be configured after installation; this is normally performed automatically by the Citrix Studio console. Configuration tasks include selecting the database (and obtaining the SQL scripting to initialize it), selecting the Citrix Configuration Service that holds the site configuration.

Note that some aspects of broker configuration (such as the port number on which the broker listens for SDK connections) cannot be configured with PowerShell cmdlets. These are configured through the use of the Broker Service executable. For more information, see about\_Broker\_PostInstallPreConfiguration.

A further important aspect of site management concerns the way in which machines providing resources identify the delivery controllers to which they belong. For more information, see about\_Broker\_ControllerDiscovery.

Managing XenDesktop sites involves the following SDK objects:

  * BrokerSite
  * BrokerController
  * BrokerDBConnection
  * BrokerDBSchema
  * BrokerDBVersionChangeScript
  * BrokerInstalledDbVersion
  * BrokerServiceInstance
  * BrokerServiceGroupMembership
  * BrokerNameCache

    For more information, see: 

* [about\_Broker\_PostInstallPreConfiguration](./about_Broker_PostInstallPreConfiguration/)
* [about\_Broker\_ControllerDiscovery](./about_Broker_ControllerDiscovery/)
* [Get-BrokerSite](./Get-BrokerSite/)
* [Get-BrokerController](./Get-BrokerController/)
* [Get-BrokerDBConnection](./Get-BrokerDBConnection/)
* [Get-BrokerDBSchema](./Get-BrokerDBSchema/)
* [Get-BrokerDBVersionChangeScript](./Get-BrokerDBVersionChangeScript/)
* [Get-BrokerInstalledDbVersion](./Get-BrokerInstalledDbVersion/)
* [Get-BrokerServiceInstance](./Get-BrokerServiceInstance/)
* [Reset-BrokerServiceGroupMembership](./Reset-BrokerServiceGroupMembership/)
* [Update-BrokerNameCache](./Update-BrokerNameCache/)

