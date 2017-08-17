---
title: "SearchCountsByAttributes Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b1a22b-c130-4187-a2dc-5fddd6c990e2
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchCountsByAttributes Data Object
Defines an object that contains a list of keyword historical search counts for the corresponding device attribute. Each search count in the list is aggregated by day, month, and year.

## Syntax

```xml
\<xs:complexType name="SearchCountsByAttributes">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Device" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="HistoricalSearchCounts" nillable="true" type="tns:ArrayOfHistoricalSearchCountPeriodic"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Device*|The device of the user who entered the search query.|*string*|
|*HistoricalSearchCounts*|An array of [HistoricalSearchCountPeriodic](../Ad Insight Version 11/historicalsearchcountperiodic-data-object.md) objects that contain a count of the number of times that the keyword was used in a search query. The array contains an item for each month in the specified date range. The items are ordered by calendar month.<br /><br />For each requested keyword that has no available data, the [HistoricalSearchCountPeriodic](../Ad Insight Version 11/historicalsearchcountperiodic-data-object.md) element will be nil.|[HistoricalSearchCountPeriodic](../Ad Insight Version 11/historicalsearchcountperiodic-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md)  
[GetHistoricalSearchCount](../Ad Insight Version 11/gethistoricalsearchcount-service-operation.md)  

