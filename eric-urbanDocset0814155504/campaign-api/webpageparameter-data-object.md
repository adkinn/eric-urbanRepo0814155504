---
title: "WebpageParameter Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b6fe110-b4e7-49e7-b6b2-57b43100d517
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# WebpageParameter Data Object
Defines the conditions or criteria that determine whether you want to show dynamic search ads.

## Syntax

```xml
<xs:complexType name="WebpageParameter">
  <xs:sequence>
    <xs:element minOccurs="0" name="Conditions" nillable="true" type="tns:ArrayOfWebpageCondition"/>
    <xs:element minOccurs="0" name="CriterionName" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Conditions*|The webpage conditions or criteria.<br /><br />You may include up to 3 individual [WebpageCondition](../campaign-api/webpagecondition-data-object.md) objects in the list. Each [WebpageCondition](../campaign-api/webpagecondition-data-object.md) contains an *Argument* and *Operand* element.<br/><br/>**Add:** Optional for biddable criterion; Required for negative criterion. If no conditions are specified, then you are effectively targeting all webpages.<br/>**Update:** Not allowed. You cannot update the webpage conditions. To update the conditions you must delete the criterion and add a new criterion.|[WebpageCondition](../campaign-api/webpagecondition-data-object.md) array|
|*CriterionName*|The criterion name that you can use to identify the criteria, for example you can filter or sort alphabetically.<br/><br/>The criterion name length must be between 1 to 2048, inclusive.<br/><br/>**Add:** Optional. If you do not specify any name, by default the name will be set to a concatenated list of conditions. Each condition will be delimited by the *and* keyword. For example if the conditions are a) *Url contains flower*, b) *Url contains book*, and c) *PageContent contains seattle*, then the default criterion name will be *Url contains flower and Url contains book and PageContent contains seattle*. If you do not specify any name, and if no conditions are specified, then you are effectively targeting all webpages and the name will be set to *All Webpages*. <br/>**Update:** Optional. If you leave this element null or empty the criterion name will not be updated. If you specify an empty string i.e. "", then the criterion name will be updated to the default value i.e. either *All Webpages* or a concatenated list of criterions.|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
[DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md)  
[Webpage](../campaign-api/webpage-data-object.md)  
