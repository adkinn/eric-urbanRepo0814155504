---
title: "AdExtensionDetailReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e323fcf-db06-4de8-a0cf-5726534ee412
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionDetailReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AdExtensionDetailReportRequest](../reporting-api/adextensiondetailreportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="AdExtensionDetailReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName" />
    <xs:enumeration value="AccountId" />
    <xs:enumeration value="TimePeriod" />
    <xs:enumeration value="CampaignName" />
    <xs:enumeration value="CampaignId" />
    <xs:enumeration value="AdGroupName" />
    <xs:enumeration value="AdGroupId" />
    <xs:enumeration value="AdTitle" />
    <xs:enumeration value="AdId" />
    <xs:enumeration value="AdExtensionType" />
    <xs:enumeration value="AdExtensionTypeId" />
    <xs:enumeration value="AdExtensionId" />
    <xs:enumeration value="AdExtensionVersion" />
    <xs:enumeration value="AdExtensionPropertyValue" />
    <xs:enumeration value="Impressions" />
    <xs:enumeration value="DeviceType" />
    <xs:enumeration value="DeviceOS" />
    <xs:enumeration value="Clicks" />
    <xs:enumeration value="Ctr" />
    <xs:enumeration value="Conversions" />
    <xs:enumeration value="CostPerConversion" />
    <xs:enumeration value="ConversionRate" />
    <xs:enumeration value="Spend" />
    <xs:enumeration value="AverageCpc" />
    <xs:enumeration value="BidMatchType" />
    <xs:enumeration value="DeliveredMatchType" />
    <xs:enumeration value="Network" />
    <xs:enumeration value="TopVsOther" />
    <xs:enumeration value="Assists" />
    <xs:enumeration value="Revenue" />
    <xs:enumeration value="ReturnOnAdSpend" />
    <xs:enumeration value="CostPerAssist" />
    <xs:enumeration value="RevenuePerConversion" />
    <xs:enumeration value="RevenuePerAssist" />
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/> 
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="AdStatus"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdExtensionId|[!INCLUDE[reportcolumn_adextensionid](../reporting-api/includes/reportcolumn-adextensionid.md)]|
|AdExtensionPropertyValue|The human readable ad extension property value. For this report only one property is available for each type of ad extension. The following are the possible property values corresponding to each *AdExtensionTypeId*:<br /><br />If  the *AdExtensionTypeId* is 10, this *AdExtensionPropertyValue* is the display text of a sitelink ad extension.<br /><br />If  the *AdExtensionTypeId* is 11, this *AdExtensionPropertyValue* is the company name of a location ad extension.<br /><br />If  the *AdExtensionTypeId* is 12 or 14, this *AdExtensionPropertyValue* is the phone number of a call ad extension.|
|AdExtensionType|[!INCLUDE[reportcolumn_adextensiontype](../reporting-api/includes/reportcolumn-adextensiontype.md)]|
|AdExtensionTypeId|[!INCLUDE[reportcolumn_adextensiontypeid](../reporting-api/includes/reportcolumn-adextensiontypeid.md)]|
|AdExtensionVersion|[!INCLUDE[reportcolumn_adextensionversion](../reporting-api/includes/reportcolumn-adextensionversion.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdId|[!INCLUDE[reportcolumn_adid](../reporting-api/includes/reportcolumn-adid.md)]|
|AdStatus|[!INCLUDE[reportcolumn_adstatus](../reporting-api/includes/reportcolumn-adstatus.md)]|
|AdTitle|[!INCLUDE[reportcolumn_adtitle](../reporting-api/includes/reportcolumn-adtitle.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AdExtensionId|
|AdExtensionPropertyValue|
|AdExtensionType|
|AdExtensionTypeId|
|Clicks|
|Ctr|
|Impressions|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdExtensionDetailReportRequest](../reporting-api/adextensiondetailreportrequest-data-object.md)

