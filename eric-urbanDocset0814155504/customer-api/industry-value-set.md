---
title: "Industry Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1a63e27-6ab0-4517-a012-57cca1b0aa69
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Industry Value Set
Defines the possible industry segments in which a customer operates.

## Syntax

```xml
<xs:simpleType name="Industry">
  <xs:restriction base="xs:string">
    <xs:enumeration value="NA" />
    <xs:enumeration value="AgencySalesHouse" />
    <xs:enumeration value="Automotive" />
    <xs:enumeration value="ConsumerPackagedGoods" />
    <xs:enumeration value="Education" />
    <xs:enumeration value="Entertainment" />
    <xs:enumeration value="FinancialServices" />
    <xs:enumeration value="FoodServices" />
    <xs:enumeration value="Gaming" />
    <xs:enumeration value="GovernmentNonprofitPolitical" />
    <xs:enumeration value="Healthcare" />
    <xs:enumeration value="Internal" />
    <xs:enumeration value="PublishingAndWebMedia" />
    <xs:enumeration value="RealEstate" />
    <xs:enumeration value="Retail" />
    <xs:enumeration value="Services" />
    <xs:enumeration value="Technology" />
    <xs:enumeration value="Telecommunications" />
    <xs:enumeration value="TravelHospitality" />
    <xs:enumeration value="Other" />
    <xs:enumeration value="Pharmaceuticals" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AgencySalesHouse|The advertising agency sales house industry.|
|Automotive|The automotive industry.|
|ConsumerPackagedGoods|The consumer packaged goods industry.|
|Education|The education industry.|
|Entertainment|The entertainment industry.|
|FinancialServices|The financial services industry.|
|FoodServices|The food services industry.|
|Gaming|The gaming industry.|
|GovernmentNonprofitPolitical|The government, non-profit, or political industry.|
|Healthcare|The healthcare industry.|
|Internal|This value is reserved for internal use.|
|NA|Not applicable.|
|Other|An industry that is not listed.|
|Pharamaceuticals|The pharmaceutical industry.|
|PublishingAndWebMedia|The publishing and web media industry.|
|RealEstate|The real estate industry.|
|Retail|The retail industry.|
|Services|The services industry.|
|Technology|The technology industry.|
|Telecommunications|The telecommunications industry.|
|TravelHospitality|The travel and hospitality industry.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
