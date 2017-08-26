---
title: "AdExtension Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aea45c83-be5a-49d6-9a6e-e3b23b2a0051
caps.latest.revision: 22
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtension Data Object
Defines the base object of an ad extension.

Do not try to instantiate an *AdExtension*. You can create one or more following objects that derive from it.
-   [AppAdExtension](../campaign-api/appadextension-data-object.md)
-   [CallAdExtension](../campaign-api/calladextension-data-object.md)
-   [CalloutAdExtension](../campaign-api/calloutadextension-data-object.md)
-   [ImageAdExtension](../campaign-api/imageadextension-data-object.md)
-   [LocationAdExtension](../campaign-api/locationadextension-data-object.md)
-   [PriceAdExtension](../campaign-api/priceadextension-data-object.md)
-   [ReviewAdExtension](../campaign-api/reviewadextension-data-object.md)
-   [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md)
-   [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md)
-   [StructuredSnippetAdExtension](../campaign-api/structuredsnippetadextension-data-object.md)

## Syntax

```xml
<xs:complexType name="AdExtension">
  <xs:sequence>
    <xs:element name="DevicePreference" type="xs:long" nillable="true" minOccurs="0"/>
    <xs:element name="ForwardCompatibilityMap" type="q53:ArrayOfKeyValuePairOfstringstring" nillable="true" minOccurs="0" xmlns:q53="http://schemas.datacontract.org/2004/07/System.Collections.Generic"/>
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    <xs:element name="Scheduling" type="tns:Schedule" nillable="true" minOccurs="0"/>
    <xs:element name="Status" type="tns:AdExtensionStatus" nillable="true" minOccurs="0"/>
    <xs:element name="Type" type="xs:string" nillable="true"/>
    <xs:element name="Version" type="xs:int" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|This element determines whether the preference is for the ad extension to be displayed on mobile devices or all devices.<br /><br />To specify a preference for mobile devices, set this element to *30001*.<br /><br />To specify all devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil.<br/><br/>**Note:** This element is only applicable for the [AppAdExtension](../campaign-api/appadextension-data-object.md) and [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md) types. For [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md) objects, you specify the *DevicePreference* for each [SiteLink](../campaign-api/sitelink-data-object.md), otherwise the operation will fail if you attempt to set the ad extension level *DevicePreference* element.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Note:** This element is not applicable for the [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md) type; You can specify a *Scheduling* element for each [SiteLink](../campaign-api/sitelink-data-object.md) object (nested list within the [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md)) instead. For all other ad extension types including [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md), the [AdExtension](../campaign-api/adextension-data-object.md) object will include the *Scheduling* element.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of ad extension. <br/><br/>For more information, see [Remarks](#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it's revised.|*int*|

## <a name="remarks"></a>Remarks
If you generate the SOAP manually, use the *type* attribute of the `<AdExtension>` node as shown in the following example to specify the type of ad extension.

```
xml
<AdExtension i:type="ReviewAdExtension" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <Id i:nil="true" />
    <Status i:nil=?true? />
      . . .
</AdExtension>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

