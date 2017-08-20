---
title: "AccountLifeCycleStatus Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66f1980c-b3dd-4180-9c71-70b5fea82fd4
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountLifeCycleStatus Value Set
Defines the possible status values of an account.

## Syntax

```xml
\<xs:simpleType name="AccountLifeCycleStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Draft" />
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Inactive" />
    \<xs:enumeration value="Pause" />
    \<xs:enumeration value="Pending" />
    \<xs:enumeration value="Suspended" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The account is active, which means that the account and its campaigns can be managed and its ads served.|
|Draft|The account is in a draft state. When you add an account, the system sets the status to Draft. After the system validates the payment instrument, the status changes to Active. You cannot add another account while the customer has an account in the Draft state.|
|Inactive|The account is inactive, which means that the system deleted the account.|
|Pause|For internal use only. You may update the account and its campaigns while the account is in the paused state.|
|Pending|For internal use only. You may update the account and its campaigns while the account is in the pending state.|
|Suspended|Your account has been suspended and no ads are eligible for delivery because of potentially fraudulent activity. <br />Please contact [Bing Ads Support](http://go.microsoft.com/fwlink/?LinkId=269631).|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]