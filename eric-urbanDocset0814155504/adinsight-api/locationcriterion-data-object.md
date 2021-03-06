---
title: "LocationCriterion Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cee6a31-509b-40fc-8b3a-616f4fdb82b8
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# LocationCriterion Data Object
The location criterion that you can include when requesting keyword ideas or traffic estimates.

## Syntax

```xml
<xs:complexType name="LocationCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="LocationId" type="xs:long"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*LocationId*|The Bing Ads identifier of the location that you want to target.<br/><br/>You can get keyword ideas and traffic estimates for country, state, metro area, and city locations. Postal code location identifiers are not supported for keyword ideas and traffic estimate requests.<br/><br/>Currently this feature is available in the United States, United Kingdom, Canada, Australia, France, and Germany. To get a list of geographical location identifiers use the Campaign Management service i.e., the [GetGeoLocationsFileUrl](~/campaign-api/getgeolocationsfileurl-service-operation.md) service operation.|*long*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  
