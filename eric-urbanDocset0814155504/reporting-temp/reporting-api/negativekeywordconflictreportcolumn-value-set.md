---
title: "NegativeKeywordConflictReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8932047-9fa3-4f1b-a090-70faa211ff86
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeywordConflictReportColumn Value Set
Defines the attributes columns that you can include in the [NegativeKeywordConflictReportRequest](../reporting-api/negativekeywordconflictreportrequest-data-object.md).

[!INCLUDE[reportcolumn_headerattributesonly](../reporting-api/includes/reportcolumn-headerattributesonly.md)]
## Syntax

```xml
\<xs:simpleType name="NegativeKeywordConflictReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AccountName" />
    \<xs:enumeration value="AccountNumber" />
    \<xs:enumeration value="AccountId" />
    \<xs:enumeration value="CampaignName" />
    \<xs:enumeration value="CampaignId" />
    \<xs:enumeration value="AdGroupName" />
    \<xs:enumeration value="AdGroupId" />
    \<xs:enumeration value="Keyword" />
    \<xs:enumeration value="KeywordId" />
    \<xs:enumeration value="NegativeKeyword" />
    \<xs:enumeration value="ConflictLevel" />
    \<xs:enumeration value="BidMatchType"/>
    \<xs:enumeration value="NegativeKeywordListId"/>
    \<xs:enumeration value="NegativeKeywordList"/>
    \<xs:enumeration value="NegativeKeywordId"/>
    \<xs:enumeration value="NegativeKeywordMatchType"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|ConflictLevel|[!INCLUDE[reportcolumn_conflictlevel](../reporting-api/includes/reportcolumn-conflictlevel.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)]|
|KeywordId|[!INCLUDE[reportcolumn_keywordid](../reporting-api/includes/reportcolumn-keywordid.md)]|
|NegativeKeyword|[!INCLUDE[reportcolumn_negativekeyword](../reporting-api/includes/reportcolumn-negativekeyword.md)]|
|NegativeKeywordId|[!INCLUDE[reportcolumn_NegativeKeywordId](../reporting-api/includes/reportcolumn-negativekeywordid.md)]|
|NegativeKeywordList|[!INCLUDE[reportcolumn_NegativeKeywordList](../reporting-api/includes/reportcolumn-negativekeywordlist.md)]|
|NegativeKeywordListId|[!INCLUDE[reportcolumn_NegativeKeywordListId](../reporting-api/includes/reportcolumn-negativekeywordlistid.md)]|
|NegativeKeywordMatchType|[!INCLUDE[reportcolumn_NegativeKeywordMatchType](../reporting-api/includes/reportcolumn-negativekeywordmatchtype.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AccountName|
|Keyword|
|NegativeKeyword|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[NegativeKeywordConflictReportRequest](../reporting-api/negativekeywordconflictreportrequest-data-object.md)

