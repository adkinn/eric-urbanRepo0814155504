---
title: "ChangeEntityReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cbb9852-4d3c-4894-b935-c686066fa4a5
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ChangeEntityReportFilter Value Set
Defines the types of entities by which you can filter the report data.

## Syntax

```xml
<xs:simpleType name="ChangeEntityReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Account" />
        <xs:enumeration value="Campaign" />
        <xs:enumeration value="AdGroup">
        <xs:enumeration value="Ad">
        <xs:enumeration value="Keyword">
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Account|The report will include data for accounts that have been added or deleted, or that have had account elements updated.<br /><br />**Note**: The report will include all entity types not represented by other filter values, for example ad extensions.|
|Ad|The report will include data for ads that have been added or deleted, or that have had ad elements updated.|
|AdGroup|The report will include data for ad groups that have been added or deleted, or that have had ad group elements updated.|
|Campaign|The report will include data for campaigns that have been added or deleted, or that have had campaign elements updated.|
|Keyword|The report will include data for keywords that have been added or deleted, or that have had keyword elements updated.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchCampaignChangeHistoryReportFilter](../reporting-api/searchcampaignchangehistoryreportfilter-data-object.md)

