---
title: "AccountThroughAdGroupReportScope Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 221440d9-0fe9-4450-b681-516762207f4f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountThroughAdGroupReportScope Data Object
Defines the set of accounts, campaigns, and ad groups to include in the report.

## Syntax

```xml
\<xs:complexType name="AccountThroughAdGroupReportScope">
  \<xs:sequence>
    \<xs:element xmlns:q2="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="AccountIds" nillable="true" type="q2:ArrayOflong" />
    \<xs:element minOccurs="0" name="AdGroups" nillable="true" type="tns:ArrayOfAdGroupReportScope" />
    \<xs:element minOccurs="0" name="Campaigns" nillable="true" type="tns:ArrayOfCampaignReportScope" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountIds*|An array of account identifiers that identifies the account data to include in the report. You can specify a maximum of 1,000 account identifiers.|*long* array|Optional|
|*AdGroups*|An array of *AdGroupReportScope* objects that identifies the ad group data to include in the report. You can specify a maximum of 300 ad group identifiers.|[AdGroupReportScope](../reporting-api/adgroupreportscope-data-object.md) array|Optional|
|*Campaigns*|An array of *CampaignReportScope* objects that identifies the campaign data to include in the report. You can specify a maximum of 300 campaign identifiers.|[CampaignReportScope](../reporting-api/campaignreportscope-data-object.md) array|Optional|

## Remarks
To get data for all accounts to which the user has access, including accounts that the user manages, set all elements of the scope object to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountReportScope](../reporting-api/accountreportscope-data-object.md)  
[AccountThroughCampaignReportScope](../reporting-api/accountthroughcampaignreportscope-data-object.md)  
[AdGroupReportScope](../reporting-api/adgroupreportscope-data-object.md)  
[ReportRequest](../reporting-api/reportrequest-data-object.md)  

