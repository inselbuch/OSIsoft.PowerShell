# OSIsoft PowerShell Plug-In Consolidated Help Files


[[_TOC_]]



##    ConvertFrom-AFRelativeTime

SYNOPSIS
    Converts a PI Time string into a DateTime
    
    

    ----------  EXAMPLE 1  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "*"
    
    This example will return a System.DateTime for the current time in UTC.
    
    ----------  EXAMPLE 2  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "*-2h"
    
    This example will return a System.DateTime for "two hours ago" in UTC.
    
    ----------  EXAMPLE 3  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "T+8h -LocalTime"
    
    This example will return a System.DateTime for "today at 8am" in the local 
    machine's time zone.
    
    ----------  EXAMPLE 4  ----------
    
    Get-PIValue -PointName "Sinusoid" -Time (ConvertFrom-AFRelativeTime 
    -RelativeTime "*") -ArchiveMode Interpolated -Connection $con
    
    This example uses the ConvertFrom-AFRelativeTime cmdlet to get the 
    interpolated value of tag "sinusoid" at the current time.


##    Add-AFAttribute

SYNOPSIS
    Add an AF Attribute
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFAttribute -Name "Interior Temperature" -Description "Interior 
    temperature in celsius for Anneal Oven 1" -CheckIn -AFElement $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates the AF Attribute "Interior Temperature" on the top level element 
    "Anneal Oven 1" on the database "AFDatabase1" on the AF Server "PIAF1". A 
    description is also added to the new attribute. The changes are 
    immediately checked in.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFAttribute -Name "Interior Temperature" -DefaultUnitOfMeasure 
    (Get-AFUnitOfMeasure -Name "degree celsius" -AFServer (Get-AFServer -Name 
    "PIAF1")) -CheckIn -AFElement $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates a new AF Attribute with name "Interior Temperature" and default 
    unit of measure "degree celsius" on the top level element "Anneal Oven 1" 
    on the database "AFDatabase1" on the AF Server "PIAF1". The changes are 
    checked in immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Add-AFAttribute -Name "Interior Temperature" -DefaultUnitOfMeasure 
    (Get-AFUnitOfMeasure -Name "degree celsius" -AFServer (Get-AFServer -Name 
    "PIAF1")) -DataReferencePluginName "PI Point" -CheckIn -AFElement 
    $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates a new AF Attribute with name "Interior Temperature" as a PI Point 
    data reference and default UOM "degrees celsius" on the top level element 
    "Anneal Oven 1" on the database "AFDatabase1" on the AF Server "PIAF1". 
    The changes are checked in immediately.
    
    ----------  EXAMPLE 4  ----------
    
    Add-AFAttribute -Name "Temperature (F)" -DefaultUnitOfMeasure 
    (Get-AFUnitOfMeasure -Name "degree fahrenheit" -AFServer (Get-AFServer 
    -Name "PIAF1")) -DataReferencePluginName "PI Point" -CheckIn -AFAttribute 
    $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Interior Temperature" -AFElement 
    $afElement
    
    Creates a new sub AF Attribute with name "Temperature (F)" as a PI Point 
    data reference and default UOM "degrees fahrenheit" on the top level 
    element "Anneal Oven 1" on the database "AFDatabase1" on the AF Server 
    "PIAF1". The changes are checked in immediately.


##    Add-AFAttributeTemplate

SYNOPSIS
    Add an AF Attribute Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFAttributeTemplate -Name "Interior Temperature" -Description 
    "Interior temperature" -CheckIn -AFElementTemplate $afEleTemplate
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates the AF Attribute Template "Interior Temperature" on the element 
    template "Oven" on the database "AFDatabase1" on the AF Server "PIAF1". 
    Changes are checked in immediately, and a description is added to the 
    attribute template.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFAttributeTemplate -Name "Interior Temperature" -DefaultUnitOfMeasure 
    (Get-AFUnitOfMeasure -Name "degree celsius" -AFServer (Get-AFServer -Name 
    "PIAF1")) -CheckIn -AFElementTemplate $afEleTemplate
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates an AF Attribute Template "Interior Temperature" on the element 
    template "Oven" on the database "AFDatabase1" on the AF Server "PIAF1" 
    with a default UOM of "degree celsius". The changes are checked in 
    immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Add-AFAttributeTemplate -Name "Interior Temperature" 
    -DataReferencePluginName "PI Point" -CheckIn -AFElementTemplate 
    $afEleTemplate
    
    Where:
    
    $afEleTemplate= Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Creates the AF Attribute Template "Interior Temperature" as a PI Point 
    data reference on the element template "Oven" on the database 
    "AFDatabase1" on the AF Server "PIAF1". The changes are checked in 
    immediately.

##    Add-AFCategory

SYNOPSIS
    Add an AF Category
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFCategory -Name "Product A Manufacturing" -Element -CheckIn 
    -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Adds a new AF Element Category "Product A Manufacturing" to the AF 
    Database "AFDatabase1" on AF Server "PIAF1". The change is checked in 
    immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFCategory -Name "KPIs" -Description "KPIs for Product A Process" 
    -Attribute -CheckIn -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Adds a new AF Attribute Category "KPIs" with a description to the AF 
    Database "AFDatabase1" on AF Server "PIAF1". The change is checked in 
    immediately.


##    Add-AFDatabase

SYNOPSIS
    Add an AF Database
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFDatabase -Name MyNewDB -AFServer (Get-AFServer -Default)
    
    This example will add a new AF Database to the default AF Server in the 
    local AF Servers list.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFDatabase -Name MyNewDB -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will add the AF Database "MyNewDB" to the AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Add-AFDatabase -Name MyNewDB -Description "New Corporate AF Database" 
    -Default -AFServer -DefaultPIServerName "DEFPISERV" (Get-AFServer -Name 
    "PIAF1")
    
    This example will add an AF Database called "MyNewDB" to the AF Server 
    "PIAF1" with a description and specified default PI Server and the new AF 
    Database will be set as the default database.


##    Add-AFElement

SYNOPSIS
    Add an AF Element
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFElement -Name "Boiler 1" -AFDatabase $afDB -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Adds the top level element "Boiler 1" to the database "AFDatabase1" on the 
    AF Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFElement -AFElement $afElement -Name "Boiler 1" -Description "Boiler 
    on Production Line 1" -CheckIn
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Adds a child element of "Production Line 1" called "Boiler 1" to the 
    database "AFDatabase1" on the AF Server "PIAF1". The change is checked in 
    immediately.


##    Add-AFElementTemplate

SYNOPSIS
    Add an AF Element Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFElementTemplate -Name "Boiler" -AFDatabase $afDB -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Adds the element template "Boiler" to the database "AFDatabase1" on the AF 
    Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFElementTemplate -Name "Boiler" -Description "Template for all 
    Boilers" -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Adds the Element Template of "Boiler" to the database "AFDatabase1" on the 
    AF Server "PIAF1" with an added description. The change is checked in 
    immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Add-AFElementTemplate -Name "Boiler" -Description "Template for all 
    Boilers" -AFCategories (Get-AFCategory -AFDatabase $afDB -Name "Boiler" 
    -Element) -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Adds the Element Template of "Boiler" to the database "AFDatabase1" on the 
    AF Server "PIAF1" with an added description. The change is checked in 
    immediately. A description is added to the element template as well as 
    adding the existing AF Category "Boilers" to the template.


##    Add-AFEventFrame

SYNOPSIS
    Add an AF Event Frame(s)
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFEventFrame -Name "Equipment Maintenance Downtime" -Description 
    "Manual downtime event" -StartTime "1-Nov-2017 08:00:00" -EndTime 
    "1-Nov-2017 17:00:00" -CheckIn -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Creates and Event Frame in the past representing a planned downtime. The 
    event frame is not tied to an AF Element Template and was not created by 
    an analysis. The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFEventFrame -Name "Boiler Downtime" -Description "Boiler downtime 
    event" -StartTime "4-Nov-2017 08:25:00" -EndTime "4-Nov-2017 08:55:00" 
    -CheckIn -AFAnalysis $afAnalysis -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElement = Get-AFElment -Name Boiler1 -Refresh -AFDatabase $afDB
    
    $afAnalysis = $afElement.Analyses[0]
    
    Creates an AF Event Frame in the past representing a downtime for 
    "Boiler1". The event frame is marked as being created by the AF Analysis 
    on the Boiler1 element. The change is checked in immediately.


##    Add-AFPort

SYNOPSIS
    Add an AF Port
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFPort -Name InputPort1 -AFPortType Input -AFElementTemplate 
    $afElementTemplate -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElementTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    This example will create a new AF Port on the Boiler AF Element Template. 
    The port will be an Input port, and the change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFPort -Name UndirectedPort1 -AFPortType Undirected -MaxConnections 5 
    -AFElement $afElement -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElement = Get-AFElement -Name WestSite -AFDatabase $afDB
    
    This example will create a new AF Port on the WestSite top level AF 
    Element. It will be undirected, restrict the number of connections to 5, 
    and the change will be checked in immediately.


##    Add-AFSecurity

SYNOPSIS
    Add AF Security to AF objects
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFSecurity -AFSecurityIdentity $afIdentity -ApplyTo $afDB 
    -AFSecurityOperation Replace -AccessRights ReadWrite -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afIdentity = Get-AFSecurityIdentity -Name Engineers -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Give the AF Security Identity "Engineers" read and write access to the AF 
    Database "AFDatabase1" on the AF Server "PIAF1". The Replace AFSecurity 
    option means this will overwrite any previously configured security for 
    Engineers security identity.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFSecurity -AFSecurityIdentity $afIdentity -ApplyTo $afDB 
    -AFSecurityOperation Merge -AccessRights Subscribe -AFServer (Get-AFServer 
    -Name PIAF1)
    
    Where:
    
    $afIdentity = Get-AFSecurityIdentity -Name Engineers -AFServer 
    (Get-AFServer -Name PIAF1)
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Give the AF Security Identity "Engineers" Subscribe permissions on the AF 
    Element "Production Line 1" on the AF Database "AFDatabase1" on the AF 
    Server "PIAF1". The Merge option is used to merge the security settings 
    already existing on the element, with the security settings to be added.


##    Add-AFSecurityIdentity

SYNOPSIS
    Adds an AF Security Identity to an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFSecurityIdentity -Name "Floor Operators" -Description "All plant 
    floor operators" -CheckIn -AFServer (Get-AFServer -Name "PIAF1")
    
    Adds an AF Security Identity "Floor Operators" to the AF Server "PIAF1". 
    The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    $MyNewIdentity = Add-AFSecurityIdentity -Name "Floor Operators" 
    -Description "All plant floor operators" -CheckIn -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    Adds an AF Security Identity "Floor Operators" to the AF Server "PIAF1" 
    and stores the new object in $MyNewIdentity. The change is checked in 
    immediately.


##    Add-AFSecurityMapping

SYNOPSIS
    Adds an AF Security Mapping to an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFSecurityMapping -Name TestUserMapping -WindowsAccount 
    "domain\testuser" -AFSecurityIdentity $Engineers -CheckIn -AFServer 
    (Get-AFServer -Name "PIAF1")
    
    Where:
    
    $Engineers = Get-AFSecurityIdentity -Name "Engineers" -Refresh -AFServer 
    (Get-AFServer -Name "PIAF1")
    
    Creates a new AF Security Mapping for the Windows Account 
    "domain\testuser" called "TestUserMapping" and maps him/her to the 
    Engineers AF Security Identity on the AF Server "PIAF1"
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFSecurityMapping -Name PIAdminstrator -WindowsAccount 
    "domain\adminaccount" -AFSecurityIdentity $Administrators -CheckIn 
    -AFServer (Get-AFServer -Name PIAF1)
    
    Where:
    
    $Administrators = Get-AFSecurityIdentity -Name "Administrators" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Creates a new AF Security Mapping for the Windows Account 
    "domain\adminaccount" called "PIAdministrator" and maps him/her to the 
    Administrators AF Security Identity on the AF Server "PIAF1"


##    Add-AFServer

SYNOPSIS
    Add an AF Server to the local AF Servers list
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFServer -Name PIAF1 -Description "Corporate PI AF Server" -Path PIAF1 
    -Timeout 00:01:00 -DefaultPIServerName "DEFPISERV"
    
    This example will add an AF Server with name PIAF1 and hostname PIAF1 and 
    default PI server DEFPISERV with a communication timeout of 1 minute. Note 
    that the network path can be a machine name, IP address, or Fully 
    Qualified Domain Name (FQDN).
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFServer -Name PIAF1 -Description "Corporate PI AF Server" -Path 
    10.32.58.22
    
    This example will add an AF Server with name PIAF1 and IP address 
    10.32.58.22 with a communication timeout (not specified) of the global 
    default, which is typically 300 seconds.


##    Add-AFTrustedProvider

SYNOPSIS
    Add a Trusted Provider in the PISystem
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Add-AFTrustedProvider -ProviderName "SampleProviderName"
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Adds the "SampleProviderName" provider as a trusted provider in PISystem 
    specified by the AFServer


##    Add-AFUnitOfMeasure

SYNOPSIS
    Add an AF Unit of Measure
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-AFUnitOfMeasure -Name "decimeter" -Abbreviation "dm" 
    -ReferenceUnitOfMeasure $refUOM -ReferenceFactor 0.1 -ReferenceOffset 0 
    -CheckIn -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $refUOM = Get-AFUnitOfMeasure -Name "meter" -AFServer $afServer
    
    Creates a new AF UOM "decimeter" using a reference factor and reference 
    offset. A decimeter is equal to 0.1 meters, with SI abbreviation "dm". The 
    change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFUnitOfMeasure -Name "decimeter" -Abbreviation "dm" 
    -ReferenceUnitOfMeasure $refUOM -ToFormula "dm = m * 10" -FromFormula "m = 
    dm / 10" -CheckIn -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $refUOM = Get-AFUnitOfMeasure -Name "meter" -AFServer $afServer
    
    Creates a new AF UOM "decimeter", using toformula and fromformula. A 
    decimeter is equal to 0.1 meters, with SI abbreviation "dm". The change is 
    checked in immediately.
    
    Note that formula UOMs have limitations and also performance impacts and 
    reference offset/factor UOMs should be used whenever possible. This is 
    example is provided for demonstration purposes only, and a "decimeter" AF 
    UOM should be created as shown in the first example.


##    Add-AFUnitOfMeasureClass

SYNOPSIS
    Add an AF Unit of Measure Class
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-UnitOfMeasureClass -Name "MyUOMClass" -CanonicalAbbreviation "MU" 
    -CanonicalUnit "MyUnit" -CheckIn -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    This example creates a new AF Unit of Measure Class on AF Server "PIAF1" 
    called "MyUOMClass". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFUnitOfMeasureClass -Name Force -CanonicalUnitOfMeasureName "newton" 
    CanonicalAbbreviation "N" -BaseUnitOfMeasureClass @($length,$time,$mass) 
    -BaseUnitOfMeasurePower @(1,-2,1) -CheckIn -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $length = Get-AFUnitOfMeasureClass -Name Length -AFServer $afServer
    
    $time = Get-AFUnitOfMeasureClass -Name Time -AFServer $afServer
    
    $mass = Get-AFUnitOfMeasureClass -Name Mass -AFServer $afServer
    
    This example would create the AF Unit of Measure "Force" on the AF Server 
    "PIAF1". This example is shown for illustrative purposes only and should 
    not be used as is because the "Force" Unit of Measure class exists by 
    default on the AF Server.


##    Add-PICollectiveMember

