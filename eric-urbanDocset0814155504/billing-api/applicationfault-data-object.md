---
title: "ApplicationFault Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fb61eb4-dd27-4517-992c-43a7756a7e30
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApplicationFault Data Object
Defines the base object from which all fault detail objects derive.

## Syntax

```xml
<xs:complexType name="ApplicationFault">
  <xs:sequence>
    <xs:element minOccurs="0" name="TrackingId" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)

