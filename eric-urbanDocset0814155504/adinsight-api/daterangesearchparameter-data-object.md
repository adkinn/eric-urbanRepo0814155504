---
title: "DateRangeSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea505912-ec46-49a0-a708-4b3b4b4041c1
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
---
# DateRangeSearchParameter Data Object
The date range search parameter that you can include when requesting keyword ideas.

For more information about the significance of the date range search parameter, see *MonthlySearchCounts* with the [KeywordIdea](../adinsight-api/keywordidea-data-object.md) object.

## Syntax

```xml
<xs:complexType name="DateRangeSearchParameter">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:SearchParameter">
      <xs:sequence>
        <xs:element xmlns:q9="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" minOccurs="0" name="EndDate" nillable="true" type="q9:DayMonthAndYear"/>
        <xs:element xmlns:q10="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" minOccurs="0" name="StartDate" nillable="true" type="q10:DayMonthAndYear"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EndDate*|The end date range of monthly search counts for the returned keyword ideas.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|
|*StartDate*|The start date range of monthly search counts for the returned keyword ideas.|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
