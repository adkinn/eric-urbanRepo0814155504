---
title: "AppealStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c30bf88f-f5bc-4388-8f7e-b1672093ec32
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppealStatus Value Set
Defines the values that you use to determine whether an editorial rejection is appealable.

## Syntax

```xml
\<xs:simpleType name="AppealStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Appealable">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AppealPending">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="NotAppealable">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Appealable|The editorial rejection is appealable.|
|AppealPending|The editorial rejection is appealable and an appeal has been submitted.|
|NotAppealable|The editorial rejection is not appealable.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md)

