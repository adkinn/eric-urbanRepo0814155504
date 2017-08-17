---
title: "BatchError Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76474f9b-3725-4018-b75d-276098599c1a
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BatchError Data Object
Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and describes the reason for the failure.

## Syntax

```xml
\<xs:complexType name="BatchError">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Code" type="xs:int" />
    \<xs:element minOccurs="0" name="Details" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="FieldPath" nillable="true" type="xs:string"/>
    \<xs:element xmlns:q9="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q9:ArrayOfKeyValuePairOfstringstring"/>
    \<xs:element minOccurs="0" name="Index" type="xs:int" />
    \<xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

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
[ApiFaultDetail](../campaign-api/apifaultdetail-data-object.md)  
[EditorialApiFaultDetail](../campaign-api/editorialapifaultdetail-data-object.md)  