SYNOPSIS
    Add a PI Data Archive to an existing PI Data Archive Collective
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PICollectiveMember -Name "PISRV3" -PICollective (Get-PICollective 
    -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Adds the PI Data Archive "PISRV3" to the PI Data Archive collective which 
    the "PISRV1" PI Data Archive server is a part of. This example should be 
    referenced for PI Data Archive versions 2016R2 or earlier.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PICollectiveMember -Name "PISRV3" -PublicCertificate $cert 
    -PICollective (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    $cert = ( Get-ChildItem -Path 'Cert:\LocalMachine\OSIsoft LLC 
    Certificates' )
    
    Adds the PI Data Archive "PISRV3" to the PI Data Archive 2017 collective 
    which the "PISRV1" PI Data Archive server is a part of. This example 
    should be referenced for PI Data Archive versions 2017 or later.
    
    Note that the self-signed certificate found at the path in the example 
    should have been created upon installation of PI Data Archive 2017 or 
    later. For more information regarding PI Data Archive 2017 certificates 
    and troubleshooting, see KB01564 and KB00800


##    Add-PIDataArchiveConnectionConfiguration

SYNOPSIS
    Add connection configuration information for a PI Data Archive in the 
    local Known Servers Table (KST)
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIDataArchiveConnectionConfiguration -Name PISRV1 -Path 
    "PISRV1.example.int" -OpenTimeout 00:01:00 -OperationTimeout 00:10:00
    
    This example will add the PI Data Archive connection configuration in the 
    Known Servers Table (KST) named "PISRV1" with an FQDN path of 
    "PISRV1.example.int", OpenTimeout of 1 minute and OperationTimeout of 10 
    minutes.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIDataArchiveConnectionConfiguration -Name PISRV1 -Path "10.32.49.71" 
    -OpenTimeout 00:00:30 -OperationTimeout 00:05:00 -DefaultServer
    
    This example will add the PI Data Archive connection configuration in the 
    Known Servers Table (KST) named "PISRV1" with an IP address path of 
    "10.32.49.71", OpenTimeout of 30 seconds and OperationTimeout of 5 
    minutes. PISRV1 will also be set as the default PI Data Archive in the KST.


##    Add-PIDigitalStateSet

SYNOPSIS
    Add a PI Digital State Set
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIDigitalStateSet -Name "BoilerState" -States 
    "ON","OFF","STARTUP","COOLDOWN" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example creates the digital state set "BoilerState" on the "PISRV1" 
    PI Data Archive. This state set contains 4 digital states with the 
    following integral representations:
    
    0="ON" : 1="OFF" : 2="STARTUP" : 3="COOLDOWN"


##    Add-PIDigitalStateToStateSet

SYNOPSIS
    Add a PI Digital State to an existing PI Digital State Set
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIDigitalStateToStateSet -Name "BoilerState" -States "Unknown" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example adds a PI Digital State "Unknown" to the "BoilerState" PI 
    Digital State Set. Since the -InsertAtIndex parameter is not specified, 
    the new state is appended to the end of the digital state set.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIDigitalStateToStateSet -Name "ProcessLoopSet" -States 
    "Pulverizing","Drying","Washing","Packaging" -InsertAtIndex 3 -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example adds four (4) digital states to the PI Digital State Set 
    "ProcessLoopSet" on the "PISRV1" PI Data Archive. The states are inserted 
    into the PI Digital State Set at index three (3). For example, if the 
    initial PI Digital State Set configuration was:
    
    0="Startup" : 1="Cooling" : 2="Grinding" : 3="Finalizing"
    
    Then the resulting PI Digital State Set configuration after running this 
    example would look like:
    
    0="Startup" : 1="Cooling" : 2="Grinding" : 3="Pulverizing" : 4="Drying" : 
    5="Washing" : 6="Packaging" : 7="Finalizing"


##    Add-PIFirewall

SYNOPSIS
    Add an entry in the PI Firewall Table
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIFirewall -Hostmask "192.168.0.56" -Value Disallow -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Adds an entry in the PI Firewall table disallowing connections from IP 
    Address 192.168.0.56 on the "PISRV1" PI Data Archive server.


##    Add-PIGroup

SYNOPSIS
    Add a new PI Group to a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIGroup -Name "PIEngineersGroup" -Description "All Floor Engineers" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example adds a new PI Group "PIEngineersGroup" with a description to 
    the "PISRV1" PI Data Archive.


##    Add-PIIdentity

SYNOPSIS
    Get a PI Security Identity
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIIdentity -Name "FloorEngineers" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Add the PI Identity "FloorEngineers" from the "PISRV1" PI Data Archive 
    server.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIIdentity -Name "BusinessDomainUsers" -Description "Identity for 
    business domain users" -DisallowUseInTrusts -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Add the PI Identity "BusinessDomainUsers" on the "PISRV1" PI Data Archive 
    server. A description is added. The Identity is also marked to disallow 
    use in trusts, since this identity is intended for business users with 
    valid PI Mappings.


##    Add-PIMapping

SYNOPSIS
    Add a PI Security Mapping
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIMapping -Name "TestMapping" -Identity "PIEngineers" -PrincipalName 
    "exampledomain\jdoe" -Description "PI Mapping for John Doe" -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Adds the PI Mapping "TestMapping" for John Doe on the "PISRV1" PI Data 
    Archive server. John Doe is mapped to the PIEngineers identity.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIMapping -Name "Domain Users Mapping" -Identity "DomainUsersReadOnly" 
    -PrincipalName "exampledomain\domainusers" -Description "Mapping for all 
    domain users" -Disabled -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Adds the PI Mapping "Domain Users Mapping" for the windows group 
    "domain\domainusers" on the "PISRV1" PI Data Archive server. 
    Example\domainusers is mapped to a custom PI Identity 
    "DomainUsersReadOnly" and is disabled upon creation. This will allow the 
    mapping to not be effective immediately, and can be enabled later.


##    Add-PIPoint

SYNOPSIS
    Add a PI Point or PI Points
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIPoint -Name DefaultTag -Connection $con
    
    This example will create a PI Point called "DefaultTag" on the server 
    specified in the $con variable with all default PI Point attributes.
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIPoint -Name BoilerTemp -Attributes @{Description="Boiler 
    Temperature";PointSource="OPC";Location1="1";Location4="1"} -Connection 
    $con
    
    This example will create a single PI Point called "BoilerTemp" on the 
    server specified in the $con variable with the attributes specified in the 
    -Attributes hash table.
    
    ----------  EXAMPLE 3  ----------
    
    Add-PIPoint -Names BoilerTemp1,BoilerTemp2 -Attributes 
    @{Description="Boiler 
    Temperature";PointSource="OPC";Location1="1";Location4="1"} -Connection 
    $con
    
    This example will create a two PI Points: BoilerTemp1 and BoilerTemp2 with 
    the same set of attributes as specified by the hashtable.
    
    ----------  EXAMPLE 4  ----------
    
    Add-PIPoint -NameAndAttributesSets @{"BoilerTemp1"=@{Description="Boiler 1 
    Temperature";PointSource="OPC";InstrumentTag="Boiler.1.Temp"};"BoilerTemp2"
    =@{Description="Boiler 2 
    Temperature";pointsource="OPC";InstrumentTag="Boiler.2.Temp"}} -Connection 
    $con
    
    This example will create a two PI Points: BoilerTemp1 and BoilerTemp2 with 
    specified attributes per point.
    
    The name of each hashtable entry is the name of the PI Point to create and 
    the value is another hashtable containing the attributes with which to 
    create the point.


##    Add-PITrust

SYNOPSIS
    Add a PI Security Trust
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PITrust -Name "PIINT1_OPC_IP" -Identity "InterfacesAndBuffering" 
    -Description "Trust for OPC Interface on PIINT1 node via IP Address" 
    -IPAddress "10.32.108.64" -NetMask "255.255.255.255" -ApplicationName 
    "OPCpE.exe" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Creates a "2+" trust for an OPC Interface on the machine with IP Address 
    10.32.108.64. The trust will allow permissions of the 
    "InterfacesAndBuffering" identity on the "PISRV1" PI Data Archive.


##    Add-PIUser

SYNOPSIS
    Add a new PI User to a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIUser -Name "John Doe" -Description "PI User Account for John Doe" 
    -Password (ConvertTo-SecureString -String "examplepassword" -AsPlainText 
    -Force) -PIGroups "PIEngineersGroup","PIReadersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example creates a new PI User "John Doe" with a password of 
    "examplepassword" and is added to two PI Groups "PIEngineersGroup" and 
    "PIReadersGroup". A description is also added
    
    Use "Get-Help ConvertTo-SecureString -Full" for more information on 
    ConvertTo-SecureString cmdlet.


##    Add-PIUserToPIGroup

SYNOPSIS
    Add an existing PI User to PI Groups on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIUserToPIGroups -Name "John Doe" -PIGroups 
    "PIEngineersGroup","PIReadersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example adds an existing PI User "John Doe" to two PI Groups 
    "PIEngineersGroup" and "PIReadersGroup".


##    Add-PIValue

SYNOPSIS
    Add one or more PI Values to a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Add-PIValue -PointName Sinusoid -Time "1-Apr-2017 20:00:00" -Value 100 
    -WriteMode Append -Connection $con
    
    Add PI Value at a Specified Time Using PointName:
    
    This example will write a value of 100 to the PI Point "Sinusoid" at the 
    time "1-Apr-2017 20:00:00" with the write mode "Append".
    
    The tag can also be specified by Point ID rather than PointName by using 
    -PointID <PointID> parameter in place of -PointName
    
    Valid options for WriteMode are: Append, AppendX, NoReplace, Remove, 
    Replace, ReplaceX
    
    ----------  EXAMPLE 2  ----------
    
    Add-PIValue -PIPoint (Get-PIValue -Name Sinusoid -Connection $con) -Time 
    "1-Apr-2017 20:00:00" -Value 100 -WriteMode NoReplace
    
    Add PI Value at a Specified Time Using PI Point Object:
    
    This example writes the same value and time as the previous example, 
    however, the PIPoint object is retrieved via Get-PIPoint and the 
    "NoReplace" WriteMode is used.
    
    Run "Get-Help Get-PIPoint" for more information on this cmdlet.
    
    ----------  EXAMPLE 3  ----------
    
    Add-PIValue -PointName Sinusoid,SinusoidU,CDT158 -Time 
    (ConvertFrom-AFRelativeTime -RelativeTime T+8h) -Value 100 -WriteMode 
    Append -Connection $con
    
    Add PI Value at a Specified Time to Multiple Tags Using PointName:
    
    This example uses ConvertFrom-AFRelativeTime to write a value of 100 at 
    8:00am to each of the tags listed: Sinusoid, SinusoidU, and CDT158.
    
    Run "Get-Help ConvertFrom-AFRelativeTime" for more information on this 
    cmdlet.
    
    ----------  EXAMPLE 4  ----------
    
    Add-PIValue (Get-PIPoint -Name Sin* -Connection $con) -Time 
    (ConvertFrom-AFRelativeTime -RelativeTime Y+17h) -Value 100
    
    Add PI Value at a Specified Time For All Tags Matching a TagMask:
    
    This example will write a value of 100 for yesterday at 5:00pm to all PI 
    Points matching the tagmask "Sin*" with the default WriteMode of Append.
    
    Sinusoid, Y+17h (yesterday at 5pm), 100
    
    SinusoidU, Y+17h (yesterday at 5pm), 100
    
    SinusoidTest, Y+17h (yesterday at 5pm), 100
    
    ----------  EXAMPLE 5  ----------
    
    Add-PIValue -PointName Sinusoid,SinusoidU,CDT158 -Time "1-Apr-2017 
    20:00:00","3-May-2017 8:00:00","5-Jun-2017 12:00:00" -Value 100,200,300 
    -WriteMode ReplaceX -Connection $con
    
    Replace PI Value at Multiple Times for Multiple Tags:
    
    This example will write the following values using ReplaceX mode:
    
    Sinusoid, 1-Apr-2017 20:00:00, 100
    
    SinusoidU, 3-May-2017 08:00:00, 200
    
    CDT158, 5-Jun-2017 12:00:00, 300
    
    Note that all arrays for input: PointName, Time, and Value must either 
    contain the same number of entries or 1. In this example, all input arrays 
    have the same number of entries, so all of the first elements are 
    associated with each other, all the second elements are associated with 
    each other, etc.


##    Clear-AFChangeTables

SYNOPSIS
    Clears ChangeTables in the PISystem
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Clear-AFChangeTables
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Clears the tables in the PI AF SQL database which record information on 
    changes in the PISystem specified by the AFServer.


##    Clear-PIArchiveQueue

SYNOPSIS
    Flush events in PI Archive Subsystem read/write cache to disk
    
    

    ----------  EXAMPLE 1  ----------
    
    Clear-PIArchiveQueue -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Flush the PI Data Archive read and write cache from the PI Data Archive 
    "PISRV1".
    
    ----------  EXAMPLE 2  ----------
    
    Clear-PIArchiveQueue -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Flush the PI Data Archive read and write cache from the PI Data Archive 
    "PISRV1", where the connection object to PISRV1 is stored in the variable 
    $con.


##    Clear-PIBufferHealthIssue

SYNOPSIS
    Clear health issues from PI Buffer Subsystem
    
    

    ----------  EXAMPLE 1  ----------
    
    Clear-PIBufferHealthIssue -HealthIssueID 11
    
    Clears the health issue ID 11 (User disabled data sending -bc stop command)
    
    ----------  EXAMPLE 2  ----------
    
    Clear-PIBufferHealthIssue -HealthIssueID 7,11
    
    Clears the health issue ID 7,11 (There are issues with physical server(s), 
    User disabled data sending -bc stop command, respectively)
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { 
    Clear-PIBufferHealthIssue -HealthIssueID 7 }
    
    Clears the health issue ID 11 (User disabled data sending -bc stop 
    command) from the PIINT1 instance of PI Buffer Subsystem.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Clear-PIBufferHealthIssue, but with 
    the network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Clear-PIBufferPointError

SYNOPSIS
    Clear point errors from PI Buffer Subsystem
    
    

    ----------  EXAMPLE 1  ----------
    
    Clear-PIBufferPointError
    
    Clears all point errors for all servers on the local instance of PI Buffer 
    Subsystem.
    
    ----------  EXAMPLE 2  ----------
    
    Clear-PIBufferPointError -PointID 1,2,3
    
    Clears point errors for PI Points with PointID 1, 2 and 3 on the local 
    instance of PI Buffer Subsystem.
    
    ----------  EXAMPLE 3  ----------
    
    Clear-PIBufferPointError -PointID 1,2,3 -LogicalServerName 
    PISRV-Collective -PhysicalServerName PISRV-1
    
    Clears point errors for PI Points with PointID 1, 2 and 3 from the PISRV-1 
    buffered server on the local instance of PI Buffer Subsystem.
    
    ----------  EXAMPLE 4  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { 
    Clear-PIBufferPointError -PointID 1 -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1 }
    
    Clears point errors for PI Point with PointID 1 on the PIINT1 instance of 
    PI Buffer Subsystem.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Clear-PIBufferPointError, but with 
    the network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Connect-AFServer

SYNOPSIS
    Connect to an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Connect-AFServer -AFServer (Get-AFServer -Default)
    
    This example will connect to the default AF Server in the local AF Servers 
    list.
    
    ----------  EXAMPLE 2  ----------
    
    Connect-AFServer -WindowsCredential (Get-Credential TestDomain\TestUser) 
    -AFServer (Get-AFServer -Name PIAF1)
    
    This example will connect to the AF Server "PIAF1" with the credentials 
    TestDomain\TestUser. Upon running the command, the user will be prompted 
    for the password of the TestDomain\TestUser account. If -WindowsCredential 
    is not specified, then the credentials of the user running PowerShell will 
    be used.
    
    ----------  EXAMPLE 3  ----------
    
    Connect-AFServer -AFConnectionPreference Any -AFServer (Get-AFServer 
    -Default)
    
    This example will connect to the default AF Server with the connection 
    preference "Any" if it is an AF Collective.

##    Connect-PIDataArchive

SYNOPSIS
    Connect to a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Connect via PI Data Archive Name: This example will connect to a PI Data 
    Archive via machine name "PISRV1". Note that PIDataArchiveMachineName can 
    be a machine name, IP address, or Fully Qualified Domain Name (FQDN). The 
    resulting PI Connection object will be stored in the variable $con.
    
    ----------  EXAMPLE 2  ----------
    
    Connect-PIDataArchive -PIDataArchiveConnectionConfiguration 
    (Get-PIDataArchiveConnectionConfiguration -Name PISRV1)
    
    Connect via Connection Configuration: This example connects to a PI Data 
    Archive or PI Collective using a PIDataArchiveConnectionConfiguration 
    object, which is returned by the Get-PIDataArchiveConnectionConfiguration 
    cmdlet. This will honor connection settings in the Known Servers Table to 
    make the connection. This returns a PI Data Archive connection object.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIDataArchiveConnectionConfiguration -Name PISRV1 | 
    Connect-PIDataArchive
    
    Connect via Connection Configuration: This example is the same as the 
    previous example, except that the PIDataArchiveConnectionConfiguration 
    object is first retrieved and then passed to Connect-PIDataArchive via the 
    PowerShell pipeline.
    
    ----------  EXAMPLE 4  ----------
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1" 
    -AuthenticationMethod Windows -OpenTimeout 00:20:00 -OperationTimeout 
    00:05:00
    
    This example connects to the PI Data Archive via machine name, and 
    overrides default parameters of OpenTimeout and OperationTimeout. The 
    authentication method is forced as WIS. If connection via WIS fails, no 
    other attempts via Trust or Explicit Login will be attempted even if 
    allowed by the PISDK protocol order.


##    ConvertFrom-AFRelativeTime

SYNOPSIS
    Converts a PI Time string into a DateTime
    
    

    ----------  EXAMPLE 1  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "*"
    
    This example will return a System.DateTime for the current time in UTC.
    
    ----------  EXAMPLE 2  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "*-2h"
    
    This example will return a System.DateTime for "two hours ago" in UTC.
    
    ----------  EXAMPLE 3  ----------
    
    ConvertFrom-AFRelativeTime -RelativeTime "T+8h -LocalTime"
    
    This example will return a System.DateTime for "today at 8am" in the local 
    machine's time zone.
    
    ----------  EXAMPLE 4  ----------
    
    Get-PIValue -PointName "Sinusoid" -Time (ConvertFrom-AFRelativeTime 
    -RelativeTime "*") -ArchiveMode Interpolated -Connection $con
    
    This example uses the ConvertFrom-AFRelativeTime cmdlet to get the 
    interpolated value of tag "sinusoid" at the current time.


##    Disable-AFExternalDataTables

SYNOPSIS
    Disables support for an AFTable to link to an external source.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Disable-AFExternalDataTables
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Disables support for an AFTable to link to an external source


##    Disable-AFExternalDataTablesNonImpersonatedUsers

SYNOPSIS
    Disables support for an AFTable to link to an external source with 
    non-impersonated users.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Disable-AFExternalDataTablesNonImpersonatedUsers
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Disables support for an AFTable to link to an external source with 
    non-impersonated users.


##    Disable-AFPropagationOfTargetDeletion

SYNOPSIS
    Disables support for propagating the deletion of targets (elements) to the 
    referencing analyses and notifications.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Disable-AFPropagationOfTargetDeletion
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Enables support for propagating the deletion of targets (elements) to the 
    referencing analyses and notifications.


##    Disable-AFSecurityIdentity

SYNOPSIS
    Disable an AF Security Identity on an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Disable-AFSecurityIdentity -CheckIn -AFSecurityIdentity $EngineersIdentity
    
    Where:
    
    $EngineersIdentity = Get-AFSecurityIdentity -Name Engineers -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Disables the AF Security Identity "Engineers" from the AF Server "PIAF1". 
    The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    $DisabledIdentity = Disable-AFSecurityIdentity -CheckIn -PassThrough 
    -AFSecurityIdentity $EngineersIdentity
    
    Where:
    
    $EngineersIdentity = Get-AFSecurityIdentity -Name Engineers -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Disables the AF Security Identity "Engineers" from the AF Server "PIAF1". 
    The change is checked in immediately. The AF Security Identity that was 
    changed is returned, and in this example will be stored in variable 
    $DisabledIdentity.


##    Disable-UomCaseSensitivity

SYNOPSIS
    Disable case-sensitivity of UOM abbreviations in the PI AF SQL Server 
    database.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Disable-UomCaseSensitivity
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    >Disable case-sensitivity of UOM abbreviations in the PI AF SQL Server 
    database.


##    Disconnect-AFServer

SYNOPSIS
    Disconnect from an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Disconnect-AFServer -AFServer (Get-AFServer -Default)
    
    This example will close a connection to the default AF Server
    
    ----------  EXAMPLE 2  ----------
    
    Disconnect-AFServer -AFServer (Get-AFServer -Name PIAF1)
    
    This example will close a connection to the AF Server "PIAF1"


##    Disconnect-PIDataArchive

SYNOPSIS
    Gracefully disconnect from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Disconnect-PIDataArchive -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName PISRV1
    
    This example will gracefully disconnect from the PI Data Archive "PISRV1" 
    as specified by the -Connection parameter.


##    Enable-AFExternalDataTables

SYNOPSIS
    Enables support for an AFTable to link to an external source.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Enable-AFExternalDataTables
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Enables support for an AFTable to link to an external source


##    Enable-AFExternalDataTablesNonImpersonatedUsers

SYNOPSIS
    Enables support for an AFTable to link to an external source with 
    non-impersonated users.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Enable-AFExternalDataTablesNonImpersonatedUsers
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Enables support for an AFTable to link to an external source with 
    non-impersonated users.


##    Enable-AFPropagationOfTargetDeletion

SYNOPSIS
    Enables support for propagating the deletion of targets (elements) to the 
    referencing analyses and notifications.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Enable-AFPropagationOfTargetDeletion
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Enables support for propagating the deletion of targets (elements) to the 
    referencing analyses and notifications.


##    Enable-AFSecurityIdentity

SYNOPSIS
    Enable an AF Security Identity on an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Enable-AFSecurityIdentity -CheckIn -AFSecurityIdentity $EngineersIdentity
    
    Where:
    
    $EngineersIdentity = Get-AFSecurityIdentity -Name Engineers -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Enables the currently disabled AF Security Identity "Engineers" from the 
    AF Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    $MyAFIdentity = Enable-AFSecurityIdentity -CheckIn -PassThrough 
    -AFSecurityIdentity $EngineersIdentity
    
    Where:
    
    $EngineersIdentity = Get-AFSecurityIdentity -Name Engineers -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Enables the currently disabled AF Security Identity "Engineers" from the 
    AF Server "PIAF1". The change is checked in immediately. The AF Security 
    Identity that was enabled is sent down the pipeline, and in this example 
    will be stored in variable $DisabledIdentity.


##    Enable-UomCaseSensitivity

SYNOPSIS
    Changes configuration of UOM abbreviations from case insensitive to case 
    sensitive in the PI AF SQL Server database.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Enable-UomCaseSensitivity
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Changes configuration of UOM abbreviations from case insensitive to case 
    sensitive in the PI AF SQL Server database.


##    Export-AFXml

SYNOPSIS
    Export XML representation of AF Objects to file or to System.IO.Stream
    
    

    ----------  EXAMPLE 1  ----------
    
    Export-AFXml -ExportMode AllReferences -File "C:\exports\afserver.xml" 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Exports the AF Server object for "PIAF1" to an xml file. Note that the AF 
    Server object only includes: AFContact, AFNotificationContactTemplate, and 
    UOMDatabase objects. All other objects must be exported via the AF 
    Database object.
    
    ----------  EXAMPLE 2  ----------
    
    Export-AFXml -ExportMode DefaultValues -File "C:\exports\afdatabases.xml" 
    -AFDatabases $AllAFDatabases
    
    Where:
    
    $AllAFDatabases = Get-AFDatabase "*" -AFServer (Get-AFServer -Name "PIAF1")
    
    Exports all AF Database objects on the PIAF1 AF Server to an xml file. 
    Default values are included in the export.
    
    ----------  EXAMPLE 3  ----------
    
    Export-AFXml -File "C:\exports\afdatabases.xml" -AFObject 
    $MySingleAFElement
    
    Where:
    
    $MySingleAFElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Exports the single AF Element object and all child objects in 
    $MySingleAFElement from the PIAF1 AF Server to an xml file. No extra 
    information is contained in the export.


##    Find-AFEventFrame

SYNOPSIS
    Find AF Event Frame(s)
    
    

    ----------  EXAMPLE 1  ----------
    
    Find-AFEventFrame -StartTime (ConvertFrom-AFRelativeTime "T") -EndTime 
    (ConvertFrom-AFRelativeTime "*") -AFSearchMode Inclusive -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Retrieves all event frames since the beginning of today (since 00:00:00) 
    on the AF Database "AFDatabase1"
    
    ----------  EXAMPLE 2  ----------
    
    Find-AFEventFrame -StartTime (ConvertFrom-AFRelativeTime "Y") -EndTime 
    (ConvertFrom-AFRelativeTime "T") -AFSortField StartTime -AFSortOrder 
    Descending -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Retrieves all event frames from yesterday on the AF Database 
    "AFDatabase1". The results are sorted based on start time starting with 
    the latest start time.
    
    ----------  EXAMPLE 3  ----------
    
    Find-AFEventFrame -StartTime (ConvertFrom-AFRelativeTime "Y") -EndTime 
    (ConvertFrom-AFRelativeTime "T") -AFSortField EndTime -AFSortOrder 
    Ascending -NameFilter "Boiler*" -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Retrieves all event frames from yesterday on the AF Database "AFDatabase1" 
    which are associated with an AF Element matching the mask "Boiler*". The 
    results are sorted based on end time starting with the earliest start time.


##    Get-AFAttribute

SYNOPSIS
    Get an AF Attribute
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFAttribute -Name "Interior Temperature" -AFElement $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Inner Temperature" -AFElement 
    $afElement
    
    Gets the AF Attribute "Inner Temperature" on the top level element "Anneal 
    Oven 1" on the database "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFAttribute -Name "Celsius" -AFAttribute $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Inner Temperature" -AFElement 
    $afElement
    
    Gets the child AF Attribute "Celsius" of the AF Attribute "Inner 
    Temperature" on the top level element "Anneal Oven 1" on the database 
    "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFAttribute -Name * -AFElement $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Gets all AF Attributes on the top level element "Anneal Oven 1" on the 
    database "AFDatabase1" on the AF Server "PIAF1".


##    Get-AFAttributeTemplate

SYNOPSIS
    Get an AF Attribute Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFAttributeTemplate -Name "Temperature" -AFElementTemplate 
    $afEleTemplate
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Gets the AF Attribute Template "Temperature" on the element template 
    "Oven" on the database "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFAttributeTemplate -Name "Fahrenheit" -AFAttributeTemplate 
    $afAttTemplate
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttTemplate = Get-AFAttributeTemplate -Name "Inner Temperature" 
    -AFElementTemplate $afElement
    
    Gets the child AF Attribute Template "Fahrenheit" of the AF Attribute 
    Template "Inner Temperature" on the element template "Oven" on the 
    database "AFDatabase1" on the AF Server "PIAF1".


##    Get-AFCategory

SYNOPSIS
    Get an AF Category
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFCategory -Name "Product A Manufacturing" -Element -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Gets an existing AF Element Category "Product A Manufacturing" from the AF 
    Database "AFDatabase1" on AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFCategory -Name "KPIs" -Attribute -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Gets an existing AF Attribute Category "KPIs" from the AF Database 
    "AFDatabase1" on AF Server "PIAF1".


##    Get-AFCheckedOutItem

SYNOPSIS
    Get a checked out AF objects
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFCheckedOutItem -AFCheckedOutMode AllObjects -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Gets all checked out items from the AF Database "AFDatabase1" on the AF 
    Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFCheckedOutItem -CheckedOutToMe -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Gets the checked out AF objects by the connected user on the AF Database 
    "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFCheckedOutItem -AllObjects -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    Gets all checked out AF objects on the AF Server "PIAF1". Note that the 
    only objects checked out on the server level are AFContact, 
    AFNotificationContactTemplate, and UOMDatabase check outs.


##    Get-AFDatabase

SYNOPSIS
    Get an AF Database
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFDatabase -Default -AFServer (Get-AFServer -Default)
    
    This example will get the default AF Database from the default AF Server 
    in the local AF Servers list.
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFDatabase -Name MyDB -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will get the AF Database "MyDB" from the AF Server "PIAF1" in 
    the local AF Servers list.
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFDatabase -Index 2 -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will get the 3rd AF Database from the AF Server "PIAF1" in 
    the local AF Servers list. Note that the index is zero-based. Therefore, 
    to get the first database, use -Index 0. To get the second database, use 
    -Index 1, etc.


##    Get-AFDiagnostics

SYNOPSIS
    Gets diagnostic information from the system.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Get-AFDiagnostics
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Gets diagnostic information from the system.


##    Get-AFElement

SYNOPSIS
    Get an AF Element
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFElement -Name "Production Line 1" -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Gets the top level element "Production Line 1" from the database 
    "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFElement -AFElement $afElement -Name "Boiler 1"
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Gets the child element of "Production Line 1" called "Boiler1" from the 
    database "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFElement -Name * -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Gets all top level elements from the database "AFDatabase1" on the AF 
    Server "PIAF1".


##    Get-AFElementTemplate

SYNOPSIS
    Get an AF Element Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFElementTemplate -Name "Boiler" -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Gets the element template "Boiler" on the database "AFDatabase1" on the AF 
    Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFElementTemplate -Name * -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Gets all AF element templates on the database "AFDatabase1" on the AF 
    Server "PIAF1".


##    Get-AFEventFrame

SYNOPSIS
    Get an AF Event Frame(s)
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 -AFServer 
    $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    This example gets the AF Event Frame with the specified GUID from the AF 
    Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFEventFrame -Name * -Refresh -AFEventFrame $MyEventFrame
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $MyEventFrame = Find-AFEventFrame -StartTime (ConvertFrom-AFRelativeTime 
    "T") -EndTime (ConvertFrom-AFRelativeTime "*") -AFSearchMode Inclusive 
    -MaxCount 1 -AFDatabase $afDB
    
    This example gets all child AF Event Frames on the parent AF Event Frame 
    stored in $MyEventFrame on the AF Database "AFDatabase1" on the AF Server 
    "PIAF1".


##    Get-AFEventFrameParent

SYNOPSIS
    Get the parent AF Event Frame of another AF Event Frame
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFEventFrameParent -AFEventFrame $ChildEventFrame
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $ChildEventFrame = Get-AFEventFrame -ID 
    7570ec51-31c6-4611-0000-000000015f31 -AFServer $afServer
    
    This example gets the parent AF Event Frame with the specified GUID from 
    the PIAF1 AF Server.


##    Get-AFPlugInVerifyLevel

SYNOPSIS
    Gets the current level of verification required for an AFPlugin to be 
    loaded from the server.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Get-AFPlugInVerifyLevel
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Gets the current level of verification required for an AFPlugin to be 
    loaded from the server.


##    Get-AFPort

SYNOPSIS
    Get an AF Port
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFPort -Name InputPort1 -AFElementTemplate $afElementTemplate
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElementTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    Gets the AF Port InputPort1 from the Boiler element template on the AF 
    Database AFDatabase1.
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFPort -Name InputPort1 -AFElement $afElement
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElement = Get-AFElement -Name WestSite -AFDatabase $afDB
    
    Gets the AF Port InputPort1 from the top level element WestSite on the AF 
    Database AFDatabase1.


##    Get-AFSecurity

SYNOPSIS
    Get AF Security entry for an AF object
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFSecurity -AFObject $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Gets the AF Security entry for the AF Database "AFDatabase1" on the AF 
    Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFSecurity -AFObject $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Gets the AF Security entry for the AF Element "Production Line 1" on the 
    AF Database "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFSecurity -AFSecurityItem Element -AFObject $afDB
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Gets the AF Security entry for the Elements collection on the AF Database 
    "AFDatabase1" on the AF Server "PIAF1".


##    Get-AFSecurityIdentity

SYNOPSIS
    Gets an AF Security Identity from an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFSecurityIdentity -Name Administrators -Refresh -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Gets the AF Security Identity "Administrators" from the AF Server "PIAF1"
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFSecurityIdentity -Name * -Refresh -AFServer (Get-AFServer -Name 
    PIAF1) | Where-Object -Property IsEnabled -EQ $False
    
    Gets all "disabled" AF Security Identities from the AF Server "PIAF1". The 
    AF Server object is refreshed before the AF Security Identites are 
    retrieved.
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFSecurityIdentity -Name * -Refresh -AFServer (Get-AFServer -Name 
    PIAF1) | Where-Object -Property IsEnabled -EQ $False | Select-Object 
    -Property Name,ModifyDate
    
    Gets all "disabled" AF Security Identities from the AF Server "PIAF1" and 
    outputs their Name and ModifyDate properties. The AF Server object is 
    refreshed before the AF Security Identities are retrieved.


##    Get-AFSecurityMapping

SYNOPSIS
    Gets an AF Security Mapping from an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFSecurityMapping -Name domain\testuser -Refresh -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Gets the AF Security Mapping "domain\testuser" from the AF Server "PIAF1"
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFSecurityMapping -Name * -Refresh -AFServer (Get-AFServer -Name 
    PIAF1) | Select-Object -Property Name,SecurityIdentity
    
    Gets all AF Security Mappings from the AF Server "PIAF1" and outputs only 
    their Name and associated AF Security Identity. The AF Server object is 
    refreshed before the AF Security Mappings are retrieved.


##    Get-AFServer

SYNOPSIS
    Get an AF Server connection configuration from local AF Server list
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFServer
    
    This example will return all locally known AF Servers.
    
    ----------  EXAMPLE 2  ----------
    
    Get-AFServer -Name PIAF1
    
    This example will return the AF Server "PIAF1" from the locally stored AF 
    Server list.
    
    ----------  EXAMPLE 3  ----------
    
    Get-AFServer -Default
    
    This example will return the default AF Server from the locally stored AF 
    Server list.
    
    ----------  EXAMPLE 4  ----------
    
    Get-AFServer -Index 0
    
    This example will return the first AF Server from the locally stored AF 
    Server list. Note that the -Index is zero-based. Therefore, if 
    "Get-AFServer" returns 3 AF Servers. The first is accessed with -Index 0, 
    the second with -Index 1, etc.


##    Get-AFTrustedProviders

SYNOPSIS
    Returns the list of trusted providers in the PISystem.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Get-AFTrustedProviders
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Returns the list of trusted providers in the PISystem.


##    Get-AFUnitOfMeasure

SYNOPSIS
    Get an AF Unit of Measure
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFUnitOfMeasure -Name "Meter" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Gets the existing AF Unit of Measure "Meter" from the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-UnitOfMeasure -Name "Degree*" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Gets all AF Units of Measure matching the name "Degree*", for example: 
    degree fahrenheit, degree celsius, etc on AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Get-UnitOfMeasure -Name "*" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Gets all AF Units of Measure on AF Server "PIAF1".


##    Get-AFUnitOfMeasureClass

SYNOPSIS
    Get an AF Unit of Measure Class
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-AFUnitOfMeasureClass -Name "Length" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Gets the existing AF Unit of Measure Class "Length" from the AF Server 
    "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-UnitOfMeasureClass -Name "*" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Gets all AF Units of Measure Classes on AF Server "PIAF1".


##    Get-PIAFLinkBatchDatabaseAnalysisStatus

SYNOPSIS
    Get the Batch Database Analysis status from the AF Link Subsystem on a PI 
    Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIAFLinkBatchDatabaseAnalysisStatus -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Batch Database analysis status from the PI AF Link Subsystem. 
    This information is used to address any issues found when preparing to 
    migrate from PI Batch Database to Event Frames.


##    Get-PIAFLinkBatchDatabaseStatistics

SYNOPSIS
    Get the Batch Database statistics from the AF Link Subsystem on a PI Data 
    Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIAFLinkBatchDatabaseStatistics -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Batch Database statistics from the PI AF Link Subsystem. This 
    information can be used to monitor a PI Batch Database to Event Frames 
    Migration.


##    Get-PIAFLinkBatchDatabaseUnmappedIdentities

SYNOPSIS
    Get a list of unmapped PI Identities for the Batch Database from the AF 
    Link Subsystem.
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIAFLinkBatchDatabaseUnmappedIdentities -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example retrieves a list of Identities that exist in the Batch 
    Database but do not currecntly have a PI Mapping created. A PI Mapping 
    must be created for each of these PI Identities before the Batch to Event 
    Frames Migration can be performed.


##    Get-PIAFLinkModuleDatabaseSecurityErrors

SYNOPSIS
    Get a list of PI AF Link security errors on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIAFLinkModuleDatabaseSecurityErrors -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example retrieves any potential security conflicts found by PI AF 
    Link on the PISRV1 PI Data Archive. No timeout is specified, so the 
    OperationTimeout parameter of the connection will be used as a timeout.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIAFLinkModuleDatabaseSecurityErrors -Connection $con).Count
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns a count of the number of PI Modules with found 
    security errors. No timeout is specified, so the OperationTimeout 
    parameter of the connection will be used as a timeout.
    
    ----------  EXAMPLE 3  ----------
    
    (Get-PIAFLinkModuleDatabaseSecurityErrors -Timeout "00:00:30" -Connection 
    $con).Errors
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example dumps all security errors found by PI AF Link. A timeout 
    timespan of 30 seconds is specified.


##    Get-PIAFLinkModuleDatabaseStatistics

SYNOPSIS
    Get the PI Module Database statistics from the PI AF Link or PI Base 
    Subsystem on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    (Get-PIAFLinkModuleDatabaseStatistics -Connection $con).AFLink
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the Module Database/AF Link statistics and configuration information 
    stored by PI AF Link Subsystem.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIAFLinkModuleDatabaseStatistics -Connection $con).Base
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the Module Database/AF Link statistics and configuration information 
    stored by PI Base Subsystem.


##    Get-PIArchiveFileInfo

SYNOPSIS
    Gets detailed PI Archive file information from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveFileInfo -Name "E:\PIArchives\piarch001-Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Get the PI Archive file information for the "piarch001" archive file. Note 
    that "piarch001" must be an archive file registered with the PI Data 
    Archive "PISRV1".
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveFileInfo -ID 0 -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName PISRV1)
    
    Get the PI Archive file information for the primary archive file (ID=0) on 
    the "PISRV1" PI Data Archive server. Because -ArchiveSet parameter is not 
    explicitly set, a value of 0 (Historical) will be used by default.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIArchiveFileInfo -ArchiveSet 1 -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName PISRV1)
    
    Get the PI Archive file information for all future archives (ArchiveSet = 
    1) on the "PISRV1" PI Data Archive server.


##    Get-PIArchiveInfo

SYNOPSIS
    Gets general PI Archive information and status
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveInfo -ArchiveSet 0 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Get the PI Archive information for the "PISRV1" PI Data Archive server. 
    -ArchiveSet is set to 0, so the historical PI Archive information will be 
    retrieved.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveInfo -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName PISRV1)
    
    Get the PI Archive information for the "PISRV1" PI Data Archive server. 
    Because -ArchiveSet parameter is not explicitly set, a value of 0 
    (Historical) will be used by default.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIArchiveInfo -ArchiveSet 1 -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName PISRV1)
    
    Get the PI Archive information for the "PISRV1" PI Data Archive server. 
    -ArchiveSet is set to 1, so the future PI Archive information will be 
    retrieved.


##    Get-PIArchiveReprocessHistory

SYNOPSIS
    Get the history of archives reprocessed via online archive reprocessing
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveReprocessHistory -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets the entire archive reprocessing history from the "PISRV1" PI Data 
    Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveReprocessHistory -StartTime (ConvertFrom-AFRelativeTime 
    *-1mo) -EndTime (ConvertFrom-AFRelativeTime *) -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the archive reprocessing history from the "PISRV1" PI Data Archive 
    for the last month.


##    Get-PIArchiveReprocessHistoryCount

SYNOPSIS
    Get the total number of archives reprocessed via online archive 
    reprocessing
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveReprocessHistoryCount -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets the total count of archives reprocessed via online archive 
    reprocessing from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveReprocessHistoryCount -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the total count of archives reprocessed via online archive 
    reprocessing from the "PISRV1" PI Data Archive.


##    Get-PIArchiveReprocessQueue

SYNOPSIS
    Get the current PI Reprocess Archive queue
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveReprocessQueue -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets the current queued PI Archive Reprocess requests from the "PISRV1" PI 
    Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveQueue -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the current queued PI Archive Reprocess requests from the "PISRV1" PI 
    Data Archive.


##    Get-PIArchiveSetSettings

SYNOPSIS
    Gets the archive set configuration from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveSetSettings $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Get the PI Archive set configuration settings for the default archive set.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveSetSettings -Name "0_Historical" -Connection 
    (Connect-PIDataArchive -PIDataArchiveMachineName PISRV1)
    
    Get the PI Archive set configuration settings for the archive set 
    (Historical) on the "PISRV1" PI Data Archive server.


##    Get-PIArchiveStatistics

SYNOPSIS
    Get archive statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIArchiveStatistics -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets the archive statistics for the "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveStatistics -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the archive statistics for the "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 3  ----------
    
    for () { Get-PIArchiveStatistics -Connection $con; Write-Host; Start-Sleep 
    -Seconds 5 }
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the archive statistics for the "PISRV1" PI Data Archive server every 
    5 seconds indefinitely and writes results to the console. Similar to 
    "piartool -as" output.


##    Get-PIBackupIdentifyReport

SYNOPSIS
    Get the PI Backup Identify report
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBackupIdentifyReport -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the backup identify report from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIBackupIdentifyReport -Connection $con).Components
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Data Archive components and descriptions identified for backup 
    on the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 3  ----------
    
    (Get-PIBackupIdentifyReport -Connection $con).Files.Name
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the files identified for backup on the "PISRV1" PI Data Archive.


##    Get-PIBackupReport

SYNOPSIS
    Get a PI Backup Report
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBackupReport -LastReport -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns the backup report object for the most recent backup 
    from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIBackupReport -LastReport -Connection $con).Summary
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns the backup report summary for the most recent backup 
    from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIBackupReport -Index 97 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns the backup report object for the backup with index 97 
    from the "PISRV1" PI Data Archive.


