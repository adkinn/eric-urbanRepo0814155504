---
title: "AccountStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98080e86-f3ff-4efc-854a-6c4c8e1c8c82
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountStatusReportFilter Value Set
Defines the account status values that you can use to filter the report data. These values are also used as column values in reports that include account status, such as the account performance report.

## Syntax

```xml
<xs:simpleType name="AccountStatusReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Active"/>
        <xs:enumeration value="Paused"/>
        <xs:enumeration value="Inactive"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain accounts that are active.|
|Inactive|The report will contain accounts that are not active.|
|Paused|The report will contain accounts that are paused.|

## Remarks
This value set is used as a set of flags. You may combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and inactive accounts in the report.

```csharp
objAccountPerfReportRequest.Status = 
    AccountStatusReportFilter.Paused | 
    AccountStatusReportFilter.Inactive;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountPerformanceReportFilter](../reporting-api/accountperformancereportfilter-data-object.md)  

