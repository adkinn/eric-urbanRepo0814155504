---
title: "ReportFormat Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8bb83da-bc3e-4984-8878-f04f262d8b20
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportFormat Value Set
Defines the file formats that you can use for a report.

## Syntax

```xml
\<xs:simpleType name="ReportFormat">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Csv"/>
    \<xs:enumeration value="Tsv"/>
    \<xs:enumeration value="Xml"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Csv|The report format will be comma-separated values (.csv).|
|Tsv|The report format will be tab-separated values (.tsv).|
|Xml|The report format will be XML (.xml).|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequest](../reporting-api/reportrequest-data-object.md)

