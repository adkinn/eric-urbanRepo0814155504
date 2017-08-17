---
title: "KeywordSearchCount Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b2aef24-b5bf-43a1-a40b-832d2b599975
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordSearchCount Data Object
Defines an object that contains a list of search counts for each device and network where the keyword was included in a search query. The data is aggregated based on the attributes specified in the request.

## Syntax

```xml
\<xs:complexType name="KeywordSearchCount">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="SearchCountsByAttributes" nillable="true" type="tns:ArrayOfSearchCountsByAttributes"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword to which the search count data applies.|*string*|
|*SearchCountsByAttributes*|An array of [SearchCountsByAttributes](../Ad Insight Version 11/searchcountsbyattributes-data-object.md) objects that contain search counts for each device and network where the keyword was included in a search query.<br /><br />For each requested keyword that has no available data, the [SearchCountsByAttributes](../Ad Insight Version 11/searchcountsbyattributes-data-object.md) element will be nil.|[SearchCountsByAttributes](../Ad Insight Version 11/searchcountsbyattributes-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetHistoricalSearchCount](../Ad Insight Version 11/gethistoricalsearchcount-service-operation.md)

