---
title: "SiteLinksAdExtension Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a40c1161-5376-4546-bc2a-617d8470fb23
caps.latest.revision: 17
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SiteLinksAdExtension Data Object
Defines an object with *multiple* sitelinks per ad extension. You can use the sitelinks to promote certain products, services, or sections of your website and take potential customers to exactly the information they were searching for. This can increase both click-through-rate and conversions.

> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../campaign-api/includes/sitelinks-migration-eta.md)] 

## Syntax

```xml
<xs:complexType name="SiteLinksAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="SiteLinks" nillable="true" type="tns:ArrayOfSiteLink" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *SiteLinksAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SiteLinks*|A list of site links. Each object contains a link to a webpage on your website. You can specify a maximum of 10 site links, and the search engine determines a subset of links to include in the ad. If you specify the *Description1* and *Description2* elements of each site link, then up to four site links will be displayed.<br/><br/>**Add:** Required<br/>**Update:** Required|[SiteLink](../campaign-api/sitelink-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *SiteLinksAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to sitelinks ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|Not supported.<br/><br/>For *SiteLinksAdExtension* objects, you specify the *DevicePreference* for each [SiteLink](../campaign-api/sitelink-data-object.md), otherwise the operation will fail if you attempt to set the ad extension level *DevicePreference* element.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|This element is not supported at the parent site link ad extension level. <br/><br/>**Note:** Whereas this element is not applicable for the *SiteLinksAdExtension* object, you can specify a *Scheduling* element within each individual [SiteLink](../campaign-api/sitelink-data-object.md) object (nested list within the *SiteLinksAdExtension*). For most other ad extension types including [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md), the [AdExtension](../campaign-api/adextension-data-object.md) object will include the *Scheduling* element.<br/><br/>**Add:** Not applicable.<br/>**Update:** Not applicable.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *SiteLinksAdExtension* when you retrieve a sitelinks ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|

[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also

[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  
[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)  
