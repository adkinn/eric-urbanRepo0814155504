---
title: "PriceAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7927427-2f90-4793-a1a9-15508253b3f1
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
---
# PriceAdExtension Data Object
Defines an ad extension that includes between 3 and 8 price table rows.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
<xs:complexType name="PriceAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="Language" type="xs:string" minOccurs="0"/>
        <xs:element name="PriceAdExtensionType" type="tns:PriceAdExtensionType" nillable="true" minOccurs="0"/> 
        <xs:element name="TableRows" type="tns:PriceTableRow" nillable="true" minOccurs="0"/> 
        <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
        <xs:element xmlns:q5="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q5:CustomParameters"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *PriceAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Language*|The language for the ad copy of your price ad extension.<br/><br/>For possible values, see [Ad Languages](~/concepts/ad-languages.md).<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*PriceAdExtensionType*|The type of the price ad extension.<br/><br/>Possible values include: *Brands*, *Events*, *Locations*, *Neighborhoods*, *ProductCategories*, *ProductTiers*, *ServiceCategories*, *Services*, *ServiceTiers*, and *Unknown*.<br /><br />**Add:** Required<br />**Update:** Read-only|[PriceAdExtensionType](../campaign-api/priceadextensiontype-value-set.md)|
|*TableRows*|The price table rows.<br/><br/>You must have between 3 and 8 price table rows.<br/><br/>**Add:** Required<br/>**Update:** Optional|[PriceTableRow](../campaign-api/pricetablerow-data-object.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all landing page URLs.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br /><br />**Add:** Optional<br />**Update:** Optional|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br /><br />**Add:** Optional<br />**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *PriceAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to price ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *PriceAdExtension* when you retrieve a price ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AdExtension](../campaign-api/adextension-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  
