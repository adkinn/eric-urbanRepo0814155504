---
title: "HistoricalSearchCountPeriodic Data Object"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a103a121-cdc2-491a-a50d-753b275c43a0
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# HistoricalSearchCountPeriodic Data Object
Defines an object that contains the number of times that the keyword was used in a search query during the specified time period.

## Syntax

```xml
\<xs:complexType name="HistoricalSearchCountPeriodic">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="SearchCount" type="xs:long" />
    \<xs:element minOccurs="0" name="DayMonthAndYear" nillable="true" type="tns:DayMonthAndYear" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DayMonthAndYear*|The time period in which the count was captured. The type of aggregation (daily, weekly, or monthly) that you specify in the request determines the length of the time period. For example, if you specified weekly aggregation, the time period is a week and the date is the Sunday of the week when the count was captured.|[DayMonthAndYear](../Ad Insight Version 11/daymonthandyear-data-object.md)|
|*SearchCount*|The number of times that the keyword was used in a search query on the specified device type during the time period. The count aggregates data from all specified countries.|*long*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md)  
[GetHistoricalSearchCount](../Ad Insight Version 11/gethistoricalsearchcount-service-operation.md)  

