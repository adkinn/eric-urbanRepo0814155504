---
title: "AdExtensionEditorialReason Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9531aabb-92ed-459e-b171-0f98f474fc0d
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionEditorialReason Data Object
Defines an object that you can use to determine the component of an ad extension that failed editorial review, and the reason for the failure.

## Syntax

```xml
<xs:complexType name="AdExtensionEditorialReason">
  <xs:sequence>
    <xs:element minOccurs="0" name="Location" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="PublisherCountries" nillable="true" type="q5:ArrayOfstring" xmlns:q5="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <xs:element minOccurs="0" name="ReasonCode" type="xs:int" />
    <xs:element minOccurs="0" name="Term" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Location*|The component of the ad extension that failed editorial review.|*string*|
|*PublisherCountries*|The list of publisher countries whose editorial guidelines do not allow the specified term.|*string* array|
|*ReasonCode*|A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](http://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx).|*int*|
|*Term*|The term that failed editorial review.<br /><br />This element will not be set if a combination of terms caused the failure or if the failure was based on a policy violation.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionEditorialReasonCollection](../campaign-api/adextensioneditorialreasoncollection-data-object.md)  

