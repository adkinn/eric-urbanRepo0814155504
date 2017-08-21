---
title: "AdDynamicTextPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a53b3aa1-d3f1-427a-b9af-9e74e3594818
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdDynamicTextPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AdDynamicTextPerformanceReportRequest Data Object](../reporting-api/addynamictextperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="AdDynamicTextPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="TimePeriod"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="Keyword"/>
    <xs:enumeration value="AdId"/>
    <xs:enumeration value="AdTitle"/>
    <xs:enumeration value="AdType"/>
    <xs:enumeration value="DestinationUrl"/>
    <xs:enumeration value="Param1"/>
    <xs:enumeration value="Param2"/>
    <xs:enumeration value="Param3"/>
    <xs:enumeration value="CurrencyCode"/>
    <xs:enumeration value="AdDistribution"/>
    <xs:enumeration value="Impressions"/>
    <xs:enumeration value="Clicks"/>
    <xs:enumeration value="Ctr"/>
    <xs:enumeration value="AverageCpc"/>
    <xs:enumeration value="Spend"/>
    <xs:enumeration value="AveragePosition"/>
    <xs:enumeration value="Conversions"/>
    <xs:enumeration value="ConversionRate"/>
    <xs:enumeration value="CostPerConversion"/>
    <xs:enumeration value="DeviceType"/>
    <xs:enumeration value="Language"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="AdStatus"/>
    <xs:enumeration value="KeywordStatus"/>
    <xs:enumeration value="TitlePart1"/>
    <xs:enumeration value="TitlePart2"/>
    <xs:enumeration value="Path1"/>
    <xs:enumeration value="Path2"/>
    <xs:enumeration value="FinalURL"/>
    <xs:enumeration value="FinalMobileURL"/>
    <xs:enumeration value="FinalAppURL"/>
    <xs:enumeration value="AdDescription"/>   
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
|AdDescription|[!INCLUDE[reportcolumn_addescription](../reporting-api/includes/reportcolumn-addescription.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdStatus|[!INCLUDE[reportcolumn_adstatus](../reporting-api/includes/reportcolumn-adstatus.md)]|
|AdTitle|[!INCLUDE[reportcolumn_adtitle](../reporting-api/includes/reportcolumn-adtitle.md)]|
|AdType|[!INCLUDE[reportcolumn_adtype](../reporting-api/includes/reportcolumn-adtype.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|DestinationUrl|[!INCLUDE[reportcolumn_destinationurl](../reporting-api/includes/reportcolumn-destinationurl.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|FinalAppURL|Reserved for future use.|
|FinalMobileURL|The Final Mobile URL of the ad, keyword, or criterion.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|FinalURL|The Final URL of the ad, keyword, or criterion.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)]|
|KeywordStatus|[!INCLUDE[reportcolumn_keywordstatus](../reporting-api/includes/reportcolumn-keywordstatus.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|Param1|[!INCLUDE[reportcolumn_param1](../reporting-api/includes/reportcolumn-param1.md)]|
|Param2|[!INCLUDE[reportcolumn_param2](../reporting-api/includes/reportcolumn-param2.md)]|
|Param3|[!INCLUDE[reportcolumn_param3](../reporting-api/includes/reportcolumn-param3.md)]|
|Path1|[!INCLUDE[reportcolumn_path1](../reporting-api/includes/reportcolumn-path1.md)]|
|Path2|[!INCLUDE[reportcolumn_path2](../reporting-api/includes/reportcolumn-path2.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TitlePart1|[!INCLUDE[reportcolumn_titlepart1](../reporting-api/includes/reportcolumn-titlepart1.md)]|
|TitlePart2|[!INCLUDE[reportcolumn_titlepart2](../reporting-api/includes/reportcolumn-titlepart2.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AdTitle|
|DestinationURL|
|Param1|
|Param2|
|Param3|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdDynamicTextPerformanceReportRequest](../reporting-api/addynamictextperformancereportrequest-data-object.md)

