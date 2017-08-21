---
title: "SearchQueryPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0d1f5cd-a164-41a4-9fdd-a61c4d8a0cb4
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchQueryPerformanceReportFilter Data Object
Defines the criteria to use to filter the search query performance report data.

## Syntax

```xml
<xs:complexType name="SearchQueryPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdStatus" type="tns:AdStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdType" type="tns:AdTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeliveredMatchType" type="tns:DeliveredMatchTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="ExcludeZeroClicks" type="xs:boolean" minOccurs="0"/>
    <xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="LanguageCode" type="q20:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q20="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="SearchQueries" type="q21:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q21="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*AdStatus*|The report will include data for ads that have the specified status value. You can specify one or more status values.|[AdStatusReportFilter](../reporting-api/adstatusreportfilter-value-set.md)|Optional|
|*AdType*|The report will include data for only the specified ad types. For example, the report can include data for product or text ads. You can specify one or more ad types.|[AdTypeReportFilter](../reporting-api/adtypereportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for campaigns that have the specified status value. You can specify one or more status values.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeliveredMatchType*|The report will include data for only the specified delivered match types (as opposed to the bid match type). For example, you can use the filter to include data for ads that were delivered using the exact or phrase match type.<br /><br />You can specify one or more delivered match types.|[DeliveredMatchTypeReportFilter](../reporting-api/deliveredmatchtypereportfilter-value-set.md)|Optional|
|*ExcludeZeroClicks*|If the value of this element is set to *true*, search terms that had one or more ad impressions but resulted in zero clicks in the specified time duration will be excluded from the report.<br /><br />The default value is *false*, in which case the report will include zero click search term data.<br /><br />**Note**: Regardless of the value of this filter, search terms with zero clicks in the last 30 days will always be excluded.|*boolean*|Optional|
|*KeywordStatus*|The report will include data for only the keyword status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](~/concepts/ad-languages.md).|*string* array|Optional|
|*SearchQueries*|The report will include data for only the specified search query strings.<br /><br />The list can contain a maximum of 30 strings, and each string can contain a maximum of 256 characters.|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [SearchQueryPerformanceReportRequest](../reporting-api/searchqueryperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchQueryPerformanceReportRequest](../reporting-api/searchqueryperformancereportrequest-data-object.md)

