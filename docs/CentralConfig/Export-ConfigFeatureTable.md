
# Export-Configfeaturetable
Returns the current feature table.
## Syntax
```
Export-ConfigFeatureTable [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

* [Set-ConfigSite](./Set-ConfigSite/)
* [Import-ConfigFeatureTable](./Import-ConfigFeatureTable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.String

## Examples

### Example 1
```
C:\PS> Export-ConfigFeatureTable

<?xml version="1.0" encoding="utf-8">

<Products xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="FeatureTable.xsd">

  <Product Code="XDT" Name="XenDesktop">

    <Editions>

      <Edition>PLT</Edition>

      <Edition>ENT</Edition>

      <Edition>APP</Edition>

      <Edition>STD</Edition>

    </Editions>

    <DefaultEdition>PLT</DefaultEdition>

    <VersionToBurninDates>

      <VersionToBurninDate Version="7.0" BurninDate="2013.0522" />

    </VersionToBurninDates>

    <LicensingModels>

      <LicensingModel>Concurrent</LicensingModel>

      <LicensingModel>UserDevice</LicensingModel>

    </LicensingModels>

    <DefaultLicensingModel>UserDevice</DefaultLicensingModel>

    <Features>

      <Feature Name="CustomRole">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="ConfigurationLogging">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleUserMode">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="MultiSessionDesktops">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleSessionDesktops">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="STD" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="MultiSessionApplications">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleSessionApplications">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="HistoricalMonitorData">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="CloudHostedMachines">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="HdxInsightIntegration">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="RemotePC">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

    </Features>

  </Product>

  <Product Code="MPS" Name="XenApp">

    <Editions>

      <Edition>PLT</Edition>

      <Edition>ENT</Edition>

    </Editions>

    <DefaultEdition>PLT</DefaultEdition>

    <VersionToBurninDates>

      <VersionToBurninDate Version="7.0" BurninDate="2013.0522" />

    </VersionToBurninDates>

    <LicensingModels>

      <LicensingModel>Concurrent</LicensingModel>

    </LicensingModels>

    <DefaultLicensingModel>Concurrent</DefaultLicensingModel>

    <Features>

      <Feature Name="CustomRole">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="ConfigurationLogging">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleUserMode">

      </Feature>

      <Feature Name="MultiSessionDesktops">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleSessionDesktops">

      </Feature>

      <Feature Name="MultiSessionApplications">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="SingleSessionApplications">

        <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>

        <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>

      </Feature>

      <Feature Name="HistoricalMonitorData">

      </Feature>

      <Feature Name="CloudHostedMachines">

      </Feature>

      <Feature Name="HdxInsightIntegration">

      </Feature>

      <Feature Name="RemotePC">

      </Feature>

    </Features>

  </Product>

</Products>
```
#### Description
Returns the current feature table.
