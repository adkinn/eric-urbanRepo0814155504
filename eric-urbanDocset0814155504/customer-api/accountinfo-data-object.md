---
title: "AccountInfo Data Object"
ms.custom: ""
ms.date: "06/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 872de819-fb03-4d45-97b3-3570b343ac48
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountInfo Data Object
Defines an account identification object that contains information that identifies an account.

## Syntax

```xml
<xs:complexType name="AccountInfo">
  <xs:sequence>
    <xs:element minOccurs="0" name="Id" type="xs:long" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="Number" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="AccountLifeCycleStatus" type="tns:AccountLifeCycleStatus" />
    <xs:element minOccurs="0" name="PauseReason" nillable="true" type="xs:unsignedByte" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountLifeCycleStatus*|The status of the account.|[AccountLifeCycleStatus](../customer-api/accountlifecyclestatus-value-set.md)|
|*Id*|The system generated identifier of the account.|*long*|
|*Name*|The name of the account.|*string*|
|*Number*|The account number.|*string*|
|*PauseReason*|A flag value that indicates who paused the account. The following are the possible values:<br /><br />1 – The user paused the account.<br /><br />2 – The billing service paused the account.<br /><br />4 – The user and billing service paused the account.|*unsignedByte*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Account](../customer-api/account-data-object.md)  

