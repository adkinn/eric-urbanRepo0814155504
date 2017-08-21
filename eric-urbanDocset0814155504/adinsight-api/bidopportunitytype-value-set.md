---
title: "BidOpportunityType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8c8bfc4-9937-4a7a-9446-0aa0e6fab643
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BidOpportunityType Value Set
Defines the possible bid opportunity types you can request when calling [GetBidOpportunities](../adinsight-api/getbidopportunities-service-operation.md).

## Syntax

```xml
<xs:simpleType name="BidOpportunityType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="FirstPage">
        <xs:enumeration value="MainLine">
        <xs:enumeration value="MainLine1">
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|FirstPage|The bid opportunity may lead to ads shown in one of the first page positions of search results.|
|MainLine|The bid opportunity may lead to ads shown in one of the mainline positions of search results.|
|MainLine1|The bid opportunity may lead to ads shown in the first mainline position of search results.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBidOpportunities](../adinsight-api/getbidopportunities-service-operation.md)  

