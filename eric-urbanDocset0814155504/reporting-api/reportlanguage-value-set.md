---
title: "ReportLanguage Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 334a903b-79f0-45c5-bb1d-32445c37040f
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportLanguage Value Set
Defines the language values that you may specify for columns of a downloaded report.

## Syntax

```xml
\<xs:simpleType name="ReportLanguage">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="English"/>
    \<xs:enumeration value="French"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|English|The report columns will be in English.|
|French|The report columns will be in French.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequest](../reporting-api/reportrequest-data-object.md)

