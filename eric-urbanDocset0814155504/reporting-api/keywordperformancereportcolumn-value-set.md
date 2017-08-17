---
title: "KeywordPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fab857c0-dbf9-4463-bc60-12e79cecc9dc
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="KeywordPerformanceReportColumn">
   <xs:restriction base="xs:string">
      <xs:enumeration value="AccountName" />
      <xs:enumeration value="AccountNumber" />
      <xs:enumeration value="AccountId" />
      <xs:enumeration value="TimePeriod" />
      <xs:enumeration value="CampaignName" />
      <xs:enumeration value="CampaignId" />
      <xs:enumeration value="AdGroupName" />
      <xs:enumeration value="AdGroupId" />
      <xs:enumeration value="Keyword" />
      <xs:enumeration value="KeywordId" />
      <xs:enumeration value="AdId" />
      <xs:enumeration value="AdType" />
      <xs:enumeration value="DestinationUrl" />
      <xs:enumeration value="CurrentMaxCpc" />
      <xs:enumeration value="CurrencyCode" />
      <xs:enumeration value="DeliveredMatchType" />
      <xs:enumeration value="AdDistribution" />
      <xs:enumeration value="Impressions" />
      <xs:enumeration value="Clicks" />
      <xs:enumeration value="Ctr" />
      <xs:enumeration value="AverageCpc" />
      <xs:enumeration value="Spend" />
      <xs:enumeration value="AveragePosition" />
      <xs:enumeration value="Conversions" />
      <xs:enumeration value="ConversionRate" />
      <xs:enumeration value="CostPerConversion" />
      <xs:enumeration value="BidMatchType" />
      <xs:enumeration value="DeviceType"/>
      <xs:enumeration value="QualityScore" />
      <xs:enumeration value="ExpectedCtr" />
      <xs:enumeration value="AdRelevance" />
      <xs:enumeration value="LandingPageExperience" />
      <xs:enumeration value="Language"/>
      <xs:enumeration value="HistoricQualityScore" />
      <xs:enumeration value="HistoricExpectedCtr" />
      <xs:enumeration value="HistoricAdRelevance" />
      <xs:enumeration value="HistoricLandingPageExperience" />
      <xs:enumeration value="QualityImpact"/>
      <xs:enumeration value="BusinessListingId" />
      <xs:enumeration value="BusinessListingName"/>
      <xs:enumeration value="BusinessCategoryId " />
      <xs:enumeration value="BusinessCategoryName" />
      <xs:enumeration value="CampaignStatus" />
      <xs:enumeration value="AccountStatus" />
      <xs:enumeration value="AdGroupStatus"/>
      <xs:enumeration value="KeywordStatus"/>
      <xs:enumeration value="Network"/>
      <xs:enumeration value="TopVsOther"/>
      <xs:enumeration value="DeviceOS " />
      <xs:enumeration value="Assists" />
      <xs:enumeration value="Revenue" />
      <xs:enumeration value="ReturnOnAdSpend"/>
      <xs:enumeration value="CostPerAssist"/>
      <xs:enumeration value="RevenuePerConversion"/>
      <xs:enumeration value="RevenuePerAssist"/>
      <xs:enumeration value="TrackingTemplate"/>
      <xs:enumeration value="CustomParameters"/>
      <xs:enumeration value="FinalURL"/>
      <xs:enumeration value="FinalMobileURL"/>
      <xs:enumeration value="FinalAppURL"/>
      <xs:enumeration value="BidStrategyType"/>
   </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdId|[!INCLUDE[reportcolumn_adid](../reporting-api/includes/reportcolumn-adid.md)]|
|AdRelevance|[!INCLUDE[reportcolumn_adrelevance](../reporting-api/includes/reportcolumn-adrelevance.md)]|
|AdType|[!INCLUDE[reportcolumn_adtype](../reporting-api/includes/reportcolumn-adtype.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|BidStrategyType|[!INCLUDE[reportcolumn_bidstrategytype](../reporting-api/includes/reportcolumn-bidstrategytype.md)]|
|BusinessCategoryId|Reserved for internal use.|
|BusinessCategoryName|Reserved for internal use.|
|BusinessListingId|Reserved for internal use.|
|BusinessListingName|Reserved for internal use.|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|CurrentMaxCpc|[!INCLUDE[reportcolumn_currentmaxcpc](../reporting-api/includes/reportcolumn-currentmaxcpc.md)]|
|CustomParameters|The current custom parameter set of the keyword.<br /><br />Each custom parameter is a key and value pair. The list of custom parameters is semicolon-delimited and each key is enclosed by braces and a leading underscore, for example *{_key1}=value1;{_key2}=value2*.|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DestinationUrl|[!INCLUDE[reportcolumn_destinationurl](../reporting-api/includes/reportcolumn-destinationurl.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|ExpectedCtr|[!INCLUDE[reportcolumn_expectedctr](../reporting-api/includes/reportcolumn-expectedctr.md)]|
|FinalAppURL|Reserved for future use.|
|FinalMobileURL|The Final Mobile URL of the keyword.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|FinalURL|The Final URL of the keyword.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|HistoricAdRelevance|[!INCLUDE[reportcolumn_historicadrelevance](../reporting-api/includes/reportcolumn-historicadrelevance.md)]|
|HistoricExpectedCtr|[!INCLUDE[reportcolumn_historicexpectedctr](../reporting-api/includes/reportcolumn-historicexpectedctr.md)]|
|HistoricLandingPageExperience|[!INCLUDE[reportcolumn_historiclandingpageexperience](../reporting-api/includes/reportcolumn-historiclandingpageexperience.md)]|
|HistoricQualityScore|[!INCLUDE[reportcolumn_historicqualityscore](../reporting-api/includes/reportcolumn-historicqualityscore.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)]|
|KeywordId|[!INCLUDE[reportcolumn_keywordid](../reporting-api/includes/reportcolumn-keywordid.md)]|
|KeywordStatus|[!INCLUDE[reportcolumn_keywordstatus](../reporting-api/includes/reportcolumn-keywordstatus.md)]|
|LandingPageExperience|[!INCLUDE[reportcolumn_landingpageexperience](../reporting-api/includes/reportcolumn-landingpageexperience.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|QualityImpact|[!INCLUDE[reportcolumn_qualityimpact](../reporting-api/includes/reportcolumn-qualityimpact.md)]|
|QualityScore|[!INCLUDE[reportcolumn_qualityscore](../reporting-api/includes/reportcolumn-qualityscore.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|
|TrackingTemplate|The current tracking template of the keyword.|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following column.

|Column|
|----------|
|TimePeriod<br /><br />**Note:** This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md)  

