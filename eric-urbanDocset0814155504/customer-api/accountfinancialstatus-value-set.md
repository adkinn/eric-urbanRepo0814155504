---
title: "AccountFinancialStatus Value Set"
ms.custom: ""
ms.date: "06/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 719aeb70-53ec-4dd9-83f2-093ff77d5252
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountFinancialStatus Value Set
Defines the possible financial status values of an account.

## Syntax

```xml
<xs:simpleType name="AccountFinancialStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Proposed" />
    <xs:enumeration value="PendingCreditCheck" />
    <xs:enumeration value="ClearFinancialStatus" />
    <xs:enumeration value="SoldToOnly" />
    <xs:enumeration value="CreditWarning" />
    <xs:enumeration value="Hold" />
    <xs:enumeration value="WriteOff" />
    <xs:enumeration value="TaxOnHold" />
    <xs:enumeration value="UserHold" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ClearFinancialStatus|The account is in good standing.|
|CreditWarning|Not used.|
|Hold|For an advertiser account, this status indicates that the account is past due. The service will not deliver the account’s ads until the account is settled. For a credit card account, this status indicates that the card has been declined three times.<br /><br />For a publisher account, this status indicates that the payout to the publisher is placed on hold by the customer service organization. The service continues to deliver the account’s ads.|
|PendingCreditCheck|Not used.|
|Proposed|For an advertiser account, this status indicates that the customer can add campaigns to the account; however, the service will not deliver the account’s ads.|
|SoldToOnly|Not used.|
|TaxOnHold|For a publisher account, this status indicates that the publisher has yet to provide a valid tax instrument. The service continues to deliver the account’s ads.|
|UserHold|For a publisher account, this status indicates that the payout to the publisher was placed on hold by publisher. The service continues to deliver the account’s ads.|
|WriteOff|The account is past due; however, collection is no longer being pursued. When this status is set, the `Status` element of the [Account](../customer-api/account-data-object.md) will be set to *Inactive*.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
