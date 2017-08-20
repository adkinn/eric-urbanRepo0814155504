---
title: "KeywordPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f92c3899-0a0b-46da-b223-ea1a2e38eb3a
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordPerformanceReportFilter Data Object
Defines the criteria to use to filter the keyword performance report data.

## Syntax

```xml
<xs:complexType name="KeywordPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdType" type="tns:AdTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="BidMatchType" type="tns:BidMatchTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="BidStrategyType" type="tns:BidStrategyTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeliveredMatchType" type="tns:DeliveredMatchTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="KeywordRelevance" type="q7:ArrayOfint" nillable="true" minOccurs="0" xmlns:q7="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="Keywords" type="q8:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q8="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="LandingPageRelevance" type="q9:ArrayOfint" nillable="true" minOccurs="0" xmlns:q9="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="LandingPageUserExperience" type="q10:ArrayOfint" nillable="true" minOccurs="0" xmlns:q10="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="LanguageCode" type="q11:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q11="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="QualityScore" type="q12:ArrayOfint" nillable="true" minOccurs="0" xmlns:q12="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*AdType*|The report will include data for only the specified ad types. For example, the report can include data for product or text ads. You can specify one or more ad types.|[AdTypeReportFilter](../reporting-api/adtypereportfilter-value-set.md)|Optional|
|*BidMatchType*|The report will include data for only the specified bid match types. For example, you can use the filter to include data for ads that were bid on using the exact or phrase match type.<br /><br />You can specify one or more bid match types.<br /><br />To filter on delivered match types, see the *DeliveredMatchType* element.|[BidMatchTypeReportFilter](../reporting-api/bidmatchtypereportfilter-value-set.md)|Optional|
|*BidStrategyType*|The report will include data for only the specified bid strategy type or types. For example, you can use the filter to include data only for keywords that were bid on using the enhanced bid strategy type.<br /><br />You can specify one or more bid strategy types.|[BidStrategyTypeReportFilter](../reporting-api/bidstrategytypereportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeliveredMatchType*|The report will include data for only the specified delivered match types.For example, you can use the filter to include data for ads that were delivered using the exact or phrase match type.<br /><br />You can specify one or more delivered match types.<br /><br />To filter on bid match types, see the *BidMatchType* element.|[DeliveredMatchTypeReportFilter](../reporting-api/deliveredmatchtypereportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data for only the specified types of devices on which the ad is displayed. For example, you can use the filter to include data for only text ads displayed on smartphones.<br /><br />You can specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*KeywordRelevance*|[!INCLUDE[reportcolumn_keywordrelevance](../reporting-api/includes/reportcolumn-keywordrelevance.md)]|*int* array||
|*KeywordStatus*|The report will include data for only the keyword status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|
|*Keywords*|The report will include data for only the specified keywords. You can specify a maximum of 75 keywords. Each keyword can contain a maximum of 100 characters.|*string* array|Optional|
|*LandingPageRelevance*|[!INCLUDE[reportcolumn_landingpageuserexperience](../reporting-api/includes/reportcolumn-landingpageuserexperience.md)]|*int* array||
|*LandingPageUserExperience*|[!INCLUDE[reportcolumn_landingpageuserexperience](../reporting-api/includes/reportcolumn-landingpageuserexperience.md)]|*int* array||
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx).|*string* array|Optional|
|*QualityScore*|The report will include data for only keywords with the specified quality scores. You can filter the report based on one or more of the following relevance values:<br /><br />0 – N/A (as shown in the web application)<br /><br />1 – Underperforming<br /><br />2 – Underperforming<br /><br />3 – Underperforming<br /><br />4 – Underperforming<br /><br />5 – Underperforming<br /><br />6 – Average performance<br /><br />7 – Competitive<br /><br />8 – Competitive<br /><br />9 – Competitive<br /><br />10 – Competitive|*int* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md)