##    Get-PIBackupState

SYNOPSIS
    Get the PI Backup State of a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBackupState -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    This example returns the backup state from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIBackupState -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns the backup state from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 3  ----------
    
    (Get-PIBackupState -Connection $con).IsInProgress
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example can be used to quickly determine if a backup is currently 
    in-progress on the "PISRV1" PI Data Archive.


##    Get-PIBackupSummary

SYNOPSIS
    Get a PI Backup Report Summary
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBackupSummary -Index 97 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example returns the backup report summary for the backup with index 
    97 from the "PISRV1" PI Data Archive.


##    Get-PIBufferConfiguration

SYNOPSIS
    Get buffer configuration for a physical buffered server
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferConfiguration -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1 -Details
    
    Gets the complete PI buffered server configuration object from the local 
    instance of PI Buffer Subsystem for the PISRV-1 machine, which is a member 
    of the PISRV-Collective PI Data Archive HA Collective.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIBufferConfiguration -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1 -Details).LogicalServers.Values.PhysicalServers
    BufferConfiguration.Values.Parameters
    
    Outputs the complete PI buffered server configuration from the local 
    instance of PI Buffer Subsystem for the PISRV-1 machine, which is a member 
    of the PISRV-Collective PI Data Archive HA Collective.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1, PIINT2 -ScriptBlock { 
    Get-PIBufferConfiguration -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1 -Details }
    
    Gets the PI buffered server information object from the PIINT1 and PIINT2 
    instances of PI Buffer Subsystem for the PISRV-1 machine, which is a 
    member of the PISRV-Collective PI Data Archive HA Collective.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Get-PIBufferConfiguration, but with 
    the network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Get-PIBufferConfigurationParameter

