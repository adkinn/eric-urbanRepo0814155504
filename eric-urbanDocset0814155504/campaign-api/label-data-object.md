---
title: "Label Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0e3906b-257a-4216-b2fe-0e3e95e297ab
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# Label Data Object
Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
<xs:complexType name="Label">
  <xs:sequence>
    <xs:element minOccurs="0" name="ColorCode" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="Description" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long"/>
    <xs:element minOccurs="0" name="Name" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ColorCode*|The label color as a hexadecimal code.<br/><br/>The hexadecimal value must have the '#' prefix. For example you can use the value of *#FFFFFF* for a white label.<br/><br/>The color can be viewed in the Bing Ads web application. Your application can display the color or utilize the hexadecimal value to categorize a set of labels.<br/><br/>**Add:** Optional. If you do not specify any color, the value will be assigned at random for each label.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)] You can update the color code but cannot remove it.|*string*|
|*Description*|The label description.<br/><br/>The label description can be between 1 to 200 characters in length.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Id*|The system-generated identifier of the label.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Name*|The label name.<br/><br/>The case-sensitive label name can be between 1 to 80 characters in length, and must be unique across all labels in the account.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[LabelAssociation](../campaign-api/labelassociation-data-object.md)  

