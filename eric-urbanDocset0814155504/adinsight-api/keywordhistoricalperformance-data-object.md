---
title: "KeywordHistoricalPerformance Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23696dd5-bf2e-4e21-b39c-3f2179e05bb3
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordHistoricalPerformance Data Object
Defines an object that contains the key performance index data for the specified keyword.

## Syntax

```xml
<xs:complexType name="KeywordHistoricalPerformance">
  <xs:sequence>
    <xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="KeywordKPIs" nillable="true" type="tns:ArrayOfKeywordKPI" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword to which the keyword performance data applies.|*string*|
|*KeywordKPIs*|An array of [KeywordKPI](../adinsight-api/keywordkpi-data-object.md) objects that contains the performance data.<br /><br />For each requested keyword that has no available data, the [KeywordKPI](../adinsight-api/keywordkpi-data-object.md) element will be nil.<br /><br />If the request specified a specific target position, the array will contain only one item per requested keyword. If the request specified All for the target position, then for each requested keyword the array will contain an item for each possible position in the search results.|[KeywordKPI](../adinsight-api/keywordkpi-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)