SYNOPSIS
    Get PI Buffer Configuration Parameters
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferConfigurationParameter
    
    Gets all PI Buffer Subsystem configuration parameters from the local 
    instance of PI Buffer Subsystem for the PISRV-1 machine, which is a member 
    of the PISRV-Collective PI Data Archive HA Collective.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIBufferConfigurationParameter -Name AuthenticationOptions
    
    Gets the AuthenticationOptions configuration parameter from the local 
    instance of PI Buffer Subsystem for the PISRV-1 machine, which is a member 
    of the PISRV-Collective PI Data Archive HA Collective.


##    Get-PIBufferedServer

SYNOPSIS
    Get a PI Buffered Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferedServer -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1
    
    Gets the PI buffered server information object from the local instance of 
    PI Buffer Subsystem for the PISRV-1 machine, which is a member of the 
    PISRV-Collective PI Data Archive HA Collective.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIBufferedServer -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1 -Details).LogicalServers.Values.PhysicalServers
    BufferConfiguration.Values.GUID
    
    Outputs the PI buffered server GUID from the local instance of PI Buffer 
    Subsystem for the PISRV-1 machine, which is a member of the 
    PISRV-Collective PI Data Archive HA Collective. This can be used to 
    identity PIBufSS queues belonging to this buffered server.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { Get-PIBufferedServer 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-1 }
    
    Gets the PI buffered server information object from the PIINT1 instance of 
    PI Buffer Subsystem for the PISRV-1 machine, which is a member of the 
    PISRV-Collective PI Data Archive HA Collective.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Get-PIBufferedServer, but with the 
    network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Get-PIBufferHealth

SYNOPSIS
    Get PI Buffer Subsystem health information
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferHealth -LogicalServerName PISRV-Collective -PhysicalServerName 
    PISRV-1
    
    Gets the buffering health information object from the local instance of PI 
    Buffer Subsystem for the PISRV-1 physical server, which is a member of 
    PISRV-Collective.
    
    ----------  EXAMPLE 2  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { Get-PIBufferHealth 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-1 }
    
    Gets the buffering health information object from the PIINT1 instance of 
    PI Buffer Subsystem for the PISRV-1 physical server, which is a member of 
    PISRV-Collective.
    
    Note the use of Invoke-Command.Failure of this example to execute properly 
    is likely not an issue with Get-PIBufferHealth, but with the network or PS 
    connection to the remote computer. Note that the OSIsoft.PowerShell module 
    must be installed on the remote computer as well for this to work.


##    Get-PIBufferLastConfigurationLoadTime

SYNOPSIS
    Get the last buffer configuration load time
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferLastConfigurationLoadTime
    
    Gets the last time which the local instance of PI Buffer Subsystem loaded 
    its configuration. Failure of this example to execute properly is likely 
    not an issue with Get-PIBufferSession, but with the network or PS 
    connection to the remote computer. Note that the OSIsoft.PowerShell module 
    must be installed on the remote computer as well for this to work.
    
    ----------  EXAMPLE 2  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { 
    Get-PIBufferLastConfigurationLoadTime }
    
    Gets the last time which the PIINT1 instance of PI Buffer Subsystem loaded 
    its configuration.
    
    Note the use of Invoke-Command.Failure of this example to execute properly 
    is likely not an issue with Get-PIBufferLastConfigurationLoadTime, but 
    with the network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Get-PIBufferPointError

SYNOPSIS
    Get point errors for a PI Buffer Subsystem
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferPointError
    
    Gets all points in error since the start of PI Buffer Subsystem on the 
    local instance.
    
    ----------  EXAMPLE 2  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { Get-PIBufferPointError }
    
    Gets all points in error since the start of PI Buffer Subsystem on the 
    PIINT1 instance. Failure of this example to execute properly is likely not 
    an issue with Get-PIBufferPointError, but with the network or PS 
    connection to the remote computer. Note that the OSIsoft.PowerShell module 
    must be installed on the remote computer as well for this to work.
    
    ----------  EXAMPLE 3  ----------
    
    $PointErrors.PhysicalServersPointErrors.Values.PointErrors
    
    Where:
    
    $PointErrors = Get-PIBufferPointError
    
    Outputs all point errors for the local PI Buffer Subsystem instance.


##    Get-PIBufferSession

SYNOPSIS
    Get a PI Buffer Session
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferSession -LogicalServerName PISRV-Collective 
    -PhysicalServerName PISRV-1
    
    Gets the PI Buffer session from the local instance of PI Buffer Subsystem 
    for the PISRV-1 machine, which is a member of the PISRV-Collective PI Data 
    Archive HA Collective.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIBufferSession -LogicalServerName PISRV-Collective
    
    Gets all PI Buffer sessions from the local instance of PI Buffer Subsystem 
    for the PISRV-Collective PI Data Archive HA Collective. For example, if 
    this is a 3-member collective, the results will contain 3 buffer sessions.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { Get-PIBufferSession 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-1 }
    
    Gets the PI Buffer session from the PIINT1 instance of PI Buffer Subsystem 
    for the PISRV-1 machine, which is a member of the PISRV-Collective PI Data 
    Archive HA Collective.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Get-PIBufferSession, but with the 
    network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Get-PIBufferVersion

SYNOPSIS
    Get the PI Buffer Subsystem version
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBufferVersion
    
    Gets the version of the PI Buffer Subsystem running on the local machine.
    
    ----------  EXAMPLE 2  ----------
    
    Invoke-Command -ComputerName PISRV1 -ScriptBlock { Get-PIBufferVersion }
    
    Get the PI Buffer Subsystem version running on the PISRV1 machine. Note 
    the use of Invoke-Command. Failure of this example to execute properly is 
    likely not an issue with Get-PIBufferVersion, but with the network or PS 
    connection to the remote computer. Note that the OSIsoft.PowerShell module 
    must be installed on the remote computer as well for this to work.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PISRV1,PIAF1,PIINT1,PIINT2 -ScriptBlock { 
    Get-PIBufferVersion }
    
    Get the PI Buffer Subsystem version running on the PISRV1, PIAF1, PIINT1, 
    and PIINT2 machines. Note the use of Invoke-Command. Failure of this 
    example to execute properly is likely not an issue with 
    Get-PIBufferVersion, but with the network or PS connection to the remote 
    computer. Note that the OSIsoft.PowerShell module must be installed on the 
    remote computer as well for this to work.


##    Get-PICollective

SYNOPSIS
    Get PI Data Archive Collective information from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PICollective -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Data Archive Collective information from the "PISRV1" PI Data 
    Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PICollective -Connection $con).CurrentRole.Role
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Uses the PI Data Archive Collective information to get the current role of 
    the "PISRV1" PI Data Archive Server.


##    Get-PIConnectionStatistics

SYNOPSIS
    Get PI connection statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIConnectionStatistics -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets all connection information from the "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIArchiveStatistics -ID 57 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the connection information for connection ID 57 from the "PISRV1" PI 
    Data Archive server
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIArchiveStatistics -Search *piadmin* -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the connection information for any connection for which a field 
    contains the string "piadmin" from the "PISRV1" PI Data Archive server


##    Get-PIDataArchiveConnectionConfiguration

SYNOPSIS
    Get connection configuration information for a PI Data Archive from the 
    Known Servers Table (KST)
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDataArchiveConnectionConfiguration -Default
    
    This example will get the PI Data Archive connection configuration from 
    the Known Servers Table (KST) for the default PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIDataArchiveConnectionConfiguration
    
    This example will get the PI Data Archive connection configuration from 
    the Known Servers Table (KST) for all PI Data Archive servers in the KST.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIDataArchiveConnectionConfiguration -Name PISRV1
    
    This example will get the PI Data Archive connection configuration from 
    the Known Servers Table (KST) for the PI Data Archive "PISRV1".


##    Get-PIDataArchiveDetails

SYNOPSIS
    Get the detailed information for a connected PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDataArchiveDetails -Connection $con
    
    This example will get the PI Data Archive details for a PI Data Archive 
    specified by the -Connection parameter. Note that you must first connect 
    to the PI Data Archive and and retrieve a PI Connection object (run 
    "Get-Help Connect-PIDataArchive" for details) before getting the PI Data 
    Archive details via this cmdlet.


##    Get-PIDataArchiveIncident

SYNOPSIS
    Get PI Data Archive Incidents
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDataArchiveIncident -Open -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all open PI Incidents from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIDataArchiveIncident -Open -Closed -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PI Incidents from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIDataArchiveIncident -Open -Closed -StartTime 
    (ConvertFrom-AFRelativeTime -RelativeTime *-1w) -EndTime 
    (ConvertFrom-AFRelativeTime -RelativeTime *) -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PI Incidents from the "PISRV1" PI Data Archive that occurred in 
    the last week.


##    Get-PIDataArchiveIncidentUpdate

SYNOPSIS
    Get PI Data Archive Incidents that were updated since a specified time
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDataArchiveIncidentUpdate -Connection $con -UpdateTime 
    (ConvertFrom-AFRelativeTime -RelativeTime *-5d)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will get PI Incidents on the "PISRV1" PI Data Archive that 
    have been updated in the last 5 days.


##    Get-PIDatabaseSecurity

SYNOPSIS
    Get PI Database Security entries for the PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDatabaseSecurity -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all entries of PI database security from the "PISRV1" PI Data Archive 
    server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIDatabaseSecurity -Name PIPoint -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the database security for the PIPoint table from the "PISRV1" PI Data 
    Archive server.


##    Get-PIDigitalStateSet

SYNOPSIS
    Get a PI Digital State Set
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIDigitalStateSet -Name "SYSTEM" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the "SYSTEM" digital state set from the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIDigitalStateSet -Name "SYSTEM" -Connection $con).ID
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the ID for the "SYSTEM" digital state set from the "PISRV1" PI Data 
    Archive. Note that the SYSTEM digital state set will always be ID = 0.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIDigitalStateSet -ID 47 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the digital state set of ID 47 from the "PISRV1" PI Data Archive.


##    Get-PIExpressionSummary

SYNOPSIS
    Get summary calculation for the specified expression
    
    

    ----------  EXAMPLE 1  ----------
    
    $results = Get-PIExpressionSummary -Times $times -Intervals 28 
    -SummaryType Average -Basis TimeWeighted -Expression "'Sinusoid'" 
    -Connection $con
    
    Where:
    
    $times = @("1-Feb-2017","1-Mar-2017")
    
    This example will calculate daily, timeweighted averages for the month of 
    February for the expression 'Sinusoid'. The StartTime of the query is the 
    first element in the $times array and the EndTime is the second element in 
    the $times array. The -Intervals is the number of equal eegments you want 
    to split the time range into, in this case 28. Since there are 28 days 
    from 1-Feb to 1-Mar, this becomes a daily average.
    
    The $results are returned as a hashtable and can be consumed in a number 
    of ways. The simplest being:
    
    $results.Value.Values[0] to extract the summary starttimes
    
    $results.Value.Values[1] to extract the summary endtimes
    
    $results.Value.Values[2] to extract the summary values
    
    $results.Value.Values[3] to extract the summary percent good of the 
    summary queries
    
    ----------  EXAMPLE 2  ----------
    
    $results = Get-PIExpressionSummary -Times $times -Intervals $intervals 
    -SummaryType Average -Basis TimeWeighted -Expression "'Sinusoid'+'CDT158'" 
    -Connection $con
    
    Where:
    
    $times = @("1-Jan-2017","1-Feb-2017","1-Mar-2017")
    
    $intervals = @(31,28)
    
    This example will return the daily time-weighted average of the sum of two 
    tags, sinusoid and cdt158, for each day in January and February of 2017.
    
    In this case we are querying over two separate intervals, the first from 
    1-Jan-2017 to 1-Feb-2017 with 31 intervals (31 days) and the second being 
    from 1-Feb-2017 to 1-Mar-2017 with 28 intervals (28 days). So, the first 
    element of $intervals applies to the first and second element of $times, 
    the second element of $intervals applies to the second and third elements 
    of $times, etc. So, $intervals must have 1 less element than $times.
    
    Note that -Times takes an array of timestamps, -Intervals takes either a 
    single integer value or an array of integer values, and -Expression takes 
    a valid PI Performance Equation expression. The results of this cmdlet 
    ($results) is a hash table. See the previous example for an example of how 
    to extract data from the results hash table.

##    Get-PIFirewall

SYNOPSIS
    Get an entry in the PI Firewall Table
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIFirewall -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all entries in the PI Firewall table from the "PISRV1" PI Data 
    Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIFirewall -Hostmask "192.168.0.56" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the entry in the PI Firewall table for the hostmask 192.168.0.56 from 
    the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIFirewall -Connection $con | Where-Object -Property Access -eq 
    "Disallow"
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all disallowed entries in the PI Firwall table from the "PISRV1" PI 
    Data Archive server.


##    Get-PIGroup

SYNOPSIS
    Gets an existing PI Group on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIGroup -Name "PIEngineersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example gets an existing PI Group "PIEngineersGroup" from the 
    "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIGroup -Name * -Connection $con | Select-Object -Property Name,Users
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example gets a list of all PI Groups and what PI Users belong to each 
    from the "PISRV1" PI Data Archive.


##    Get-PIIdentity

SYNOPSIS
    Get a PI Security Identity
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIIdentity -Name "PIEngineers" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Get the PI Identity "PIEngineers" from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIIdentity -Name "*" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PI Identities from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 3  ----------
    
    (Get-PIIdentity -Name "*" -Connection $con).Name
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a simple list of just names of PI Identities on the "PISRV1" Data 
    Archive server.
    
    ----------  EXAMPLE 4  ----------
    
    Get-PIIdentity -Name "*" -Connection $con | Where-Object -Property 
    IsEnabled -is $true
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a list of only PI Identities which are enabled on the "PISRV1" Data 
    Archive server.


##    Get-PILicenseAllowedApplication

SYNOPSIS
    Get a list of explicitly allowed applications for connecting to the 
    specified PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PILicenseAllowedApplication -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a list of all explicitly allowed application connections for the 
    "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PILicenseAllowedApplication -ApplicationType OSIInterface -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a list of explicitly allowed PI Interface connections for the 
    "PISRV1" PI Data Archive.


##    Get-PILicenseEntry

SYNOPSIS
    Get a PI License Entry for an application on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PILicenseEntry -Name PI-IN-OS-OPC.Default -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI License Entry for an OPC Interface connection on the "PISRV1" 
    PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PILicenseEntry -Name * -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all the PI License Entries for all possible connections on the 
    "PISRV1" PI Data Archive.


##    Get-PILicenseReport

SYNOPSIS
    Get a PI License Report for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PILicenseReport -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI License Report for the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PILicenseReport -Connection $con).Usage.CurrentPercentMatch
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the current license "percent match" for a PI Data Archive. If the 
    percent match falls below the "Required Percent Match", a new license file 
    should be generated. Contact technical support for more information.


##    Get-PILicenseUser

SYNOPSIS
    Get a PI License User on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PILicenseUser -Name "pibasess_14e1bf4d-df7e-464a-a617-78edf6bd11f0" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI License User information for PI Base Subsystem on the "PISRV1" 
    PI Data Archive. License users are PI Data Archive Subsystems (EX: 
    piarchss, pisnapss, pibasess, etc) and the names are 
    <subsystemname>_<PIServerGUID>. If you do not specify a name, all license 
    users are returned.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PILicenseUser -Name * -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all the PI License Users on the "PISRV1" PI Data Archive.


##    Get-PIMapping

SYNOPSIS
    Get a PI Security Mapping
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIMapping -Name 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Mapping 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" from the 
    "PISRV1" PI Data Archive server.
    
    Note that name of the mapping is typically Windows_[WindowsSID] where 
    [WindowsSID] is the Windows SID of the Windows User or Group the mapping 
    is for.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIMapping -Name "*" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PI Mappings from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIMapping -Name "*" -Connection $con | Where-Object -Property Identity 
    -eq "piadmin"
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a list of only PI Mappings which are mapped to the "piadmin" identity 
    on the "PISRV1" Data Archive server. This might be helpful when trying to 
    better lock down access to the PI Data Archive.


##    Get-PIMessage

SYNOPSIS
    Get PI Messages from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIMessage -StartTime (ConvertFrom-AFRelativeTime -RelativeTime *-2h) 
    -EndTime (ConvertFrom-AFRelativeTime -RelativeTime *) -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Retrieves all PI Messages from the "PISRV1" PI Data Archive server for the 
    last two hours.
    
    Run "Get-Help ConvertFrom-AFRelativeTime -Full" for more information on 
    using the ConvertFrom-AFRelativeTime cmdlet.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIMessage -StartTime "5-Apr-2017 12:00:00" -EndTime "5-Apr-2017 
    16:00:00" -Count 100 -SeverityType Warning -Program piarchss -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will retrieve the first 100 messages during the time range 
    "5-Apr-2017 12:00:00" to "5-Apr-2017 16:00:00" with severity of "Warning" 
    or greater, for the program name piarchss (PI Archive Subsystem).
    
    The severity level parameter indicates the minimum severity level of 
    message to retrieve. Severities are ranked as follows:
    
    Debug < Informational < Warning < Error < Critical
    
    Therefore, a specified severity level of "Warning" will only show messages 
    with severity level of Warning, Error, or Critical.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIMessage -StartTime "8-Jan-2017 08:00:00" -EndTime "8-Jan-2017 
    12:00:00" -Message "*PostEvent Failed*" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will retrieve messages during the time range "8-Jan-2017 
    08:00:00" to "8-Jan-2017 12:00:00" where the message body contains the 
    string "*PostEvent Failed*" Note that wildcards are allowed. The -Message 
    parameter can be used in conjunction with other filters from the previous 
    example such as -Program, -SeverityType, -Source1, etc.
    
    ----------  EXAMPLE 4  ----------
    
    Get-PIMessage -StartTime "22-Aug-2017 00:00:00" -EndTime "23-Aug-2017 
    00:00:00" -ID 7138 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will retrieve messages with message ID 7138 during the time 
    range "22-Aug-2017 00:00:00" to "23-Aug-2017 00:00:00" . The message ID of 
    7138 corresponds to:
    
    Unsuccessful login Error: [-10413] No trust relation for this request


##    Get-PIPoint

