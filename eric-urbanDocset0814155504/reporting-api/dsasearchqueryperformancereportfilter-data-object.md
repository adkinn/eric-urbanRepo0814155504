---
title: "DSASearchQueryPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/20/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 592b629a-54a4-4a89-accf-d9b03b7dbe52
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DSASearchQueryPerformanceReportFilter Data Object
Defines the criteria to use to filter the DSA search query performance report data.

## Syntax

```xml
<xs:complexType name="DSASearchQueryPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdStatus" type="tns:AdStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="ExcludeZeroClicks" type="xs:boolean" minOccurs="0"/>
    <xs:element name="LanguageCode" type="q20:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q20="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="SearchQueries" type="q20:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q21="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*AdStatus*|The report will include data for ads that have the specified status value. You can specify one or more status values.|[AdStatusReportFilter](../reporting-api/adstatusreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for campaigns that have the specified status value. You can specify one or more status values.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*ExcludeZeroClicks*|If the value of this element is set to *true*, search terms that had one or more ad impressions but resulted in zero clicks in the specified time duration will be excluded from the report.<br /><br />The default value is *false*, in which case the report will include zero click search term data.<br /><br />**Note**: Regardless of the value of this filter, search terms with zero clicks in the last 30 days will always be excluded.|*boolean*|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](~/concepts/ad-languages.md).|*string* array|Optional|
|*SearchQueries*|The report will include data for only the specified search query strings.<br /><br />The list can contain a maximum of 30 strings, and each string can contain a maximum of 256 characters.|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [DSASearchQueryPerformanceReportRequest](../reporting-api/dsasearchqueryperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]

## See Also
[DSASearchQueryPerformanceReportRequest](../reporting-api/dsasearchqueryperformancereportrequest-data-object.md)  
