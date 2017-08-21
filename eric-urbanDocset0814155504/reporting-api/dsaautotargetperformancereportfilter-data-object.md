---
title: "DSAAutoTargetPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/17/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d039f02-3a92-4f9a-8b45-fc1c318e60ed
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DSAAutoTargetPerformanceReportFilter Data Object
Defines the criteria to use to filter the DSA auto target performance report data.

## Syntax

```xml
<xs:complexType name="DSAAutoTargetPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DynamicAdTargetStatus" type="tns:DynamicAdTargetStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="BidStrategyTypes" type="tns:BidStrategyTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="LanguageCode" type="q20:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q20="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*BidStrategyTypes*|The report will include data for only the specified bid strategy types.|[BidStrategyTypeReportFilter](../reporting-api/bidstrategytypereportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for campaigns that have the specified status value. You can specify one or more status values.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DynamicAdTargetStatus*|The report will include data for only the dynamic ad targets that have the specified status.|[DynamicAdTargetStatusReportFilter](../reporting-api/dynamicadtargetstatusreportfilter-value-set.md)|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](~/concepts/ad-languages.md).|*string* array|Optional|


## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [DSAAutoTargetPerformanceReportRequest](../reporting-api/dsaautotargetperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]

## See Also
[DSAAutoTargetPerformanceReportRequest](../reporting-api/dsaautotargetperformancereportrequest-data-object.md)  
