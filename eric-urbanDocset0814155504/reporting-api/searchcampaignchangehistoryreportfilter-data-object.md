---
title: "SearchCampaignChangeHistoryReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 964c0c0c-47f9-43e9-a4bd-4621a85b3866
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchCampaignChangeHistoryReportFilter Data Object
Defines the criteria to use to filter the campaign change history report data.

## Syntax

```xml
\<xs:complexType name="SearchCampaignChangeHistoryReportFilter">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdDistribution" nillable="true" type="tns:AdDistributionReportFilter" />
    \<xs:element minOccurs="0" name="HowChanged" nillable="true" type="tns:ChangeTypeReportFilter" />
    \<xs:element minOccurs="0" name="ItemChanged" nillable="true" type="tns:ChangeEntityReportFilter" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*HowChanged*|The report will include data for only the specified type of change. For example, you can use the filter to include data only for updates or deletions.<br /><br />You may specify only one type of change.|[ChangeTypeReportFilter](../reporting-api/changetypereportfilter-value-set.md)|Optional|
|*ItemChanged*|The report will include data for only the specified type of entity. For example, you can use the filter to include data only for changes to ad groups or campaigns.<br /><br />You may specify only one type of entity.|[ChangeEntityReportFilter](../reporting-api/changeentityreportfilter-value-set.md)|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [SearchCampaignChangeHistoryReportRequest](../reporting-api/searchcampaignchangehistoryreportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]