SYNOPSIS
    Gets PI Point(s) from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    $pipoints = Get-PIPoint -Name Sinu* -Attributes 
    tag,recono,pointid,pointsource,ptsecurity,datasecurity -Connection $con
    
    This example returns the tag name, record number, point ID, point source, 
    point security ACL, and data security ACL for all tags whose name begins 
    with "sinu". Note that wildcard searches are supported in this cmdlet. If 
    you want to return all of the tag attributes, use the switch 
    -AllAttributes instead of -Attributes.
    ----------  EXAMPLE 2  ----------
    
    $pipoints = Get-PIPoint -WhereClause "pointsource:=OPC" -AllAttributes 
    -Connection $con
    
    This example will get all points that have a pointsource = "OPC" with all 
    attributes included.
    ----------  EXAMPLE 3  ----------
    
    $pipoints = Get-PIPoint -WhereClause "creationdate:>1-Jun-2017" 
    -Connection $con
    
    This example will get all points created on the PI Data Archive since June 
    1, 2017.
    ----------  EXAMPLE 4  ----------
    
    $pipoints = Get-PIPoint -WhereClause "creationdate:>1-Jun-2017 
    pointsource:=OPC" -Connection $con
    
    This example combines the previous two examples and gets the PI Points 
    with pointsource OPC that were created since June 1, 2017. The conditions 
    are "and" conditions.

##    Get-PIPointClass

SYNOPSIS
    Get a PI Point Class from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIPointClass -Name "Classic" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Point Class "Classic" from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIPointClass -Name "Totalizer" -Connection $con).Value
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the default PIPoint attributes and attribute values for the PI Point 
    Class "Totalizer" from the "PISRV1" PI Data Archive server.


##    Get-PIPointSource

SYNOPSIS
    Get a PI PointSource
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIPointSource -Name "OPC" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PointSource "OPC" and the number of PI Points associated with 
    that point source from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIPointSource -Name "*" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PointSources and the number of PI Points associated with each 
    point source from the "PISRV1" PI Data Archive server.


##    Get-PISnapshotStatistics

SYNOPSIS
    Get snapshot statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PISnapshotStatistics -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Gets the snapshot statistics on the "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 2  ----------
    
    Get-PISnapshotStatistics -ArchiveSet 1 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the snapshot statistics for future tags on the "PISRV1" PI Data 
    Archive server
    
    ----------  EXAMPLE 3  ----------
    
    for () { Get-PISnapshotStatistics -Connection $con; Write-Host; 
    Start-Sleep -Seconds 5 }
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the snapshot statistics for the "PISRV1" PI Data Archive server every 
    5 seconds indefinitely and writes results to the console. Similar to 
    "piartool -ss" output.


##    Get-PIStatus

SYNOPSIS
    Get information about a PI Status code
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIStatus -Status -7
    
    Gets the information related to error code "-7". Note that this is a 
    PI-specific error code because it is negative. The code translates to:
    
    [-7] Tag Already Exists
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIStatus -Status 5
    
    Gets the information related to error code "5". Note that this is not a 
    PI-specific error code because it is positive. The code translates to:
    
    [5] Access is denied.


##    Get-PIThreadInformation

SYNOPSIS
    Get Thread Information for a PI Subsystem on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIThreadInformation -Subsystem Archive -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the thread information objects for the PI Archive Subsystem from the 
    PISRV1 PI Data Archive
    
    ----------  EXAMPLE 2  ----------
    
    (Get-PIThreadInformation -Subsystem Archive -Connection $con | 
    Where-Object -Property ThreadType -EQ Flush).Details
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the historical flush thread details for the PI Archive Subsystem on 
    the PISRV1 PI Data Archive
    
    ----------  EXAMPLE 3  ----------
    
    (Get-PIThreadInformation -Subsystem Archive -Connection $con | 
    Where-Object -Property ThreadType -EQ RPC).Details
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the RPC thread details for the PI Archive Subsystem on the PISRV1 PI 
    Data Archive
    
    ----------  EXAMPLE 4  ----------
    
    (Get-PIThreadInformation -Subsystem Base -Connection $con | Where-Object 
    -Property ThreadType -EQ RPC).Details
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the RPC thread details for the PI Base Subsystem on the PISRV1 PI 
    Data Archive


##    Get-PITrust

SYNOPSIS
    Get a PI Security Trust
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PITrust -Name "PIINT1_OPC_IPAddress" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Trust "PIINT1_OPC_IPAddress" from the "PISRV1" PI Data Archive 
    server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PITrust -Name "PIINT1*" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all PI Trusts that start with PIINT1 from the "PISRV1" PI Data 
    Archive server. Wildcards are supported by the -Name parameter in this 
    cmdlet.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PITrust -Name "*" -Connection $con | Group-Object -Property 
    ApplicationName
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets a list of all PI Trusts on the "PISRV1" Data Archive server and 
    groups the results by the ApplicationName the trust is configured for.


##    Get-PITuningParameter

SYNOPSIS
    Get PI Data Archive tuning parameters for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PITuningParameter Server_AuthenticationPolicy -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the Server_AuthenticationPolicy tuning parameter from the "PISRV1" PI 
    Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PITuningParameter -Name * -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets all tuning parameters from the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PITuningParameter -Name * -Connection $con | Select-Object -Property 
    name,takeseffect,description
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Creates a list of all tuning parameters and their associated description, 
    as well as when the parameter takes effect. This can be helpful for 
    reference or for help when looking for settings or configuration 
    information for a parameter.


##    Get-PIUpdateManagerConsumerStatistics

SYNOPSIS
    Get PI Update Manager consumer statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIUpdateManagerConsumerStatistics -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager consumer statistics for all consumers on the 
    "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIUpdateManagerConsumerStatistics -Name *ProcBook* -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager consumer statistics for all consumers matching 
    the string "*procbook*" (ProcessBook consumers) on the "PISRV1" PI Data 
    Archive server


##    Get-PIUpdateManagerProducerStatistics

SYNOPSIS
    Get PI Update Manager producer statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIUpdateManagerProducerStatistics -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager producer statistics for all producers on the 
    "PISRV1" PI Data Archive server
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIUpdateManagerProducerStatistics -Name snapshots -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager producer statistics for snapshot updates on the 
    "PISRV1" PI Data Archive server


##    Get-PIUpdateManagerSignupStatistics

SYNOPSIS
    Get PI Update Manager signup statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIUpdateManagerSignupStatistics -Connection $con | Sort-Object 
    -Property Producer
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager signup statistics on the "PISRV1" PI Data 
    Archive server, then sorts the output by Producer. This is similar output 
    to "piartool.exe -ss -sp"
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIUpdateManagerSignupStatistics -Connection $con | Sort-Object 
    -Property Pending -Descending
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager signup statistics on the "PISRV1" PI Data 
    Archive server, then sorts the output and lists signups with most pending 
    events first.


##    Get-PIUpdateManagerStatistics

SYNOPSIS
    Get Global PI Update Manager statistics for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIUpdateManagerStatistics -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the global PI Update Manager signup statistics on the "PISRV1" PI 
    Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    for () { Get-PIUpdateManagerStatistics -Connection $con; Write-Host; 
    Start-Sleep -Seconds 5 }
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the PI Update Manager signup statistics on the "PISRV1" PI Data 
    Archive server, and re-outputs the results every 5 seconds/


##    Get-PIUser

SYNOPSIS
    Gets an existing PI User on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIUser -Name "John Doe" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example gets an existing PI User "John Doe" from the "PISRV1" PI Data 
    Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIUser -Name * -Connection $con | Select-Object -Property Name,Groups
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example gets a list of all PI Users and what PI Groups they belong to 
    from the "PISRV1" PI Data Archive.


##    Get-PIValue

SYNOPSIS
    Get a PI Value at a specified time or for a specified time range.
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIValue -PointName Sinusoid -Time "5-Aug-2017 10:00:00" -ArchiveMode 
    Interpolated -Connection $con
    
    Get PI Value at a Specified Time Using PointName:
    
    This example will retrieve an interpolated value at 10:00am on Aug 5, 2017 
    for the PI Point "Sinusoid". Valid options for -ArchiveMode are: Previous, 
    Auto, Before, Interpolated, After, Next. Interpolated is the default 
    ArchiveMode.
    
    The tag can also be specified by Point ID rather than PointName by using 
    -PointID <PointID> parameter in place of -PointName
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIValue -PIPoint (Get-PIPoint -Name Sinusoid -Connection $con) -Time 
    "5-Aug-2017 10:00:00" -ArchiveMode Interpolated
    
    Get PI Value at a Specified Time Using PIPoint Object:
    
    This example does the same thing as the first example, except that the 
    PIPoint object is supplied via Get-PIPoint instead of specifying the 
    PointName string.
    
    ----------  EXAMPLE 3  ----------
    
    Get-PIValue -PointName Sinusoid -StartTime "5-Aug-2017 10:00:00" -Count 10 
    -Reverse -Connection $con
    
    Get Number of Events From a StartTime:
    
    This example will retrieve the 10 events prior to the specified StartTime 
    of "5-Aug-2017 10:00:00" for the PointName "Sinusoid".
    
    If -Reverse is not specified, events after the StartTime are returned. If 
    -Reverse is specified (as in this case) events prior to the StartTime are 
    returned.
    
    Instead of -PointName, either -PointID or -PIPoint can also be used to 
    define the PI Point for which to retrieve the values.
    
    ----------  EXAMPLE 4  ----------
    
    Get-PIValue -PIPoint (Get-PIPoint -Name Sinusoid -Connection $con) 
    -StartTime "5-Aug-2017 10:00:00" -EndTime "6-Aug-2017 10:00:00" -MaxCount 
    1000
    
    Get PI Values in a Time Range:
    
    This example uses -PIPoint and Get-PIPoint to retrieve values for Sinusoid 
    between the 5th and 6th of August, 2017 at 10:00:00. -MaxCount is used in 
    this case to protect against querying too many values, and will only 
    return up to 1000 values if more than 1000 values exist in the time range.
    
    If -MaxCount is not specified, then all values in the time range will be 
    returned.
    
    ----------  EXAMPLE 5  ----------
    
    Get-PIValue -PIPoint (Get-PIPoint -Name Sinusoid -Connection $con) 
    -StartTime (ConvertFrom-AFRelativeTime -RelativeTime "*-4h") -EndTime 
    (ConvertFrom-AFRelativeTime -RelativeTime "*")
    
    Get PI Values in a Time Range Using ConvertFrom-AFRelativeTime:
    
    This example uses -PIPoint and Get-PIPoint to retrieve values for Sinusoid 
    for the last 4 hours using ConvertFrom-AFRelativeTime.
    
    Run "Get-Help ConvertFrom-AFRelativeTime" for more details.
    
    ----------  EXAMPLE 6  ----------
    
    Get-PIValue -PIPoint (Get-PIPoint -Name Sinusoid -Connection $con) -Time 
    (ConvertFrom-AFRelativeTime -RelativeTime "*") -ArchiveMode Previous
    
    Get Snapshot Value for a Tag:
    
    This example will get the snapshot value for a tag. Note that -ArchiveMode 
    Previous must be used with a relative time of "*", otherwise an 
    interpolated value (default) will be returned, which is not the correct 
    snapshot value.
    
    ----------  EXAMPLE 7  ----------
    
    Get-PIValue -InterpolatedEvents -PIPoint (Get-PIPoint -Name Sinusoid 
    -Connection $con) -StartTime (ConvertFrom-AFRelativeTime -RelativeTime 
    "y") -EndTime (ConvertFrom-AFRelativeTime -RelativeTime "t") -MaxCount 10
    
    Get Snapshot Value for a Tag:
    
    This example will get the interpolated events for the specified PI Point. 
    Note that -InterpolatedEvents must be used to get interpolated events.


##    Import-AFXml

SYNOPSIS
    Import XML representation of AF Objects from file or System.IO.Stream
    
    

    ----------  EXAMPLE 1  ----------
    
    Import-AFXml -File C:\MyAFElements.xml -AFObject (Get-AFDatabase -Name 
    MyDatabase -AFServer (Get-AFServer -Name "PIAF1")) -ImportMode AllowCreate
    
    Imports the AF Element objects in MyAFElements.xml into the AF Database 
    "MyDatabase" on the PIAF1 AF Server. The AllowCreate option means that if 
    the element is not found, it will be created.


##    Lock-AFEventFrame

SYNOPSIS
    Lock an AF Event Frame
    
    

    ----------  EXAMPLE 1  ----------
    
    Lock-AFEventFrameParent -AFEventFrame $MyEventFrame -CheckIn
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $MyEventFrame = Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 
    -AFServer $afServer
    
    This example locks the AF Event Frame stored in $MyEventFrame. The change 
    is checked in immediately.


##    New-AFCheckIn

SYNOPSIS
    Check in changes to an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    New-AFCheckIn -AFDatabase $afDB -AFCheckedOutMode 
    AllObjectsCheckedOutThisSession
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Checks in all checked out objects in the current session in the AF 
    Database "AFDatabase1" on the AF Server "PIAF1"
    
    ----------  EXAMPLE 2  ----------
    
    New-AFCheckIn -AFServer $afDB -AFCheckedOutMode 
    AllObjectsCheckedOutThisSession
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    Checks in all checked out objects in the current session in the AF 
    Server"PIAF1". Note that the only objects checked out on the server level 
    are AFContact, AFNotificationContactTemplate, and UOMDatabase check outs.
    
    ----------  EXAMPLE 3  ----------
    
    New-AFCheckin -ItemToCheckIn $checkedoutElement
    
    Where:
    
    $checkedoutElement is an AF Element that has previously been checked out. 
    This can be done explicitly with New-AFCheckOut or implicitly by making a 
    change to the object.
    
    Checks in the checked out AF Element stored in $checkedoutElement. This 
    variable can also store multiple AF Elements and all will be checked in.
    
    ----------  EXAMPLE 4  ----------
    
    New-AFCheckin -ItemToCheckIn $checkedoutElement1, $checkedoutAttribute1, 
    $checkedoutAttribute2
    
    Where:
    
    $checkedoutElement1, $checkedoutAttribute1, and $checkedoutAttribute2 are 
    an AF Element, AF Attribute, and AF Attribute (respectively) which have 
    all been checked out.
    
    Checks in the comma separated list of AF Objects to the AF Server.


##    New-AFCheckOut

SYNOPSIS
    Check out AF Objects on an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    New-AFCheckOut -ItemsToCheckOut (Get-AFElement -Name Boiler1 -AFDatabase 
    $afDB)
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Explicitly checks out the top level element "Boiler1" on the AF Database 
    "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    $MyCheckedOutElement = New-AFCheckOut -ItemsToCheckOut (Get-AFElement 
    -Name Boiler1 -AFDatabase $afDB) -PassThrough
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Explicitly checks out the top level element "Boiler1" on the AF Database 
    "AFDatabase1" on the AF Server "PIAF1". The object which is checked out is 
    returned by the cmdlet and stored in variable $MyCheckedOutElement for 
    further use.
    
    ----------  EXAMPLE 3  ----------
    
    New-AFCheckOut -ItemsToCheckOut $MyAFElements
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    $MyAFElements = Get-AFElement -Name * -AFDatabase $afDB
    
    Explicitly checks out all top level elements on the AF Database 
    "AFDatabase1" on the AF Server "PIAF1".


##    New-PIArchive

SYNOPSIS
    Creates a new PI Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    New-PIArchive -Name E:\PIArchives\piarch009.arc -Size 1024 -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Creates a new archive file at E:\PIArchives\piarch000.arc and attempts 
    registration with the "PISRV1" PI Data Archive server. This archive has an 
    undefined start time and end time.
    
    ----------  EXAMPLE 2  ----------
    
    New-PIArchive -Name "D:\Program Files\PI\arc\piarch008.arc" -StartTime 
    "01-Jan-2016" -EndTime "01-Feb-2016" -Size 512 -ArchiveSet 0 -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Creates a new archive file for the month of Jan, 2016 with fixed size of 
    512 MB at "D:\Program Files\PI\arc\piarch008.arc" and attempts to 
    registration with the "PISRV1" PI Data Archive server. Note that the path 
    to the archive contains a space so the entire path must be enclosed in 
    double quotes.


##    New-PIBackupRestoreFile

SYNOPSIS
    Create a new archive manager data file
    
    

    ----------  EXAMPLE 1  ----------
    
    Get-PIBackupRestoreFile -OutputDirectory D:\PIBackup 
    -HistoricalArchiveDirectory "F:\PI\PIArchives" -NumberOfArchives 50 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will create a copy of the current archive manager data file 
    (piarstat.dat) in the D:\PIBackup directory. The resulting file will 
    include the archive registration information for the 50 most recent 
    historical archives on the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Get-PIBackupRestoreFile -OutputDirectory D:\PIBackup -ArchiveDirectories 
    "F:\PI\HistPIArchives","H:\PI\FuturePIArchives" -NumberOfArchives 15 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will create a copy of the current archive manager data file 
    (piarstat.dat) in the D:\PIBackup directory. The resulting file will 
    include the archive registration information for the 15 most recent 
    historical archives and all the future archives on the "PISRV1" PI Data 
    Archive.
    
    Note this example only potentially applies to PI Data Archive 2015 or 
    later.


##    New-PICollective

SYNOPSIS
    Create a new PI Data Archive Collective information from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    New-PICollective -Name PI-Collective -Description "Corporate PI 
    Collective" -Secondaries "PISRV2" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    The example creates a new PI Data Archive Collective with the "PISRV1" PI 
    Data Archive server as the primary member, and "PISRV2" as the only 
    secondary member.
    
    Note that this cmdlet does not automatically initialize each secondary 
    member. This still must be done manually by taking a backup of the primary 
    PI Data Archive once the collective is formed, and restoring the backup on 
    each secondary member.
    
    ----------  EXAMPLE 2  ----------
    
    New-PICollective -Name PI-Collective -Description "Corporate PI 
    Collective" -Secondaries "PISRV2","PISRV3" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    The example creates a new PI Data Archive Collective with the "PISRV1" PI 
    Data Archive server as the primary member, with "PISRV2" and "PISRV3" as 
    the secondary members.
    
    Note that this cmdlet does not automatically initialize each secondary 
    member. This still must be done manually by taking a backup of the primary 
    PI Data Archive once the collective is formed, and restoring the backup on 
    each secondary member.


##    Register-PIArchive

SYNOPSIS
    Registers a PI Archive file with a PI Data Archive server.
    
    

    ----------  EXAMPLE 1  ----------
    
    Register-PIArchive -Name E:\PIArchives\piarch008.arc -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Registers the archive file found at E:\PIArchives\piarch008.arc on the 
    "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Register-PIArchive -Name "D:\Program Files\PI\arc\piarch008.arc" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Registers the archive file found at "D:\Program 
    Files\PI\arc\piarch008.arc" on the "PISRV1" PI Data Archive server. Note 
    that the path to the archive contains a space so the entire path must be 
    enclosed in double quotes.


##    Remove-AFAttribute

SYNOPSIS
    Remove an AF Attribute
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFAttribute -Name "Interior Temperature" -CheckIn -AFElement 
    $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Deletes the AF Attribute "Interior Temperature" on the top level element 
    "Anneal Oven 1" on the database "AFDatabase1" on the AF Server "PIAF1". 
    The changes are immediately checked in.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFAttribute -Name "Temperature (F)" -CheckIn -AFAttribute 
    $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Interior Temperature" -AFElement 
    $afElement
    
    Deletes the AF Sub Attribute "Temperature (F)" from the AF Attribute 
    "Interior Temperature" on the top level element "Anneal Oven 1" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The changes are 
    immediately checked in.


##    Remove-AFAttributeTemplate

