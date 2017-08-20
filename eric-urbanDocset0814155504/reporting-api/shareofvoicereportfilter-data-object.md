---
title: "ShareOfVoiceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36684945-ed43-42e9-a825-3fc5880075bf
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ShareOfVoiceReportFilter Data Object
Defines the criteria to use to filter the share of voice report data.

## Syntax

```xml
\<xs:complexType name="ShareOfVoiceReportFilter">
  \<xs:sequence>
    \<xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="BidMatchType" type="tns:BidMatchTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="BidStrategyType" type="tns:BidStrategyTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeliveredMatchType" type="tns:DeliveredMatchTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="Keywords" type="q29:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q29="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    \<xs:element name="LanguageCode" type="q30:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q30="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*BidMatchType*|The report will include data for only the specified bid match types. For example, you can use the filter to include data for ads that were bid on using the exact or phrase match type.<br /><br />You can specify one or more bid match types.<br /><br />To filter on delivered match types, see the *DeliveredMatchType* element.|[BidMatchTypeReportFilter](../reporting-api/bidmatchtypereportfilter-value-set.md)|Optional|
|*BidStrategyType*|The report will include data for only the specified bid strategy type or types. For example, you can use the filter to include data only for keywords that were bid on using the enhanced bid strategy type.<br /><br />You can specify one or more bid strategy types.|[BidStrategyTypeReportFilter](../reporting-api/bidstrategytypereportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeliveredMatchType*|The report will include data for only the specified delivered match types. For example, you can use the filter to include data for ads that were delivered using the exact or phrase match type.<br /><br />You can specify one or more delivered match types.<br /><br />To filter on bid match types, see the *BidMatchType* element.|[DeliveredMatchTypeReportFilter](../reporting-api/deliveredmatchtypereportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data for only the specified types of devices on which the ad is displayed. For example, you can use the filter to include data only for text ads displayed on smartphones.<br /><br />You can specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*KeywordStatus*|The report will include data for only the keyword status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|
|*Keywords*|The report will include data for only the specified keywords. You can specify a maximum of 75 keywords. Each keyword can contain a maximum of 100 characters.|*string[]*|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx).|*string* array|Optional|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ShareOfVoiceReportRequest](../reporting-api/shareofvoicereportrequest-data-object.md)

