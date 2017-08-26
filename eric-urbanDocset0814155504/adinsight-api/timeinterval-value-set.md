---
title: "TimeInterval Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b02381b5-98a6-48dc-8b62-54f8562136bf
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TimeInterval Value Set
Defines the possible time periods that determine the pool of data that the service uses to get the performance statistics of a keyword.

## Syntax

```xml
<xs:simpleType name="TimeInterval">
  <xs:restriction base="xs:string">
    <xs:enumeration value="LastMonth" />
    <xs:enumeration value="LastWeek" />
    <xs:enumeration value="LastDay" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|LastMonth|Use data from the previous calendar month. Note that it can take up to 72 hours for the previous calendar month's data to be available. For example, if you request data on August 1st, 2nd or 3rd, and July's data is not ready, the response will be based on June's data.|
|LastWeek|Use data from last week, Sunday through Saturday. The data is refreshed every Sunday. Note that it can take up to 72 hours for the previous week's data to be available. For example, if you request data on the 4th Monday of the month, and data for the 3rd Sunday through 3rd Saturday is not ready, the response will be based on data for the 2nd Sunday through 2nd Saturday.|
|LastDay|Use data from yesterday. If data from yesterday is not yet available, data from the most recently completed day is provided. Note that it can take up to 72 hours for the most recent day's data to be available.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)

