---
title: "CustomerFinancialStatus Value Set"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d678724f-6501-486a-8214-61aba95566e8
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomerFinancialStatus Value Set
Defines the possible financial status values of a customer.

## Syntax

```xml
<xs:simpleType name="CustomerFinancialStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="ProposalsOnly" />
    <xs:enumeration value="PendingCreditCheck" />
    <xs:enumeration value="ClearFinancialStatus" />
    <xs:enumeration value="SoldToOnly" />
    <xs:enumeration value="CreditHold" />
    <xs:enumeration value="CreditWarning" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ClearFinancialStatus|The customer is in good standing.|
|CreditHold|One of the customer’s accounts is past due.|
|CreditWarning|Not used.|
|PendingCreditCheck|The customer is undergoing a credit check as part of the customer sign-up process. The service will not deliver the customer’s ads until the credit check is complete. This status applies only to premium customers.|
|ProposalsOnly|Not used.|
|SoldToOnly|The customer is considered to be a credit risk. You cannot set the `BillToCustomerId` element of the [Account](../customer-api/account-data-object.md) for a customer that has this status. This status applies only to premium customers.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Customer](../customer-api/customer-data-object.md)

