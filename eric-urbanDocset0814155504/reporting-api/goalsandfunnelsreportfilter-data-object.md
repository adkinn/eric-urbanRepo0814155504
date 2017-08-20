---
title: "GoalsAndFunnelsReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e192f0c6-db81-444a-b342-7e6d83f3715c
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GoalsAndFunnelsReportFilter Data Object
Defines the criteria to use to filter the goals and funnels report data.

## Syntax

```xml
\<xs:complexType name="GoalsAndFunnelsReportFilter">
  \<xs:sequence>
    \<xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeviceOS" type="tns:DeviceOSReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="GoalIds" type="q23:ArrayOflong" nillable="true" minOccurs="0" xmlns:q23="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    \<xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeviceOS*|The report will include data where the ad is displayed on the specified device operating systems. For example, you may use the filter to include data for only ads displayed on Windows devices.|[DeviceOSReportFilter](../reporting-api/deviceosreportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data where the ad is displayed on the specified device types. For example, you may use the filter to include data for only ads displayed on smartphones.<br /><br />You may specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*GoalIds*|The report will include data for only the specified goals. The list can contain a maximum of 300 identifiers.|*long* array|Optional|
|*KeywordStatus*|The report will include data for only the keyword status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|

## Remarks
Because goals are unique to accounts, the goals that you specify in the filter must belong to the accounts that you specify in the *Scope* element of the [GoalsAndFunnelsReportRequest](../reporting-api/goalsandfunnelsreportrequest-data-object.md); otherwise, the report will not contain data associated with the specified goals.

Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [GoalsAndFunnelsReportRequest](../reporting-api/goalsandfunnelsreportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[GoalsAndFunnelsReportRequest](../reporting-api/goalsandfunnelsreportrequest-data-object.md)

