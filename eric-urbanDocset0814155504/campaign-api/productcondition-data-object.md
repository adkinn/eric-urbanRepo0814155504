---
title: "ProductCondition Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38d46c06-742e-41f9-b670-0559eed6dbbf
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductCondition Data Object
Defines a condition that determines whether a product is selected from a customer’s [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] catalog file.

## Syntax

```xml
<xs:complexType name="ProductCondition">
  <xs:sequence>
    <xs:element minOccurs="0" name="Attribute" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Operand" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Attribute*|The condition’s attribute value.<br /><br />An attribute’s value must exactly match the value specified in the customer’s [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] catalog file.<br /><br />The available *Attribute* and *Operand* values vary depending on the criterion type.<br /><br />For [ProductScope](../campaign-api/productscope-data-object.md) and [ProductPartition](../campaign-api/productpartition-data-object.md) conditions, see [Bing Shopping Product Conditions](https://msdn.microsoft.com/library/bing-ads-campaign-management-bing-shopping-campaigns.aspx#conditions).<br /><br />**Add or Apply:** Required<br/>**Update:** Optional|*string*|
|*Operand*|The condition’s operand. The operands implicitly include the equal operator. For example, read Brand as Brand=.<br /><br />**Add or Apply:** Required<br/>**Update:** Optional|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Bing Shopping Campaigns](https://msdn.microsoft.com/library/bing-ads-campaign-management-bing-shopping-campaigns.aspx)  
[ProductScope](../campaign-api/productscope-data-object.md)  
[ProductPartition](../campaign-api/productpartition-data-object.md)  

