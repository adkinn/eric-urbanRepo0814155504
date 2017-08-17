---
title: "KeywordLocation Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b62c334b-75a1-436d-965f-746e48a44df8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordLocation Data Object
Defines an object that contains the location, network, device, and the percentage of time that a user entered a search query.

## Syntax

```xml
<xs:complexType name="KeywordLocation">
  <xs:sequence>
    <xs:element minOccurs="0" name="Device" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="Location" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Percentage" type="xs:double" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Device*|The device of the user who entered the search query.|*string*|
|*Location*|The country, state, metropolitan area, or city where users entered the search query.|*string*|
|*Percentage*|The percentage of time that users searched for the keyword from the location. The value is specified in the range 0.0 through 100.0.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md)  
[GetKeywordLocations](../adinsight-api/getkeywordlocations-service-operation.md)  

