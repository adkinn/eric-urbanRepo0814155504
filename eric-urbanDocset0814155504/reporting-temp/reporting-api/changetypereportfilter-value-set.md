---
title: "ChangeTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f975b9c-f939-45bc-9494-234ad3d56f34
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ChangeTypeReportFilter Value Set
Defines the types of changes to entities by which you can filter the report data. These values are also used as column values in the `HowChanged` column of the campaign change history report. For more information, see [SearchCampaignChangeHistoryReportColumn](../reporting-api/searchcampaignchangehistoryreportcolumn-value-set.md).

## Syntax

```xml
\<xs:simpleType name="ChangeTypeReportFilter">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Added" />
        \<xs:enumeration value="Deleted" />
        \<xs:enumeration value="Changed">
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Added|The report will include data for entities that have been added.|
|Changed|The report will include data for elements of entities whose values have been updated.|
|Deleted|The report will include data for entities that have been deleted.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchCampaignChangeHistoryReportFilter](../reporting-api/searchcampaignchangehistoryreportfilter-data-object.md)
[SearchCampaignChangeHistoryReportColumn](../reporting-api/searchcampaignchangehistoryreportcolumn-value-set.md)

