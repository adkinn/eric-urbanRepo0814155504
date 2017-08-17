---
title: "SortOrder Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0c44b96-4168-4785-9834-b3783f47b6bb
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SortOrder Value Set
Defines the ascending or descending sort order of values within the specified report column.

## Syntax

```xml
\<xs:simpleType name="SortOrder">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Ascending" />
    \<xs:enumeration value="Descending" />
  \</xs:restriction>
\</xs:simpleType>
```

## Members

|Member|Description|
|----------|---------------|
|Ascending|The results will be sorted ascending.|
|Descending|The results will be sorted descending.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportSort](../reporting-api/keywordperformancereportsort-data-object.md)

