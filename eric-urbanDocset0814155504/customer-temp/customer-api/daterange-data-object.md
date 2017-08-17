---
title: "DateRange Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd33b450-6122-4b81-bc00-56409ada8ee4
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DateRange Data Object
Defines a date range object.

## Syntax

```xml
\<xs:complexType name="DateRange">
  \<xs:sequence>
    \<xs:element name="MinDate" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="MaxDate" type="xs:string" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MaxDate*|The maximum date.<br /><br />**Note:** The date format should be specified as *"yyyyMMdd"*. For example December 31, 2050 should be specified as *"20501231"*.|*string*|
|*MinDate*|The minimum date.<br /><br />**Note:** The date format should be specified as *"yyyyMMdd"*. For example April 3, 2017 should be specified as *"20170403"*.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)

