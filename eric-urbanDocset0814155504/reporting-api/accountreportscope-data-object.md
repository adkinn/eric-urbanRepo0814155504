---
title: "AccountReportScope Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27ad4fda-d389-4cbf-8dea-378eda4c5d4a
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountReportScope Data Object
Defines the set of accounts to include in the report.

## Syntax

```xml
<xs:complexType name="AccountReportScope">
  <xs:sequence>
    <xs:element xmlns:q1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="AccountIds" nillable="true" type="q1:ArrayOflong" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountIds*|An array of a maximum of 1,000 account identifiers that identifies the account data to include in the report.<br /><br />To include every account to which the user has access, including accounts that the user manages, set this element to NULL.|*long* array|Optional for [AccountPerformanceReportRequest](../reporting-api/accountperformancereportrequest-data-object.md).|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountPerformanceReportRequest](../reporting-api/accountperformancereportrequest-data-object.md)  
[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)  
[AccountThroughCampaignReportScope](../reporting-api/accountthroughcampaignreportscope-data-object.md)  
[AdGroupReportScope](../reporting-api/adgroupreportscope-data-object.md)  
[BudgetSummaryReportRequest](../reporting-api/budgetsummaryreportrequest-data-object.md)  

