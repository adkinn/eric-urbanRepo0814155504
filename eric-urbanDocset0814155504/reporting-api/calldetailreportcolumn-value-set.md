---
title: "CallDetailReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6148881f-182f-465b-b3c9-065710ca46ef
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CallDetailReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [CallDetailReportRequest](../reporting-api/calldetailreportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="CallDetailReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="StartTime"/>
    <xs:enumeration value="EndTime"/>
    <xs:enumeration value="Duration"/>
    <xs:enumeration value="CallStatus"/>
    <xs:enumeration value="CallTypeName"/>
    <xs:enumeration value="AreaCode"/>
    <xs:enumeration value="City "/>
    <xs:enumeration value="State"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/>
    <xs:enumeration value="AdGroupStatus"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AreaCode|[!INCLUDE[reportcolumn_areacode](../reporting-api/includes/reportcolumn-areacode.md)]|
|CallStatus|[!INCLUDE[reportcolumn_callstatus](../reporting-api/includes/reportcolumn-callstatus.md)]|
|CallTypeName|[!INCLUDE[reportcolumn_calltypename](../reporting-api/includes/reportcolumn-calltypename.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|City|[!INCLUDE[reportcolumn_city](../reporting-api/includes/reportcolumn-city.md)] The location where the user was in physically when they clicked the ad.|
|Duration|[!INCLUDE[reportcolumn_duration](../reporting-api/includes/reportcolumn-duration.md)]|
|EndTime|[!INCLUDE[reportcolumn_endtime](../reporting-api/includes/reportcolumn-endtime.md)]|
|StartTime|[!INCLUDE[reportcolumn_starttime](../reporting-api/includes/reportcolumn-starttime.md)]|
|State|[!INCLUDE[reportcolumn_state](../reporting-api/includes/reportcolumn-state.md)] The location where the user was in physically when they clicked the ad.|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|CallStatus|
|CallTypeName|
|EndTime|
|StartTime|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[CallDetailReportRequest](../reporting-api/calldetailreportrequest-data-object.md)