SYNOPSIS
    Remove an AF Attribute Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFAttributeTemplate -Name "Temperature" -AFElementTemplate 
    $afEleTemplate -CheckIn
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Anneal Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Removes the AF Attribute Template "Temperature" from the element template 
    "Oven" on the database "AFDatabase1" on the AF Server "PIAF1". The change 
    is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFAttributeTemplate -AFAttributeTemplate $afAttTemplate -CheckIn
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttTemplate = Get-AFAttributeTemplate -Name "Temperature" 
    -AFElementTemplate $afElement
    
    Removes the AF Attribute Template "Temperature" from the element template 
    "Oven" on the database "AFDatabase1" on the AF Server "PIAF1". The change 
    is checked in immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Remove-AFAttributeTemplate -Name "Fahrenheit" -AFAttributeTemplate 
    $afAttTemplate -CheckIn
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttTemplate = Get-AFAttributeTemplate -Name "Temperature" 
    -AFElementTemplate $afElement
    
    Removes the Child AF Attribute Template "Fahrenheit" from the parent AF 
    Attribute Template "Temperature" on the element template "Oven" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The change is checked in 
    immediately.


##    Remove-AFCategory

SYNOPSIS
    Remove an AF Category
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFCategory -Name "Product A Manufacturing" -Element -AFDatabase 
    $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Deletes an existing AF Element Category "Product A Manufacturing" from the 
    AF Database "AFDatabase1" on AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFCategory -Name "KPIs" -Attribute -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Deletes an existing AF Attribute Category "KPIs" from the AF Database 
    "AFDatabase1" on AF Server "PIAF1".
    
    ----------  EXAMPLE 3  ----------
    
    Remove-AFCategory -AFCategory $afCategory -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    $afCategory = Get-AFCategory -Name "Delete this Category" -Element 
    -AFDatabase $afDB
    
    Deletes an existing AF Element Category "Delete this Category" from the AF 
    Database "AFDatabase1" on AF Server "PIAF1".


##    Remove-AFDatabase

SYNOPSIS
    Removes an AF Database
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFDatabase -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase MyAFDB -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will remove the AF Database "MyAFDB" from AF Server "PIAF1" 
    by passing the AFDatabase object to Remove-AFDatabase
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFDatabase -Name MyAFDB -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will remove the AF Database "MyAFDB" from the AF Server 
    "PIAF1".


##    Remove-AFElement

SYNOPSIS
    Remove an AF Element
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFElement -AFElement $afElement -CheckIn
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Removes the element "Production Line 1" on the database "AFDatabase1" on 
    the AF Server "PIAF1". The change will be checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFElement -Name "Boiler 1" -AFDatabase $afDatabase
    
    Where:
    
    $afDatabase = Get-AFDatabase -Name "AFDatabase1" -CheckIn -AFServer 
    (Get-AFServer -Name "PIAF1")
    
    Removes the top level element "Boiler 1" from the database "AFDatabase1" 
    on the AF Server "PIAF1".


##    Remove-AFElementTemplate

SYNOPSIS
    Remove an AF Element Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFElementTemplate -Name "Boiler" -AFDatabase $afDB -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Deletes the element template "Boiler" on the database "AFDatabase1" on the 
    AF Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFElementTemplate -AFElementTemplate $afEleTemplate -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afEleTemplate = Get-AFElementTemplate -Name "Boiler" -AFDatabase $afDB
    
    Deletes the AF element template "Boiler" on the database "AFDatabase1" on 
    the AF Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Remove-AFElementTemplate -Name "*" -AFDatabase $afDB -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Deletes all element templates on the database "AFDatabase1" on the AF 
    Server "PIAF1". The change is checked in immediately.


##    Remove-AFEventFrame

SYNOPSIS
    Remove an AF Event Frame(s)
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFEventFrame -AFEventFrame $MyEventFrame -CheckIn
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    $MyEventFrame = Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 
    -AFServer $afServer
    
    This example deletes the AF Event Frame stored in $MyEventFrame. The 
    change is checked in immediately.


##    Remove-AFOrphans

SYNOPSIS
    Deletes orphaned child elements in the PISystem
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Remove-AFOrphans -Delay 0
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Deletes all orphaned child element objects in the PISystem immediately (no 
    delay).


##    Remove-AFPort

SYNOPSIS
    Remove an AF Port
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFPort -Name InputPort1 -AFElementTemplate $afElementTemplate 
    -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElementTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    Removes the existing AF Port InputPort1 from the Boiler element template 
    on the AF Database AFDatabase1. The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFPort -AFPort $MyAFPort -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElementTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    $MyAFPort = Get-AFPort -Name InputPort1 -AFElementTemplate 
    $afElementTemplate
    
    Removes the AF Port InputPort1 from the Boiler element template on the AF 
    Database AFDatabase1.


##    Remove-AFSecurity

SYNOPSIS
    Remove an AF Security Identity from an AF object
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFSecurity -AFSecurityIdentity $afIdentity -ApplyTo $afDB -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Where:
    
    $afIdentity = Get-AFSecurityIdentity -Name Engineers -AFServer 
    (Get-AFServer -Name PIAF1)
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    Removes the AF Security Identity "Engineers" from the AF Database 
    "AFDatabase1" on the AF Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFSecurity -AFSecurityIdentity $afIdentity -ApplyTo $afElement 
    -ApplyToChildren -AFServer (Get-AFServer -Name PIAF1)
    
    Where:
    
    $afIdentity = Get-AFSecurityIdentity -Name Engineers -AFServer 
    (Get-AFServer -Name PIAF1)
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Removes the AF Security Identity "Engineers" from the AF Element 
    "Production Line 1" on the AF Database "AFDatabase1" on the AF Server 
    "PIAF1". The Identity is also removed from all child elements of 
    "Production Line 1".


##    Remove-AFSecurityIdentity

SYNOPSIS
    Removes an existing AF Security Identity from an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFSecurityIdentity -Name "Engineers" -CheckIn -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Removes the existing AF Security Identity "Engineers" from the AF Server 
    "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFSecurityIdentity -AFSecurityIdentity $EngineersIdentity -CheckIn
    
    Where:
    
    $EngineersIdentity = Get-AFSecurityIdentity -Name "Engineers" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Removes the existing AF Security Identity "Engineers" from the AF Server 
    "PIAF1". The change is checked in immediately.


##    Remove-AFSecurityMapping

SYNOPSIS
    Remove an AF Security Mapping from an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFSecurityMapping -Name "domain\testuser" -CheckIn -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Removes an existing AF Security Mapping called "domain\testuser" from the 
    AF Server "PIAF1". The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFSecurityMapping -AFSecurityMapping $TestUser -CheckIn -AFServer 
    (Get-AFServer -Name PIAF1)
    
    Where:
    
    $TestUser = Get-AFSecurityMapping -Name "domain\testuser" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Removes an existing AF Security Mapping called "domain\testuser" from the 
    AF Server "PIAF1". The change is checked in immediately.


##    Remove-AFServer

SYNOPSIS
    Remove an AF Server connection configuration from local AF Server list
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFServer -Name PIAF1
    
    This example will remove the AF Server named "PIAF1" from the local AF 
    Server list.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-AFServer -AFServer (Get-AFServer -Name PIAF1)
    
    This example will remove the AF Server named "PIAF1" from the local AF 
    Server list using the Get-AFServer cmdlet to get the AF Server.
    
    Run "Get-Help Get-AFServer -Examples" for more information on this cmdlet.
    
    ----------  EXAMPLE 3  ----------
    
    Remove-AFServer -AFServer (Get-AFServer -Default)
    
    This example will remove the default AF Server from the local AF Server 
    list using the Get-AFServer cmdlet to get the AF Server. The next indexed 
    AF Server will become the new default AF Server.


##    Remove-AFTrustedProvider

SYNOPSIS
    Removes the specified trusted provider subject name from the list of 
    trusted providers in the PISystem.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Remove-AFTrustedProvider -ProviderName "SampleProviderName"
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Removes the "SampleProviderName" provider as a trusted provider in 
    PISystem specified by the AFServer.


##    Remove-AFUnitOfMeasure

SYNOPSIS
    Remove an AF Unit of Measure
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFUnitOfMeasure -Name "decimeter" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Removes the existing AF Unit of Measure "decimeter" from the AF Server 
    "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Remove-UnitOfMeasure -AFUnitOfMeasure $UOMtoDelete -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $UOMtoDelete = Get-AFUnitOfMeasure -Name "decimeter" -AFServer $afServer
    
    Removes the existing AF Unit of Measure "decimeter" from the AF Server 
    "PIAF1".


##    Remove-AFUnitOfMeasureClass

SYNOPSIS
    Remove an AF Unit of Measure Class
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-AFUnitOfMeasureClass -Name "MyUOMClass" -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    Removes the existing AF Unit of Measure Class "MyUOMClass" from the AF 
    Server "PIAF1".
    
    ----------  EXAMPLE 2  ----------
    
    Remove-UnitOfMeasureClass -AFUnitOfMeasureClass $UOMClassToRemove
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $UOMClassToRemove = Get-AFUnitOfMeasureClass -Name "MyUOMClass" -AFServer 
    $afServer
    
    Removes the existing AF Unit of Measure Class "MyUOMClass" from the AF 
    Server "PIAF1".


##    Remove-PIBufferedServer

SYNOPSIS
    Remove a PI Buffered Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIBufferSession -LogicalServerName PISRV-OldStandalone
    
    This example removes the buffered server "PISRV1-OldStandalone" from the 
    local PI Buffer Subsystem instance. The user is prompted for confirmation 
    before the server is removed.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-PIBufferSession -LogicalServerName PISRV-OldCollective -Force
    
    This example removes the buffered server "PISRV1-OldCollective" from the 
    local PI Buffer Subsystem instance. The buffered server is removed 
    immediately without prompting for confirmation from the user.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { Remove-PIBufferedServer 
    -LogicalServerName PISRV-OldStandalone }
    
    This example removes the buffered server "PISRV1-OldStandalone" from the 
    PIINT1 PI Buffer Subsystem instance. The user is prompted for confirmation 
    before the server is removed.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Remove-PIBufferedServer, but with the 
    network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Remove-PICollective

