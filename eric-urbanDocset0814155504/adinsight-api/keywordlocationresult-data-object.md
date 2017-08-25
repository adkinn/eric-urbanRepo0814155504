---
title: "KeywordLocationResult Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b5bd2d7-20e3-43fb-9432-f51197ebe4d0
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordLocationResult Data Object
Defines an object that contains the locations where users were located when they searched for the specified keyword.

## Syntax

```xml
<xs:complexType name="KeywordLocationResult">
  <xs:sequence>
    <xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="KeywordLocations" nillable="true" type="tns:ArrayOfKeywordLocation" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword.|*string*|
|*KeywordLocations*|An array of [KeywordLocation](../adinsight-api/keywordlocation-data-object.md) objects that contains the users? geographical locations and the percentage of times that users searched for the keyword from that location.|[KeywordLocation](../adinsight-api/keywordlocation-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordLocations](../adinsight-api/getkeywordlocations-service-operation.md)

