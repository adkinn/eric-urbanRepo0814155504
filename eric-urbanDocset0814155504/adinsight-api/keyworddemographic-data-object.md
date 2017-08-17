---
title: "KeywordDemographic Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b9e9c87-7c95-4798-9e9b-6d67b87492d4
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordDemographic Data Object
Defines an object that contains the device, age and gender of the user who entered the search query, if known.

## Syntax

```xml
<xs:complexType name="KeywordDemographic">
  <xs:sequence>
    <xs:element minOccurs="0" name="Device" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="Age18_24" type="xs:double" />
    <xs:element minOccurs="0" name="Age25_34" type="xs:double" />
    <xs:element minOccurs="0" name="Age35_49" type="xs:double" />
    <xs:element minOccurs="0" name="Age50_64" type="xs:double" />
    <xs:element minOccurs="0" name="Age65Plus" type="xs:double" />
    <xs:element minOccurs="0" name="AgeUnknown" type="xs:double" />
    <xs:element minOccurs="0" name="Female" type="xs:double" />
    <xs:element minOccurs="0" name="Male" type="xs:double" />
    <xs:element minOccurs="0" name="GenderUnknown" type="xs:double" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Age18_24*|The percentage of time that users 18 through 24 years of age searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*Age25_34*|The percentage of time that users 25 through 34 years of age searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*Age35_49*|The percentage of time that users 35 through 49 years of age searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*Age50_64*|The percentage of time that users 50 through 64 years of age searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*Age65Plus*|The percentage of time that users 65 years of age or older searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*AgeUnknown*|Not used.|*double*|
|*Device*|The device of the user who entered the search query.|*string*|
|*Female*|The percentage of time that female users searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|
|*GenderUnknown*|Not Used.|*double*|
|*Male*|The percentage of time that male users searched for the keyword. The value is specified in the range 0.0 through 1.0.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md)
[GetKeywordDemographics](../adinsight-api/getkeyworddemographics-service-operation.md)

