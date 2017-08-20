---
title: "PriceTableRow Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c976c92-6198-4195-8169-4ae528327b46
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# PriceTableRow Data Object
Defines pricing information by currency and unit that you can use with price ad extensions.

## Syntax

```xml
<xs:complexType name="PriceTableRow">
  <xs:sequence>
    <xs:element name="CurrencyCode" type="xs:string" minOccurs="0" nillable="true" />
    <xs:element name="Description" type="xs:string" minOccurs="0" nillable="true" />
    <xs:element xmlns:q60="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q60:ArrayOfstring"/>
    <xs:element xmlns:q61="http://schemas.microsoft.com/2003/10/Serialization/Arrays" name="FinalUrls" nillable="true" type="q61:ArrayOfstring"/>
    <xs:element name="Header" type="xs:string" minOccurs="0" nillable="true" />
    <xs:element name="Price" type="xs:double" minOccurs="0" nillable="true" />
    <xs:element name="PriceQualifier" type="tns:PriceQualifier" minOccurs="0" nillable="true" />
    <xs:element name="PriceUnit" type="tns:PriceUnit" minOccurs="0" nillable="true" />
    <xs:element minOccurs="0" name="TermsAndConditions" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="TermsAndConditionsUrl" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CurrencyCode*|The currency code for the listed price.<br/><br/>For more information, see [Currencies](https://msdn.microsoft.com/library/bing-ads-currencies.aspx).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Description*|The description must provide further information about the header that is also defined in this object.<br/><br/>The description can contain a maximum of 25 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*FinalMobileUrls*|The mobile landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]<br /><br />**Add:** Optional<br />**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string* array|
|*FinalUrls*|The landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that if the price ad extension's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br /><br />**Add:** Optional<br />**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string* array|
|*Header*|The header that precedes the pricing data.<br/><br/>The header can contain a maximum of 25 characters.<br/><br/>The header must tie directly to the [PriceAdExtensionType](../campaign-api/priceadextensiontype-value-set.md) that you defined for the [PriceAdExtension](../campaign-api/priceadextension-data-object.md).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Price*|The price that you are advertising.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*double*|
|*PriceUnit*|The price unit.<br/><br/>Possible values include: *Average*, *From*, *UpTo*, *None*, and *Unknown*.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[PriceUnit](../campaign-api/priceunit-value-set.md)|
|*PriceQualifier*|The price qualifier.<br/><br/>Possible values include: *PerDay*, *PerHour*, *PerMonth*, *PerNight*, *PerWeek*, *PerYear*, *None*, and *Unknown*. <br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[PriceQualifier](../campaign-api/pricequalifier-value-set.md)|
|*TermsAndConditions*|Reserved for future use.|*string*|
|*TermsAndConditionsUrl*|Reserved for future use.|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[PriceAdExtension](../campaign-api/priceadextension-data-object.md)  
