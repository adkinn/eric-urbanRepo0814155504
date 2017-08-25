---
title: "EditorialError Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81a14495-f215-463c-a062-9e78b6f7e818
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EditorialError Data Object
Defines an error object that identifies the entity with the batch of entities that failed editorial review.

## Syntax

```xml
<xs:complexType name="EditorialError">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BatchError">
      <xs:sequence>
        <xs:element minOccurs="0" name="Appealable" nillable="true" type="xs:boolean" />
        <xs:element minOccurs="0" name="DisapprovedText" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="Location" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="PublisherCountry" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="ReasonCode" nillable="true" type="xs:int" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *EditorialError* object derives from the [BatchError](../campaign-api/batcherror-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Appealable*|Reserved for future use.|*boolean*|
|*DisapprovedText*|The text that caused the entity to be disapproved.<br /><br />For text length violations, this element specifies the number of characters by which the specified text exceeds the maximum.|*string*|
|*Location*|The element or property of the entity that caused the entity to be disapproved.|*string*|
|*PublisherCountry*|The corresponding country or region for the flagged editorial issue.|*string*|
|*ReasonCode*|A numeric code that identifies the error. For more information, see [Editorial Failure Reason Codes](http://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx).|*int*|

## <a name="InheritedElements"></a>Inherited Elements
The *EditorialError* object derives from the [BatchError](../campaign-api/batcherror-data-object.md) object, and inherits the following elements. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Code*|A numeric error code that identifies the error.|*int*|
|*Details*|A message that provides additional details about the batch error. This string can be empty.|*string*|
|*ErrorCode*|A symbolic string constant that identifies the error. For example, UserIsNotAuthorized.|*string*|
|*FieldPath*|The name of the data object's element where the error occurred. For example if the *TrackingUrlTemplate* of a [Campaign](../campaign-api/campaign-data-object.md) contains invalid text, the value of this *FieldPath* element is TrackingUrlTemplate.<br /><br />**Note:** This value is subject to change, so you should not take a dependency on the current string format.<br /><br />**Note:** This element is not supported for all errors. The field path is supported for errors related to *FinalMobileUrls*, *FinalUrls*, *TrackingUrlTemplate*, and *UrlCustomParameters* elements of the respective [Campaign](../campaign-api/campaign-data-object.md), [AdGroup](../campaign-api/adgroup-data-object.md), [TextAd](../campaign-api/textad-data-object.md), [ProductAd](../campaign-api/productad-data-object.md), [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md), [Keyword](../campaign-api/keyword-data-object.md), and [SiteLink](../campaign-api/sitelink-data-object.md) objects. It is also supported for errors related to all fields of the [CalloutAdExtension](../campaign-api/calloutadextension-data-object.md) and [ReviewAdExtension](../campaign-api/reviewadextension-data-object.md) objects.|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this data object.|*KeyValuePairOfstringstring* array|
|*Index*|The zero-based index of the item in the batch of items in the request message that failed.|*int*|
|*Message*|A message that describes the error.|*string*|
|*Type*|Reserved for internal use.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[EditorialApiFaultDetail](../campaign-api/editorialapifaultdetail-data-object.md)  
[Editorial Failure Reason Codes](http://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx)  

