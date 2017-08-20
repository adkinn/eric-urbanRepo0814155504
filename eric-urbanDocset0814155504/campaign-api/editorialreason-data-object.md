---
title: "EditorialReason Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8855cb88-dd05-4e4f-9059-e15718849c43
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EditorialReason Data Object
Defines an object that you can use to determine the component of an ad or keyword that failed editorial review, and the reason for the failure.

## Syntax

```xml
<xs:complexType name="EditorialReason">
  <xs:sequence>
    <xs:element minOccurs="0" name="Location" type="q10:AdComponent" xmlns:q10="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts" />
    <xs:element minOccurs="0" name="PublisherCountries" nillable="true" type="q39:ArrayOfstring" xmlns:q39="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <xs:element minOccurs="0" name="ReasonCode" type="xs:int" />
    <xs:element minOccurs="0" name="Term" nillable="true type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Location*|The component of the ad or keyword that failed editorial review.|*string*|
|*PublisherCountries*|A list of countries where the ad or keyword failed editorial review. The string contains the country’s two character country code.|*string* array|
|*ReasonCode*|A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](http://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx).|int|
|*Term*|The term that failed editorial review.<br /><br />This element cannot be set if a combination of terms caused the failure or if the failure was based on a policy violation.|string|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md)  
[Editorial Failure Reason Codes](http://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx)  

