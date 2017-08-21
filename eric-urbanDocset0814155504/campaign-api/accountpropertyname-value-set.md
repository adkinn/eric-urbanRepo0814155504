---
title: "AccountPropertyName Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 043ab933-eeb2-4d7a-afd5-083db0740396
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# AccountPropertyName Value Set
Defines the name of account level properties.

## Syntax

```xml
<xs:simpleType name="AccountPropertyName">
  <xs:restriction base="xs:string">
    <xs:enumeration value="None" />
    <xs:enumeration value="TrackingUrlTemplate" />
    <xs:enumeration value="MSCLKIDAutoTaggingEnabled" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|MSCLKIDAutoTaggingEnabled|Used to get or set the property that determines whether MSCLKID auto-tagging is enabled for the account.|
|None|Reserved for internal use.|
|TrackingUrlTemplate|Used to get or set the account's tracking template.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AccountProperty](../campaign-api/accountproperty-data-object.md)  
[GetAccountProperties](../campaign-api/getaccountproperties-service-operation.md)  
[SetAccountProperties](../campaign-api/setaccountproperties-service-operation.md)  
