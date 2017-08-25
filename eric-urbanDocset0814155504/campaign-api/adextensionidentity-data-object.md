---
title: "AdExtensionIdentity Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19f4c0b3-42f8-4486-96cf-6d41940c1062
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionIdentity Data Object
Defines an object that identifies an ad extension revision.

## Syntax

```xml
<xs:complexType name="AdExtensionIdentity">
  <xs:sequence>
    <xs:element name="Id" type="xs:long" />
    <xs:element name="Version" type="xs:int" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The system-generated identifier of the ad extension.|*long*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it?s revised.|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)

