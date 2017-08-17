---
title: "Date Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad6cda77-721a-499c-821e-0fcfdbe02e34
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Date Data Object
Represents a date.

## Syntax

```xml
\<xs:complexType name="Date">
  \<xs:sequence>
    \<xs:element name="Day" type="xs:int" />
    \<xs:element name="Month" type="xs:int" />
    \<xs:element name="Year" type="xs:int" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Day*|Specifies the day of the month.<br/><br/>**Add:** Required<br/>**Update:** Required|*int*|
|*Month*|Specifies the month.<br/><br/>**Add:** Required<br/>**Update:** Required|*int*|
|*Year*|Specifies the year.<br/><br/>**Add:** Required<br/>**Update:** Required|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)

