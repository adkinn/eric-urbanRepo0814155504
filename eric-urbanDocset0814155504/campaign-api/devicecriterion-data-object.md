---
title: "DeviceCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a2e569a-2d19-4c5b-8336-7885540dc938
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# DeviceCriterion Data Object
Defines a criterion that can be used to show ads on specific devices.

When you target by device, you choose to show ads to potential customers when they're using desktops and tablets or smartphones. 

Each device criterion defines a device name for the accompanying criterion bid adjustment. 

The maximum number of device criterions that you can specify per campaign or ad group is three. You must either have three separate criterions for *Computers*, *Smartphones*, and *Tablets*, otherwise no device criterions can exist for the campaign or ad group.

The *DeviceCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. If ad group level device criterions are specified, the campaign level device criterions are ignored for that ad group. In other words the ad group device criterions override the campaign device criterions, and are not applied as a union.   



[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
<xs:complexType name="DeviceCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element name="DeviceName" type="xs:string" nillable="true" />
        <xs:element xmlns:q25="http://schemas.microsoft.com/2003/10/Serialization/Arrays" name="OSNames" nillable="true" type="q25:ArrayOfstring"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *DeviceCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DeviceName*|The name of the device to target.<br/><br/>The following are the possible device names that you can specify.<br />- Computers<br />- Smartphones<br />- Tablets<br /><br />Three separate bids for Computers, Tablets, and Smartphones should always be specified together. If you do not add individual device criterions representing each of the three device types, the missing device criterions will be added with the default bid adjustment of zero.<br /><br />**Add:** Required. Three separate criterions for *Computers*, *Smartphones*, and *Tablets* should be specified together in the same add criterions request. If you do not add individual device criterions representing each of the three device types, no device criterions will be added to the campaign or ad group.<br />**Update:** Not allowed. If you specify this element it must match the existing setting.|*string*|
|*OSNames*|Reserved for internal use.<br/><br/>If you specify this element the add and update operations will not fail, but the OS names will not be set. When you retrieve this object, the *OSNames* element will be nil.<br /><br />**Add:** Not allowed.<br />**Update:** Not allowed.|*string* array|


## <a name="InheritedElements"></a>Inherited Elements
The *DeviceCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to device criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Device* when you retrieve a device criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
