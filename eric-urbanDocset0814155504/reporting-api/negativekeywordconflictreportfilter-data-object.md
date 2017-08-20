---
title: "NegativeKeywordConflictReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12be9610-7d38-44b2-995a-1be44d14c500
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeywordConflictReportFilter Data Object
Defines the criteria to use to filter the negative keyword conflict report data.

## Syntax

```xml
\<xs:complexType name="NegativeKeywordConflictReportFilter">
  \<xs:sequence>
    \<xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will only include data for accounts with the specified status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will only include data for ad groups with the specified status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will only include data for campaigns with the specified status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*KeywordStatus*|The report will only include data for keywords with the specified status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [NegativeKeywordConflictReportRequest](../reporting-api/negativekeywordconflictreportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[NegativeKeywordConflictReportRequest](../reporting-api/negativekeywordconflictreportrequest-data-object.md)

