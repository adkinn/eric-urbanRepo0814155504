---
title: "AdGroupBidLandscape Data Object"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 201cca69-caa9-4c20-b56f-030bfa377fad
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupBidLandscape Data Object
Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the ad group identifier given the suggested bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
<xs:complexType name="AdGroupBidLandscape">
  <xs:sequence>
    <xs:element name="AdGroupId" type="xs:long" minOccurs="0"/>
    <xs:element name="AdGroupBidLandscapeType" type="tns:AdGroupBidLandscapeType" minOccurs="0"/>
    <xs:element name="StartDate" type="tns:DayMonthAndYear" nillable="true" minOccurs="0"/>
    <xs:element name="EndDate" type="tns:DayMonthAndYear" nillable="true" minOccurs="0"/>
    <xs:element name="BidLandscapePoints" type="tns:ArrayOfBidLandscapePoint" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupBidLandscapeType*|Indicates whether all or a subset of an ad group's existing keywords were used to determine the bid landscape.|[AdGroupBidLandscapeType](../adinsight-api/adgroupbidlandscapetype-value-set.md)|
|*AdGroupId*|The ad group identifier.|*long*|
|*BidLandscapePoints*|The list of the total estimated clicks, cost, and impressions from *StartDate* to *EndDate* given the suggested bid.|[BidLandscapePoint](../adinsight-api/bidlandscapepoint-data-object.md) array|
|*EndDate*|The most recent date used to calculate the bid landscape. The end date should be approximately 2 days prior to today's date when the service is called.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|
|*StartDate*|The first date used to calculate the bid landscape. The start date is usually seven days prior to the end date.<br /><br />The difference between the start and end dates could be less than seven if performance data is not available, for example with a new ad group.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBidLandscapeByAdGroupIds](../adinsight-api/getbidlandscapebyadgroupids-service-operation.md)  

