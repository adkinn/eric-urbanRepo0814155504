---
title: "AdRotation Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3235ecdb-a5ea-4eec-899b-a020f291199d
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdRotation Data Object
Defines an object that specifies the type of ad rotation to apply to the ad group.

## Syntax

```xml
\<xs:complexType name="AdRotation">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="EndDate" nillable="true" type="xs:dateTime" />
    \<xs:element minOccurs="0" name="StartDate" nillable="true" type="xs:dateTime" />
    \<xs:element minOccurs="0" name="Type" nillable="true" type="tns:AdRotationType" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EndDate*|Reserved for future use only. Must be null.|*dateTime*|
|*StartDate*|Reserved for future use only. Must be null.|*dateTime*|
|*Type*|The type of ad rotation to apply to the ad group.<br /><br />Possible values are *OptimizeForClicks* and *RotateAdsEvenly*.<br/><br/>**Add:** Optional. If not specified, the default value is *OptimizeForClicks*.<br/>**Update:** Optional|[AdRotationType](../campaign-api/adrotationtype-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)

