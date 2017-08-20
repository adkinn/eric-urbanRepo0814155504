---
title: "WebpageCondition Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef9ee8db-f0c6-4a82-a7d6-f2c368f53645
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# WebpageCondition Data Object
Defines a condition or criterion that helps determine whether you want to show dynamic search ads.

## Syntax

```xml
<xs:complexType name="WebpageCondition">
  <xs:sequence>
    <xs:element minOccurs="0" name="Argument" nillable="true" type="xs:string"/>
    <xs:element xmlns:q7="https://bingads.microsoft.com/CampaignManagement/v10" minOccurs="0" name="Operand" type="q7:WebpageConditionOperand"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Argument*|The webpage condition or criterion. The condition is met if the webpage property that is referenced by the operand contains or equals the argument's value.<br/><br/>For example you can set this string to the URL, category, page title, or page content for your site.<br/><br/>**Add:** Required<br/>**Update:** Not applicable. You cannot update the webpage conditions. To update the conditions you must delete the criterion and add a new criterion.|*string*|
|*Operand*|The webpage condition operand.<br/><br/>**Add:** Required<br/>**Update:** Not applicable. You cannot update the webpage conditions. To update the conditions you must delete the criterion and add a new criterion.|[WebpageConditionOperand](../campaign-api/webpageconditionoperand-value-set.md)|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
[DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md)  
[Webpage](../campaign-api/webpage-data-object.md)  
[WebpageParameter](../campaign-api/webpageparameter-data-object.md)  