SYNOPSIS
    Remove all members from a PI Data Archive Collective
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PICollective -PICollective (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes all members from the PI Data Archive Collective which "PISRV1" is 
    a member


##    Remove-PICollectiveMember

SYNOPSIS
    Remove a PI Data Archive from an existing PI Data Archive Collective
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PICollectiveMember -Name "PISRV2" -PICollective (Get-PICollective 
    -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes the PI Data Archive "PISRV2" from the PI Data Archive collective 
    which the "PISRV1" PI Data Archive server is a part of. If multiple 
    members are to be removed, run the command again for each member to be 
    removed.


##    Remove-PIDataArchiveConnectionConfiguration

SYNOPSIS
    Removes a connection configuration entry in the local Known Servers Table 
    (KST)
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIDataArchiveConnectionConfiguration -Name PISRV1
    
    This example removes the Known Servers Table (KST) entry for PISRV1. Note 
    that PISRV1 cannot be the default PI Data Archive.


##    Remove-PIDigitalStateFromStateSet

SYNOPSIS
    Remove a PI Digital State from a PI Digital State Set
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIDigitalStateFromStateSet -StateName "OFF" -Name "BoilerState" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example removes the digital state "OFF" from the PI Digital State Set 
    "BoilerState" on the "PISRV1" PI Data Archive. If the original PI Digital 
    State Set configuration was as follows:
    
    0="ON" : 1="OFF" : 2="STARTUP" : 3="COOLDOWN"
    
    Then after running this example, the "BoilerState" PI Digital State Set 
    would now look like the following:
    
    0="ON" : 1="STARTUP" : 2="COOLDOWN"


##    Remove-PIDigitalStateSet

SYNOPSIS
    Remove a PI Digital State Set from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIDigitalStateSet -Name "BoilerState" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example removes the PI Digital State Set "BoilerState" from the 
    "PISRV1" PI Data Archive.


##    Remove-PIFirewall

SYNOPSIS
    Add an entry in the PI Firewall Table
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIFirewall -Hostmask "192.168.0.56" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes an entry in the PI Firewall table for IP Address 192.168.0.56 on 
    the "PISRV1" PI Data Archive server.


##    Remove-PIGroup

SYNOPSIS
    Removes an existing PI Group on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIGroup -Name "PIEngineersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example removes an existing PI Group "PIEngineersGroup" from the 
    "PISRV1" PI Data Archive.


##    Remove-PIIdentity

SYNOPSIS
    Remove a PI Security Identity
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIIdentity -Name "ProductionLine_Engineers" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes the PI Identity "FloorEngineers" to "ProductionLine_Engineers" on 
    the "PISRV1" PI Data Archive server.


##    Remove-PIMapping

SYNOPSIS
    Remove a PI Security Mapping
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIMapping -Name 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes the PI Mapping 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" from the 
    "PISRV1" PI Data Archive server.


##    Remove-PIPoint

SYNOPSIS
    Remove a PI Point from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIPoint -Name BoilerTemp1 -Connection $con
    
    This example will delete the PI Point "BoilerTemp1" from the PI Data 
    Archive specified by the -Connection parameter.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-PIPoint -Name BoilerTemp1,BoilerTemp2,BoilerTemp3 -Connection $con
    
    This example will delete the tags contained in a comma separated list from 
    the PI Data Archive specified by the -Connection parameter.


##    Remove-PITrust

SYNOPSIS
    Remove a PI Security Trust
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PITrust -Name "PIINT1_OPC_IPAddress" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Removes the PI Trust "PIINT1_OPC_IPAddress" from the "PISRV1" PI Data 
    Archive server.


##    Remove-PIUser

SYNOPSIS
    Removes an existing PI User from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIUser -Name "John Doe" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example removes an existing PI User "John Doe" from the "PISRV1" PI 
    Data Archive. To remove multiple PI Users, rerun the command for each PI 
    User to remove.


##    Remove-PIUserFromPIGroup

SYNOPSIS
    Remove a PI User from PI Groups on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIUserFromPIGroup -Name "John Doe" -PIGroups 
    "PIEngineersGroup","PIReadersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example removes the PI User "John Doe" from two PI Groups 
    "PIEngineersGroup" and "PIReadersGroup" on the "PISRV1" PI Data Archive.


##    Remove-PIValue

SYNOPSIS
    Remove a PI Value or Values from a PI Data Archive.
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIValue -PointName Sinusoid -Time "1-Aug-2017 11:00:00" -Value 100 
    -Connection $con
    
    Remove PI Value at a Specified Time Using PointName:
    
    This example will remove a value of 100 at a timestamp of "1-Aug-2017 
    11:00:00" from the Sinusoid tag on the PI Data Archive specified in the 
    -Connection.
    
    ----------  EXAMPLE 2  ----------
    
    Remove-PIValue -PIPoint (Get-PIPoint -Name Sinusoid -Connection $con) 
    -Time "1-Aug-2017 11:00:00" -Value 100
    
    Remove PI Value at a Specified Time Using PIPoint object:
    
    This example will remove a value of 100 at a timestamp of "1-Aug-2017 
    11:00:00" from the Sinusoid tag. The PI Point for which to remove the 
    value is obtained using Get-PIPoint and passed to the -PIPoint parameter. 
    Run "Get-Help Get-PIPoint" for more information on this cmdlet.
    
    ----------  EXAMPLE 3  ----------
    
    Remove-PIValue -Connection $con -Event (Get-PIValue -PointName Sinusoid 
    -StartTime "01-Jul-2017 00:00:00" -EndTime "02-Jul-2017 00:00:00")
    
    Remove a Range of Events Using Event:
    
    This example will remove the values from the PI Point Sinusoid for the 
    time range of 01-Jul to 02-Jul. The values to be removed are first 
    obtained using Get-PIValue and the resulting events are passed to the 
    -Event parameter to be removed.
    
    ----------  EXAMPLE 4  ----------
    
    Remove-PIValue -PointName Sinusoid,SinusoidU,CDT158 -Time 
    (ConvertFrom-AFRelativeTime -RelativeTime T+8h) -Value 100 -Connection $con
    
    Remove PI Value at a Specified Time Using PointName for Multiple Tags:
    
    This example will remove a value of 100 at a timestamp of "Today at 
    8:00am" from the tags in the PointName array: Sinusoid, SinusoidU, and 
    CDT158.
    
    ----------  EXAMPLE 5  ----------
    
    Remove-PIValue -PointName Sinusoid,SinusoidU,CDT158 -Time "01-Aug-2017 
    10:00:00","01-Aug-2017 11:00:00","01-Aug-2017 9:00:00" -Value 100,200,300 
    -Connection $con
    
    Remove PI Values at a Specified Times Using PointName for Multiple Tags:
    
    This example will remove a value of 100 at a timestamp of 01-Aug-2017 
    10:00:00 from Sinusoid, a value of 200 at 01-Aug-2017 11:00:00 from 
    SinusoidU, and a value of 300 at a timestamp of 01-Aug-2017 9:00:00 for 
    CDT158.
    
    Note that in this case the PointName, Time, and Value arrays all have the 
    same number of elements (3). Therefore, each first element is associated 
    with each other, each second element is associated with each other, etc.
    
    ----------  EXAMPLE 6  ----------
    
    Remove-PIValue -Event (Get-PIValue -PointName sinusoid -StartTime 
    (ConvertFrom-AFRelativeTime *-4h) -EndTime (ConvertFrom-AFRelativeTime *) 
    -Connection $con | Where-Object -Property Value -IsNot [System.Single]) 
    -Connection $con
    
    Remove Digital State Values for a PI Point for a Time Range:
    
    This example will remove all digital state values found in the last four 
    hours for the PI Point Sinusoid. The digital state values are determined 
    by checking the Value object type of events returned by Get-PIValue. If 
    they are not of type [System.Single], which corresponds to a PI Value type 
    of "Float32", then they will be removed. Assuming this tag is of type 
    Float32, the digital state values will be removed from the archives for 
    the PI Point Sinusoid.


##    Rename-PIDigitalStateSet

SYNOPSIS
    Rename a PI Digital State Set on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PIDigitalStateSet -ExistingName "BoilerState" -NewName 
    "BoilerXState" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example renames the PI Digital State Set "BoilerState" to 
    "BoilerXState" on the "PISRV1" PI Data Archive.


##    Rename-PIGroup

SYNOPSIS
    Renames an existing PI Group on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PIGroup -ExistingName "PIEngineersGroup" -NewName 
    "FloorEngineersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example renames an existing PI Group "PIEngineersGroup" to 
    "FloorEngineersGroup" on the "PISRV1" PI Data Archive.


##    Rename-PIIdentity

SYNOPSIS
    Rename a PI Security Identity
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PIIdentity -ExistingName "FloorEngineers" -NewName 
    "ProductionLine_Engineers" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Renames the PI Identity "FloorEngineers" to "ProductionLine_Engineers" on 
    the "PISRV1" PI Data Archive server.


##    Rename-PIMapping

SYNOPSIS
    Rename a PI Security Mapping
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PIMapping -ExistingName 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" -NewName "Jane 
    Doe" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Renames the PI Mapping 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-53017" to Jane Doe on 
    the "PISRV1" PI Data Archive server.
    
    Note that name of the mapping is typically Windows_[WindowsSID] where 
    [WindowsSID] is the Windows SID of the Windows User or Group the mapping 
    is for.
    
    Note that the mapping "Name" displayed in PI SMT is actually the 
    PrincipalName property of the PI Mapping object. This cmdlet edits the 
    Name property of the PI Mapping. So this name change will not affect what 
    is displayed in PI SMT.


##    Rename-PIPoint

SYNOPSIS
    Rename a PI Point on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PIPoint -Name "Boiler Temp 1" -NewName "Boiler_Temperature_1" 
    -Connection $con
    
    This example will rename the PI Point "Boiler Temp 1" to 
    "Boiler_Temperature_1".


##    Rename-PITrust

SYNOPSIS
    Rename a PI Security Trust
    
    

    ----------  EXAMPLE 1  ----------
    
    Rename-PITrust -ExistingName "PIINT1Trust" -NewName "PIINT1_OPCInt_IP" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Renames the "PIINT1Trust" as "PIINT1_OPCInt_IP" on the PI Data Archive 
    server "PISRV1"


##    Rename-PIUser

SYNOPSIS
    Rename an existing PI User on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Remove-PIUser -Name "John Doe" -NewName "John M Doe" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example renames an existing PI User "John Doe" to "John M Doe" on the 
    "PISRV1" PI Data Archive.


##    Reset-AFPathCache

SYNOPSIS
    Rebuilds the path cache to each element in the PI AF SQL Server database.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Rebuild-AFPathCache
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Rebuilds the path cache to each element in the PI AF SQL Server database.


##    Reset-AFServerIndex

SYNOPSIS
    Rebuilds every index in the PI AF SQL Server database.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Reindex-AFServer
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Rebuilds every index in the PI AF SQL Server database.


##    Reset-PIAFLinkModuleDatabaseFromAF

SYNOPSIS
    Reset the PI Module Database based on elements in the synchronized AF 
    Element
    
    

    ----------  EXAMPLE 1  ----------
    
    Reset-PIAFLinkModuleDatabaseFromAF -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Initiates a reset of the PI Module Database using the contents of the 
    associated AF Root Element.


##    Reset-PITuningParameter

SYNOPSIS
    Reset a PI Data Archive tuning parameter on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Reset-PITuningParameter Archive_LowDiskSpaceMB -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Resets the Archive_LowDiskSpaceMB tuning parameter from the "PISRV1" PI 
    Data Archive server. The default value for Archive_LowDiskSpaceMB can be 
    examined using "Get-PITuningParameter -Name Archive_LowDiskSpaceMB 
    -Connection $con".


##    Set-AFAttribute

SYNOPSIS
    Sets an AF Attribute
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFAttribute -NewName "Interior Temperature" -Description "Interior 
    temperature in celsius for Anneal Oven 1" -CheckIn -AFAttribute 
    $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Inner Temperature" -AFElement 
    $afElement
    
    Edits the AF Attribute "Inner Temperature" on the top level element 
    "Anneal Oven 1" on the database "AFDatabase1" on the AF Server "PIAF1". A 
    new name is given to the attribute, as well as a new description. Changes 
    are checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFAttribute -DefaultUnitOfMeasure (Get-AFUnitOfMeasure -Name "Degrees 
    Celsius" -AFServer (Get-AFServer -Name "PIAF1")) -CheckIn -AFAttribute 
    $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Interior Temperature" -AFElement 
    $afElement
    
    Sets the default unit of measure to "Degrees Celsius" for the AF Attribute 
    "Interior Temperature" on the top level element "Anneal Oven 1" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The changes are checked 
    in immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Set-AFAttribute -DataReferencePluginName "PI Point" -CheckIn -AFAttribute 
    $afAttribute
    
    Where:
    
    $afElement = Get-AFElement -Name "Anneal Oven 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttribute = Get-AFAttribute -Name "Interior Temperature" -AFElement 
    $afElement
    
    Sets the AF Attribute as a PI Point data reference for the AF Attribute 
    "Interior Temperature" on the top level element "Anneal Oven 1" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The changes are checked 
    in immediately.


##    Set-AFAttributeTemplate

SYNOPSIS
    Sets an AF Attribute Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFAttributeTemplate -NewName "Interior Temperature" -Description 
    "Interior temperature" -CheckIn -AFAttributeTemplate $afAttTemplate
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttTemplate = Get-AFAttributeTemplate -Name "My Attribute Template" 
    -AFElement $afEleTemplate
    
    Renames the AF Attribute Template "My Attribute Template" to "Interior 
    Temperature" on the element template "Oven" on the database "AFDatabase1" 
    on the AF Server "PIAF1". Changes are checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFAttributeTemplate -DefaultUnitOfMeasure (Get-AFUnitOfMeasure -Name 
    "degree celsius" -AFServer (Get-AFServer -Name "PIAF1")) -CheckIn 
    -AFAttributeTemplate $afAttAttribute
    
    Where:
    
    $afEleTemplate = Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttAttribute = Get-AFAttributeTemplate -Name "Interior Temperature" 
    -AFElementTemplate $afEleTemplate
    
    Sets the default unit of measure to "degree celsius" for the AF Attribute 
    Template "Interior Temperature" on the element template "Oven" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The changes are checked 
    in immediately.
    
    ----------  EXAMPLE 3  ----------
    
    Set-AFAttributeTemplate -DataReferencePluginName "PI Point" -CheckIn 
    -AFAttributeTemplate $afAttTemplate
    
    Where:
    
    $afEleTemplate= Get-AFElementTemplate -Name "Oven" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    $afAttTemplate = Get-AFAttributeTemplate -Name "Interior Temperature" 
    -AFElementTemplate $afEleTemplate
    
    Sets the AF Attribute Template "Interior Temperature" as a PI Point data 
    reference on the element template "Oven" on the database "AFDatabase1" on 
    the AF Server "PIAF1". The changes are checked in immediately.


##    Set-AFCategory

SYNOPSIS
    Set an AF Category
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFCategory -NewName "Product A Manufacturing" -CheckIn -AFCategory 
    $afCategory
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    $afCategory = Get-AFCategory -Name "New Category 1" -Element -AFDatabase 
    $afDB
    
    Renames an existing AF Element Category "New Category 1" to "Product A 
    Manufacturing" on the AF Database "AFDatabase1" on AF Server "PIAF1". The 
    change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFCategory -Description "KPIs for Product A Process" -CheckIn 
    -AFCategory $afCategory
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    $afCategory = Get-AFCategory -Name "KPIs" -Element -AFDatabase $afDB
    
    Adds a description to the existing AF Attribute Category "KPIs" on the AF 
    Database "AFDatabase1" on AF Server "PIAF1". The change is checked in 
    immediately.


##    Set-AFDatabase

SYNOPSIS
    Sets an AF Database
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFDatabase -NewName MyAFDB_Renamed -Description "New Description for 
    AF Database" -DefaultPIServerName "DEFPISERV" -AFDatabase $afDB
    
    Where:
    
    $afDB = Get-AFDatabase MyAFDB -AFServer (Get-AFServer -Name "PIAF1")
    
    This example will rename the AF Database "MyAFDB" to "MyAFDB_Renamed" and 
    also set the description to "New Description for AF Database" along with 
    default PI Server "-DefaultPIServerName "DEFPISERV"
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFDatabase -Default -AFDatabase (Get-AFDatabase -Name MyAFDB -AFServer 
    (Get-AFServer -Default))
    
    This example will set the AF Database "MyAFDB" as the default database on 
    the default AF Server in one line.


##    Set-AFElement

SYNOPSIS
    Set an AF Element
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFElement -NewName "Boiler Set 1" -AFElement $afElement -CheckIn
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Renames the top level element "Production Line 1" to "Boiler Set 1" on the 
    database "AFDatabase1" on the AF Server "PIAF1". The change will be 
    checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFElement -Description "First Production Line" -AFCategories 
    (Get-AFCategory -AFDatabase (Get-AFDatabase "AFDatabase1" -AFServer 
    (Get-AFServer -Name "PIAF1")) -Name "MyCategory" -Element) -CheckIn 
    -AFElement $afElement
    
    Where:
    
    $afElement = Get-AFElement -Name "Production Line 1" -AFDatabase 
    (Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1"))
    
    Edits the top level AF Element "Production Line 1" on database 
    "AFDatabase1" on AF Server "PIAF1" with a new description and sets the 
    element category to an existing AF Category "MyCategory". The change is 
    checked in immediately.


##    Set-AFElementTemplate

SYNOPSIS
    Set an AF Element Template
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFElementTemplate -NewName "Boiler" -AFElementTemplate $afEleTemplate 
    -CheckIn
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afEleTemplate = Get-AFElementTemplate -Name MyEleTemplate -AFDatabase 
    $afDB
    
    Renames the element template "MyEleTemplate" to "Boiler" on the database 
    "AFDatabase1" on the AF Server "PIAF1". The change is checked in 
    immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFElementTemplate -Description "Template for all Boilers" 
    -AllowExtensions $true -CheckIn -AFElementTemplate $afEleTemplate
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afEleTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    Sets the description for element template "Boiler" on the database 
    "AFDatabase1" on the AF Server "PIAF1". The change is checked in 
    immediately and the template is set to allow extensions.
    
    ----------  EXAMPLE 3  ----------
    
    Set-AFElementTemplate -AFCategories (Get-AFCategory -AFDatabase $afDB 
    -Name "Boiler" -Element) -AFElementTemplate $afEleTemplate
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afEleTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    Assigns the element template of "Boiler" on the database "AFDatabase1" on 
    the AF Server "PIAF1" to have the AF element category "Boiler". The change 
    is checked in immediately.


##    Set-AFEventFrame

SYNOPSIS
    Set an AF Event Frame
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFEventFrame -Description "Modified endtime: Manual downtime event" 
    -EndTime "1-Nov-2017 18:30:00" -CheckIn -AFAnalysis $afAnalysis 
    -AFEventFrame $MyEventFrame
    
    Where:
    
    $MyEventFrame = Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 
    -AFServer (Get-AFServer -Name PIAF1)
    
    $afElement = Get-AFElment -Name Boiler1 -Refresh -AFDatabase $afDB
    
    $afAnalysis = $afElement.Analyses[0]
    
    This example edits the description and the end time for an event frame. 
    The analysis that is associated with the event frame is updated as well. 
    The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFEventFrame -Description "Golden Batch" -CheckIn -AFDatabase $afDB
    
    Where:
    
    $MyEventFrame = Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 
    -AFServer (Get-AFServer -Name PIAF1)
    
    This example edits the description of an event frame to mark it as a good 
    reference event frame. The change is checked in immediately.


##    Set-AFFileOptions

SYNOPSIS
    Sets the file options used to validate an AFFile stored in the PISystem.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Set-AFFileOptions -AllowedFileExtensions "xyz" "abc" 
    -MaxFileLength 10
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Sets the file options used to validate an AFFile stored in the PISystem.


##    Set-AFPlugInVerifyLevel

SYNOPSIS
    Configures the level of verification required for an AFPlugIn to be loaded 
    from the server.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Set-AFPlugInVerifyLevel -Level RequireSigned
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Configures the level of verification required for an AFPlugIn to be loaded 
    from the server.


##    Set-AFPort

SYNOPSIS
    Set an AF Port
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFPort -Description "Input port for Boiler template" -MaxConnections 
    10 -AFPort $MyAFPort
    
    Where:
    
    $afDB = Get-AFDatabase "AFDatabase1" -AFServer (Get-AFServer -Name "PIAF1")
    
    $afElementTemplate = Get-AFElementTemplate -Name Boiler -AFDatabase $afDB
    
    $MyAFPort = Get-AFPort -Name InputPort1 -AFElementTemplate 
    $afElementTemplate
    
    Edits the AF Port InputPort1 from the Boiler element template on the AF 
    Database AFDatabase1 with an updated description and max number of 
    connections allowed.


##    Set-AFSecurityIdentity

SYNOPSIS
    Sets an AF Security Identity on an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFSecurityIdentity -NewName "Rolling Operators" -Description "All 
    plant floor operators for rolling operation" -CheckIn -AFSecurityIdentity 
    $OldIdentity
    
    Where:
    
    $OldIdentity = Get-AFSecurityIdentity -Name "Floor Operators" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Edits an AF Security Identity "Floor Operators" on the AF Server "PIAF1" 
    to have a new name "Rolling Operators" and an updated description. The 
    change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    $EditedIdentity = Set-AFSecurityIdentity -NewName "Rolling Operators" 
    -Description "All plant floor operators for rolling operation" -CheckIn 
    -PassThrough -AFSecurityIdentity $OldIdentity
    
    Where:
    
    $OldIdentity = Get-AFSecurityIdentity -Name "Floor Operators" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    Edits an AF Security Identity "Floor Operators" on the AF Server "PIAF1" 
    to have a new name "Rolling Operators" and an updated description. The 
    change is checked in immediately. The edited security AF Security Identity 
    is returned, and in this example is stored in $EditedIdentity.


##    Set-AFSecurityMapping

SYNOPSIS
    Set an AF Security Mapping on an AF Server
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFSecurityMapping -AFSecurityIdentity $Administrators -Description 
    "TestUser now added as administrator" -CheckIn -AFSecurityMapping $TestUser
    
    Where:
    
    $TestUser = Get-AFSecurityMapping -Name "domain\testuser" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    $Administrators = Get-AFSecurityIdentity -Name "Administrators" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    This example edits the current mapping for "domain\testuser" and sets his 
    AF Identity to give him "Administrators" permissions. The description is 
    also updated to reflect this change. The change is checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFSecurityMapping -NewName "TestUser_Administrator" -CheckIn 
    -AFSecurityMapping $TestUser
    
    Where:
    
    $TestUser = Get-AFSecurityMapping -Name "domain\testuser" -Refresh 
    -AFServer (Get-AFServer -Name "PIAF1")
    
    This example renames the mapping for "domain\testuser" on the "PIAF1" AF 
    Server to "TestUser_Administrator". The change is checked in immediately.


##    Set-AFServer

SYNOPSIS
    Sets an AF Server connection configuration in the local AF Server list
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFServer -Description "New description for Corporate AF Server" 
    -DefaultPIServerName "DEFPISERV" -AFServer (Get-AFServer -Name PIAF1)
    
    This example will edit the description and default PI server of the AF 
    Server PIAF1
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFServer -NewName NewDefaultServerName -Timeout 00:01:00 -AFServer 
    (Get-AFServer -Default)
    
    This example will rename the default AF Server in the local AF Server 
    list. This should not be confused with renaming the AF Server machine or 
    changing the network path to the AF Server. See the next example to change 
    the network path for an existing AF Server entry in the local AF Servers 
    list.
    
    This example also sets the communication timeout to 1 minute for the 
    default server.
    
    ----------  EXAMPLE 3  ----------
    
    Set-AFServer -Path PIAF1.example.int (Get-AFServer -Name PIAF1)
    
    This example will set the network path for the AF Server PIAF1 to be a 
    Fully Qualified Domain Name (FQDN). Note that the network path can be a 
    hostname, IP address, or Fully Qualified Domain Name (FQDN).


##    Set-AFServerID

SYNOPSIS
    Changes the ID for the PISystem to the specified Guid.
    
    

    ----------  EXAMPLE 1  ----------
    
    $afServer | Set-AFServerID
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    Changes the ID for the PISystem by creating a new Guid.
    
    ----------  EXAMPLE 2  ----------
    
    $afServer | Set-AFServerID -ID $newID
    
    Where:
    
    $afServer = Get-AFServer -Name "AFServerMachineName"
    
    $newID = New-Guid
    
    Changes the ID for the PISystem to the specified $newID.


##    Set-AFUnitOfMeasure

SYNOPSIS
    Set an AF Unit of Measure
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-AFUnitOfMeasure -Description "Decimeter is an SI unit of length 
    representing 0.1 meters" -AFUnitOfMeasure $refUOM -CheckIn -AFServer 
    $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $afUOM = Get-AFUnitOfMeasure -Name "decimeter" -AFServer $afServer
    
    Edits the AF UOM "decimeter" by adding a description. The change is 
    checked in immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Set-AFUnitOfMeasure -NewName "decimetre" -AFUnitOfMeasure $afUOM -CheckIn 
    -AFServer $afServer
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $refUOM = Get-AFUnitOfMeasure -Name "decimeter" -AFServer $afServer
    
    Renames an existing AF UOM "decimeter" to "decimetre". The change is 
    checked in immediately.


##    Set-AFUnitOfMeasureClass

SYNOPSIS
    Set an AF Unit of Measure Class
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-UnitOfMeasureClass -NewName "MyChangedUOMClass" -CheckIn 
    -AFUnitOfMeasureClass $afUOMClassToRename
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $afUOMClassToRename = Get-AFUnitOfMeasureClass -Name "MyUOMClass" 
    -AFServer $afServer
    
    This example renames an existing AF Unit of Measure Class "MyUOMClass" on 
    AF Server "PIAF1" to "MyChangedUOMClass". The change is checked in 
    immediately.
    
    ----------  EXAMPLE 2  ----------
    
    Add-AFUnitOfMeasureClass -Description "My Unit of Measure Class" -CheckIn 
    -AFUnitOfMeasureClass $afUOMClass
    
    Where:
    
    $afServer = Get-AFServer -Name PIAF1
    
    $afUOMClass = Get-AFUnitOfMeasureClass -Name "MyOUMClass" -AFServer 
    $afServer
    
    Set a description to the AF UOM Class "MyUOMClass" on the AF Server 
    "PIAF1". The change is checked in immediately.


##    Set-PIAFLinkTracing

SYNOPSIS
    Enable or disable PI AF Link tracing on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIAFLinktrace -Enable -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Enables PI AF Link tracing on the PISRV1 PI Data Archive. The Timeout and 
    LogFile parameters are not specified, so defaults are used. I.E. The trace 
    will timeout after 5 minutes (unless manually disabled - see next example) 
    and messages will be written to the PI Message Log.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIAFLinktrace -Disable -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will manually disable a PI AF Link Trace currently in 
    progress.
    
    ----------  EXAMPLE 3  ----------
    
    Set-PIAFLinktrace -Enable -Timeout "00:10:00" -LogFile 
    C:\Logs\aflinktrace.txt -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example will enable a PI AF Link Trace on the PISRV1 PI Data Archive 
    that will timeout after 10 minutes, and where the messages will be written 
    to C:\Logs\aflinktrace.txt rather than the PI Message Log.


##    Set-PIArchiveSetSettings

SYNOPSIS
    Sets the archive set configuration from a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIArchiveFileInfo -SetSettings $settings -Connection $con
    
    Where:
    
    $settings = Get-PIArchiveFileInfo
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Set the PI Archive Set settings to the values set
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIArchiveFileInfo -Name "HistoricalSet" -ArchiveSizeMB 1024 
    -ShiftFrequency -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName PISRV1)
    
    Set the PI Archive Set settings for the primary archive file (ID=0) on the 
    "PISRV1" PI Data Archive server. Because -ArchiveSet parameter is not 
    explicitly set, a value of 0 (Historical) will be used by default.


##    Set-PIBufferingControlState

SYNOPSIS
    Set the PI Buffer control state
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIBufferingControlState -ControlCommand StopBuffering 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-2
    
    Sets the buffer state of "StopBuffering" on the "PISRV-2" (which is a 
    member of "PISRV-Collective") on the local PI Buffer Subsystem instance. 
    The user is prompted for confirmation before the server is removed. The 
    default timeout of 1 minute is used.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIBufferingControlState -ControlCommand StartBuffering 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-2
    
    Sets the buffer state of "StartBuffering" on the "PISRV-2" (which is a 
    member of "PISRV-Collective") on the local PI Buffer Subsystem instance. 
    The user is prompted for confirmation before the server is removed. The 
    default timeout of 1 minute is used.
    
    ----------  EXAMPLE 3  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { 
    Set-PIBufferingControlState -ControlCommand StopBuffering 
    -LogicalServerName PISRV-Collective -PhysicalServerName PISRV-2 }
    
    Sets the buffer state of "StopBuffering" on the "PISRV-2" (which is a 
    member of "PISRV-Collective") on the local PI Buffer Subsystem instance. 
    The user is prompted for confirmation before the server is removed. The 
    default timeout of 1 minute is used.
    
    Note the use of Invoke-Command. Failure of this example to execute 
    properly is likely not an issue with Set-PIBufferingControlState, but with 
    the network or PS connection to the remote computer. Note that the 
    OSIsoft.PowerShell module must be installed on the remote computer as well 
    for this to work.


##    Set-PICollective

SYNOPSIS
    Edit name, description, or ID of a PI Data Archive Collective
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PICollective -NewName "Renamed-Collective" -PICollective 
    (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Renames the PI Data Archive Collective which "PISRV1" is a member to 
    "Renamed-Collective".
    
    ----------  EXAMPLE 2  ----------
    
    Set-PICollective -NewName "Renamed-Collective" -Description "New corporate 
    PI Collective" -PICollective (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Renames the PI Data Archive Collective which "PISRV1" is a member to 
    "Renamed-Collective" and edits the description to "New corporate PI 
    Collective".


##    Set-PICollectiveMember

SYNOPSIS
    Edit the configuration of a PI Data Archive Collective Member
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PICollectiveMember -Name PISRV2 -Description "Secondary PI Collective 
    Member" -CommPeriod "00:00:15" -SyncPeriod "00:00:10" 
                     -PICollective (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Sets a new description, communication period, and synchronization period 
    on the PI Data Archive Collective Member "PISRV2".
    
    ----------  EXAMPLE 2  ----------
    
    Set-PICollectiveMember -Name "PISRV2" -PublicCertificate $cert 
    -PICollective (Get-PICollective -Connection $con)
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    $cert = ( Get-ChildItem -Path 'Cert:\LocalMachine\OSIsoft LLC 
    Certificates' )
    
    Applies a new public certificate to the secondary member "PISRV2". This 
    example should only be referenced for PI Data Archive versions 2017 or 
    later.
    
    Note that the self-signed certificate found at the path in the example 
    should have been created upon installation of PI Data Archive 2017 or 
    later. For more information regarding PI Data Archive 2017 certificates 
    and troubleshooting, see KB01564 and KB00800


##    Set-PIDataArchiveConnectionConfiguration

SYNOPSIS
    Set connection configuration information for a PI Data Archive in the 
    local Known Servers Table (KST)
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIDataArchiveConnectionConfiguration -Path "PISRV1.example.int" 
    -OpenTimeout 00:01:00 -OperationTimeout 00:10:00 
    -PIDataArchiveConnectionConfiguration $configuration
    
    Where:
    
    $configuration = Get-PIDataArchiveConnectionConfiguration -Name PISRV1
    
    Edit Standalone Server Settings: This example will set the PI Data Archive 
    connection configuration in the Known Servers Table (KST) for the "PISRV1" 
    entry. The path is set to the FQDN of PISRV1.example.int, with an 
    OpenTimeout of 1 minute and OperationTimeout of 10 minutes.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIDataArchiveConnectionConfiguration -MemberNode PISRV2 -Priority 2 
    -Path "PISRV2.example.int" -OpenTimeout 00:01:00 -OperationTimeout 
    00:10:00 -PIDataArchiveConnectionConfiguration $configuration
    
    Where:
    
    $configuration = Get-PIDataArchiveConnectionConfiguration -Name 
    PIDA-Collective
    
    Edit PI Collective Member Settings: This example will set the PI Data 
    Archive connection configuration in the Known Servers Table (KST) for the 
    "PISRV2" entry, which is a member of the PI Collective "PIDA-Collective". 
    The path is set to the FQDN of PISRV2.example.int, a priority of "2", with 
    an OpenTimeout of 1 minute and OperationTimeout of 10 minutes.
    
    ----------  EXAMPLE 3  ----------
    
    Set-PIDataArchiveConnectionConfiguration -Default 
    -PIDataArchiveConnectionConfiguration $configuration
    
    Where:
    
    $configuration = Get-PIDataArchiveConnectionConfiguration -Name PISRV1
    
    This example will set the PI Data Archive "PISRV1" as the default PI Data 
    Archive in the Known Servers Table (KST).


##    Set-PIDatabaseSecurity

SYNOPSIS
    Set a PI Database Security entry on the PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIDatabaseSecurity -Name PIMapping -Security "piadmin: A(r,w) | 
    piadmins: A(r,w) | PIAdministrators: A(r,w) | PIWorld: A(r)" -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Sets the PI Database Security for the PIPoint table on the "PISRV1" PI 
    Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIDatabaseSecurity -Name PIPoint -Security ((Get-PIPoint -Name 
    sinusoid -Attributes datasecurity -Connection 
    $con).Attributes.datasecurity) -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Gets the ACL security string from the PI Point Sinusoid's datasecurity 
    attribute, and sets the security string for the PIPoint table database 
    security to be the same value. Note: this example does not demonstrate a 
    security best practice and is not recommended, and is intended only to 
    demonstrate cmdlet usability.


##    Set-PIDigitalStateSet

SYNOPSIS
    Set a PI Digital State Set
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIDigitalStateSet -Name "StamperStatus" -States "RUNNING","OFF" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example edits an existing digital state set "StamperStatus" on the 
    "PISRV1" PI Data Archive. This states contained in the PI Digital State 
    Set will be set with the following integral representations:
    
    0="RUNNING" : 1="OFF"


##    Set-PIGroup

SYNOPSIS
    Edits an existing PI Group on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIGroup -Name "PIEngineersGroup" -Description "PI Group for all floor 
    engineers" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example edits the description on an existing PI Group 
    "PIEngineersGroup" on the "PISRV1" PI Data Archive.


##    Set-PIIdentity

SYNOPSIS
    Set a PI Security Identity
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIIdentity -Name PIEngineers -Enabled $false -CanDelete $true 
    -AllowUseInMappings $true -AllowUseInTrusts $true -AllowExplicitLogin 
    $false -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Edits the PI Identity "FloorEngineers" as can be deleted, disables the 
    identity, allowed for use in both mappings and trusts, and disables 
    explicit login on the "PISRV1" PI Data Archive server.
    
    Note that $true and $false should be used to pass boolean values in 
    PowerShell. However, you can also pass 0 for $false and 1 for $true. 
    However, using the PowerShell boolean values helps improve read-ability.


##    Set-PIMapping

SYNOPSIS
    Set a PI Security Mapping
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIMapping -Name 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-42999" -Disabled $true 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Disables the PI Mapping 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-42999" on the "PISRV1" 
    PI Data Archive server.
    
    Note that name of the mapping is typically Windows_[WindowsSID] where 
    [WindowsSID] is the Windows SID of the Windows User or Group the mapping 
    is for.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIMapping -Name 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-42999" -Identity 
    "piadmins" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Sets the identity for the PI Mapping 
    "Windows_S-1-5-21-2084324470-1890137325-1469997231-42999" to be 
    "piadmins", overwriting whatever the previous identity was set as.
    
    Note: The name of the mapping is typically Windows_[WindowsSID] where 
    [WindowsSID] is the Windows SID of the Windows User or Group the mapping 
    is for.
    
    Note: $true and $false should be used to pass boolean values in 
    PowerShell. However, you can also pass 0 for $false and 1 for $true. 
    However, using the PowerShell boolean values helps improve read-ability.


##    Set-PIPoint

SYNOPSIS
    Set the attributes of a PI Point
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIPoint -Name BoilerTemp1 -Attributes 
    @{zero="50";span="100";displaydigits="-7"} -Connection $con
    
    This example will edit the PI Point configuration for a pre-existing tag 
    named "BoilerTemp1" by setting the attributes specified by the -Attributes 
    hashtable.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PIPoint -ID 16 -Attributes @{zero="50";span="100";displaydigits="-7"} 
    -Connection $con
    
    This example will edit the PI Point configuration for a pre-existing tag 
    with ID 16 by setting the attributes specified by the -Attributes 
    hashtable.
    
    ----------  EXAMPLE 3  ----------
    
    $piPoint | Set-PIPoint -Attributes 
    @{zero="50";span="100";displaydigits="-7"}
    
    Where:
    
    $piPoint = Get-PIPoint -Name Sinusoid -Connection $conn
    
    This example will edit the PI Point configuration for a pre-existing tag 
    with ID 16 by setting the attributes specified by the -Attributes 
    hashtable.
    
    ----------  EXAMPLE 4  ----------
    
    Set-PIPoint -Name BoilerTemp1 -Attributes @{ptsecurity="piadmin: A(r,w) | 
    piadmins: A(r,w) | PIEngineers: A(r) | PIWorld: 
    A(r)";datasecurity="piadmin: A(r,w) | piadmins: A(r,w) | PIEngineers: A(r) 
    | PIWorld: A(r)"} -Connection $con
    
    This example will set the point and data security strings for the 
    "BoilerTemp1" PI Point. Note that this operation will not append security 
    strings, but instead overwrite any security settings previously set.


##    Set-PIPointSource

SYNOPSIS
    Set a PI PointSource
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIPointSource -Name "PItoPI_Corp" -Description "PItoPI tags coming 
    from Corporate PI Server"  -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Sets the description for the PointSource "OPC" on the "PISRV1" PI Data 
    Archive server.


##    Set-PITrust

SYNOPSIS
    Set a PI Security Trust
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PITrust -Name "PIINT1_OPC_IP" -Disabled $true -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Edits the PI Trust "PIINT1_OPC_IP" as disabled on the "PISRV1" PI Data 
    Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Set-PITrust -Name "PIINT1_OPC_IP" -Identity "InterfacesAndBuffers" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Edits the PI Trust "PIINT1_OPC_IP" to use the "InterfacesAndBuffers" 
    identity, overwriting the previous setting on "PISRV1" PI Data Archive.


##    Set-PITuningParameter

SYNOPSIS
    Set a PI Data Archive tuning parameter value for a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PITuningParameter -Name Archive_AutoArchiveFileSize -Value 1024 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Sets the Archive_AutoArchiveFileSize tuning parameter to 1024MB (1 GB) on 
    the "PISRV1" PI Data Archive server.


##    Set-PIUser

SYNOPSIS
    Edits an existing PI User on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIUser -Name "John Doe" -Description "Lead Floor Engineer" -PIGroups 
    "EngineerLeadsGroup","PIReadersGroup","PIEngineersGroup" -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example edits an existing PI User "John Doe" on the "PISRV1" PI Data 
    Archive with an updated description and is assigned to three PI Groups.


##    Set-PIUserPassword

SYNOPSIS
    Set the password for an existing PI User on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Set-PIUserPassword -Name "John Doe" -ExistingPassword 
    (ConvertTo-SecureString -string "password" -AsPlainText -Force) 
    -NewPassword (ConvertTo-SecureString -string newP@ssw0rd -AsPlainText 
    -Force) -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example sets a new PI User Password for the existing PI User "John 
    Doe" on the "PISRV1" PI Data Archive.
    
    Use "Get-Help ConvertTo-SecureString -Full" for more information on 
    ConvertTo-SecureString cmdlet.


##    Start-PIAFLinkBatchDatabaseAnalysis

SYNOPSIS
    Starts an analysis of the PI Batch Database for Batch Database to Event 
    Frames Migration
    
    

    ----------  EXAMPLE 1  ----------
    
    Start-PIAFLinkBatchDatabaseAnalysis -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Starts the PI Batch Database analysis by the PI AF Link Subsystem. The 
    results of this analysis is used to address any issues found when 
    preparing to migrate from PI Batch Database to Event Frames. Use 
    Get-PIAFLinkBatchDatabaseAnalysisStatus to review the results of the 
    analysis.


##    Start-PIAFLinkBatchDatabaseMigration

SYNOPSIS
    Starts PI Batch Database to AF Event Frame Migration
    
    

    ----------  EXAMPLE 1  ----------
    
    Start-PIAFLinkBatchDatabaseMigration -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Starts the migration of the entire PI Batch Database to AF Event Frames.
    
    WARNING: Once a PI Batch Database to Event Frames Migration has occurred, 
    the Batch Database is read-only. PI Batch to Event Frames migration is a 
    one-time operation and should only be done after any internal approvals, 
    as well as PI Batch Database Analysis has been performed and any potential 
    issues addressed.
    
    See "Get-Help Start-PIAFLinkBatchDatabaseAnalysis -Full" for more 
    information on running the analysis of the PI Batch database.


##    Start-PIArchiveReprocess

SYNOPSIS
    Starts/queues a PI Archive to be reprocessed
    
    

    ----------  EXAMPLE 1  ----------
    
    Start-PIArchiveReprocess -Name "F:\PIArchives\piarch001.arc" 
    -RegistrationState Register -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Starts/queues the piarch001.arc archive for reprocessing on the "PISRV1" 
    PI Data Archive. After reprocessing, the resulting archive will attempt to 
    be registered.
    
    ----------  EXAMPLE 2  ----------
    
    Start-PIArchiveReprocess -Name 
    "F:\PIArchives\piarch001.arc","F:\PIArchives\piarch002.arc" 
    -RegistrationState DoNotRegister -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Queues two archives for reprocessing: "piarch001.arc" and "piarch002.arc". 
    Following successful reprocessing, do not attempt to register reprocessed 
    archives.
    
    When queueing multiple archives for reprocessing, use 
    "Get-PIArchiveReprocessQueue" to view status of queued reprocess requests. 
    Run "Get-Help Get-PIArchiveReprocessQueue -Full" for more information.
    
    ----------  EXAMPLE 3  ----------
    
    Start-PIArchiveReprocess -Name "E:\Program Files\PI\arc\piarch001.arc" 
    -RegistrationState MaintainRegistration -Connection $con 
    -DeleteInputArchive
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Starts reprocessing "piarch001.arc" on the "PISRV1" PI Data Archive. 
    Following successful reprocessing, maintain the registration status of 
    input archive. If input archive was registered, attempt to register output 
    archive. If input was not registered, do not attempt to register output 
    archive.
    
    Upon successful reprocessing, this example will delete the input archive. 
    This option should be used with caution so as to not mistakenly delete 
    archive files.


##    Start-PIArchiveShift

SYNOPSIS
    Initiate a PI Archive shift
    
    

    ----------  EXAMPLE 1  ----------
    
    Start-PIArchiveShift -Connection (Connect-PIDataArchive 
    -PIDataArchiveMachineName "PISRV1")
    
    Initiates a PI Archive shift on the "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Start-PIArchiveShift -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Initiates a PI Archive Shift on the PI Data Archive "PISRV1", where the 
    connection object to PISRV1 is stored in the variable $con.


##    Start-PIBackup

SYNOPSIS
    Initiate a PI Backup on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Start-PIBackup -BackupLocation E:\PIBackup -NumberOfArchives 3 -Type 
    Incremental -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example initiates an incremental backup of the "PISRV1" PI Data 
    Archive. The backup will be written to E:\PIBackup and will include 3 
    historical archives, in addition to any files that have changed since the 
    last backup. (incremental)
    
    ----------  EXAMPLE 2  ----------
    
    Start-PIBackup -BackupLocation E:\PIBackup -Type Copy -ArchiveIndex 
    0,12,13,14 -ExcludeFuture -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example initiates a copy backup of the "PISRV1" PI Data Archive. The 
    backup will be written to E:\PIBackup and will include 4 historical 
    archives, specifically those with index 0 (primary archive), 12, 13 and 
    14. No future archives will be backed up.


##    Stop-PIArchiveReprocess

SYNOPSIS
    Stops/cancels a PI Archive from being reprocessed
    
    

    ----------  EXAMPLE 1  ----------
    
    Stop-PIArchiveReprocess -Name "F:\PIArchives\piarch001.arc" -Connection 
    (Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1")
    
    Stops/cancels the piarch001.arc archive reprocessing on the "PISRV1" PI 
    Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Stop-PIArchiveReprocess -Name 
    "F:\PIArchives\piarch006.arc","F:\PIArchives\piarch007.arc" -Connection 
    $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Stops/cancels two archives for reprocessing: "piarch006.arc" and 
    "piarch007.arc"


##    Stop-PIBackup

SYNOPSIS
    Stop execution of a PI Backup on a PI Data Archive
    
    

    ----------  EXAMPLE 1  ----------
    
    Stop-PIBackup -Connection (Connect-PIDataArchive -PIDataArchiveMachineName 
    "PISRV1")
    
    This example stops a running PI Backup on the "PISRV1" PI Data Archive.
    
    ----------  EXAMPLE 2  ----------
    
    Stop-PIBackup -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    This example stops a running PI Backup on the "PISRV1" PI Data Archive.


##    Undo-AFCheckOut

SYNOPSIS
    Undo a check out of AF objects
    
    

    ----------  EXAMPLE 1  ----------
    
    Undo-AFCheckOut -AFDatabase $afDB -Force
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    Undo the checkout of the AF Database "AFDatabase1" on the AF Server 
    "PIAF1". The -Force parameter is specified so this will also undo any 
    check out of AF objects under the database object that were checked out by 
    other users.
    
    ----------  EXAMPLE 2  ----------
    
    Undo-AFCheckOut -ItemsToCheckOut $MyAFElement  -PassThrough
    
    Where:
    
    $afDB = Get-AFDatabase -Name "AFDatabase1" -AFServer (Get-AFServer -Name 
    "PIAF1")
    
    $MyRenamedAFElement = Set-AFElement -NewName "IncorrectlyRenamedElement" 
    -AFElement $MyAFElement -PassThrough
    
    In this example, an AF Element stored in $MyAFElement was incorrectly 
    renamed to "IncorrectlyRenamedElement" with the Set-AFElement cmdlet. 
    Because this change was not immediately checked in with the -CheckIn 
    parameter, we can undo the check out as shown above.


##    Unlock-AFEventFrame

SYNOPSIS
    Unlock an AF Event Frame
    
    

    ----------  EXAMPLE 1  ----------
    
    Unlock-AFEventFrameParent -AFEventFrame $MyEventFrame
    
    Where:
    
    $afServer = Get-AFServer -Name "PIAF1"
    
    $MyEventFrame = Get-AFEventFrame -ID 7570ec51-31c6-4611-0000-000000015f31 
    -AFServer $afServer
    
    This example unlocks the AF Event Frame stored in $MyEventFrame, assuming 
    the event frame was already locked.


##    Unregister-PIArchive

SYNOPSIS
    Unregisters a registered PI Archive file with a PI Data Archive server.
    
    

    ----------  EXAMPLE 1  ----------
    
    Unregister-PIArchive -Name E:\PIArchives\piarch008.arc -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Unregisters the archive file found at E:\PIArchives\piarch008.arc from the 
    "PISRV1" PI Data Archive server.
    
    ----------  EXAMPLE 2  ----------
    
    Unregister-PIArchive -Name "D:\Program Files\PI\arc\piarch008.arc" 
    -Connection $con
    
    Where:
    
    $con = Connect-PIDataArchive -PIDataArchiveMachineName "PISRV1"
    
    Unregisters the archive file found at "D:\Program 
    Files\PI\arc\piarch008.arc" from the "PISRV1" PI Data Archive server. Note 
    that the path to the archive contains a space so the entire path must be 
    enclosed in double quotes.


##    Update-PIBufferConfiguration

SYNOPSIS
    Reload the PI Buffer Subsystem configuration
    
    

    ----------  EXAMPLE 1  ----------
    
    Update-PIBufferConfiguration
    
    This example forces the local instance of PI Buffer Subsystem to 
    reload/refresh all buffer configuration data
    
    ----------  EXAMPLE 2  ----------
    
    Invoke-Command -ComputerName PIINT1 -ScriptBlock { 
    Update-PIBufferConfiguration }
    
    This example forces the PIINT1 instance of PI Buffer Subsystem to 
    reload/refresh all buffer configuration data. Note the use of 
    Invoke-Command. Failure of this example to execute properly is likely not 
    an issue with Update-PIBufferConfiguration, but with the network or PS 
    connection to the remote computer. Note that the OSIsoft.PowerShell module 
    must be installed on the remote computer as well for this to work.
