---
title: "DayMonthAndYear Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f960cd7a-65e3-4683-abb4-d3fe01329c16
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DayMonthAndYear Data Object
Defines an object that you use to specify the start and end dates of a date range.

## Syntax

```xml
\<xs:complexType name="DayMonthAndYear">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Day" type="xs:int" />
    \<xs:element minOccurs="0" name="Month" type="xs:int" />
    \<xs:element minOccurs="0" name="Year" type="xs:int" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Day*|The day of the month.|*int*|
|*Month*|The month specified as an integer value in the range of 1 through 12, where 1 is January and 12 is December.|*int*|
|*Year*|The year specified as a four-digit integer value.|*int*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[DateRangeSearchParameter](../Ad Insight Version 11/daterangesearchparameter-data-object.md)  
[GetHistoricalSearchCount](../Ad Insight Version 11/gethistoricalsearchcount-service-operation.md)  
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
[HistoricalSearchCountPeriodic](../Ad Insight Version 11/historicalsearchcountperiodic-data-object.md)  
[KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md)  

