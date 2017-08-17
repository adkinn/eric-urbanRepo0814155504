---
title: "Address Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 118bba37-b2a1-4600-8b92-a4a8d303f973
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Address Data Object
Defines a postal address.

## Syntax

```xml
\<xs:complexType name="Address">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="City" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="CountryCode" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xsd:long" />
    \<xs:element minOccurs="0" name="Line1" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="Line2" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="Line3" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="Line4" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="PostalCode" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="StateOrProvince" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="TimeStamp" nillable="true" type="xsd:base64Binary" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*City*|The city, which can contain a maximum of 35 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*CountryCode*|The country/region code. For possible values, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes.aspx).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Id*|The system generated identifier of the address object.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Line1*|The first line of the address, which can contain a maximum of 35 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Line2*|The second line of the address, which can contain a maximum of 35 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Line3*|The third line of the address, which can contain a maximum of 35 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Line4*|The fourth line of the address, which can contain a maximum of 35 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*PostalCode*|The Postal or ZIP Code, which can contain a maximum of 10 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*StateOrProvince*|The state or province. This element is required for countries that define sub geographies, but should be set to null for countries that do not define sub geographies, such as Singapore.<br /><br />For possible values, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes.aspx).<br /><br />**Note:** You must use the state or province code without country prefix. For example given US-WA, you should use only the WA suffix for Washington state.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Timestamp*|A time-stamp value that the system uses internally to reconcile updates to the address.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*base64Binary*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]