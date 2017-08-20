---
title: "KeywordBidLandscape Data Object"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14cedde4-e67d-4ad5-8829-87aa75e8ca23
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordBidLandscape Data Object
Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the keyword identifier given the suggested bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="KeywordBidLandscape">
  \<xs:sequence>
    \<xs:element type="xs:long" name="KeywordId" minOccurs="0"/>
    \<xs:element type="tns:DayMonthAndYear" name="StartDate" nillable="true" minOccurs="0"/>
    \<xs:element type="tns:DayMonthAndYear" name="EndDate" nillable="true" minOccurs="0"/>
    \<xs:element type="tns:ArrayOfBidLandscapePoint" name="BidLandscapePoints"  nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BidLandscapePoints*|The list of the total estimated clicks, cost, and impressions from *StartDate* to *EndDate* given the suggested bid.|[BidLandscapePoint](../adinsight-api/bidlandscapepoint-data-object.md) array|
|*EndDate*|The most recent date used to calculate the bid landscape. The end date should be approximately 2 days prior to today's date when the service is called.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|
|*KeywordId*|The keyword identifier.|*long*|
|*StartDate*|The first date used to calculate the bid landscape. The start date is usually seven days prior to the end date.<br /><br />The difference between the start and end dates could be less than seven if performance data is not available, for example with a new keyword.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBidLandscapeByKeywordIds](../adinsight-api/getbidlandscapebykeywordids-service-operation.md)

