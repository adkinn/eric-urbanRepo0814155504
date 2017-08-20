---
title: "Address Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b20a4beb-ea0e-4b46-bc91-9904852540e3
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Address Data Object
Defines a postal address.

## Syntax

```xml
<xs:complexType name="Address">
  <xs:sequence>
    <xs:element name="CityName" nillable="true" type="xs:string" />
    <xs:element name="CountryCode" nillable="true" type="xs:string" />
    <xs:element name="PostalCode" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ProvinceCode" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ProvinceName" nillable="true" type="xs:string" />
    <xs:element name="StreetAddress" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="StreetAddress2" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CityName*|The name of the city where the street address is located. The name can contain a maximum of 80 characters.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*CountryCode*|The country where the street address is located. The country code must contain a 2 character country code. For a list of possible country codes that you can specify, see [Geographical Location Codes](http://msdn.microsoft.com/library/bing-ads-geographical-location-codes).<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*PostalCode*|The postal or zip code. The postal code can contain a maximum of 80 characters.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*ProvinceCode*|A code that identifies the state or province where the street address is located. For example, WA. The code can contain a maximum of 50 characters.<br /><br />You must specify either *ProvinceName* or *ProvinceCode*.<br /><br />**Note:** The *ProvinceCode* and *ProvinceName* are not required if the *CountryCode* element is set to either *FR*, *IE*, or *SG*.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*ProvinceName*|The name of the state or province where the street address is located. For example, Washington. The name can contain a maximum of 50 characters.<br /><br />You must specify either *ProvinceName* or *ProvinceCode*.<br /><br />**Note:** The*ProvinceCode* and *ProvinceName* are not required if the *CountryCode* element is set to either *FR*, *IE*, or *SG*.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*StreetAddress*|The first line of the address. The first line can contain a maximum of 80 characters.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*StreetAddress2*|The second line of the address. The second line can contain a maximum of 80 characters.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[LocationAdExtension](../campaign-api/locationadextension-data-object.md)  

