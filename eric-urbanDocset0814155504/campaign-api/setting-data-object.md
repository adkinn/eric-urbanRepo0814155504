---
title: "Setting Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f1bdd44-5118-4df1-a503-8205398780ab
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Setting Data Object
Defines the base class of a setting.

Do not try to instantiate a *Setting*. You can create one or more following objects that derive from it.
- [DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md)  
- [ShoppingSetting](../campaign-api/shoppingsetting-data-object.md)  

## Syntax

```xml
<xs:complexType name="Setting">
  <xs:sequence>
    <xs:element minOccurs="0" name="Type" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of setting. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a [DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md) or [ShoppingSetting](../campaign-api/shoppingsetting-data-object.md).

If you generate the SOAP manually, use the *type* attribute of the `<Setting>` node as shown in the following example, to specify that the setting is a shopping setting.

```xml
<Setting i:type="ShoppingSetting">
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)  
[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)  
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  
[Campaign](../campaign-api/campaign-data-object.md)  

