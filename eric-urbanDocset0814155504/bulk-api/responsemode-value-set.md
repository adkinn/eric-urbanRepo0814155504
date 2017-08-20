---
title: "ResponseMode Value Set"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1da59195-ea12-4781-8594-b8d9a78638ea
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ResponseMode Value Set
Defines elements to specify whether the bulk service should return upload errors with their corresponding data.

## Syntax

```xml
\<xs:simpleType name="ResponseMode">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="ErrorsOnly" />
    \<xs:enumeration value="ErrorsAndResults" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ErrorsAndResults|Return errors and results in the bulk upload response file.|
|ErrorsOnly|Return errors only in the bulk upload response file.|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[GetBulkUploadUrl](../bulk-api/getbulkuploadurl-service-operation.md)

