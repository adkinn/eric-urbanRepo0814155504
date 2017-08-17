---
title: "KeywordPerformanceReportSort Data Object"
ms.custom: ""
ms.date: "05/31/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1570e2ca-4a81-4b65-b4cb-46d3747b632f
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordPerformanceReportSort Data Object
Defines a keyword performance report column and corresponding sort order.

## Syntax

```xml
<xs:complexType name="KeywordPerformanceReportSort">
  <xs:sequence>
    <xs:element name="SortColumn" type="tns:KeywordPerformanceReportColumn"/>
    <xs:element name="SortOrder" type="tns:SortOrder"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*SortColumn*|The keyword performance report column by which to sort.|[KeywordPerformanceReportColumn](../reporting-api/keywordperformancereportcolumn-value-set.md)|Required|
|*SortOrder*|Defines the ascending or descending sort order of values within the specified report column.|[SortOrder](../reporting-api/sortorder-value-set.md)|Required|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md)

