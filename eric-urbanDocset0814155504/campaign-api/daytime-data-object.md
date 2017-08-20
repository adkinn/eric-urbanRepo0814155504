---
title: "DayTime Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3819c232-240a-439e-b913-c2b2aba35874
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DayTime Data Object
Defines a day of the week and time range for ad extension scheduling. 

## Syntax

```xml
\<xs:complexType name="DayTime">
  \<xs:sequence>
    \<xs:element name="Day" type="tns:Day"/>
    \<xs:element name="EndHour" type="xs:int"/>
    \<xs:element name="EndMinute" type="tns:Minute"/>
    \<xs:element name="StartHour" type="xs:int"/>
    \<xs:element name="StartMinute" type="tns:Minute"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Day*|The scheduled day of week.<br/><br/>**Add:** Required.<br/>**Update:** The *DayTime* object cannot be updated. |[Day](../campaign-api/day-value-set.md)|
|*EndHour*|The scheduled end hour.<br/><br/>The possible values range from 0 to 24, where *0* is equivalent to 12:00AM and *12* is 12:00PM.<br/><br/>**Add:** Required. <br/>**Update:** The *DayTime* object cannot be updated. |*int*|
|*EndMinute*|The scheduled end minute.<br /><br />The possible values range from 0 to 60.<br/><br/>**Add:** Required.<br/>**Update:** The *DayTime* object cannot be updated. |[Minute](../campaign-api/minute-value-set.md)|
|*StartHour*|The scheduled start hour.<br/><br/>The possible values range from 0 to 23, where *0* is equivalent to 12:00AM and *12* is 12:00PM.<br/><br/>**Add:** Required.<br/>**Update:** The *DayTime* object cannot be updated. |*int*|
|*StartMinute*|The scheduled start minute.<br /><br />The possible values range from 0 to 60.<br/><br/>**Add:** Required.<br/>**Update:** The *DayTime* object cannot be updated. |[Minute](../campaign-api/minute-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  
