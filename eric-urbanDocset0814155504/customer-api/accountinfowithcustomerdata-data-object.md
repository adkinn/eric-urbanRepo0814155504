---
title: "AccountInfoWithCustomerData Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cf03825-9396-483d-854e-c4c5ae4f0330
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountInfoWithCustomerData Data Object
Defines an object that contains information that identifies an account and the customer that manages or owns the account.

## Syntax

```xml
<xs:complexType name="AccountInfoWithCustomerData">
  <xs:sequence>
    <xs:element minOccurs="0" name="CustomerId" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="CustomerName" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="AccountId" type="xs:long" />
    <xs:element minOccurs="0" name="AccountName" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="AccountNumber" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="AccountLifeCycleStatus" type="tns:AccountLifeCycleStatus" />
    <xs:element minOccurs="0" name="PauseReason" nillable="true" type="xs:unsignedByte" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The system generated identifier of the account.|*long*|
|*AccountLifeCycleStatus*|The status of the account.|[AccountLifeCycleStatus](../customer-api/accountlifecyclestatus-value-set.md)|
|*AccountName*|The name of the account.|*string*|
|*AccountNumber*|The system generated account number that is used to identify the account in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The account number has the form X*nnnnnnn*, where *nnnnnnn* is a series of digits.|*string*|
|*CustomerId*|The system generated identifier of the customer that manages or owns the account.<br /><br />If this account is the result of an account match using the [FindAccountsOrCustomersInfo](../customer-api/findaccountsorcustomersinfo-service-operation.md), the customer identifier is that of the customer that owns the account. However, if the account is the result of a customer match, the customer identifier is that of the reseller that manages the account, if the account is managed by a reseller; otherwise, the identifier is that of the customer that owns the account.|*long*|
|*CustomerName*|The name of the customer that manages or owns the account.|*string*|
|*PauseReason*|A flag value that indicates who paused the account. The following are the possible values:<br /><br />1 – The user paused the account.<br /><br />2 – The billing service paused the account.<br /><br />4 – The user and billing service paused the account.|*unsignedByte*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[FindAccountsOrCustomersInfo](../customer-api/findaccountsorcustomersinfo-service-operation.md)

