---
title: "AccountThroughCampaignReportScope Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22654a11-bae7-41cc-82ce-c4be566e2750
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountThroughCampaignReportScope Data Object
Defines the set of accounts and campaigns to include in the report.

## Syntax

```xml
\<xs:complexType name="AccountThroughCampaignReportScope">
  \<xs:sequence>
    \<xs:element xmlns:q4="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="AccountIds" nillable="true" type="q4:ArrayOflong" />
    \<xs:element minOccurs="0" name="Campaigns" nillable="true" type="tns:ArrayOfCampaignReportScope" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountIds*|An array of account identifiers that identifies the account data to include in the report. You can specify a maximum of 1,000 account identifiers.|*long* array|Optional|
|*Campaigns*|An array of *CampaignReportScope* objects that identifies the campaign data to include in the report. You can specify a maximum of 300 campaign identifiers.|[CampaignReportScope](../reporting-api/campaignreportscope-data-object.md) array|Optional|

## Remarks
To get data for all accounts to which the user has access, including accounts that the user manages, set all elements of the scope object to NULL.

> [!NOTE]
> Either the *AccountIds* or *Campaigns* element is required when submitting a [BudgetSummaryReportRequest](../reporting-api/budgetsummaryreportrequest-data-object.md).

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountReportScope](../reporting-api/accountreportscope-data-object.md)  
[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)  
[CampaignPerformanceReportRequest](../reporting-api/campaignperformancereportrequest-data-object.md)  

