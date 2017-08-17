---
title: "ApplicationFault Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8488e1f6-8103-4b8e-839c-705dfc1caf90
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApplicationFault Data Object
Defines the base object from which all fault detail objects derive.

## Syntax

```xml
\<xs:complexType name="ApplicationFault">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="TrackingId" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`TrackingId`|The identifier of the log entry that contains the details of the API call.|`string`|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]