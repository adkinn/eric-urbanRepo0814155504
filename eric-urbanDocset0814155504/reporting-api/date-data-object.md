---
title: "Date Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7add054c-b26b-49ca-bde9-9bf8f98a4048
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Date Data Object
Defines a calendar date by month, day, and year.

## Syntax

```xml
\<xs:complexType name="Date">
  \<xs:sequence>
    \<xs:element type="xs:int" name="Day"/>
    \<xs:element type="xs:int" name="Month"/>
    \<xs:element type="xs:int" name="Year"/>
  \</xs:sequence>
\</xs:complexType>
```

## Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|Day|Specifies the day of the month.|*int*|
|Month|Specifies the month.|*int*|
|Year|Specifies the year.|*int*|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]