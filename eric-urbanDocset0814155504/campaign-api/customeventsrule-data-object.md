---
title: "CustomEventsRule Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43468cdb-b589-4fbb-be4e-98b01d3360e3
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomEventsRule Data Object
Defines a custom events remarketing rule. 

Remarketing rules are conditions used to determine who to add to your remarketing list. For the custom events rule, you must include one or more of the following conditional event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*). If more than one condition is specified, the conditions are joined using the logical *AND* operator. In other words the visitor will only be added to your remarketing list if all of the specified rule conditions are met.

For a detailed example, see the [Remarks](#remarks) section below.

## Syntax

```xml
<xs:complexType name="CustomEventsRule">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:RemarketingRule">
      <xs:sequence>
        <xs:element minOccurs="0" name="Action" nillable="true" type="xs:string"/>
        <xs:element xmlns:q9="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="ActionOperator" type="q9:StringOperator"/>
        <xs:element minOccurs="0" name="Category" nillable="true" type="xs:string"/>
        <xs:element xmlns:q10="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="CategoryOperator" type="q10:StringOperator"/>
        <xs:element minOccurs="0" name="Label" nillable="true" type="xs:string"/>
        <xs:element xmlns:q11="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="LabelOperator" type="q11:StringOperator"/>
        <xs:element minOccurs="0" name="Value" nillable="true" type="xs:decimal"/>
        <xs:element xmlns:q12="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="ValueOperator" type="q12:NumberOperator"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *CustomEventsRule* object inherits elements from the [RemarketingRule](../campaign-api/remarketingrule-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Action*|The type of user interaction you want to track. For example 'play' or 'pause'.<br/><br/>If this element is specified during an add or update operation, then the *ActionOperator* element is also required.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *ActionOperator* and *Action* during update, any existing *ActionOperator* and *Action* settings will be deleted.|*string*|
|*ActionOperator*|The operator that can be applied to the value of the *Action* element.<br/><br/>If this element is specified during an add or update operation, then the *Action* element is also required.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *ActionOperator* and *Action* during update, any existing *ActionOperator* and *Action* settings will be deleted.|[StringOperator](../campaign-api/stringoperator-value-set.md)|
|*Category*|The category of event you want to track. For example, 'video'.<br/><br/>If this element is specified during an add or update operation, then the *CategoryOperator* element is also required.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *CategoryOperator* and *Category* during update, any existing *CategoryOperator* and *Category* settings will be deleted.|*string*|
|*CategoryOperator*|The operator that can be applied to the value of the *Category* element.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *CategoryOperator* and *Category* during update, any existing *CategoryOperator* and *Category* settings will be deleted.|[StringOperator](../campaign-api/stringoperator-value-set.md)|
|*Label*|The name of the element that caused the action. For example 'trailer' or 'behindthescenes'.<br/><br/>If this element is specified during an add or update operation, then the *LabelOperator* element is also required.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *LabelOperator* and *Label* during update, any existing *LabelOperator* and *Label* settings will be deleted.|*string*|
|*LabelOperator*|The operator that can be applied to the value of the *Label* element.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *LabelOperator* and *Label* during update, any existing *LabelOperator* and *Label* settings will be deleted.|[StringOperator](../campaign-api/stringoperator-value-set.md)|
|*Value*|A positive integer value associated with that event. For example the value could be the duration of time that the video played.<br/><br/>If this element is specified during an add or update operation, then the *ValueOperator* element is also required.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *ValueOperator* and *Value* during update, any existing *ValueOperator* and *Value* settings will be deleted|*decimal*|
|*ValueOperator*|The operator that can be applied to the value of the *Value* element.<br/><br/>**Add:** Optional if you include one or more of the other events; You must include one or more of the following event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*).<br/>**Update:** Optional if you include one or more of the other events; If you do not include *ValueOperator* and *Value* during update, any existing *ValueOperator* and *Value* settings will be deleted.|[NumberOperator](../campaign-api/numberoperator-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *CustomEventsRule* object inherits the following elements from the [RemarketingRule](../campaign-api/remarketingrule-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to custom events rules, and might not apply to other objects that inherit the same elements from the [RemarketingRule](../campaign-api/remarketingrule-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the remarketing rule. For more information about remarketing rule types, see the [RemarketingRule Data Object Remarks](../campaign-api/remarketingrule-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## <a name="Remarks"></a>Remarks
For the *CustomEvents* rule, you must include one or more of the following conditional event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*). If more than one condition is specified, the conditions are joined using the logical *AND* operator. In other words the visitor will only be added to your remarketing list if all of the specified rule conditions are met.

For example let's say that the following custom events are set.

```xml
<Rule i:type="a:CustomEventsRule" xmlns:a="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11">
  <a:Type>CustomEvents</a:Type>
  <a:Action>play</a:Action>
  <a:ActionOperator>Equals</a:ActionOperator>
  <a:Category>video</a:Category>
  <a:CategoryOperator>Equals</a:CategoryOperator>
  <a:Label>trailer</a:Label>
  <a:LabelOperator>Equals</a:LabelOperator>
  <a:Value>5</a:Value>
  <a:ValueOperator>Equals</a:ValueOperator>
</Rule>
```

The above definition is translated to the following logical expression:

*(Category Equals video) and (Action Equals play) and (Label Equals trailer) and (Value Equals 5)*

Evaluation of the logical expression determines who will be added to the remarketing list.

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
